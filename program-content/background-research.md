# Canvas LMS Digital Accessibility Remediation — Background Research

*Prepared for the SFSU AT Canvas Remediation Program · July 2026*
*Method: multi-agent web research across 23 primary sources; 18 key claims adversarially verified (3 independent checks each). Claims from sources whose verification pass did not complete are included where the source is a primary institutional page; treat those as single-sourced.*
*Updated July 2026 to integrate the `research/` folder: the **CSU ATI Digital Content Remediation Prioritization Framework** (the CO's official systemwide playbook — full reading: `research/csu-ati-remediation-framework-reading.md`), the ATI Remediation Hub, the CSU STEM Course Materials Accessibility Working Group findings, the **Accessible Math practical remediation guide** (full reading: `research/accessible-math-reading.md`), the CSUSM faculty guide, and the ASU PDF_Accessibility pipeline (`research/asu-pdf-accessibility-reading.md`).*

---

## 1. Executive Summary — What This Means for SF State

1. **The compliance deadline moved to April 26, 2027 — but the CSU says don't slow down.** On April 20, 2026, the DOJ published an Interim Final Rule extending the ADA Title II digital accessibility deadline from April 2026 to **April 26, 2027** for large public entities (April 2028 for entities under 50k population). WCAG 2.1 AA remains the standard, obligations remain fully in effect, and the CSU Chancellor's Office ATI directive is explicit: campuses should "redouble their efforts" and use the extra year to *improve quality, build sustainable practices, and ensure consistent outcomes* — which is precisely a mandate for the kind of standardized, lifecycle-driven program SF State is building. ([CSU ATI](https://ati.calstate.edu/policy/2026-title-ii-update), [CSUN](https://www.csun.edu/universal-design-center/accessible-technology-initiative/ada-title-ii-update), verified 3-0)

2. **LMS content is squarely covered — the DOJ deliberately removed the course-content exemption.** The final rule dropped proposed exceptions for password-protected class/course content at public postsecondary schools, so Canvas course content must meet WCAG 2.1 AA. Legacy documents are excepted *only if no longer used*; anything students still rely on in an active course requires remediation. Compliance can't be contracted away to vendors (relevant to Instructure, the captioning vendor, and any tool SF State buys).

3. **The dominant successful program model is a three-legged stool: minimum faculty requirements + faculty support/training + central remediation services.** No campus succeeds with only one leg. Within central services, the recurring staffing pattern is **hub-and-spoke**: student employees handle basic content at scale; professional specialists handle complex content (STEM, LaTeX, multilingual, data visualizations); department liaisons provide a single point of contact. SF State's student-assistant model matches national practice exactly. (UW report, verified 3-0)

4. **Every CSU peer deploys UDOIT as an instructor-facing, distributed tool — SF State's centralized-service ambition goes beyond most peers, and that's an opportunity.** CSUN, Cal State LA, CSUSB, and CSU Fullerton all run UDOIT as faculty self-service. Fullerton is the closest analog to SF State's plan: a central **"Titan Accessible"** remediation service run out of Academic Technology, with all requests tracked in ServiceNow. Pair UDOIT's institutional-level scanning (and the free Cidiscape batch-scan admin tool) with a central work queue and SF State leapfrogs the pure self-service model.

5. **Prioritization at peer campuses is mostly severity- or request-driven, *not* disability-enrollment-driven — SF State's DPRC-coordination plan would be ahead of the field.** The closest existing patterns: the CCC alternate-media workflow (DSPS students notified 4+ weeks pre-term so requests front-load remediation) and CSU Fullerton (AIM Specialist added as TA to accommodated students' Canvas courses for direct material access). A course-level triage feed from DPRC enrollment data is a genuine innovation with clear precedent components.

6. **AI's accepted role is narrow: prioritization input and first-pass drafts with mandatory human review — never a substitute.** EDUCAUSE and UW both document that overlays/auto-fixes don't change underlying structure and can create new barriers. UW's practices are a good template: contractual bar on vendors training AI models on university content; ASR captions acceptable only for low-priority single-use video; accuracy thresholds route everything else to human review.

7. **Don't build training from scratch.** The CCC Accessibility Center catalog (WebAIM Document Training cohorts, a 5-course PDF series covering OCR/tables/tagging, 20-minute "Accessibility Basics" micro-courses with badges) is free but formally limited to CCC employees — a partnership/access question to resolve. Clemson's prerequisite-sequenced PDF curriculum is public and directly reusable for student-worker training. **Correction to our kick-off framing: AIMHub is not a training resource** — it's the CSU/CCC accessible-materials *exchange* (alternate media file sharing for verified-disability accommodations), and SF State should use it for exactly that.

8. **The Chancellor's Office has published an official playbook for exactly this program — and funds it.** The **CSU ATI Digital Content Remediation Prioritization Framework** (rev. 03/2025; full reading in `research/csu-ati-remediation-framework-reading.md`) is the CO's first structured guidance on campus LMS remediation, and it validates our architecture nearly point for point: student-assistant central teams, work-study staffing, trickle-down training with student leads, TidyUP→UDOIT triage, course-copy remediation, on-demand lanes with 24–48h urgent SLAs, and section-by-section KPI checklists. Critically, **CO ATI issued student-assistant hiring funds to every campus (FY24–25 IFT) with a second round allocated on demonstrated progress** — our Phase 5 metrics are also the funding case. Confirm SFSU's allocation with the ATI coordinator.

9. **Systemwide tooling and vendor lanes already exist — use them before buying anything.** CSU holds a **72-concurrent-user Equidox license (~3 seats per campus, unlimited named accounts, more negotiable)**; an **Allyant (CommonLook) Master Procurement Agreement** for discounted outsourced remediation is in progress (our natural Tier-C/overflow lane); the ATI Remediation Hub Canvas course carries **CO-produced Acrobat training videos for student assistants** (~70 min across 5 modules) plus job-description templates and the Cal Poly **MIDAS** Commons template for standing up student remediation teams; **PAC** is the prescribed free PDF/UA QA gate. Chico State's decade-refined throughput data (avg **1 hr/easy file, 4 hrs/difficult file** per trained student; 17 students × 11 hrs/wk ≈ 1,060 files/month) is our capacity-planning benchmark.

10. **"Passes the checker" does not mean "readable" for STEM/math content.** The CSU STEM Course Materials Accessibility Working Group's NVDA testing (Dec 2025, `research/STEM_WG_Summary12_2_25.docx`) found complex math garbled in *every* pipeline tested — LaTeX→Pandoc HTML, MathML, R/Quarto HTML — even in files that pass tagging checks in Canvas; faculty could not reconstruct their own formulas from audio. HTML beats PDF but is still imperfect; RStudio itself is unusable with screen readers. This hardens our Phase 1 rule that STEM is an escalation category, adds **NVDA listening checks as the real QA gate for math**, and gives us a systemwide WG to escalate to instead of solving math accessibility alone. **We now also hold the production workflow for the specialist end of that escalation** — math-aware OCR (Mathpix) → rebuild in Word/LaTeX with real equation objects → export via the lanes that preserve math markup (Word Save-As-PDF with structure tags; DAISY WordToEPUB for EPUB 3/HTML with MathML) — from the Accessible Math guide (`research/accessible-math-reading.md`; digest in §13).

---

## 2. Regulatory Context: ADA Title II, WCAG 2.1 AA, and the CSU ATI

### The rule
- April 2024: DOJ finalized the ADA Title II rule requiring state/local government entities — explicitly including the CSU — to meet **WCAG 2.1 Level AA** for web content and mobile apps used to deliver programs, services, and activities. This encompasses Canvas course content. ([CSU ATI](https://ati.calstate.edu/policy/2026-title-ii-update), verified 3-0)
- WCAG 2.1 AA is the *floor*; newer standards (2.2) are permitted if equal or better.

### The deadline (updated April 2026)
- **Original:** April 24, 2026 (entities ≥50,000 population).
- **Current:** DOJ Interim Final Rule published April 20, 2026 extends the deadline to **April 26, 2027** for large entities; April 26, 2028 for small entities and special districts. (Verified 3-0 against CSU ATI, CSUN, Cal State LA, and legal-analysis sources.)
- The extension is a **timing adjustment only** — DOJ attributes it to implementation challenges, not reduced expectations. (Verified 3-0)
- **Cal State LA's guidance adds a wrinkle:** newly created/published web content must comply with WCAG 2.1 AA **as of April 24, 2026** — i.e., *new Canvas content must be born-accessible now*; the 2027 date governs legacy remediation. (Verified 3-0; this is one campus's published interpretation — worth confirming with CO ATI.)
- Separate track: HHS's Section 504 rule keeps a **May 2026** deadline for HHS-funded entities; not extended by the DOJ IFR.

### Scope and exceptions (what legally must be remediated)
Four exceptions matter for LMS work, per CSUN's and Cal State LA's published interpretations:
1. **Archived web content** — content 3+ years old, kept for reference, unmodified.
2. **Pre-existing conventional electronic documents** (Word/PPT/PDF/spreadsheets created before the compliance date) — **unless still used to access or participate in services.** Active course documents cannot be exempted as "pre-existing."
3. **Third-party content** with no university contract.
4. **Password-protected documents for a specific individual.**

Critical caveats:
- The proposed exception for **password-protected course content was deliberately removed** from the final rule — the DOJ said it "would exacerbate existing educational inequities." Canvas courses are covered.
- Excepted documents must still be provided in accessible form **on request, in a timely manner** (Cal State LA frames ~5 business days as reasonable for archival content).
- **Compliance cannot be outsourced**: vendor-operated platforms and deliverables (LMS, captioning vendor output, embedded tools) must meet WCAG 2.1 AA on the university's behalf.
- DOJ's own commentary: proactive remediation during the compliance window is "more efficient and effective" than reactive scrambling — reactive/on-demand remediation is the most expensive mode.

### CSU governance
- Title II readiness runs through the **CSU ATI's existing mechanisms**: the ATI Capability Maturity Model and annual campus reporting, which the Chancellor's Office says now formally align with what the DOJ rule requires. (Verified 3-0)
- Systemwide posture post-extension: "stay the course," redouble efforts, use the year for quality and sustainability. (Verified 3-0)
- **The operational arm of that posture is the CSU ATI Digital Content Remediation Prioritization Framework** (rev. 03/2025, CC-BY 4.0) — the CO's first structured campus-remediation guidance, distributed with an assets library through the **ATI Remediation Hub** Canvas course, and backed by **targeted student-assistant hiring funds (FY24–25 IFT to all campuses; round 2 tied to demonstrated progress)**. Note it predates the deadline extension — its April 2026 dates are stale; its structure is not. Full reading: `research/csu-ati-remediation-framework-reading.md`.
- Peer example of ATI planning: CSU Fullerton's 2025–2029 ATI Plan reorganizes campus accessibility work explicitly around the Title II deadline, with its ATI Steering Committee assessing progress on the deadline date.

---

## 3. Program & Service Models at Other Campuses

### The three-element model (University of Washington)
UW's Course Content Working Group on PDF Accessibility (March 2025) — the most thorough public program-design document found — concludes a successful model combines **three elements, not one** (verified 3-0):
1. **Minimum faculty requirements** — e.g., meet or exceed a minimum LMS-checker course score (suggested: Ally score ≥80%), paired with an institutional bargain: *"if you meet these minimum requirements, we'll help you do everything else you need."*
2. **Faculty support** — training, templates, consultation.
3. **Central services** — professional remediation for what faculty can't do.

### Staffing: hub-and-spoke with a student tier
UW's recommended structure (verified 3-0), matching SF State's plan almost exactly:
- **Student staff handle basic content at scale.**
- **Professional staff with subject-matter expertise** handle complex, discipline-specific remediation: STEM/LaTeX, languages/multilingual, visual arts, data visualizations, math notation.
- **Departmental liaisons / faculty ambassadors** give each unit a single point of contact while central staff divide work efficiently.

### Named models worth knowing
| Model | Description |
|---|---|
| **Northwestern model** | Central accessibility teams remediate *all* Canvas PDFs on faculty's behalf. |
| **Georgia Tech AccessCorps** | Students enroll in credit-bearing courses to learn and practice remediation — a workforce pipeline. |
| **CSU Fullerton "Titan Accessible"** | Central remediation service (documents, course readers, audio/video) promoted via Academic Technology and college-based instructional designers; every request tracked in ServiceNow. The closest CSU analog to SF State's plan. |
| **UW-Whitewater CATLST** | Teaching-center-run PDF remediation service **staffed by student employees**; faculty upload inaccessible PDFs for remediation. (Verified 3-0) |
| **Highline College (hybrid)** | Faculty self-serve simple documents via SensusAccess automated conversion; complex documents escalate via an intake form to a central Accessible Technology Program. |
| **MSU liaison model** | Each Major Administrative Unit designates Digital Accessibility Liaisons; central Power BI dashboard delivers unit-level metrics to them. |

UW's report explicitly **rejected PDF bans and Canvas file-type restrictions** as policy options.

### The CSU's own service blueprint (ATI Remediation Framework §4–5)
The framework prescribes a **two-lane central service** every CSU campus should run — the closest thing to a required model for us:
- **Whole-course lane:** instructor request form (personalized links; course URL, type, needed-by date) → task-management board (Kanban or ITSM; example stage models from 7 to 12 stages) → **LMS admin duplicates the course** (work never touches the live shell; copies in a dedicated sub-account; Designer role; students never in courses they take) → capture pre-remediation score → **TidyUP cleanup with full file archive** → remediate (complex work central; easy RCE fixes stay with faculty; STEM/complex escalates to vendor) → QA → return with a completion email and an **unpublished maintenance-resources module inserted in the course**.
- **On-demand lane:** file-upload form, urgency metadata, **24–48 hr urgent / 2–3 business-day standard turnaround**, staff triage, vendor escalation; explicitly also for staff/administrative documents (flyers, handbooks) — plan for that demand.
- **Maintenance loop:** dashboards watch new uploads into remediated courses; faculty-responsibility lapses trigger re-education ("expect a few rounds before habits form"); beyond-scope content auto-opens a ticket.

### Distributed (self-service) reality at CSU peers
CSUSB, Cal State LA, and CSUN all deploy UDOIT as instructor-facing self-service — faculty scan and fix their own courses, with a central unit (Accessible Technology Services at CSUSB; CETL EdTech at Cal State LA) providing support and documentation rather than doing the remediation. Cal State LA splits labor: faculty use UDOIT/UFIXIT for in-Canvas content, while **ITS Campus Accessibility provides free document conversion/remediation for files faculty didn't create or find difficult**. Faculty there are told they are *not* required to fix every flagged issue immediately — a phased posture. **CSUSM** runs the same pattern on the Ally stack: its faculty guide (`research/CSUSM Faculty guide course accessibility.md`) sequences TidyUp cleanup → Ally course report → easiest/lowest-scoring fixes first → built-in Canvas checker → captioning via Panopto/Kaltura, with a monthly self-review cadence and a final checklist — a ready-made template for our Phase 6 faculty-facing guide (swap Ally for UDOIT).

### Governance argument for AT ownership
EDUCAUSE's analysis is direct: **accommodation offices were never designed to be the primary mechanism for institution-wide digital accessibility** — when core content is inaccessible, disability services gets pushed into permanent triage. Systemic accessibility (policies, procurement, templates, born-accessible authoring) must be owned institutionally — IT, academic leadership, procurement — freeing the disability office for individual student needs. This directly supports SF State's structure: AT runs the program; DPRC partners on prioritization and accommodations.

---

## 4. Scanning Tools: UDOIT Deep Dive and the Ecosystem

### UDOIT fundamentals
- Originally built by the **University of Central Florida** as open source; **Cidi Labs** has been exclusive hosting/support provider for the commercial **UDOIT Advantage** cloud version since 2019. Campuses can self-host the open-source version or subscribe to SaaS (priced annually by FTE/student count, Year-1 implementation fee).
- Scans Canvas course content and files against WCAG 2.1: announcements, assignments, discussions, pages, syllabus, modules; flags missing alt text, heading structure, table headers, contrast, captions, non-descriptive links.
- **UFIXIT** fixes flagged issues directly in Canvas, including bulk fixes. Results triage into **High / Medium / Low impact**.
- Cal State LA's deployment computes a **weighted course score: High-impact issues 60%, Medium 30%, Low 10%** — a ready-made severity signal for prioritization and reporting.
- UDOIT Advantage adds: account/course-level scorecards, **historical trend tracking**, batch remediation, smart filtering (scan only in-use content), one-step document→Canvas Page conversion, and **PDF file scanning with alternate-format generation** (HTML, ePub, audio, plain text) — base UDOIT does not remediate documents.
- **Cidiscape** (free companion admin tool for Cidi Labs customers) batches courses and scans them all with UDOIT — the key to institution-scale scanning.
- **Known gaps** (from UW's deployment docs): cannot scan classic quiz questions/question banks (API limitation — descriptions only), does not scan New Quizzes, does not cover every WCAG criterion. UDOIT alone is not a compliance audit.

### Deployment patterns at peers
- **CSUN & Cal State LA:** "clean up then scan" — run **CIDI Labs TidyUP** to remove unused content first, then UDOIT. (Verified 3-0.) Don't pay student-hours remediating content nobody uses.
- **Cal State LA:** UDOIT available in every course but **opt-in per course** via Settings → Navigation (instructor-initiated scanning). (Verified 2-0)
- **CSU Fullerton:** switched from Anthology Ally to UDOIT; uses both tools' analytics to **measure faculty usage** of the tool itself.
- **UW:** runs UDOIT and Ally **simultaneously as complements** (Ally strong on files, UDOIT broader on course content); recommends UDOIT's scanned-PDF→Canvas-page conversion as a remediation path (with copyright caution for course readings).
- **CSUN:** two-tool split — UDOIT for LMS, PopeTech (WebAIM/WAVE-based) for enterprise web scanning.

### Market context
- Canvas has **no native course-level or institution-wide accessibility reporting** — its built-in checker is page-by-page only; third-party tools are required for whole-institution audits.
- Four main vendors: **Anthology Ally** (~73% market share, ~2% growth), **YuJa Panorama** (~17% share, ~48% CAGR — the fast-growing challenger), **UDOIT**, **PopeTech**. Fewer than 1% of US institutions had any dedicated accessibility solution as of 2024.
- Practitioner consensus: tools don't replace staffing — even fully deployed platforms still require instructional designers supporting faculty and disability services supporting students.
- Scanner blind spots for video are significant (see §6): Ally doesn't check videos uploaded directly to Canvas, doesn't check embedded Panopto video, and doesn't flag unedited YouTube auto-captions.

---

## 5. Document Remediation: Workflows, Standards, Staffing, QA

### Scale of the problem (UW's Ally data, one large public university)
- **55,939 image/scanned PDFs** flagged in Canvas between Autumn 2023 and Spring 2024; **over one million total PDF issue occurrences** (6% severe / 58% major / 37% minor).
- UW's disability services accommodation-driven operation in 2023–24: **521 students, 4,500+ accommodation requests across 3,450 courses, 41,000+ pages remediated** (~3,100 pages of math notation), **~$2M** charged for accommodation services. This is the cost baseline of purely *reactive* remediation that proactive programs aim to shrink.

### The reference workflow (Clemson's 9-step PDF sequence)
Clemson publishes the cleanest public remediation checklist, built around Adobe Acrobat, directly usable as a student-worker training/QA sequence:
1. Fix color contrast and descriptive links
2. Scanned as image? → **OCR first** (convert image to real text)
3. Untagged? → run automatic tagging
4. Verify logical reading order
5. Correct tag structure
6. Accurate image alt text
7. Metadata: title, language, security settings
8. Form accessibility
9. **Final QA: run Acrobat's automated accessibility check and resolve all remaining issues**

Two program-design principles from Clemson:
- **Source-first remediation:** PDF-level fixes are lost whenever the source is re-exported. Fix the Word/PowerPoint source where possible; "start with an accessible source."
- **Prerequisite-sequenced training:** remediators complete "PDF Fundamentals" and "Checking PDF Accessibility" modules before touching the workflow guide.

### The CCC alternate-media production standard (California's operational template)
The CCC Accessibility Center's alternate media workflow is the most complete lifecycle model found:
- **Front-loaded intake:** DSPS-approved students notified **at least 4 weeks before term start** to submit alternate-format requests.
- **Every request logged in a tracking system at intake**; process formally closes with the specialist **recording production metrics and delivery information**.
- **Source-first sequencing:** request accessible files from the publisher or the system-level Alternate Text Production Center (ATPC) before converting in-house.
- **Minimum in-house capacity standard:** every college should produce at least short, simple, error-free documents in e-text, braille, tactile graphics, large print, and audio.
- **Reference toolchain:** Adobe Acrobat Professional, **ABBYY FineReader** (OCR), Microsoft Word, Duxbury Braille Translator, campus literacy software (e.g., Kurzweil 3000), braille embosser, high-speed production scanner. (Matches the tool decisions from our kick-off: Acrobat/Equidox for tagging, ABBYY for OCR.)

### The CSU systemwide document toolchain (ATI framework "Recommended Tools & Services")
The framework blesses the same stack and adds the licensing/procurement facts:
- **Acrobat Pro** for final remediation/validation of complex documents, with the **CO ATI student-training video series** (Intro to PDF Accessibility ~15 min · Accessibility Checker ~10 · Tagging Content Correctly ~20 · Remediating Scanned Documents ~15 · Final Review & PAC Testing ~10) hosted in the Remediation Hub.
- **Equidox** for high-volume simple-to-moderate PDFs — **CSU systemwide license: 72 concurrent users (~3 per campus), unlimited named accounts, expandable by negotiation.**
- **ABBYY FineReader** for OCR-first conversion of scanned/legacy documents, with pre-tagging export toward Acrobat/Equidox.
- **PAC (PDF Accessibility Checker)** as the free post-remediation PDF/UA validation gate (structure tree, visual reading-order preview, compliance report). The framework cites PAC 2021; use the current release.
- **Allyant (CommonLook)** for professional outsourced remediation — a **Master Procurement Agreement for discounted rates is in progress**; the framework's stated escalation triggers: impractical complexity/size, workflow at capacity, staffing shortage threatening continuity.
- **UDOIT + TidyUP** CSU-negotiated for scanning and triage ("eliminate duplicate/archived content, create a remediation backlog based on real data").

### Student-worker staffing precedents
- UW-Whitewater: PDF remediation service staffed by student employees, simple faculty upload intake. (Verified 3-0)
- UW (proposed): students embedded per college/department; central experts for logistics, training, escalation.
- Georgia Tech AccessCorps: for-credit course pipeline producing trained student remediators.
- Highline College: automated self-service (SensusAccess) absorbs simple documents so humans only touch complex ones; central intake form for escalation. HTML recommended as best Canvas output format; Word (.docx) for distribution.
- **The CSU ATI framework operationalizes the student model systemwide:** prioritize **work-study** hires (wages partially covered by financial aid) but over-hire and pre-train a bench against award fluctuations; **trickle-down training** — one staffer trains a core of 3–4 students who become student leads training the next cohort; prescribed modules (Acrobat for PDF — required even where Equidox exists, for continuity; WebAIM for Office; vendor materials for captioning); **crosscheck certification** — early work peer/supervisor-reviewed before release; staff retained for complex escalation and QA. Example job descriptions live in the Remediation Hub assets; Cal Poly's **MIDAS** Canvas Commons template packages the team-startup materials.

### Throughput benchmarks (Chico State — ~a decade of student-team data)
The framework's capacity model, "within 20% of estimates consistently over several years": **17 student assistants × ~11 hrs/week**, well-trained.
| File class | Time per file | Per-student weekly output |
|---|---|---|
| Easy (short, well-structured) | avg **1 hr** (top performers ~30 min) | 12–15 (top: 20) |
| Difficult (scanned, complex tables, multimedia) | avg **4 hrs** (range 3–5) | 4–5 |

With 12 students on easy + 5 on difficult: **~265 files/week ≈ 1,060/month**. Use these as Phase 1 planning numbers until our own tracker data supersedes them — and log time-to-completion averages from day one, as the framework itself instructs.

---

## 6. Video & Captioning Workflows

### UW's tiered captioning priority framework (the model to adapt)
| Tier | Trigger | Standard |
|---|---|---|
| **High** | Student has requested a captioning accommodation | **99%+ accuracy** (human-verified) |
| **Medium** | Reused recordings; recordings reported as poorly captioned | **97%+ accuracy** |
| **Low** | Single-use, one-course recordings | Unedited ASR acceptable |

- Rationale: **machine captions are "rarely accurate enough to meet accessibility requirements"** — they require human review/editing. Vendor accuracy estimates can serve as the routing threshold for human review.
- **Vendor price points UW gathered:** 3Play ASR $0.10/min · Echo Labs ASR+human review $0.45/min · Panopto manual $1.00/min · 3Play full manual $1.85/min. For UW's ~2M minutes: ~$3.7M full-human vs ~$900K AI-with-human-review.
- **Scale baseline:** 47,000 recordings created/uploaded in one quarter's courses; >60% had only auto-captions, <2% manual.
- **Scanners don't cover video:** Ally misses direct-to-Canvas uploads and embedded Panopto, and doesn't flag unedited YouTube auto-captions. Caption compliance requires its own tracking (CanvasBot's video inventory capability is directly relevant here).

### Platform strategies at peers
- **CSUN:** move course video into department-managed YouTube or Panopto specifically to simplify captioning; Panopto self-service closed captions.
- **UW-Whitewater:** all instructor video through Kaltura (Canvas "My Media") for automatic captions/transcripts.
- **MSU:** captioning completion metrics (total videos, captioned videos, captioned duration) across YouTube and Kaltura folded into the central accessibility dashboard.
- **CSU ATI framework:** names **Verbit and Echo Labs** as the vendor lane, recommends captioning through streaming-platform integrations where available (e.g., Verbit-in-Panopto), and directs teams to assess **moving stray media (Zoom recordings, instructor YouTube, embedded Canvas media) onto the centralized platform for remediation** — the same consolidation logic as our Canvas Studio policy. (Kick-off context: SFSU intends to exit its Verbit contract, so treat Verbit references as pattern, not prescription.)
- **SF State's Canvas Studio plan matches this pattern** — the policy conclusion from our own kick-off (require faculty upload to Canvas Studio, which handles captioning) is the same consolidation move CSUN/UW-W made with their platforms. The vendor-review tier (professional captioning vendor for accommodation-triggered content) layers UW's high tier on top.

### Staffing pattern
UW's proposed **Student Accessibility Teams**: student workers submit recordings to captioning/audio-description vendors, then **review and edit vendor output before publication**, with a central expert team for training and escalation — a template for how SF State student assistants can own the captioning pipeline around the outsourced vendor.

---

## 7. AI Use — and Its Limits

Consensus across EDUCAUSE and UW sources:
- **Overlays and AI "quick-fix" tools don't change underlying content structure**, can create a false sense of security, and can introduce *new* barriers for assistive-technology users.
- Accepted roles for AI/automation: **testing input, prioritization/triage, first-pass drafts (ASR captions, auto-tagging) with mandatory human review.** Not substitutes for accessible design or human QA.
- **Contractual guardrail (UW/Cidi Labs):** data processing agreement bars the vendor from training AI models on university course materials or user activity. SF State should replicate this clause in any AI-adjacent tool contract, including UDOIT Advantage's SpeedFIXIT.
- DOJ economics argument reinforces this: proactive structured remediation beats reactive automation-dependent scrambling.

This validates SF State's "AI where available, but limited" stance and gives it concrete shape: AI for triage and first drafts; humans (student assistants → specialists) for verification and everything student-facing.

---

## 8. Prioritization Frameworks

### Severity-based triage with SLAs (MSU — the most operationalized model)
- Three tiers defined **functionally by user impact**, not by WCAG checklist order:
  - **Critical** — blocks task completion, no workaround → fix within **2 months**
  - **Significant** — major friction → **4 months**
  - **Minor** — technically non-compliant but doesn't impede tasks → **6 months**
- Notable stance: impact-over-compliance. Pure technical WCAG violations that don't affect users get the longest window.

### Impact/usage-based (Cal State LA)
Legacy content "reviewed and remediated over time, with updates prioritized based on impact and usage." (Verified 3-0)

### The CSU ATI framework's criteria set (§1.5 — the official menu)
Rank courses by: enrollment size · course impact (GE/core vs elective) · frequency/complexity of flagged issues · **high DFW/withdrawal/incomplete rates** (may correlate with unaddressed barriers) · **gatekeeper status** (required for graduation/major progression) · **accommodation-request history** · **instructor readiness/willingness** (maximize short-term impact) · **reuse across sections and semesters** (ROI amplifier). Pilot on "jumbo"/high-visibility courses; run a semester-based cycle covering both whole-course and just-in-time needs. It also formalizes **archiving as scope reduction**: matriculated courses controlled via Canvas Terms need no remediation once archived (a recovered course must comply before re-release); watch never-concluded "community courses" (orientation shells).

### The most complete accommodation-triggered campaign on record (Cal State LA "AIM for Student Success," in the framework's appendices)
The end-to-end mechanics, directly reusable: provost announces the no-cost service campus-wide → deans amplify with supplied toolkits → faculty teaching courses **where a student has an accommodation request** get **personalized request-form links in notification waves** (~2-week cadence, two dean follow-ups for non-responders) → on consent, CETL copies the Canvas course, ITS remediates the copy, faculty imports it for the coming term → completion email covers what was fixed, import steps, and upkeep → faculty recognized as **"Accessible All-Stars"** (showcase page, digital badge, chair/dean notified, explicitly encouraged for **RTP dossiers**). Still request-gated — faculty must return the form — which is exactly the gap SF State's enrollment-driven triage would close.

### Request-driven (CSU Fullerton)
Prioritizes faculty who actively reach out; each semester an automated-plus-manual evaluation produces a summary report of LMS content requiring remediation, presented to IT management.

### Accommodation-driven / disability-services-coordinated (closest to SF State's DPRC goal)
- **CCC model:** DSPS students notified ≥4 weeks pre-term; their requests front-load and drive the remediation queue.
- **CSU Fullerton:** AIM Specialist is added as a **TA in the Canvas courses of students approved for alternate-format accommodations**, giving remediation staff timely direct access to course materials.
- **UW captioning:** accommodation request = automatic top tier.
- **Notably absent anywhere:** systematic enrollment-data-driven course triage (scan DPRC registrations each term → rank course shells → proactively remediate before the student hits a barrier). Published frameworks (MSU explicitly) prioritize by generic severity, not disabled-student enrollment. **SF State building this would be genuinely novel**, assembled from proven parts: Fullerton's DPRC-AT data link + CCC's lead-time standard + MSU's severity SLAs.

### Scope reduction as a strategy (UC Riverside)
UCR archived thousands of legacy/inactive Canvas courses (K16 Solutions' Canvas Archiving) rather than remediating everything — concentrating effort on active courses while keeping historical content retrievable. (Caveat: source is K16-sponsored vendor content.) The cheaper equivalent for SF State: TidyUP-style cleanup and an archiving policy before remediation begins — never remediate content nobody uses.

---

## 9. Lifecycle Management, Tracking, and Reporting

### Intake → tracking → metrics (the CCC lifecycle template)
Every request logged at intake in a tracking system; production proceeds through acquire-source → convert → QA → deliver; process closes with **production metrics and delivery information recorded**. AIMHub's project rationale states the underlying pain point: campuses keep reinventing organizational/tracking systems, and that administrative overhead steals time from actual remediation — an argument for building SF State's tracking layer once, properly, with the engineering team.

### Ticketing
CSU Fullerton stores **all remediation requests in ServiceNow** — remediation-as-a-service with standard enterprise ticketing. SF State can adopt the same pattern or build a purpose-specific queue (see the lifecycle-tooling plan file).

### Dashboards (MSU's Power BI Accessibility Dashboard — the reference implementation)
- LMS course accessibility scores (their "Spartan Ally" deployment) as aggregate percentage + course counts **by department**, refreshing weekly.
- **Video captioning tracking** across platforms: total videos, captioned videos, captioned duration.
- Website scores (Silktide vs WCAG 2.2 AA) triaged critical/significant/minor, weighted by page count.
- **Training completion rates and vendor VPAT status folded into the same leadership-facing view.**
- Access role-gated to unit liaisons; primary liaisons can sponsor additional users.

### The framework's built-in reporting vocabulary
Every section of the CSU ATI framework closes with an **Implementation Checklist (KPIs)** — baseline data generated, stakeholders convened, prioritization rubric built, request-form response rates, turnaround times, courses/files remediated, student hours, training completions, **cost-avoidance metrics** — and the advanced guide prescribes SMART monthly targets by modality/course tier, quarterly leadership reviews, and ticket-closure surveys. Mirroring these checklists in our Phase 5 dashboard makes CO ATI reporting (and the round-2 funding case) a query instead of a project. Its maintenance pattern is also concrete: dashboards watch **new uploads into remediated courses**; faculty-scope lapses trigger re-education follow-ups; beyond-scope items auto-open tickets.

### Reporting cadences seen in the field
- Ally-using institutions run **quarterly institutional reports**, track trends over time, share with leadership, and use issue-area summaries to plan training; Canvas **sub-accounts produce department/division-level reports**. Faculty-contract rules can constrain admin scanning of individual instructors' courses — check SFSU's CBA implications early.
- CSU Fullerton: semesterly LMS content summary reports to IT management.
- UDOIT Advantage natively provides course/account scorecards + historical trends — the data source for most of this without custom scraping; CanvasBot can fill the gaps (video inventory, document census) UDOIT doesn't cover.

---

## 10. Custom Tooling Built by Universities

- **UDOIT itself** is the flagship precedent: built by UCF, open-sourced (GitHub), later commercialized through Cidi Labs — proof that university-built LMS accessibility tooling can become ecosystem infrastructure.
- **AIMHub** (CSU + CCC systems): unified web platform for exchanging already-converted accessible instructional materials between campus disability offices. Launched Aug 2017 (CSU, replacing CSU CAM) / June 2018 (CCC, replacing AMX Database). Strictly accommodation-driven (verified print disabilities); an *exchange*, not a repository — no permanent storage of copyrighted materials; legally grounded in the Chafee Amendment (17 U.S.C. §121) and California AB 422/AB 386. Open to CSU, UC, and CCC campuses. **Use it to avoid re-converting textbooks another campus already did.**
- **Cidiscape** (Cidi Labs, free): batch/institution-scale UDOIT scanning.
- **K16 Canvas Archiving** (vendor, used by UCR): legacy-course archiving to shrink remediation scope.
- **SensusAccess** (used by Highline): automated self-service document conversion absorbing the simple end of the demand curve.
- **CanvasBot v2** (SF State, https://github.com/Fontaineconsult/canvas-bot-v2): content-graph extraction/inventory of Canvas courses — the census layer none of the commercial scanners fully provide (especially for video sources and file inventories across courses). Position it as the data backbone for prioritization and progress reporting rather than as a remediation tool.
- **ASU PDF_Accessibility** (Arizona State AI Cloud Innovation Center, MIT, https://github.com/ASUCICREPO/PDF_Accessibility): open-source, AWS-native **batch** PDF remediation pipeline — Adobe Auto-Tag API + Amazon Bedrock AI alt-text (PDF→PDF), and Bedrock Data Automation + Nova Pro (PDF→HTML) — targeting WCAG 2.1 AA at ~cents/page vs. $1–$4/page manual. Higher-ed origin (Ohio State Libraries), same ADA Title II driver. A candidate **bulk "first-pass lane"** for the legacy backlog, ahead of human QA; requires AWS/Bedrock + Adobe API, a FERPA/data-governance review, and is a prototype ("not warranted for production"). **Full reading:** `research/asu-pdf-accessibility-reading.md`.

---

## 11. Reusable Training Resources (Don't Build From Scratch)

| Resource | What it is | Access constraint |
|---|---|---|
| **CCC Accessibility Center self-paced catalog** | Free courses hosted in the @ONE Canvas Catalog (CVC@ONE account required) | Formally limited to **CCC system employees** — SF State needs to resolve access (partnership, or use as syllabus blueprint) |
| **WebAIM Document Training** (via CCCAC) | Facilitated cohorts starting first Monday monthly, in WebAIM's Canvas instance; 60-business-day window; Certificate of Completion | Registration via CCCAC |
| **CCCAC PDF Accessibility series** | 5 courses: OCR, accessible tables, common/less-common PDF grouping tags, block tags — maps exactly onto student-assistant PDF training needs | Same as above |
| **CCCAC "Accessibility Basics" micro-courses** | 8 non-facilitated ~20-minute modules (alt text, captions, doc structure, tables, contrast, links, emails, plain language) with digital badges — ideal student-worker onboarding format | Same as above |
| **Clemson Digital Accessibility guides** | Public, prerequisite-sequenced PDF curriculum: Fundamentals → Checking → 9-step Remediation workflow | **Public, no constraint** |
| **Cidi Labs UDOIT User Guide + Video Library** | Vendor training used by CSUSB instead of building in-house | Public/customer |
| **UW-Whitewater "Accessibility in Action"** | Workshop series model (Digital Accessibility 101, Slides & Video, Canvas Pages + UDOIT, Accessible Data) + two self-paced Canvas courses | Public pages; format to imitate |
| **CO ATI Acrobat video series** ⭐ | 5 modules (~70 min total) built for **student-assistant onboarding**: Intro to PDF Accessibility · Accessibility Checker · Tagging Content Correctly · Remediating Scanned Documents · Final Review & PAC Testing | In the **ATI Remediation Hub** Canvas course — get team access via the SFSU ATI coordinator |
| **ATI Remediation Hub assets** | Example student job descriptions, campaign examples, Equidox guides, framework companion files | Same access route |
| **Cal Poly "MIDAS Document Remediation Resources"** | Canvas Commons template packaging startup materials for a student remediation team | Canvas Commons (CSU) |
| **CSUSM faculty guide** | One-page faculty self-service sequence (TidyUp → accessibility report → easy fixes → checker → captions) with a final checklist | In `research/`; template for our Phase 6 faculty guide (swap Ally→UDOIT) |
| **AIMHub** | ⚠️ *Not training* — CSU/CCC alternate-media **exchange** for accommodation-driven materials | Open to CSU campuses; use for document exchange, not curriculum |

---

## 12. Synthesis: Design Implications for SF State

1. **Timeline:** ~9.5 months to April 26, 2027 for legacy content; born-accessible expectations for new content arguably already in effect (April 2026, per Cal State LA's reading). CSU CO says use the extension for quality and sustainability — exactly the mandate for standardized processes over heroics.
2. **Model:** Adopt the three-element structure (requirements + support + central service). SF State already has the central-service and support legs planned; the *minimum-requirements* leg (e.g., a UDOIT score threshold with an institutional support bargain) needs a policy conversation with Academic Senate/administration later — Phase 6 material. **The CSU ATI framework now supplies the official two-lane service blueprint (whole-course + on-demand) — align our Phase 1/2 operations with it so our program reads as framework implementation, not local invention.**
3. **Staffing:** Hub-and-spoke is validated everywhere — and **funded**: CO ATI issues student-assistant hiring money (round 2 tied to demonstrated progress). Adopt the framework's work-study-first, over-hire-and-bench, trickle-down-training, crosscheck-certification model; plan capacity with Chico's benchmarks (~1 hr easy / ~4 hrs difficult per file) until our own tracker data supersedes them. Define the escalation boundary (STEM/math notation, complex tables, forms, braille/tactile) to specialists or the **Allyant MPA lane**; liaison contacts per college as the program matures.
4. **Scan strategy:** TidyUP-style cleanup → UDOIT scan → prioritized queue. Get Cidiscape (or UDOIT Advantage institutional scanning) for batch coverage. Treat UDOIT as necessary-not-sufficient: it misses quizzes, some WCAG criteria, and most video — CanvasBot fills the census gap. **For STEM content the gap is worse: passing tag checks ≠ readable math (§13) — NVDA listening checks are the real gate.**
5. **Prioritization:** Build the DPRC-enrollment-driven triage feed — no published peer does this systematically; the components all have precedent (Fullerton's DPRC↔AT data link, CCC's 4-week lead standard, MSU's severity SLAs, Cal State LA's impact/usage weighting, and now the framework's full criteria menu: DFW rates, gatekeeper courses, reuse, instructor readiness). Layer: (a) DPRC-registered courses first, (b) then high-enrollment/high-reuse courses, (c) severity-weighted within each course. The AIM campaign's wave-notification + personalized-form machinery is the outreach half of this system, ready to copy.
6. **Documents first is the right call:** the PDF problem dominates every campus's data (UW: 1M+ issue occurrences), the workflows are the most mature and teachable (Clemson 9-step, CCC toolchain, CO ATI video series), and it's where student labor scales best. Use the CSU seats we already have (Equidox 72-license pool) before buying tools.
7. **Video:** adopt UW's three-tier accuracy framework around Canvas Studio + the outsourced vendor; students QA vendor output; track caption coverage independently of UDOIT/Ally (scanner blind spot) via CanvasBot inventory.
8. **AI:** triage and first-pass only; human review mandatory for anything student-facing; no-training-on-our-data clauses in vendor contracts. The CO's own framing agrees: "AI may handle up to 80% of the workload, but the final 20% demands a human touch."
9. **Lifecycle:** log every item at intake, close every item with production metrics (CCC pattern); ServiceNow-style ticketing or custom queue; MSU-style department-level dashboard for leadership; quarterly trend reporting. **Mirror the framework's per-section KPI checklists so CO ATI reporting and the round-2 funding case fall out of the same data.** Check faculty-contract constraints on course scanning early.
10. **Reuse:** CO ATI Acrobat videos + Remediation Hub assets + Cal Poly MIDAS template (our system), Clemson guides (public), Cidi Labs materials, CSUSM guide as the faculty-facing template, AIMHub for alternate-media exchange. Build only what's genuinely missing: the DPRC triage feed, the CanvasBot-driven content census, and the program dashboard.

---

## 13. STEM & Math Accessibility — WG Findings (Dec 2025) + the In-House Remediation Workflow

*Sources: `research/STEM_WG_Summary12_2_25.docx` — CSU STEM Course Materials Accessibility Working Group, NVDA audio testing of real faculty files (LaTeX, R/Quarto, Pandoc, MathML, HTML) — and `research/Accessible Math.docx`, a practical creation/remediation workflow guide (full reading: `research/accessible-math-reading.md`). The WG supplies the warning; the guide supplies the workflow.*

### What the testing showed
- **Text, tables, and simple math read correctly; complex math fails everywhere.** Square roots, superscripts, nested equations, and symbolic notation came out garbled across *every* pipeline tested — LaTeX→Pandoc HTML, MathML output, R-generated HTML. Faculty could not reconstruct their own formulas from the audio.
- **Passing a tagging check is not evidence of accessibility:** files that "pass" tag scanning in Canvas still failed to read math correctly. (Directly extends §4's "UDOIT is necessary-not-sufficient" to a category where the checker gap is worst.)
- **HTML > PDF, but not solved:** Pandoc/MathML HTML conversions are better than PDF yet still muddle complex expressions — conversion alone doesn't buy compliance for math-heavy content.
- **R specifics:** R-generated HTML reads object references as "dollar sign" repeatedly (students confirmed it's unusable); **RStudio itself is not screen-reader accessible** — blind students need alternative environments (VS Code), and Week-1 setup instructions must say so. Reference: Dr. Jonathan Godfrey's work on R as a blind statistician.
- **Interim guidance from the WG:** author in source (Overleaf/TEX, `.qmd`/`.Rmd`) and output at least one accessible format (HTML or DOCX); **avoid PDF for student-facing math/code materials**; equations-as-images with alt text are acceptable only within character limits and not as a long-term strategy.

### What the WG is building (don't duplicate)
A standard LaTeX→accessible HTML/DOCX workflow; a Quarto template with accessible structure (titles, headings, lists, tables); instructor guidance for supporting blind students in R-based courses.

### The specialist workflow (Accessible Math guide — `research/accessible-math-reading.md`)
What the Tier-C in-house lane actually *does* with a math document:
- **Target-format hierarchy:** HTML+MathML (LMS/OER content) · EPUB 3+MathML (textbooks) · Word with native equations (handouts) · tagged PDF 2.0 (only when PDF is genuinely required — consistent with the WG's "avoid student-facing PDF for math").
- **Rebuild threshold is explicit:** mostly-text with a few simple equations → remediate the PDF; STEM textbook / problem set / research article / any *scanned* math PDF → **recreate from scratch**. Never tag flattened math.
- **Workflow:** math-aware OCR (**Mathpix** full-PDF webapp → Word/HTML/LaTeX/Markdown; MathKicker and EquatIO as alternatives — ordinary ABBYY/Acrobat OCR mangles notation) → rebuild the accessibility skeleton → **verify every equation by hand** (Mathpix Snip → "MathML for Word" for stragglers; Word Equation Editor/MathType; TeXstudio/Overleaf for the LaTeX lane) → alt text/long descriptions for graphs → checkers → **export via the lanes that preserve math markup**: Word File→Save As→PDF with "Document structure tags for accessibility" (per the guide, the *only* Word export producing correct `Formula` tags), or the free DAISY **WordToEPUB** add-in (EPUB 3 with MathML; HTML with MathJax).
- **Math-capable reading tools** for listening QA and alternate-media delivery: Central Access Reader (free, CWU), Kurzweil 3000 (EPUB w/ MathML), EquatIO. NVDA/JAWS remain the compliance gate.
- **Caveats:** Mathpix/MathKicker are cloud — same FERPA/data-handling review as Equidox before student-content uploads; and per the WG's findings, no output of this workflow is done until it **passes a listening check** — "Mathpix converted it" is not evidence.

### Program implications for SF State
1. **Hardens the Phase 1 Tier-C rule:** students never remediate math; even specialists shouldn't trust checker-clean output — **NVDA (or equivalent) listening checks are the QA gate for any math content.**
2. **Escalation destination found:** the systemwide STEM WG is where our hard math cases and workflow questions go — coordinate rather than solve alone (add to the Tier-C routing list alongside vendor/AIMHub).
3. **Source-first is even more binding for STEM:** get the TEX/QMD source and regenerate; tagging flattened math is wasted effort (the WG's data now proves what our SOP asserted).
4. **Faculty guidance (Phase 6):** math/stats course templates should come from the WG's Quarto/LaTeX workflow products; include accessible-IDE setup instructions for data-science courses — plus the guide's authoring rules: native equation editors (Word Equation Editor supports LaTeX input), never screenshots of equations.
5. **In-house Tier-C capacity is now buildable:** the specialist workflow above gives the escalation lane an SOP basis, and the tooling shortlist is concrete — Mathpix license, MathType, WordToEPUB (free), a LaTeX editor, Central Access Reader for listening QA. The bulk-AI lane stays math-free (the ASU pipeline produces no MathML — `research/asu-pdf-accessibility-reading.md`); math content routes here instead.

---

## Sources

**Local research folder (`research/`)**
- CSU ATI — Digital Content Remediation Prioritization Framework, rev. 03/2025 (`Chico LA Systemwide LMS Remediation Framework_v1.pdf`; full reading: `csu-ati-remediation-framework-reading.md`)
- CSU ATI Remediation Hub Canvas course intro (`remediation-hub`)
- CSU STEM Course Materials Accessibility WG — Dec 1 2025 summary (`STEM_WG_Summary12_2_25.docx`)
- Accessible Math — practical creation/remediation workflow guide (`Accessible Math.docx`; full reading: `accessible-math-reading.md`; provenance to confirm)
- CSUSM — Guide to Making Your Canvas Course Accessible (`CSUSM Faculty guide course accessibility.md`)
- ASU AI CIC — PDF_Accessibility pipeline (full reading: `asu-pdf-accessibility-reading.md`)

**CSU / policy**
- CSU Chancellor's Office ATI — 2026 Title II Update: https://ati.calstate.edu/policy/2026-title-ii-update
- CSUN Universal Design Center — ADA Title II Update: https://www.csun.edu/universal-design-center/accessible-technology-initiative/ada-title-ii-update
- Cal State LA — ADA Title II Update: https://www.calstatela.edu/accessibility/ada-title-ii-update
- Cal State LA CETL — Canvas Accessibility (UDOIT): https://www.calstatela.edu/cetl/edtech/canvas-accessibility-udoit
- CSUSB ATS — UDOIT for Canvas: https://www.csusb.edu/ats/instructional-materials/udoit-canvas
- CSU Fullerton — ATI Plan 2025–2029: https://www.fullerton.edu/ATI/_resources/pdfs/CSUF-ATI-Plan2025-2029.pdf
- CSU Chico — Accessible Instructional Materials procedures: https://www.csuchico.edu/ati/procedures/accessible-instructional-materials.shtml

**Program models / workflows**
- UW Course Content Action Team — PDF report: https://www.washington.edu/accessibility/academic-course-content-action-team/pdf-report/
- UW Course Content Action Team — Video/Audio report: https://www.washington.edu/accessibility/academic-course-content-action-team/video-audio-report/
- UW-Whitewater CATLST — Digital Accessibility Resources: https://www.uww.edu/catlst/digital-accessibility-resources
- Clemson — PDF Remediation guide: https://www.clemson.edu/accessibility/digital/guides/pdf/remediation/
- MSU — Prioritization Guidance: https://webaccess.msu.edu/tools/Prioritization_Guidance
- MSU — Accessibility Dashboard: https://webaccess.msu.edu/liaisons/dashboard
- CCC Accessibility Center — Alternate Media Workflow: https://cccaccessibility.org/alternate-media/alternate-media-workflow
- CCC Accessibility Center — Self-paced training: https://cccaccessibility.org/index.php/tools-training/self-paced
- AIMHub: https://aimhub.org/

**Tools / market / legal analysis**
- Cidi Labs — UDOIT: https://cidilabs.com/landing/udoit/
- Canvas Community — institution-wide audit thread: https://community.canvaslms.com/t5/Accessibility/Advice-for-Accessibility-audit-across-the-school/m-p/600063
- EDUCAUSE Review — The Case for Embedded Digital Accessibility: https://er.educause.edu/articles/2026/2/the-case-for-embedded-digital-accessibility
- EDUCAUSE (sponsored, K16) — UC Riverside LMS archiving: https://er.educause.edu/articles/sponsored/2025/3/lms-archiving-fast-tracking-wcag-compliance-at-uc-riverside
- Brown & Gold — DOJ web accessibility rule takeaways: https://browngold.com/blog/eight-key-takeaways-from-the-dojs-new-web-and-mobile-accessibility-rule-for-public-entities/
- Jackson Lewis — DOJ deadline extension analysis: https://www.jacksonlewis.com/insights/doj-extends-public-entities-compliance-deadline-ada-related-website-accessibility-hhss-may-2026-deadline-still-looms
- Instructure webinar — Scaling Accessibility in Canvas: https://www.instructure.com/resources/webinar/many-hands-lighter-work-scaling-accessibility-canvas-lms
