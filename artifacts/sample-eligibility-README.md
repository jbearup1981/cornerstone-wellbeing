---
title: "Sample Eligibility README"
date: "2026-05-17"
tags: []
---
# Cornerstone Well-Being Program — Eligibility File Specification

Companion documentation for `sample-eligibility-acme-manufacturing.csv`. This artifact is a sample of the weekly eligibility extract Nexus Benefit Solutions will deliver to Capitol Group for ingestion into the CEHAS system. CEHAS uses this file to drive invoice generation and ACH reimbursement.

**Program:** Cornerstone Well-Being Program (Section 125 fixed-indemnity wellbeing plan with virtual primary care via [[Amaze_Health|Amaze Health]])
**Producer:** Nexus Benefit Solutions
**Consumer:** Capitol Group / CEHAS
**Format:** CSV, UTF-8, comma-delimited, header row required, RFC 4180 quoting

---

## Column Specification

| # | Column | Type | Allowed Values / Format | Description |
|---|--------|------|------------------------|-------------|
| 1 | `employee_id` | string | `<group-prefix>-NNNN` | Internal employer payroll ID. Stable, never reused. Primary key for ongoing tracking. |
| 2 | `ssn_last4` | string | 4 digits | Last 4 of SSN. Used only as a secondary match key. Full SSN is NOT transmitted in this file. |
| 3 | `first_name` | string | free text | Legal first name. |
| 4 | `last_name` | string | free text | Legal last name. Hyphens and apostrophes allowed. |
| 5 | `date_of_birth` | date | `YYYY-MM-DD` | Required for all rows. Used for member matching and Amaze enrollment. |
| 6 | `plan_election` | enum | `Plan 1500`, `Plan 1200`, `Plan 900`, `Plan 700`, `Plan 500`, `Plan 350` | The 6 plan levels. For Opt-Out, Pending, Non-Qualified, or Terminated rows this reflects the elected/intended plan; premium will be zero. |
| 7 | `enrollment_status` | enum | `Enrolled`, `Opt-Out`, `Non-Qualified`, `Pending`, `Terminated` | Current eligibility state. Drives whether CEHAS bills/reimburses for the period. |
| 8 | `effective_date` | date | `YYYY-MM-DD` | Date of program enrollment or status assignment. |
| 9 | `term_date` | date | `YYYY-MM-DD` or empty | Populated only when `enrollment_status = Terminated`. Last day of coverage. |
| 10 | `opt_out_flag` | bool | `Y` / `N` | `Y` indicates employee declined enrollment. Mutually exclusive with `non_qualified_flag = Y`. |
| 11 | `non_qualified_flag` | bool | `Y` / `N` | `Y` indicates employee was screened out of the program by Nexus pre-tax modeling. |
| 12 | `non_qualified_reason` | enum | `LOW_WAGES`, `W4_DEPENDENTS_MAX`, `NEGATIVE_NET_IMPACT`, `OTHER`, or empty | Reason code populated only when `non_qualified_flag = Y`. |
| 13 | `email` | string | RFC 5322 | Required per Connie. Used by Capitol / Amaze for member outreach and account activation. |
| 14 | `phone` | string | `NNN-NNNN` or `NNN-NNN-NNNN` | Mobile preferred. Used for Amaze SMS engagement. |
| 15 | `dependent_count` | int | 0–10 | Spouse + children covered under the program. Informational; program is employee-only premium structure. |
| 16 | `group_name` | string | free text | Employer legal/DBA name. |
| 17 | `group_id` | string | `<CLIENT>-<STATE>-NNN` | Nexus-assigned group identifier. Stable across renewals. |
| 18 | `pay_frequency` | enum | `Weekly`, `Biweekly`, `Semimonthly`, `Monthly` | Drives CEHAS billing cadence and reimbursement timing. |
| 19 | `gross_pay` | decimal | dollars, 2 places | Most recent per-period gross pay used to validate qualification. |
| 20 | `w4_filing_status` | enum | `Single`, `Married Filing Jointly`, `Head of Household`, `Married Filing Separately` | Federal W4 filing status. |
| 21 | `w4_dependents` | int | 0–10 | W4 claimed dependents (count, not dollar amount). |
| 22 | `pretax_deduction` | decimal | dollars, 2 places | Per-pay-period pre-tax premium deducted from employee paycheck. Zero for Opt-Out / Non-Qualified / Pending / Terminated. |
| 23 | `reimbursement_amount` | decimal | dollars, 2 places | Per-pay-period indemnity benefit reimbursed via ACH. By program design equals `pretax_deduction` so net impact is zero. |
| 24 | `net_paycheck_impact` | decimal | dollars, 2 places | Reimbursement minus pretax_deduction adjusted for tax savings. For enrolled members on this plan, net impact is `0.00` (program is paycheck-neutral pre-tax). |

---

## File Naming Convention

```
cornerstone-eligibility_<group-id>_<YYYY-MM-DD>.csv
```

Example: `cornerstone-eligibility_ACME-MI-001_2026-05-16.csv`

- `<group-id>` matches the `group_id` column value
- `<YYYY-MM-DD>` is the file generation date (typically the Friday of the payroll week)
- One file per group per week. Multi-group employers will receive one file per group_id.

---

## Delivery Cadence

- **Frequency:** Weekly, aligned with the client's payroll cycle.
- **Trigger:** File is generated the day after each payroll close (typically Friday for Biweekly clients, Monday for Weekly clients).
- **First file:** Full census on/before the go-live date (`effective_date` for the bulk of enrolled members).
- **Subsequent files:** Full census (not delta) every week — CEHAS treats each file as authoritative state for that group as of the file generation date.
- **Off-cycle:** Mid-cycle terminations or new hires are reflected in the following week's file. Term-date and effective-date columns carry the actual event date.

---

## PII Handling & Secure Delivery

This file contains PII subject to GLBA and (where applicable) HIPAA-adjacent handling standards:

- **PII fields:** `ssn_last4`, `first_name`, `last_name`, `date_of_birth`, `email`, `phone`, `gross_pay`, `w4_filing_status`, `w4_dependents`
- **Full SSN is NOT transmitted.** Only the last 4 digits, as a secondary match key.
- **At rest (Nexus):** Files stored in restricted-access [[OneDrive]] folder with audit logging; retained 7 years per recordkeeping policy.
- **In transit (proposed — pending Capitol/CEHAS IT confirmation):**
  1. **Preferred:** SFTP push to a Capitol-designated endpoint with key-based auth. Nexus will provide a public SSH key for whitelisting.
  2. **Acceptable alternative:** Encrypted email (S/MIME or password-protected ZIP with the password delivered out-of-band via phone/SMS to Connie or a CEHAS-designated recipient).
- **At rest (Capitol/CEHAS):** Capitol's standard PII handling controls apply. Nexus requests confirmation of encryption-at-rest and access-logging on the ingest landing zone.
- **No transmission via plain email.** Files containing this PII set will not be sent as unencrypted attachments to standard email.
- **Breach notification:** Either party will notify the other within 24 hours of any suspected unauthorized access.

---

## Open Items for Capitol / CEHAS Review

1. Confirm SFTP vs. encrypted email as the primary delivery channel.
2. Confirm whether CEHAS prefers `ssn_last4` or `employee_id` as the primary match key.
3. Confirm CEHAS handling of `Pending` rows — bill on file receipt, or wait for status to flip to `Enrolled`?
4. Confirm whether `Terminated` rows should continue to appear in subsequent files (e.g., for 30/60/90 days) or drop out after the file containing the term_date.
5. Confirm acceptable file size / row count ceiling per file (relevant for larger groups in the future).
