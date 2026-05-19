---
title: "Interactive Tracker Setup"
date: "2026-05-18"
tags: []
---
# Everyday Wellbeing Hub — Project Tracker Setup

The Project Tracker section on [the hub](https://jbearup1981.github.io/cornerstone-wellbeing/) is a **statically rendered HTML table** styled to match the rest of the hub. The **source of truth for collaboration** is a Microsoft Excel workbook in Jason's [[OneDrive]] for Business — Capitol, Insight, and Nexus team members edit there. The hub view is refreshed manually from that workbook as status changes.

## Why this split

The earlier design embedded Excel Online directly via an iframe. That was killed because the embed looked out-of-place against the cream / navy / rust / DM Serif visual identity of the rest of the hub. The new pattern keeps the collaboration upside of [[OneDrive]] (anonymous edit, no login, native [[M365]] tool for partners) but presents the data to the audience in the hub's native style.

| Layer | Where | Who touches it |
|---|---|---|
| **Source of truth (editable)** | OneDrive Excel workbook | Capitol, Insight, Nexus team members |
| **Hub view (static)** | `index.html` `#tracker` section | Jason / Nexus (manual refresh from CSV or Excel) |
| **Seed data** | `artifacts/tracker-seed.csv` | Jason / whoever regenerates the hub view |

## File location

**[[OneDrive]] path:** `EverydayWellbeing/EverydayWellbeing_Project_Tracker.xlsx`

**Anonymous edit URL (shared with Capitol / Insight ops):**
`https://nexusbenefitsolutions-my.[[SharePoint|sharepoint]].com/:x:/p/jason/IQC0pvmc1hLhQoV0orwGIDpPAUNHgS_CXn_SVt12RpeW8Og`

This URL is wired into the **"Open editable tracker"** CTA button at the top of the tracker section on the hub. Anonymous edit — no Microsoft account required.

Item ID (for [[Graph API]] calls): `01WKQNOI5UU34ZZVQS4FBIK5FCXQDCAOSP`

## Schema

| Column | Type | Values |
|---|---|---|
| Task | Text | Task description (primary) |
| Owner | Dropdown | Nexus / Capitol / Insight / Amaze |
| Owner Detail | Text | Specific person(s), e.g. "Connie" or "[[Howard]] ↔ Connie" |
| Status | Dropdown | Open · In Flight · Delivered — Awaiting Review · Scheduled · Blocked · Future Phase · Done |
| Updated | Date | YYYY-MM-DD — partner updates when they touch their row |
| Notes | Long text | Free-form context, links, blockers |

Seed data lives in `artifacts/tracker-seed.csv` — 11 rows matching the hub tracker.

## How to update the hub display

The hub tracker is static HTML, so it does **not** auto-sync from Excel. When status changes meaningfully:

**Option A — Hand-edit (fastest for 1–2 row changes):**
1. Open `index.html` and jump to `#tracker`
2. Find the row(s) to update
3. Adjust the `<span class="status-pill ...">` class and label, and bump the `<td class="updated-cell">` date
4. Also update `artifacts/tracker-seed.csv` so the CSV stays consistent
5. Commit + push — GitHub Pages redeploys in ~30s

**Option B — Regenerate from CSV (clean rebuild):**
1. Update `artifacts/tracker-seed.csv` (all 11 rows live here)
2. Regenerate the table body in `index.html` from the CSV
3. Commit + push

## Available status pill classes

| CSS class | Visual | Use for |
|---|---|---|
| `.status-pill.open` | terracotta tint | "Open" |
| `.status-pill.in-flight` | terracotta tint | "In flight" |
| `.status-pill.scheduled` | slate / muted tint | "Scheduled" |
| `.status-pill.delivered` | teal tint | "Delivered — awaiting review" |
| `.status-pill.done` | navy tint | "Done" |
| `.status-pill.blocked` | red tint | "Blocked" |
| `.status-pill.future` | muted gray tint | "Future phase" |

## Available owner badge classes

| CSS class | Org | Color |
|---|---|---|
| `.owner-badge.nexus` | Nexus | terracotta |
| `.owner-badge.capitol` | Capitol | dark navy |
| `.owner-badge.insight` | Insight | violet / purple (~#5B2F8A) |
| `.owner-badge.amaze` | Amaze | teal |

## Granting edit access to a new person

Just share the **anonymous edit URL** (above) with them privately. No code change. No deploy. They click the link, the workbook opens in Excel Online, they edit their row, changes save automatically.

If you want to **revoke** anonymous edit access: [[OneDrive]] → file → Manage Access → remove the "Anyone with the link can edit" entry. You can replace it with named-person edit invites if the policy ever changes.

## Future enhancement — Live sync from Excel

A future iteration could read the workbook via [[Graph API]] at build time (or via a GitHub Action on a cron) and regenerate the static HTML table automatically. Not built for this session — manual refresh is fine for the Friday delivery cadence.

## Files

- `index.html` — tracker section at `#tracker` (static HTML table + CTA button)
- `artifacts/tracker-seed.csv` — 11-row seed data (source for the hub table)
- This file (`INTERACTIVE-TRACKER-SETUP.md`) — setup + maintenance reference
