# Cascade Tower — AI Workshop Datasets

## About This Repository

This repository contains five synthetic datasets created for an AI in Construction workshop at **UBC Vancouver, Master of Engineering in Project and Construction Management**.

All five datasets describe the **same fictional project** — Cascade Tower — so students can cross-reference findings across disciplines and see how a single mid-project event (a facade supplier failure in Month 6) ripples through schedule, cost, safety, risk, and BIM coordination data.

**These datasets are fictional.** All names, addresses, companies, and individuals are invented for educational purposes.

---

## The Project: Cascade Tower

| Field | Details |
|---|---|
| **Project Name** | Cascade Tower |
| **Location** | 1200 W Georgia St, Vancouver, BC |
| **Owner** | Cascade Development Corp |
| **General Contractor** | Pacific Builders Ltd |
| **Contract Value** | $82,000,000 CAD (Stipulated Sum) |
| **Contract Type** | CCDC 2 Stipulated Price |
| **Project Type** | 25-storey mixed-use tower (4 floors retail/commercial, 21 floors residential, 2-level underground parkade) |
| **Total Area** | ~28,500 m² |
| **Duration** | 18 months |
| **Planned Start** | January 6, 2025 |
| **Planned Substantial Completion** | June 27, 2026 |
| **Data "as-of" Date** | March 31, 2026 (Month 15 of 18) |

### The Key Project Event: Facade Supplier Failure (June 2025)

In **Month 6 (June 2025)**, the originally specified curtain wall supplier failed thermal cycling quality assurance testing. Pacific Builders switched to a backup supplier (GlassWorks Pacific) using a unitized curtain wall system, requiring a 4-week design redesign and a 3-week delayed delivery. This caused a **21-day impact to the critical path** and approximately **$2.8M in additional costs** (cost delta + acceleration measures). This event is visible across all five datasets.

---

## Datasets

### 1. `cascade_tower_schedule.csv` — Schedule Performance
**Workshop use:** Build a Gantt-style schedule dashboard showing planned vs. actual dates, delay analysis, and critical path status.

**Links to CIVL 520** (Construction Planning and Control)

| Column | Description |
|---|---|
| Activity_ID | Unique activity identifier |
| WBS_Code | Work Breakdown Structure code |
| Activity_Name | Description of the activity |
| Phase | Project phase (Preconstruction, Substructure, Superstructure, Envelope, Interior, Closeout) |
| Discipline | Responsible discipline |
| Planned_Start / Planned_Finish | Baseline dates |
| Actual_Start / Actual_Finish | Recorded dates (blank = not yet complete) |
| Planned_Duration_Days / Actual_Duration_Days | Duration in working days |
| Predecessor | Activity predecessor(s) |
| Float_Days | Total float on this activity |
| Critical_Path | Yes/No |
| Percent_Complete | 0–100 |
| Status | Complete / In Progress / Not Started |
| Delay_Days | Positive = delay, negative = ahead |
| Delay_Reason | Explanation for delays |

**Records:** 42 activities across 18 months

---

### 2. `cascade_tower_earned_value.csv` — Earned Value & Cost Performance
**Workshop use:** Build an EV dashboard with SPI/CPI trend charts, cost variance analysis, and forecast-at-completion.

**Links to CIVL 522** (Project and Construction Economics)

| Column | Description |
|---|---|
| Month / Period_End_Date / Month_Number | Time period |
| Phase | Active project phase |
| BCWS_Planned_Value | Budgeted cost of work scheduled (monthly, CAD) |
| BCWP_Earned_Value | Budgeted cost of work performed (monthly, CAD) |
| ACWP_Actual_Cost | Actual cost of work performed (monthly, CAD) |
| SPI | Schedule Performance Index (monthly) |
| CPI | Cost Performance Index (monthly) |
| SV_Schedule_Variance | EV − PV (monthly) |
| CV_Cost_Variance | EV − AC (monthly) |
| BAC_Budget_At_Completion | Original budget ($82M) |
| EAC_Estimate_At_Completion | Forecasted final cost |
| VAC_Variance_At_Completion | BAC − EAC |
| TCPI | To-Complete Performance Index |
| Cumulative_* | Running totals for all EV metrics |
| Percent_Planned / Percent_Earned | Schedule progress metrics |
| Notes | Key events explaining performance |

**Records:** 18 months (Months 1–15 have actuals; Months 16–18 are planned only)

---

### 3. `cascade_tower_safety.csv` — Safety Incidents & Near Misses
**Workshop use:** Build a safety dashboard with incident trend analysis, severity breakdown, trade/subcontractor heat maps, and corrective action tracking.

**Links to CIVL 521** (Construction Methods and Performance)

| Column | Description |
|---|---|
| Incident_ID | Unique identifier (SAF-XXX) |
| Date / Time | When the incident occurred |
| Phase | Project phase |
| Location / Floor_Level / Activity | Where and what was happening |
| Incident_Type | Near Miss, Struck By, Fall from Height, Electrical, etc. |
| Severity | 1 (Near Miss) → 4 (Fatality/Critical) |
| Description | Full incident narrative |
| Worker_Trade / Worker_Experience_Years | Who was involved |
| PPE_Compliant | Was PPE worn correctly? |
| Weather / Temperature_C | Site conditions |
| Immediate_Action | What was done immediately |
| Root_Cause | Why it happened |
| Corrective_Action | What was changed to prevent recurrence |
| Days_Lost | Lost time days |
| Near_Miss | Boolean — was this a near miss? |
| Reported_To_WorkSafeBC | Boolean |
| Subcontractor | Company responsible |

**Records:** 27 incidents and near misses across 15 months

---

### 4. `cascade_tower_risk_register.csv` — Project Risk Register
**Workshop use:** Build an interactive risk matrix dashboard with likelihood/impact heat map, risk category analysis, cost exposure totals, and status tracking.

**Links to CIVL 522 & CIVL 523** (Project Economics and Project Management)

| Column | Description |
|---|---|
| Risk_ID | Unique identifier (RSK-XXX) |
| Date_Identified / Last_Updated | Lifecycle dates |
| Category / Subcategory | Risk taxonomy |
| Risk_Title / Risk_Description | What the risk is |
| Phase_Affected / Discipline | Scope of impact |
| Likelihood | 1–5 scale (1 = Rare, 5 = Almost Certain) |
| Impact | 1–5 scale (1 = Negligible, 5 = Critical) |
| Risk_Score | Likelihood × Impact |
| Risk_Rating | Low / Medium / High / Critical |
| Risk_Owner | Who manages this risk |
| Mitigation_Strategy / Mitigation_Actions | Prevention |
| Contingency_Plan | Response if risk occurs |
| Status | Active / Mitigated / Realized / Closed |
| Trigger_Event | What activates the contingency |
| Cost_Exposure | Maximum financial exposure (CAD) |
| Schedule_Exposure_Days | Maximum schedule impact |
| Actual_Impact | What actually happened (for realized risks) |
| Notes | Additional context |

**Records:** 15 risks across all project phases

---

### 5. `cascade_tower_clash_detection.csv` — BIM Clash Detection Report
**Workshop use:** Build a clash analysis dashboard with clash counts by discipline pair, severity/status breakdown, cost impact summary, and resolution timeline.

**Links to CIVL 526** (Virtual Design and Construction)

| Column | Description |
|---|---|
| Clash_ID | Unique identifier (CLH-XXX) |
| Date_Detected / Date_Resolved | Lifecycle dates |
| Status | Resolved / Open |
| Priority | Minor / Major / Critical |
| Clash_Type | Hard Clash or Clearance |
| Discipline_A / Element_Type_A / Element_ID_A | First clashing element |
| Discipline_B / Element_Type_B / Element_ID_B | Second clashing element |
| Floor_Level / Zone / Grid_Location | Where in the building |
| Description | What the conflict is |
| Clearance_Required_mm / Actual_Clearance_mm | Geometry of the clash |
| Assigned_To | Responsible party |
| Resolution_Method | Design Revision / Coordination / Pending |
| Resolution_Description | How it was fixed |
| Cost_Impact | CAD cost of resolution |
| RFI_Number | Linked RFI reference |
| Days_To_Resolve | Resolution time |
| Detection_Source | How found (BIM Coordination) |
| BIM_Model_Version | Model version when detected |

**Records:** 42 clashes (38 resolved, 4 open as of March 31, 2026)

---

## The Unifying Story

Students working on different datasets will be able to cross-reference the **same events**:

| Event | Schedule | Earned Value | Safety | Risk | Clashes |
|---|---|---|---|---|---|
| Facade supplier failure (Jun 2025) | A3020 — 25-day delay | Month 6 SPI drop to 0.85 | — | RSK-003 Realized | CLH-022 generator/facade conflict |
| Fall from height (Jul 2025) | Minor cascade on core walls | Month 7 cost increase | SAF-009 (28 days lost) | RSK-005 Realized | — |
| Curtain wall late delivery (Nov 2025) | A4000 — 21-day delay | Month 11 SPI drop to 0.81 | SAF-017 (bracket failure) | RSK-011 Active | CLH-016, CLH-022 |
| BAS/electrical integration | A7010 In Progress | — | SAF-025 (minor shock) | RSK-015 Active | CLH-023, CLH-035 |

---

## Suggested AI Prompts (Workshop Starting Points)

Each student should paste their CSV into Claude, ChatGPT, or Gemini and use a prompt like:

**Schedule:**
> "Here is construction project schedule data for Cascade Tower. Build me an interactive HTML dashboard that shows: (1) a bar chart of planned vs actual duration by phase, (2) a table of all delayed activities sorted by delay days, and (3) a summary card showing total critical path delay."

**Earned Value:**
> "Here is 15 months of earned value data for an $82M construction project. Build me an interactive HTML dashboard with: (1) SPI and CPI trend lines over time, (2) a cumulative S-curve comparing BCWS, BCWP, and ACWP, and (3) a forecast-at-completion summary with variance from budget."

**Safety:**
> "Here is a construction safety incident log. Build me an interactive HTML dashboard showing: (1) incident frequency by month, (2) a severity breakdown chart, (3) a heat map of incidents by trade/subcontractor, and (4) a summary of total lost-time days."

**Risk:**
> "Here is a project risk register. Build me an interactive HTML dashboard with: (1) a likelihood vs impact risk matrix with colour coding, (2) a bar chart of total cost exposure by risk category, (3) a status breakdown (Active/Mitigated/Realized), and (4) a table of the top 5 highest-scoring risks."

**BIM Clashes:**
> "Here is a BIM clash detection report from a construction project. Build me an interactive HTML dashboard showing: (1) clash counts by discipline pair as a matrix or chart, (2) a breakdown of clashes by priority and status, (3) total cost impact by discipline, and (4) average days to resolve by priority level."

---

## License

These datasets are released for educational use. All data is fictional.

Created for the UBC MEng PCM AI Workshop, April 2026.
