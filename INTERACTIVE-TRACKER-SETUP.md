# Cornerstone Hub — Interactive Project Tracker Setup

The Project Tracker section on [the hub](https://jbearup1981.github.io/cornerstone-wellbeing/) is now a live, partner-editable view embedded from **Google Sheets**. Until you wire up the Sheet (5-minute one-time step below), the page falls back to the previous static table — so the hub is never broken, just less interactive.

## Why Google Sheets

| Option | Friction for Capitol / Insight | Verdict |
|---|---|---|
| **Google Sheets** | None — "Anyone with the link" can edit, no account creation, no invites | **Chosen** |
| Airtable | Free to view, but editing requires an Airtable account for each partner | Too much friction |
| Notion (via MCP) | Public pages are read-only for non-members; edit needs invited guests | Wrong tool for cross-org editing |
| GitHub Issues | Partners need GitHub accounts | Nonstarter |

Jason already runs Google Workspace. Capitol and Insight ops people can edit a status cell from a phone in 10 seconds with no login.

## 5-Minute Setup (Jason does this once)

### 1. Create the Sheet from the seed CSV
- Open Google Drive → **New → Google Sheets → Blank spreadsheet**
- **File → Import → Upload** → drag `cornerstone-wellbeing/artifacts/tracker-seed.csv`
- Import location: **Replace spreadsheet** · Separator: **Comma** · Convert text to numbers/dates: **Yes**
- Rename the file: **Cornerstone Well-Being — Live Tracker**
- Rename the tab: **Tracker**

### 2. Format for readability (optional but recommended, ~2 min)
- Freeze row 1: View → Freeze → 1 row
- Bold row 1
- Format column D (Status) → Data → Data validation → "Dropdown" with values: `Open`, `In Flight`, `Delivered — Awaiting Review`, `Scheduled`, `Blocked`, `Future Phase`, `Done`
- Format column E (Updated) → Format → Number → Date
- Optional: conditional formatting on Status column for color pills (Open = orange, Done = green, Blocked = red, Future Phase = gray)

### 3. Publish for embed (read-only view)
- **File → Share → Publish to web**
- Link tab: choose the **Tracker** sheet (not "Entire Document")
- Format: **Web page**
- Click **Publish** → confirm
- Copy the published URL — looks like `https://docs.google.com/spreadsheets/d/e/<KEY>/pubhtml?gid=0&single=true`

### 4. Wire the embed into the hub
- Open `cornerstone-wellbeing/index.html`
- Search for `TRACKER_EMBED_URL` (one occurrence in the tracker section)
- Uncomment the `<iframe>` block (remove the surrounding `<!--` and `-->`)
- Replace `TRACKER_EMBED_URL` with the published URL from step 3
- Optionally delete the `<!-- BEGIN: static fallback -->` block — or leave it; it'll be visually replaced by the iframe
- Commit + push: the GitHub Pages site updates within ~60 seconds

### 5. Grant edit access (private — do NOT publish this link)
- Back in the Sheet: **Share** (top right)
- General access: **Anyone with the link** → role **Editor**
- Copy the link
- Send privately to:
  - Brenda Manning (Capitol liaison)
  - Connie (Capitol Group)
  - Howard Lancaster (Insight Benefits) + his team — Brenda Brown, Lindsay Kepley, Breanne Marsiglia
  - Dave Silverstein (Amaze Health) if relevant
- Tell them: "Find your row, update Status + Notes + Updated date. Page on the hub refreshes within a minute."

**Important:** the embedded `/pubhtml` URL on the hub is **read-only**. The editable link is separate and only goes to people you trust. The hub viewer never sees the edit link.

## Schema

| Column | Type | Values |
|---|---|---|
| Task | Text | The task description (primary) |
| Owner | Single select | Nexus / Capitol / Insight / Amaze |
| Owner Detail | Text | Specific person(s), e.g. "Connie" or "Howard ↔ Connie" |
| Status | Single select | Open · In Flight · Delivered — Awaiting Review · Scheduled · Blocked · Future Phase · Done |
| Updated | Date | YYYY-MM-DD — partner updates when they touch their row |
| Notes | Long text | Free-form context, links, blockers |

Seed data lives in `artifacts/tracker-seed.csv` — 11 rows matching the original static tracker.

## Maintenance

- **Adding a new task:** add a row in the Sheet. The embed picks it up automatically.
- **Removing a task:** delete the row. Same.
- **Re-publishing isn't needed** after the first publish — Google keeps the published view in sync with the live Sheet (1-minute cache).
- **Pause an embed:** File → Share → Publish to web → "Stop publishing". The iframe will go blank — that's why the static fallback exists.
- **Force a manual refresh of the published view:** Publish to web → "Automatically republish when changes are made" should already be on.

## Granting edit access to a new person

Just share the editable Sheet URL with them. No code change. No deploy.

If you want to **revoke** access from someone specific, change General access to "Restricted" and add named editors instead — same Share dialog.

## Fallback Plan (if the embed breaks)

The static `<table class="tracker-table">` is still in `index.html` inside `.tracker-embed-fallback`. If the iframe ever 404s or Google retires `/pubhtml`:

1. Remove the `<iframe>` block from the tracker section
2. The fallback table renders automatically
3. Update the static table by hand for the time being
4. (Optional) Switch the embed to Airtable: re-import `tracker-seed.csv`, create a free Airtable base, get the embed iframe from Share → Embed this view, paste into `index.html`

## Files

- `index.html` — tracker section at `#tracker`, iframe + fallback wrapper
- `artifacts/tracker-seed.csv` — 11-row seed for the Sheet
- This file (`INTERACTIVE-TRACKER-SETUP.md`) — setup + maintenance reference
