# Cornerstone Well-Being Program — Step-by-Step Runbook Detail

Operational detail for every step in every flow diagram on the project hub. Each block is written for the Capitol Group ops team (Scott, Connie, CEHAS IT) primary, with Insight Benefits secondary. Read as an internal operations runbook — no marketing language.

---

## Diagram 1 — Sales-to-Handoff Funnel

### Step 1.1 — Discovery

- **Owner:** Nexus — Jason plus the originating advisor (Ken, Cam, Tom, or a GA-channel advisor)
- **What happens:** First substantive conversation with the prospect. The advisor learns the business — headcount, industry, payroll system, turnover pattern, benefit philosophy, who owns HR and payroll internally. Jason sits on this call personally; the design of the sales function is that the owner is on every deal during qualification, not after.
- **Inputs:**
  - Prospect referral or warm intro
  - Basic company profile (headcount, industry, location)
  - Any prior benefit history the advisor already knows
- **Outputs:**
  - Discovery notes captured in NexHub CRM
  - A first read on whether the group fits the Nexus Standard profile
  - Decision to advance to Qualification or to redirect to the Capitol-routed bucket
- **Duration:** 30–60 minutes per prospect
- **Tools:** NexHub CRM, Microsoft Teams or in-person meeting, Outlook calendar
- **Dependencies:** Prospect agrees to a conversation; advisor has cleared the meeting with Jason
- **What can go wrong:** Advisor goes too deep into product before establishing fit, which forces a harder qualification reversal later. Discovery notes get stored in the advisor's head instead of the CRM, so handoff suffers downstream.
- **Escalation:** Jason directly — he is already on the call

### Step 1.2 — Qualification

- **Owner:** Nexus — Jason (final call), supported by the originating advisor
- **What happens:** The deal is measured against the Nexus Standard profile: 50–1,000 employees (sweet spot 50–300), stable workforce, qualifying wages, a real payroll function, and operational maturity. This is deliberately a tight filter. Groups that do not clear it either route to the Capitol bucket on reduced Nexus comp, or do not move forward at all.
- **Inputs:**
  - Discovery notes
  - Prospect-provided headcount, turnover read, payroll system, and industry
  - Two-bucket routing criteria
- **Outputs:**
  - Bucket decision (Nexus Standard, Capitol-routed, or pass)
  - Documented rationale in CRM
  - Green light to request payroll data
- **Duration:** 15–30 minutes of decision work, often inside the discovery call
- **Tools:** NexHub CRM, two-bucket routing reference on the hub
- **Dependencies:** Discovery complete; enough data to assess against the profile
- **What can go wrong:** Forcing a borderline group through Standard to keep the deal alive. The Davenport adjunct-faculty story is the cautionary tale — population volatility downstream comes from qualification slippage upstream.
- **Escalation:** Jason has final call; if the advisor disagrees, escalate same-day rather than push through

### Step 1.3 — Payroll Report Build

- **Owner:** Nexus — Wendy or Shea (Implementation), supported by client HR/payroll contact
- **What happens:** Wendy or Shea pulls the current payroll register and the W-4 filing status report directly with the client's payroll owner. This is technically still sales, but it is the first place sales bleeds into implementation. The two files feed the quoting tool's AI census audit.
- **Inputs:**
  - Client's current payroll register (export from ADP, I-Solved, Paycom, Paychex, Kronos, or a manual export from an edge-case system)
  - W-4 filing status report
  - Read access to or a screen-share with the client's payroll system, where granted
- **Outputs:**
  - Cleaned payroll dataset loaded into the Nexus quoting platform
  - Initial flag list (qualification, W-4 discrepancies, wage-band edge cases)
- **Duration:** 30–90 minutes of live work, plus async cleanup
- **Tools:** Client payroll system, Nexus quoting platform, secure file transfer (email or SharePoint), Teams screen-share
- **Dependencies:** Qualification passed; client has identified the payroll owner and authorized the data pull
- **What can go wrong:** Client payroll owner is slow to respond, dragging out the funnel. Edge-case payroll systems (ADP Run, Gusto, Heartland, QuickBooks) require manual export, which is error-prone if the admin is junior.
- **Escalation:** Wendy / Shea → Jason if the client is non-responsive; advisor re-engages the relationship

### Step 1.4 — Quote Generation

- **Owner:** Nexus — Wendy/Shea operate the platform; Jason reviews
- **What happens:** The Nexus quoting platform runs the AI census audit, flags qualification issues, surfaces W-4-versus-paycheck discrepancies, builds an eligibility cheat sheet, and generates per-employee before-and-after paycheck views. Output is a proposal-ready dataset.
- **Inputs:**
  - Cleaned payroll dataset from Step 1.3
  - Selected plan tier (Plan 1500 / 1200 / 900 — subject to Capitol confirmation on Cornerstone benefit schedule)
  - Current IRS Pub 15-T tax tables (loaded in the platform)
- **Outputs:**
  - Per-employee before/after paycheck statements
  - Employer-level FICA savings summary
  - Eligibility cheat sheet (who qualifies, who doesn't, who's borderline)
  - Discrepancy report (W-4 vs. actual withholding)
- **Duration:** 15–30 minutes of platform time; longer if the dataset needs cleanup passes
- **Tools:** Nexus quoting platform (Replit-built, integrated in NexHub CRM)
- **Dependencies:** Step 1.3 complete and data cleaned; plan tier confirmed
- **What can go wrong:** Bad source data flows through to bad output. High-earner Social Security wage-base cases need the platform's flag to fire correctly so projected savings aren't overstated.
- **Escalation:** Wendy/Shea → Jason for any flagged anomaly before the proposal goes out

### Step 1.5 — Proposal

- **Owner:** Nexus — Jason plus originating advisor; Wendy/Shea support with materials
- **What happens:** The quoting output is packaged into the formal proposal. Employer sees the FICA savings model and admin fee structure; each employee gets a personalized before/after statement. The presentation is intentionally transparent — if the data tells a borderline story, that story gets told, not buried.
- **Inputs:**
  - Quote output from Step 1.4
  - Employer proposal PDF and per-employee packet zip from the platform
  - Plan summary materials (Amaze Health, indemnity schedule, opt-out path)
- **Outputs:**
  - Employer-facing proposal delivered
  - Employee-facing packet ready for distribution after sign
  - Documented client questions / objections
- **Duration:** 60–90 minute proposal meeting; 1–3 weeks of client-side review thereafter
- **Tools:** Nexus quoting platform exports, PDF, Outlook, Teams
- **Dependencies:** Step 1.4 complete and reviewed by Jason
- **What can go wrong:** Client gets the proposal and goes dark. Internal champion (CFO or HR director) loses momentum if there isn't a clear next step on calendar. Compliance questions surface late because Capitol's contract package wasn't on the table early.
- **Escalation:** Originating advisor owns follow-up cadence; Jason re-engages at the principal level if the deal stalls past two weeks

### Step 1.6 — Sign

- **Owner:** Nexus — originating advisor closes; Jason countersigns Nexus-side
- **What happens:** Employer signs the Request for Coverage and the surrounding contract package (ASA, Compliance Protection Document). The employer signature is the first step in the CEHAS e-sign sequence — see Diagram 5. Both sides go in eyes wide open; if anything in the conversation says this isn't a fit, the deal does not move.
- **Inputs:**
  - Final proposal accepted by the employer
  - Contract package (ASA, Compliance Protection, Request for Coverage) — currently pending from Connie
  - CEHAS e-sign envelope configured
- **Outputs:**
  - Employer signature captured
  - Deal status flipped to Won in NexHub
  - Trigger sent to CEHAS for countersignature (Step 5.2)
- **Duration:** Same-day to one week after proposal acceptance
- **Tools:** CEHAS e-sign system, NexHub CRM, Outlook
- **Dependencies:** Proposal accepted; contract templates received from Connie; CEHAS and insurer signature contacts confirmed
- **What can go wrong:** Contract templates not yet finalized between Connie's team and Nexus, causing a stall at the signature stage. Employer's counsel asks for red-lines that need to round-trip through Capitol.
- **Escalation:** Jason → Brenda Manning → Scott / Connie for any contract red-line that requires Capitol-side change

### Step 1.7 — Handoff to Implementation

- **Owner:** Nexus — Wendy or Shea (Implementation) receives; Jason owns the warm handoff
- **What happens:** With the employer signed, the file formally transitions from sales to implementation. Because Wendy/Shea were already in the payroll report build during sales, the handoff is a continuation, not a cold transfer. The implementation kickoff call is scheduled within five business days of signature.
- **Inputs:**
  - Signed contract package
  - Quoting platform dataset (already loaded)
  - Sales notes from CRM
  - Client payroll owner contact and any access already established
- **Outputs:**
  - Implementation file opened
  - Kickoff call on calendar
  - Project timeline shared with client (4–6 week education window targeted)
- **Duration:** Internal handoff complete within 1–2 business days of signature
- **Tools:** NexHub CRM, Outlook calendar, shared OneDrive/SharePoint folder for client artifacts
- **Dependencies:** Employer signature captured (Step 1.6); CEHAS countersignature in progress (Step 5.2) — implementation does not need to wait on full countersignature to begin payroll setup work
- **What can go wrong:** Sales hands off without complete CRM notes and the implementation team rebuilds context the client has already given. The client experiences "telling the same story twice," which damages trust early.
- **Escalation:** Jason if the handoff stalls past five business days

---

## Diagram 2 — Implementation Flow

### Step 2.1 — Signed Proposal (received)

- **Owner:** Nexus — Wendy/Shea (Implementation)
- **What happens:** The signed proposal lands with implementation. Wendy/Shea confirm all source artifacts are in place: signed contracts, quoting dataset, payroll system access, named payroll owner on the client side. Implementation kickoff is scheduled.
- **Inputs:**
  - Signed contract package
  - Client payroll system credentials or access method
  - Sales handoff packet from Step 1.7
- **Outputs:**
  - Implementation file confirmed complete
  - Kickoff call on calendar
  - Internal RACI confirmed (Nexus / Insight / Capitol roles)
- **Duration:** 1–2 business days after signature
- **Tools:** NexHub CRM, OneDrive/SharePoint, Outlook
- **Dependencies:** Step 1.7 handoff complete
- **What can go wrong:** Missing artifacts force implementation to re-engage the client for items that should already be in hand. Insight does not yet know the group is incoming.
- **Escalation:** Wendy/Shea → Jason; Jason loops Insight (Brenda Brown or Howard) into the kickoff invite

### Step 2.2 — Payroll System Setup

- **Owner:** Insight Benefits — Brenda Brown / Howard's team, supported by Nexus (Wendy)
- **What happens:** Two payroll codes are configured in the client's payroll system: a Section 125 pre-tax deduction code for the employee contribution, and a separate reimbursement code for the indemnity payments, which are not wages and must be coded as such. Getting both codes correct here is the single biggest determinant of whether the downstream cycle stays clean.
- **Inputs:**
  - Client payroll system access
  - Plan tier and contribution amounts
  - Indemnity reimbursement spec from carrier
- **Outputs:**
  - Section 125 deduction code live in client payroll system
  - Indemnity reimbursement code live in client payroll system
  - Test record run end-to-end (where the system supports it)
- **Duration:** 1–3 business days, depending on payroll system and admin responsiveness
- **Tools:** Client payroll system (ADP, I-Solved, Paycom, Paychex, Kronos for Standard; ADP Run, Gusto, Heartland, QuickBooks for Edge case)
- **Dependencies:** Step 2.1 complete; client payroll admin available
- **What can go wrong:** Reimbursement coded as wages (gets FICA'd, defeats the model). Edge-case payroll systems don't expose the configuration cleanly; manual workarounds carry forward into the audit cycle.
- **Escalation:** Insight → Wendy → Jason; Brenda Manning if a payroll vendor needs Capitol-level intervention

### Step 2.3 — Initial File Build

- **Owner:** Insight Benefits — Brenda Brown / implementation team, supported by Nexus
- **What happens:** Insight builds the first payroll/eligibility file using the quoting dataset and the freshly configured payroll codes. For sophisticated payroll systems, the deliverable is an upload-ready file. For systems that require manual entry, Insight delivers the same data in a format the client admin can work from line by line.
- **Inputs:**
  - Quoting platform dataset (employee list, elections, contributions)
  - Confirmed payroll codes from Step 2.2
  - Client payroll system capability profile
- **Outputs:**
  - Initial payroll file (upload-ready or manual-entry format)
  - First eligibility file in the agreed format for CEHAS ingest
  - Audit baseline saved in the Nexus system
- **Duration:** 1–3 business days
- **Tools:** Nexus eligibility/audit platform, Insight workflow tools, client payroll system
- **Dependencies:** Step 2.2 codes live; CEHAS eligibility file format finalized (currently pending CEHAS IT)
- **What can go wrong:** Format drift between what Nexus produces and what CEHAS expects, requiring a rework cycle on file 1. Manual-entry clients fat-finger the import.
- **Escalation:** Insight → Wendy; Connie / CEHAS IT for any format question

### Step 2.4 — 100% First-Run Audit

- **Owner:** Insight Benefits — operations team, with Nexus reviewing flagged exceptions
- **What happens:** The first payroll run after go-live is audited line by line — not a spot check. Every deduction, every reimbursement, every eligibility flag is reconciled against what was sold and what was set up. The intent is to catch any setup error before it compounds across a second cycle.
- **Inputs:**
  - First post-go-live payroll register
  - Initial eligibility file from Step 2.3
  - Quoting platform baseline
- **Outputs:**
  - 100% reconciliation report
  - Exception list (if any) with assigned owners
  - Sign-off that the group is in cycle
- **Duration:** 2–4 hours of audit work the day of / day after the first run
- **Tools:** Nexus eligibility/audit platform, client payroll system, Excel for exception tracking
- **Dependencies:** Step 2.3 complete; first payroll run has executed
- **What can go wrong:** Variances surface that trace back to Step 2.2 coding errors — the cost of catching them here is small; the cost of not catching them grows every cycle. Client admin disagrees with a flagged variance and the conversation has to happen real-time.
- **Escalation:** Insight ops → Wendy → Jason for any variance that requires a client conversation above the payroll admin level

### Step 2.5 — Employee Education

- **Owner:** Nexus — originating advisor and Jason own the message; Amaze supplies clinical content; Insight supports operationally
- **What happens:** A 4–6 week education window opens before go-live. Each employee receives a personalized before/after paycheck statement, Amaze Health welcome materials, and a clearly marked opt-out path that routes through Amaze. Employees see exactly what is changing on their check, what they are getting in return, and how to decline.
- **Inputs:**
  - Per-employee paycheck packets from Step 1.4
  - Amaze Health welcome and onboarding materials
  - Opt-out instructions
- **Outputs:**
  - Education materials distributed (employer-facilitated)
  - Opt-out elections collected
  - Employee questions logged and answered
  - Final enrollment file reflecting opt-outs ready for go-live
- **Duration:** 4–6 weeks
- **Tools:** Email, employer comms channels, Amaze portal, optional Employee Navigator content
- **Dependencies:** Steps 2.2 and 2.3 in progress; education timeline agreed with client leadership
- **What can go wrong:** Employer pushes the education window short to chase a go-live date — opt-out rate spikes after go-live because employees felt rushed. Communication channel mismatch (email-only at a manufacturing site, for example) leaves part of the population uninformed.
- **Escalation:** Originating advisor → Jason if the employer compresses the window beyond what's reasonable

### Step 2.6 — Go-Live

- **Owner:** Nexus + Insight jointly; Capitol/CEHAS receives the first eligibility push
- **What happens:** The group goes live on the agreed effective date. First payroll runs with the Section 125 deduction and the indemnity reimbursement code active for enrolled employees. First eligibility file flows to CEHAS for invoicing. The 100% first-run audit (Step 2.4) catches any issue before cycle two.
- **Inputs:**
  - Completed setup (Steps 2.2 / 2.3)
  - Final enrollment file post-education window
  - Coverage effective date confirmed
- **Outputs:**
  - First payroll cycle complete with new codes live
  - First eligibility file delivered to CEHAS
  - First invoice generated by CEHAS
  - Group flipped from "Implementation" to "In Service" in the CRM
- **Duration:** Effective date is a single day; the surrounding go-live window spans the first full payroll cycle
- **Tools:** Client payroll system, Nexus audit system, CEHAS ingest channel
- **Dependencies:** Steps 2.1–2.5 complete; coverage effective date confirmed in carrier paper
- **What can go wrong:** Effective date misalignment between payroll cycle and carrier coverage start, which creates a partial-cycle invoicing oddity that CEHAS has to reconcile manually. Last-minute opt-outs that miss the file freeze.
- **Escalation:** Wendy → Jason → Brenda Manning / Connie for any cross-org coordination on the effective date

---

## Diagram 3 — Two-Bucket Decision

### Step 3.1 — Incoming Deal Evaluation (the criteria)

- **Owner:** Nexus — Jason makes the final call; advisor presents the facts
- **What happens:** Every incoming deal is evaluated against the Nexus Standard criteria during qualification. The evaluation is not a soft preference — it is a routing decision that determines economics and operational ownership for the life of the case.
- **Inputs:**
  - Discovery and qualification notes
  - Group size, industry, turnover, payroll system, operational maturity read
  - Originating advisor's read on client comfort with the model
- **Outputs:**
  - Bucket assignment (Standard, Capitol-routed, or pass)
  - Documented rationale
  - Economics path locked for this deal
- **Duration:** A single decision moment, usually inside or right after the qualification call
- **Tools:** NexHub CRM, two-bucket routing reference
- **Dependencies:** Discovery and qualification complete
- **What can go wrong:** Soft routing — calling something Standard because the advisor wants the full economics, when the profile says otherwise. That kind of slippage shows up six months later as Insight hour overruns.
- **Escalation:** Jason; for genuine edge cases Jason can consult Brenda Manning on the political read with Capitol

### Step 3.2 — Nexus Standard Routing (YES)

- **Owner:** Nexus — end-to-end for the life of the case
- **What happens:** Deal proceeds through the full Nexus funnel (Diagram 1), the full Nexus implementation (Diagram 2), and the full Nexus ongoing service cycle (Bonus section). Insight provides TPA-side labor; Capitol holds the carrier paper but is invisible to the client. Nexus runs full economics.
- **Inputs:**
  - Standard bucket assignment from Step 3.1
- **Outputs:**
  - Deal moves to Discovery (Step 1.1) and continues through full funnel
  - Insight notified that a Standard group is incoming
  - Full Nexus comp structure applied
- **Duration:** N/A — this is a routing step, not a workflow step
- **Tools:** NexHub CRM (deal record with bucket flag)
- **Dependencies:** Step 3.1 routing decision
- **What can go wrong:** Group profile drifts post-routing (acquisition, leadership change, turnover spike) and the bucket should be revisited. Currently there is no formal "re-bucket" trigger — TBD with team whether to define one at, say, 12 months in service.
- **Escalation:** Jason on any mid-life rerouting question

### Step 3.3 — Capitol-Routed Bucket (NO)

- **Owner:** Capitol Group — operations and existing broker/TPA network
- **What happens:** Deal is handed back to Capitol. Capitol owns the operational lift — onboarding, payroll handling, ongoing service — through its existing broker and TPA network. Nexus stays out of the day-to-day work and receives reduced comp for distribution only. Distribution partners (the advisor or external broker who brought the deal) still get paid; the client still gets placed.
- **Inputs:**
  - Capitol-routed assignment from Step 3.1
  - Originating advisor / broker information for the comp split
- **Outputs:**
  - Deal warm-handed to Capitol with originating advisor introduced
  - Reduced Nexus comp structure applied
  - Capitol-side onboarding initiated through their existing channels
- **Duration:** Handoff completes within five business days of bucket assignment
- **Tools:** NexHub CRM (deal flagged as Capitol-routed), email to Capitol intake (TBD with team — formal intake address pending)
- **Dependencies:** Step 3.1 routing decision; Capitol has confirmed the operational receiving channel for these handoffs (TBD with Connie / Scott)
- **What can go wrong:** No defined Capitol receiving channel means deals stall at the handoff. The originating advisor loses visibility into the deal status and feels like the relationship went into a black hole.
- **Escalation:** Jason → Brenda Manning → Scott; longer-term, a defined Capitol intake contact resolves this

---

## Diagram 4 — Eligibility → Invoicing Loop

### Step 4.1 — Nexus produces eligibility file

- **Owner:** Insight Benefits operations, using the Nexus eligibility/audit system
- **What happens:** On the agreed weekly cadence (aligned to the client's payroll cycle), Insight produces the eligibility file for each participating employer. The file reflects the current cycle's payroll audit — who is still qualified, who is no longer qualified, newly eligible employees, terminations, and any reclassifications.
- **Inputs:**
  - Current cycle payroll register from the client
  - Prior cycle eligibility baseline
  - Audit output from the Nexus system (see Bonus Steps 1–4)
- **Outputs:**
  - Updated eligibility file in the agreed format containing: employer ID, employee ID, SSN or masked equivalent, plan election, enrollment status, opt-out flag, non-qualified flag, employee email, dependent info, coverage effective date, termination date
- **Duration:** 30 minutes per group per cycle on average (within the 12-hour annual Insight budget)
- **Tools:** Nexus eligibility/audit platform, secure delivery channel to CEHAS
- **Dependencies:** Client payroll register received; cycle audit complete; CEHAS file format finalized (currently pending CEHAS IT)
- **What can go wrong:** Format drift if CEHAS spec evolves without coordinated update on the Nexus side. Late payroll register from the client pushes the file delivery past CEHAS's ingest window.
- **Escalation:** Insight → Wendy; Connie / CEHAS IT for any format-side question

### Step 4.2 — CEHAS ingests

- **Owner:** Capitol Group — CEHAS captive admin system; April / CEHAS IT on the operational side
- **What happens:** CEHAS receives the eligibility file and ingests it into the captive admin system on the weekly cadence. Delivery method is open — either CSV push from Nexus (Option A) or CEHAS-side pull via system access (Option B). Decision pending Capitol's operational preference.
- **Inputs:**
  - Eligibility file from Step 4.1
- **Outputs:**
  - Updated roster in CEHAS captive admin
  - Ingest confirmation / exception report back to Nexus/Insight (TBD with team — confirm whether CEHAS sends a receipt)
- **Duration:** Same-day ingest after delivery
- **Tools:** CEHAS captive admin system, agreed delivery channel (CSV push or system access)
- **Dependencies:** Step 4.1 delivered; delivery method decision locked; CEHAS IT format finalized
- **What can go wrong:** File rejected for format / schema issue and the cycle has to be reworked. No receipt mechanism means Nexus doesn't know whether the file landed clean.
- **Escalation:** Connie / April / CEHAS IT; Nexus loops in Brenda Manning if cross-org delay

### Step 4.3 — Invoice generation

- **Owner:** Capitol Group — CEHAS / April
- **What happens:** CEHAS generates the invoice for the employer based on the current eligibility roster. Invoice reflects the active enrolled population per plan tier. This is the financial side of the loop — Capitol bills off whatever Nexus sent.
- **Inputs:**
  - Current ingested eligibility roster
  - Plan tier rates
- **Outputs:**
  - Employer invoice
  - Invoice copy to Nexus/Insight for reference and reconciliation
- **Duration:** Generated within one business day of ingest
- **Tools:** CEHAS captive admin / billing system
- **Dependencies:** Step 4.2 ingest clean
- **What can go wrong:** Invoice variance from prior cycle goes out without a heads-up to the employer, generating a payroll-admin support call. The accident-coverage one-payroll-cycle grace period on terminations needs to be reflected in the billing or a termed employee gets billed an extra cycle.
- **Escalation:** April → Connie; Insight loops in Wendy if the employer disputes the invoice

### Step 4.4 — ACH collection

- **Owner:** Capitol Group — CEHAS
- **What happens:** CEHAS initiates ACH collection from the employer for the invoiced amount. ACH settles on the standard cycle. This closes the loop: Nexus produced eligibility, CEHAS billed off it, employer paid against it.
- **Inputs:**
  - Generated invoice from Step 4.3
  - Employer ACH authorization on file
- **Outputs:**
  - Funds collected
  - Settlement record back to CEHAS
  - Downstream carrier and reinsurance economics settle from this collection
- **Duration:** Standard ACH settlement (1–3 business days)
- **Tools:** CEHAS ACH processing
- **Dependencies:** Step 4.3 invoice generated; employer ACH authorization in place from onboarding
- **What can go wrong:** ACH return for insufficient funds or revoked authorization. Employer banking change not communicated to CEHAS.
- **Escalation:** CEHAS → Connie → Brenda Manning → Jason for client-facing collection conversations

---

## Diagram 5 — Contract Signature Sequence

### Step 5.1 — Employer signs

- **Owner:** Nexus — originating advisor and Jason on the relationship; Insight supports the operational signature mechanics
- **What happens:** The employer signs the contract package (ASA, Compliance Protection Document, Request for Coverage) first. This is the entry into the formal signature sequence. The CEHAS e-sign workflow captures the employer signature and triggers the next leg.
- **Inputs:**
  - Final contract package
  - Employer signatory identified (typically CFO or owner)
  - CEHAS e-sign envelope configured
- **Outputs:**
  - Employer signature captured
  - Trigger to CEHAS for countersignature
- **Duration:** Same-day to one week after proposal acceptance
- **Tools:** CEHAS e-sign system, Outlook for routing
- **Dependencies:** Contract templates finalized (pending Connie); employer signatory identified
- **What can go wrong:** Employer's counsel requests red-lines after the envelope is already configured, forcing a re-route. Wrong signatory inside the employer's org delays execution.
- **Escalation:** Originating advisor → Jason → Brenda Manning / Connie on any contract red-line

### Step 5.2 — CEHAS countersigns

- **Owner:** Capitol Group — CEHAS signatory (contact details pending from Connie)
- **What happens:** CEHAS countersigns the executed contract package after employer signature. This confirms Capitol-side acceptance of the operational and captive relationship for this employer.
- **Inputs:**
  - Employer-signed contract package
- **Outputs:**
  - CEHAS countersignature captured
  - Trigger to insurer for the final countersignature
- **Duration:** 1–3 business days after Step 5.1
- **Tools:** CEHAS e-sign system
- **Dependencies:** Step 5.1 complete; CEHAS signatory contact confirmed (currently pending)
- **What can go wrong:** Pending signatory contact means the envelope sits idle. Operational acceptance criteria CEHAS uses for countersignature aren't documented externally — TBD with team whether there's a checklist Nexus should pre-clear.
- **Escalation:** Connie → CEHAS internal; Brenda Manning if the stall is more than three business days

### Step 5.3 — Insurer countersigns

- **Owner:** Insurance carrier (under Capitol's captive/reinsurance structure)
- **What happens:** The insurance carrier countersigns the package as the final signature. This is what makes the coverage formally bound for the employer.
- **Inputs:**
  - CEHAS-countersigned contract package
- **Outputs:**
  - Insurer countersignature captured
  - Fully executed contract package
- **Duration:** 1–3 business days after Step 5.2
- **Tools:** CEHAS e-sign system, carrier signature workflow
- **Dependencies:** Step 5.2 complete; insurer signature contact confirmed (currently pending from Connie)
- **What can go wrong:** Carrier-side review introduces unexpected questions that bounce the package back. Signature contact unavailability creates calendar delay.
- **Escalation:** Connie owns the carrier-side relationship; Brenda Manning if escalation is needed

### Step 5.4 — Distribution to all parties

- **Owner:** Capitol Group — CEHAS distributes; Nexus archives
- **What happens:** Once fully executed, copies of the contract package are distributed to the client (employer), Nexus Benefit Solutions, CEHAS, and the insurance carrier. All four parties hold a copy of the executed package.
- **Inputs:**
  - Fully executed contract package
  - Distribution list with current contact emails for all four parties
- **Outputs:**
  - Executed package delivered to all parties
  - Copy archived in NexHub deal record
  - Implementation team formally green-lit (Diagram 2 already running in parallel)
- **Duration:** Same-day to one business day after Step 5.3
- **Tools:** Email, SharePoint/OneDrive archive, CEHAS distribution mechanism
- **Dependencies:** Step 5.3 complete
- **What can go wrong:** Distribution list out of date — copy goes to a stale email at the client or at Nexus. Nexus's local archive isn't kept in sync with what CEHAS holds as canonical.
- **Escalation:** Wendy/Shea on archive issues; Connie on CEHAS distribution issues

---

## Bonus — Ongoing Service Process (Weekly/Biweekly Cycle)

This is the recurring service cycle that runs for the life of the group. Insight owns the steady-state cadence (Brenda Brown likely as primary). The full cycle stays inside the 30-minute-per-group-per-cycle budget that supports the 12-hour annual Insight figure.

### Bonus Step 1 — Pull payroll register from client

- **Owner:** Insight Benefits — operations team
- **What happens:** Each payroll cycle, Insight pulls the payroll register from the client. Two delivery patterns: the client emails the report on a standing schedule, or Insight accesses the client's payroll system directly when that has been set up during implementation.
- **Inputs:**
  - Standing pull schedule with the client
  - Payroll system access or scheduled email delivery
- **Outputs:**
  - Current cycle payroll register in hand at Insight
- **Duration:** 5 minutes if the client is on schedule; longer if Insight has to chase
- **Tools:** Client payroll system, email, secure file transfer
- **Dependencies:** Standing schedule established during implementation; access provisioned
- **What can go wrong:** Client misses the standing send and the cycle starts late. Payroll admin turnover at the client means the access pattern breaks.
- **Escalation:** Insight → Wendy; advisor re-engages the relationship if the access pattern needs to be re-established

### Bonus Step 2 — Ingest into Nexus audit system

- **Owner:** Insight Benefits operations, using the Nexus eligibility/audit system
- **What happens:** The payroll register is ingested into the Nexus quoting and audit system — the same engine that ran the initial census audit during sales. The system loads the file, normalizes the data, and prepares the baseline for the eligibility audit.
- **Inputs:**
  - Current payroll register from Bonus Step 1
  - Prior cycle baseline in the system
- **Outputs:**
  - Cycle data loaded and ready for audit
- **Duration:** 5 minutes for Standard payroll systems; longer for Edge-case manual workflows
- **Tools:** Nexus eligibility/audit platform
- **Dependencies:** Bonus Step 1 complete; Standard vs. Edge-case payroll system handling defined
- **What can go wrong:** Edge-case manual exports fat-fingered on ingest. Schema change at the client's payroll system breaks the ingest mapping.
- **Escalation:** Insight → Wendy on mapping or schema issues

### Bonus Step 3 — Eligibility audit (qualification check)

- **Owner:** Nexus audit system (automated), reviewed by Insight
- **What happens:** The system runs the eligibility audit against the new file. It identifies who is still qualified, who is no longer qualified due to a pay change, leave, or status shift, who is newly eligible because a new hire has cleared the waiting period, and who needs to be reclassified. Output is a variance view.
- **Inputs:**
  - Ingested current cycle data
  - Prior cycle eligibility baseline
- **Outputs:**
  - Variance view: still-qualified, no-longer-qualified, newly eligible, reclassifications
- **Duration:** Minutes — automated
- **Tools:** Nexus eligibility/audit platform
- **Dependencies:** Bonus Step 2 complete
- **What can go wrong:** Edge case at the wage-band boundary slips through the qualification logic. High-earner Social Security wage-base cliffs need the system flag to fire correctly mid-year.
- **Escalation:** Insight ops → Wendy on any logic question

### Bonus Step 4 — Variance review

- **Owner:** Insight Benefits — operations reviewer (human-in-the-loop)
- **What happens:** Insight reviews the variance view at a glance before anything is pushed downstream. Pattern watched for is the wild swing — a count that moves more than the population should reasonably move in a single cycle. The posture is "Houston, we have a problem" — pause, verify, then proceed. The Davenport adjunct-faculty episode is the in-house cautionary tale for this step.
- **Inputs:**
  - Variance view from Bonus Step 3
- **Outputs:**
  - Approved variance set, or a paused cycle with verification questions for the client
- **Duration:** 5–10 minutes on a clean cycle; longer on any pause
- **Tools:** Nexus eligibility/audit platform
- **Dependencies:** Bonus Step 3 complete
- **What can go wrong:** Reviewer rubber-stamps a wild swing because the cycle is "due." That's exactly the failure mode the step exists to prevent.
- **Escalation:** Insight → Wendy → originating advisor if a client conversation is needed before push

### Bonus Step 5 — Email payroll admin with changes

- **Owner:** Insight Benefits — operations
- **What happens:** Insight emails the client's payroll admin with the changes for the current cycle. This keeps the client informed in real time and creates an audit trail of every cycle's deltas. The communication is operational and routine — it doesn't escalate unless the changes are material.
- **Inputs:**
  - Approved variance set from Bonus Step 4
- **Outputs:**
  - Payroll admin email sent with the cycle's changes
  - Reply / acknowledgment logged
- **Duration:** 5 minutes
- **Tools:** Outlook
- **Dependencies:** Bonus Step 4 approved
- **What can go wrong:** Payroll admin doesn't read the email and a change surprises them next cycle. Payroll admin turnover means the standing distribution is stale.
- **Escalation:** Insight → Wendy if the admin is non-responsive across multiple cycles

### Bonus Step 6 — Push eligibility file to Capitol/CEHAS

- **Owner:** Insight Benefits — operations, delivering to CEHAS
- **What happens:** Insight pushes the updated eligibility file to CEHAS on the weekly cadence. This is the file that drives invoicing and ACH (Diagram 4). Without this push the entire downstream financial loop sits on stale data.
- **Inputs:**
  - Approved eligibility file from Bonus Steps 4–5
- **Outputs:**
  - Eligibility file delivered to CEHAS via agreed channel (CSV push or system access)
- **Duration:** 2–5 minutes
- **Tools:** Agreed delivery channel
- **Dependencies:** Bonus Step 4 approved; CEHAS format finalized; delivery method locked
- **What can go wrong:** Delivery slips past the CEHAS ingest window and the cycle's invoicing lags. Format drift between Nexus output and CEHAS expectation.
- **Escalation:** Insight → Wendy; Connie / CEHAS IT for any format issue

### Bonus Step 7 — Amaze handles disenrollment requests

- **Owner:** Amaze Health — direct member channel
- **What happens:** Employees who decide they no longer want to participate route through Amaze directly. Amaze processes the disenrollment, and the change flows back to Insight on the next eligibility cycle, where it appears as a flag on the variance view and is reflected in the next file push to CEHAS.
- **Inputs:**
  - Employee disenrollment request to Amaze
- **Outputs:**
  - Disenrollment recorded at Amaze
  - Change flowed to Insight for the next cycle
- **Duration:** Same-day at Amaze; visible to the rest of the system on the next cycle
- **Tools:** Amaze member channel, eventual reflection in the Nexus audit system
- **Dependencies:** Member knows the opt-out path routes through Amaze (set during education in Step 2.5)
- **What can go wrong:** Employee tells the employer instead of Amaze, change doesn't reach Insight cleanly, and the next eligibility file is stale by one cycle. Coverage-grace handling on the accident layer needs to be respected in the termination date on the file.
- **Escalation:** Amaze → Insight → Wendy if a disenrollment reconciliation issue surfaces

---

*Last updated: May 16, 2026. Items marked "TBD with team" are open coordination points between Nexus, Capitol/CEHAS, and Insight and will be resolved as the Friday 5/22 walkthrough and the 5/25–5/26 Capitol ops review land.*
