---
title: "README"
date: "2026-05-17"
tags: []
---
# Quoting Platform Screenshots

Captured from the live [[NexHub CRM]] quoting platform (`[[NexHub CRM|nexhub]].nexusbenefitsolutions.com/tools/proforma/`) on May 16, 2026. All shots use the **Harloff Manufacturing Company** demo group (quote ID 12, flagged "demo" in the CRM) — synthetic group built for the Insight team demo and Capitol walkthroughs, not a real client.

## Inventory

| # | File | Screen | Source URL |
|---|------|--------|-----------|
| 1 | `01-quote-builder.png` | New quote creation page (org attached, name, pay frequency, state, demo flag) | `/tools/proforma/new?org_id=2521` |
| 2 | `02-census-audit.png` | Eligibility Analysis History — list of every payroll cycle audited, with employee counts, qualified counts, changes, status | `/tools/proforma/12/eligibility-analysis` |
| 3 | `03-eligibility-cheat-sheet.png` | Income/W-4 lookup table by filing status (Standard, $2k dependents, $4k dependents) across Plan 1500/1200/900 and Single/Married/Head of Household | Cheat sheet panel on `/tools/proforma/12` |
| 4 | `04-proforma.png` | Full pro-forma proposal — cover, employer savings + per-paycheck deduction summary, employer details, FAQ, team page | `/tools/proforma/12/proposal/snapshot/audited` |
| 5 | `05-service-screen.png` | Live group service view — enrollment management, pending/accepted counts, next payroll cycle, audit launch | `/tools/proforma/12` |
| 6 | `06-weekly-audit.png` | Single-cycle payroll audit detail — qualified/changed/new/dropped counts, Payroll Administrator Action Report, per-employee eligibility analysis with before/after paychecks | `/tools/proforma/12/eligibility-analysis/121` |
| 7 | `07-email-output.png` | Auto-generated email-to-payroll-admin modal — to/cc, subject, body with cycle changes summary, send action | "Email to Payroll Admin" button on cycle audit detail |

## PII / Demo Data Notes

- All shots use the **Harloff Manufacturing demo group** (`org_id=2521`, quote 12, marked `demo`).
- Employee names visible in shots 6 (per-employee eligibility table) appear synthetic but were not individually verified — if any appear questionable before publishing, redact via post-capture editing.
- Shot 1 was originally captured against a real client (Sena Info Technologies) and re-captured against Harloff before being saved.
- No SSNs, real wages, or sensitive client identifiers appear in any shot.

## Capture Method

Driven via raw Chrome DevTools Protocol over the Comet debug port (`localhost:9222`), reusing the existing authenticated [[NexHub CRM|NexHub]] tab. Source script: `5-technology/browser-automation/cwb_shoot.mjs`. Microsoft SSO completed silently via Comet's [[LastPass]] extension. Full-page captures use `Emulation.setDeviceMetricsOverride` + `captureBeyondViewport`.
