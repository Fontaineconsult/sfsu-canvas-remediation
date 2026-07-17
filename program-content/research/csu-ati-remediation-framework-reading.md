# Full Reading — CSU ATI Digital Content Remediation Prioritization Framework

*Knowledge-base entry for the SFSU AT Canvas Remediation Program · added July 2026*
*Source: `Chico LA Systemwide LMS Remediation Framework_v1.pdf` (57 pp., "Revision 032025", CC-BY 4.0) plus the ATI Remediation Hub Canvas-course intro page (`remediation-hub` in this folder). Authored by the CSU Chancellor's Office ATI with heavy Chico State and Cal State LA contribution (Chico's throughput model; Cal State LA's AIM for Student Success campaign appears in the appendices).*

---

## TL;DR for SF State

This is the **official CSU systemwide playbook for exactly the program we are building** — the first structured CO guidance on campus-level LMS remediation. It validates nearly every design decision already in our plans (student-assistant central team, TidyUP→UDOIT→prioritized queue, Equidox/Acrobat/ABBYY toolchain, course duplication workflow, severity + accommodation prioritization, dashboards) and adds four things our plans didn't have:

1. **Money:** CO ATI issues targeted funding to campuses for **hiring student assistants** (FY24–25 IFT went to all campuses May 16; round 2 allocation depends on demonstrated progress and sustainability planning). → *Ask the SFSU ATI coordinator what SFSU received / must show.*
2. **Systemwide tooling & vendor lanes we can just use:** a CSU-wide **Equidox license (72 concurrent users, ~3 per campus, negotiable)**; an in-progress **Allyant (CommonLook) Master Procurement Agreement** for discounted outsourced remediation; **CO ATI Acrobat training video series** for student assistants (~70 min total); **PAC** as the free PDF/UA validation gate; UDOIT + TidyUP already CSU-negotiated.
3. **Hard throughput numbers (Chico State, ~decade of data):** the missing capacity-planning benchmark for Phase 1.
4. **A complete whole-course remediation workflow** (request form → task management → Canvas course duplication → remediate → QA → return to instructor), with communication templates from provost-level down to individual faculty — the operational blueprint for our Phase 2 and the outreach model for Phases 4/6.

One framing note: the framework is built around the **original April 2026 deadline** (pre-dates the DOJ extension to April 26, 2027) — timelines inside it are stale, the structure is not.

---

## 1. What it is

- The CSU Chancellor's Office ATI's **Digital Content Remediation Prioritization Framework** — "the first time the Chancellor's Office has provided structured guidance and best practices for campus-level remediation efforts" (Remediation Hub intro).
- Organized as: Inventory & Assessment → Awareness/Communication → Capacity Development → Whole-Course Workflow → On-Demand Remediation → Public-Facing Content → Optimization/Maintenance → Recommended Tools → Beginner/Intermediate/Advanced quick-start guides → communication-template appendices.
- Lives with supporting assets (job descriptions, examples) in the **ATI Remediation Hub Canvas course**; the Hub also points at the Canvas Commons template **"Cal Poly MIDAS Document Remediation Resources"** for campuses starting student remediation teams.
- Explicit philosophy: **sustainability over one-time outsourcing** — build internal student-worker capacity rather than spending seed funds on vendors; "AI may handle up to 80% of the workload, but the final 20% demands a human touch, which student teams can often address more affordably."

## 2. Funding (the headline for us)

- CO ATI issued an **Interagency Financial Transaction (IFT) to all campuses (FY 2024–25, May 16)** targeted at **hiring student assistants** for digital content remediation.
- Round 1 is **seed funding** to pilot sustainable models; **round 2 allocations will be informed by demonstrated progress and commitment to long-term accessibility planning** — i.e., our Phase 5 metrics/reporting are also the funding case.
- The Hub explicitly discourages using the money to outsource with minimal staff ("zero capacity and one student … is hardly going to be a sustainable workflow").

**SFSU actions:** confirm what SFSU received and how it was spent; align our reporting so round 2 sees "demonstrated progress"; use the framework's own KPI checklists (§9 below) as the reporting vocabulary the CO expects.

## 3. Capacity & throughput (Chico State model — our planning benchmark)

Team: **17 student assistants × ~11 hrs/week, well-trained.** Consistently within 20% of estimates over several years (except one 9-month staffing transition).

| File class | Definition | Time | Per-student weekly output |
|---|---|---|---|
| **Easy** | Short, well-structured, minimal barriers | 0–3 hrs (avg **1 hr**; top performers ~30 min) | 12–15 avg; up to 20 |
| **Difficult** | Long/complex: scanned PDFs, detailed tables, embedded multimedia | 3–5 hrs (avg **4 hrs**) | 4–5 |

Split 12 students on easy + 5 on difficult → **~265 files/week ≈ ~1,060 files/month**.

Rules of thumb for us: **~1 hr/easy file, ~4 hrs/difficult file per trained student**; expect a training ramp before hitting those numbers; measure our own averages from tracker data (the framework says to log time-to-completion averages for exactly this reason).

## 4. Staffing & training model

- **Work-study first** (wages partially covered by financial aid), but over-hire and pre-train a bench because awards fluctuate; befriend financial aid + division budget staff; example job descriptions in the Hub assets.
- **Trickle-down training:** a staff member trains an initial core of **3–4 students**, who become **student leads** who train the next cohort.
- **Training modules prescribed:** (a) **PDF — Acrobat proficiency required even though Equidox is available** (continuity if Equidox goes away); (b) **Office — WebAIM training** (lighter lift); (c) **captioning — vendor tool materials**.
- **Crosscheck certification:** early work of each student is peer- or supervisor-reviewed before final implementation (matches our "100% QA on first N documents" gate).
- Staff stay in the loop for **complex-file escalation and QA**.

## 5. Whole-course remediation workflow (framework §4 — the Phase 2 blueprint)

1. **Request form** (Qualtrics or ITSM): course name/URL, instructor contact, desired return date, course type (multi-section / large lecture / blueprint / online) for prioritization. Personalized links; deactivate the form when too little time remains before term (route to on-demand instead). Track response rates; chase non-responding colleges via deans/chairs.
2. **Task management:** Kanban (Trello/MeisterTask/Notion) or ITSM (Jira/ServiceNow); ingest form submissions automatically; three example stage models from simple (7 stages) to granular (12: New Request → Review → Copy Course → Add Team → Capture Score Data → Remove Duplicate Files → Inventory Content → Internal Remediation → Send to External Vendor → QA → Complete → Notify Faculty). Auto-assign single-owner stages; manually assign skill-matched work.
3. **Canvas course prep (with LMS admin):** **duplicate the course** (work never happens in the live shell); consistent naming convention; consider a **dedicated Canvas sub-account for remediation copies** (clean counts + sub-account admin access for the team); **Designer role** for remediators; add students to assigned courses only — and **never to courses they are taking**; capture **pre-remediation accessibility score**; run **TidyUP** to kill duplicates/unused files (archive everything first — zip in-course or OneDrive/Drive).
4. **Remediate:** central team does the technically complex work (PDF tagging, captioning); instructors keep the easy in-RCE fixes (headings, alt text, links, contrast). Experienced staff review content first and **escalate complex/STEM files to vendors**. TidyUP batch-downloads files; UDOIT's "Review Course Files" flags issues and offers replace-file upload; batch content by type for specialist processing (SharePoint/Drive folders; metadata/folder conventions to return files to the right course).
5. **Return:** restore instructor access; completion email details what was fixed and what remains theirs; **insert an unpublished module of maintenance resources into the returned course** (nice touch worth copying).

## 6. On-demand lane (framework §5)

Parallel intake for individual files: form with **direct file upload**, urgency, file types, needed-by date; cap files per request; **defined turnaround (24–48 hrs urgent; 2–3 business days standard)**; experienced staffer triages; complex files escalate to vendor; also serves **staff/administrative documents** (flyers, handbooks) — plan for that demand.

## 7. Prioritization criteria (framework §1.5 — feeds our Phase 4 stack)

Beyond our existing enrollment/severity/accommodation criteria, the framework adds: **DFW/incomplete rates** (may correlate with unaddressed barriers), **gatekeeper courses** (required for graduation/major progression), **instructor readiness/willingness** (maximize short-term impact), **materials reused across sections/semesters** (ROI amplifier), GE/core status, accommodation-request history, audit/LMS-report complexity data. Pilot with "jumbo"/high-visibility courses; semester-based cycle covering whole-course + just-in-time.

Also: **archive to shrink scope** — control matriculated-course availability via Canvas Terms; watch community courses (orientation shells) that never conclude; archived courses need no remediation, but a recovered course must comply before re-release.

## 8. Communication machinery (appendices A–F — the Phase 4/6 outreach model)

The embedded worked example is **Cal State LA's "AIM for Student Success"** campaign:
- **Provost announces** the no-cost service campus-wide → **deans amplify** with college messaging (toolkits provided) → **targeted notification emails in waves** to faculty teaching priority courses (triggered by a student's accommodation request), each with a **personalized request-form link** → two dean follow-ups for non-responders (~2-week cadence: weeks of Apr 15 / Apr 29 / May 6 / May 20).
- Faculty consent is the ask; CETL copies the course; ITS remediates in the copy; faculty imports the accessible copy for fall.
- **Recognition system:** "Accessible All-Stars" — showcase page, digital badge, explicit encouragement to cite it in **RTP dossiers**, chair/dean notified. Cheap, real faculty incentive.
- Appendix F completion email: what was fixed, how to import, how to keep it accessible, how to request more, how to watch the Ally/UDOIT score.
- Plus: Q&A sessions (≤45 min), accessibility office hours (student-staffed with on-call staff escalation), faculty-champion fellowships, a single **services-hub webpage** (forms + training + FAQs).

## 9. Post-remediation maintenance & KPIs

- **Responsibility split (example to adapt):** faculty/staff own alt text, headings, document language, Google docs, pre-publish checks, submitting complex items, and ≥1 training; **central team owns PDFs-beyond-that, all captioning, just-in-time guidance, and course monitoring**.
- **Monitoring:** Power BI-style dashboard watches **new uploads into remediated courses** and their compliance level → faculty-responsibility items trigger re-education follow-ups ("expect a few rounds before habits form"); beyond-scope items auto-open a ticket for the team.
- Every section ends with an **Implementation Checklist (KPIs)** — ready-made progress-reporting vocabulary for CO ATI: baseline data generated, stakeholders convened, gap analysis done, prioritization rubric built, request-form response rates, turnaround times, courses/files remediated, student hours, cost avoidance, training completions.
- Quarterly metric reviews; ticket-closure surveys; SMART monthly targets by modality/course tier/remediation type.

## 10. Recommended tools & services (framework §"LEON" — systemwide stack)

| Tool | Framework role | Notes for us |
|---|---|---|
| **Adobe Acrobat Pro** | Final remediation/validation of complex docs | + **CO ATI student-training video series**: Intro to PDF Accessibility (~15 min) · Accessibility Checker (~10) · Tagging Content Correctly (~20) · Remediating Scanned Documents (~15) · Final Review & PAC Testing (~10) — in the Remediation Hub |
| **Equidox** | High-volume simple-to-moderate PDFs; easy entry point for non-experts | **CSU systemwide license: 72 concurrent users ≈ 3/campus; unlimited named accounts; more negotiable** |
| **ABBYY FineReader** | OCR scanned/image PDFs before tagging; pre-tagging export | Matches our SOPs |
| **PAC (PDF Accessibility Checker)** | Post-remediation PDF/UA validation: structure tree, reading-order preview, compliance report | Framework cites PAC 2021; we standardize on the current release (our SOPs say PAC 2024) — same tool, use latest |
| **Allyant (CommonLook)** | Professional outsourced remediation | **Master Procurement Agreement in progress for discounted rates** — our Tier-C/overflow lane |
| **UDOIT** | Canvas scanning, prioritization data, alternate formats | CSU-negotiated |
| **TidyUP** | File audit, duplicate/outdated cleanup, backlog by type/age/usage | "Triage before remediating" |

Vendor escalation triggers it names: document too complex/large to be practical in-house; workflow at capacity causing delays; staffing shortage threatening continuity. Media vendors named: **Verbit, Echo Labs** (via platform integrations, e.g. Verbit-in-Panopto).

## 11. Where it diverges from / adds nothing to our plans

- **Deadline is stale** (April 2026 throughout, incl. the Cal State LA presidential memo) — superseded by the April 26, 2027 IFR; see `../background-research.md` §2.
- **Request-driven posture:** its whole-course lane is instructor-consent/request-initiated. Our Phase 4 DPRC-enrollment triage goes further than anything in it — the framework's accommodation-triggered outreach (AIM) is the closest thing and still waits for a faculty form submission. Our plan to proactively rank and remediate remains the novel piece.
- **No document census layer** — it leans entirely on Ally/UDOIT scores; CanvasBot's inventory role is untouched.
- **Public-facing web/mobile section (§6)** is out of our program's current scope (AT web team territory) but useful if scope ever expands.

## 12. Immediate actions this reading generates

1. **Daniel → SFSU ATI coordinator:** SFSU's IFT student-assistant funding status (round 1 use, round 2 requirements); our Equidox seat count in the 72-license pool; Allyant MPA status/pricing; access to the ATI Remediation Hub Canvas course (assets: job descriptions, examples) for the whole core team.
2. **Phase 1:** adopt Chico throughput benchmarks for capacity planning; add CO ATI Acrobat video series + Cal Poly MIDAS Commons template to the training catalog; name Allyant as the default outsource lane pending the MPA.
3. **Phase 2:** adopt framework §4 as the operational blueprint (course duplication in a sub-account, Designer role, pre/post score capture, TidyUP-with-archive, unpublished maintenance module on return).
4. **Phase 4/6:** adopt the AIM campaign mechanics (provost → deans → personalized wave notifications → recognition w/ RTP citation) as the outreach template.
5. **Reporting:** mirror the framework's section KPI checklists in our Phase 5 dashboard so CO ATI reporting is a query, not a project.
