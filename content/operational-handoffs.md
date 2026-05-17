---
title: "Operational Handoffs"
date: "2026-05-17"
tags: []
---
# Operational Handoffs — Cornerstone Well-Being Program

This document defines the operational seams between Nexus Benefit Solutions, Capitol Group / CEHAS, and Insight Benefits for the Cornerstone Well-Being Program (Powered by [[Amaze_Health|Amaze Health]]). It is intended as a working spec for the Capitol ops team. Section content reflects the operational substance discussed on the Monday call with Connie.

---

## Eligibility File Format + Invoicing Handoff

The eligibility-to-invoicing flow runs on a weekly cadence aligned to the client's payroll cycle:

1. The Nexus system produces and maintains the eligibility file for each participating employer.
2. Capitol's CEHAS system ingests the eligibility file weekly.
3. CEHAS generates the corresponding invoice and initiates ACH collection from the employer.

### Required fields in the eligibility file

- Employee identifiers (employer ID, employee ID, SSN or masked equivalent per agreed standard)
- Plan election
- Enrollment status (active, pending, termed)
- Opt-out flag
- Non-qualified flag
- Employee email address
- Dependent information (where applicable to the elected coverage)
- Coverage effective date
- Termination date, if applicable

### Delivery method — open decision

Two delivery options are on the table. Both are workable; the decision is operational preference on Capitol's side:

- **Option A — CSV push.** Nexus delivers a CSV file to Capitol's intake on the agreed weekly cadence.
- **Option B — System access.** Capitol is granted read access to the live Nexus eligibility data and pulls on its own schedule.

This decision is pending. Nexus will produce a sample eligibility CSV deliverable for CEHAS review to support the conversation.

---

## Contract Package & E-Sign Flow

Three core contracts are executed at employer onboarding:

- **Administrative Services Agreement (ASA)** — defines the operational and administrative relationship between the employer and the program administrator.
- **Compliance Protection Document** — captures the regulatory obligations and the compliance coverages provided through the program.
- **Request for Coverage** — the employer's formal enrollment instrument into the program.

### CEHAS e-sign workflow

Signatures are sequenced, not parallel:

1. Employer signs first.
2. CEHAS countersigns.
3. Insurer countersigns.

### Distribution after execution

Once fully executed, copies of the contract package are distributed to:

- The client (employer)
- Nexus Benefit Solutions
- CEHAS
- The insurance carrier

### Pending items

- Connie to provide the latest versions of the ASA, Compliance Protection document, and Request for Coverage.
- CEHAS and insurer signature contact details to be confirmed by Connie.

---

## Payroll System Support Matrix

Nexus and Insight are set up to handle the payroll systems below. "Standard" means the system supports a clean export Nexus can ingest directly into the structured upload format. "Edge case" means the system requires a manual workflow.

| System | Handling |
|---|---|
| ADP (Workforce Now) | Standard — export report, structured upload format |
| I-Solved | Standard |
| Paycom | Standard |
| Paychex | Standard |
| Kronos / UKG | Standard (encountered less frequently) |
| ADP Run | Edge case — manual self-service export required |
| Gusto | Edge case — manual handling |
| Heartland | Edge case — manual handling |
| [[QuickBooks]] Payroll | Edge case — manual handling, often used by smaller groups outside Nexus profile |

Nexus is not building integrations for every payroll system on the market — that would explode scope without proportional return. Standard systems get clean exports and flow through the ingestion pipeline. Edge cases get manual workflows, with the same audit and approval gates applied at the end.

The edge-case systems tend to correlate with smaller and less operationally mature employers. That correlation is itself a qualification signal and informs how groups are scoped during the proposal stage.

[[Brenda|Brenda Manning]] is compiling the prioritized payroll vendor list. That work is in flight and will refine this matrix as new systems are encountered in production.

### Implementation flow context

For reference, the broader implementation flow that feeds this matrix:

- The Nexus system builds proposals and auto-converts acceptances into paperwork.
- Wendy runs payroll kickoff calls with the employer and builds payroll reports where required.
- The Nexus system ingests payroll registers and compares them to the census to surface discrepancies.
- A human-in-the-loop step is retained for the final payroll change audit and approval — automated comparison surfaces the deltas, a person signs off.

---

## Edge Cases & Compliance Notes

- **Accident coverage grace.** Accident coverage carries a one-payroll-cycle grace period after the last premium payment. Termination handling on the eligibility file should reflect this so invoicing and coverage status stay aligned.
- **High-earner Social Security tax cliff.** The Nexus quoting system flags high-earner scenarios during proposal generation where the Social Security wage base affects the projected FICA savings. This prevents the program from being presented to an employee population in a way that overstates tax savings for earners above the wage base.
