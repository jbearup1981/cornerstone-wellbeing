---
title: "Interactive Tracker Setup"
date: "2026-05-17"
tags: []
---
# Cornerstone Hub — Interactive Project Tracker Setup

The Project Tracker section on [the hub](https://jbearup1981.github.io/cornerstone-wellbeing/) is a live, partner-editable view embedded from **Microsoft Excel Online** (the workbook lives on Jason's [[OneDrive]] for Business). If the iframe ever fails to load, the page falls back to a static snapshot table — so the hub is never broken, just less interactive.

## Why Excel Online / OneDrive

| Option | Friction for Capitol / Insight | Verdict |
|---|---|---|
| **Excel Online ([[M365]])** | Anonymous edit link — no Microsoft account required, no invites. Capitol and Insight both run on M365 so it's already a native tool. | **Chosen** |
| Google Sheets | Capitol and Insight live in M365; introducing Google Drive added friction. | Replaced |
| Airtable | Free to view, but editing requires an Airtable account for each partner | Too much friction |
| [[Notion]] | Public pages are read-only for non-members; edit needs invited guests | Wrong tool for cross-org editing |
| GitHub Issues | Partners need GitHub accounts | Nonstarter |

Capitol and Insight ops people can edit a status cell from a phone in 10 seconds with no login. Jason controls the file from his [[OneDrive]].

## File Location

**[[OneDrive]] path:** `CornerstoneProgram/Cornerstone_Project_Tracker.xlsx`

**Direct web URL (Jason's owner view):**
`https://nexusbenefitsolutions-my.[[SharePoint|sharepoint]].com/personal/jason_nexusbenefitsolutions_com/_layouts/15/Doc.aspx?sourcedoc=%7B9CF9A6B4-12D6-42E1-8574-A2BC06203A4F%7D&file=Cornerstone_Project_Tracker.xlsx`

Item ID (for [[Graph API]] calls): `01WKQNOI5UU34ZZVQS4FBIK5FCXQDCAOSP`

## Share Links (Generated via Microsoft Graph)

| Link | Scope | Used For |
|---|---|---|
| **Anonymous Edit** | `anonymous` / `edit` | Sent privately to Capitol + Insight ops team. Do NOT publish. |
| **Anonymous View** | `anonymous` / `view` | Used as the iframe `src` on the public hub (with `?action=embedview`). |

Microsoft Graph does not currently support `type: embed` for [[SharePoint]] Online business tenants (returns `notSupported`). The workaround is to use the anonymous view-only share URL and append `?action=embedview&wdAllowInteractivity=True&wdHideGridlines=True` — this is the same Doc.aspx embedview that Microsoft serves via the "Embed" UI in [[OneDrive]].

## How the Workbook Is Built

The file is generated from `artifacts/tracker-seed.csv` (11 seed rows). Styling applied:

- **Header row:** forest green (#2D5F3F) fill, white bold text, frozen
- **Status column (D):** color-coded fill per status value + data-validation dropdown (Open · In Flight · Delivered — Awaiting Review · Scheduled · Blocked · Future Phase · Done)
- **Owner column (B):** dropdown (Nexus · Capitol · Insight · Amaze)
- **Auto-filter** on the header row
- **Column widths + wrap text** sized for the Notes column

Build script (one-shot, lives in `/tmp/build_and_upload.py` during the setup session): converts CSV → styled XLSX with `openpyxl`, uploads to [[OneDrive]] via Graph (`PUT /me/drive/root:/path:/content`), creates anonymous edit + view links via `POST /me/drive/items/{id}/createLink`. Token pulled from `~/.config/[[M365|m365]]-mcp/token_cache.json` — needs `Files.ReadWrite.All` + share-link permissions.

## 5-Minute Setup (one-time, already done)

1. ✅ CSV → styled XLSX
2. ✅ Upload to [[OneDrive]] at `/CornerstoneProgram/Cornerstone_Project_Tracker.xlsx`
3. ✅ Anonymous edit link created (private — see Vault)
4. ✅ Anonymous view link created and wired into the iframe on `index.html`
5. ✅ Static fallback table preserved in HTML (hidden via `:has(iframe)` CSS when the embed loads)

## Schema

| Column | Type | Values |
|---|---|---|
| Task | Text | The task description (primary) |
| Owner | Dropdown | Nexus / Capitol / Insight / Amaze |
| Owner Detail | Text | Specific person(s), e.g. "Connie" or "[[Howard]] ↔ Connie" |
| Status | Dropdown | Open · In Flight · Delivered — Awaiting Review · Scheduled · Blocked · Future Phase · Done |
| Updated | Date | YYYY-MM-DD — partner updates when they touch their row |
| Notes | Long text | Free-form context, links, blockers |

Seed data lives in `artifacts/tracker-seed.csv` — 11 rows matching the original static tracker.

## Maintenance

- **Adding a new task:** open the workbook (Jason's [[OneDrive]] or via the edit link), add a row. The embedded iframe picks it up on the next page load (Excel Online caches ~1 minute).
- **Removing a task:** delete the row. Same.
- **Re-uploading isn't needed** — the file lives in OneDrive, edits sync instantly to the embed view.
- **Pause the embed:** in OneDrive, right-click the file → Manage Access → revoke the anonymous view link. The iframe will go blank; the static fallback will not appear automatically (it's hidden by the `:has(iframe)` rule). To restore the fallback in that case, remove the `<iframe>` tag from `index.html` and commit.

## Granting edit access to a new person

Just share the **anonymous edit URL** privately with them. No code change. No deploy. They click the link, the file opens in Excel Online in their browser, they edit their row, changes save automatically.

If you want to **revoke** anonymous edit access, go to [[OneDrive]] → file → Manage Access → remove the "Anyone with the link can edit" entry. You can replace it with named-person edit invites (Brenda, Connie, [[Howard]], Brenda Brown, Lindsay Kepley, Breanne Marsiglia) if the org policy demands it later.

## Tenant Policy Notes

- Jason's tenant **allows anonymous edit links** (confirmed: `createLink` with `scope: anonymous` + `type: edit` returned 201). If a future tenant policy change blocks anonymous edits, fall back to:
  1. Anonymous view link (still works for the embed)
  2. Per-person edit invites for the named partners
  3. "Anyone in [tenant] with the link can edit" — but this requires partner emails to be added as guest users in the tenant first.
- `type: embed` is **not supported** on [[SharePoint]] Online business tenants via Graph (returns `notSupported`). The Doc.aspx `?action=embedview` URL accomplishes the same thing.

## Fallback Plan (if the embed breaks)

The static `<table class="tracker-table">` is still in `index.html` inside `.tracker-embed-fallback`. The CSS rule `.tracker-embed-wrap:has(iframe) .tracker-embed-fallback { display: none; }` hides it while the iframe is present.

If the iframe ever 404s or Microsoft retires the embed URL format:

1. Remove the `<iframe>` block from the tracker section in `index.html`
2. The fallback table renders automatically (the `:has(iframe)` rule no longer matches)
3. Update the static table by hand for the time being
4. (Optional) re-run the upload script with a fresh share link

## Files

- `index.html` — tracker section at `#tracker`, iframe + fallback wrapper
- `artifacts/tracker-seed.csv` — 11-row seed for the workbook
- This file (`INTERACTIVE-TRACKER-SETUP.md`) — setup + maintenance reference
