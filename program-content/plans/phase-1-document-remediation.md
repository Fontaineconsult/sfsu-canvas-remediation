# Phase 1 — Document Remediation Service

*Status: **ACTIVE** — top program priority. Student team exists; responsibility assigned to Academic Technology.*
*Research basis: background-research.md §5, §11, §12.*

> **📂 Detailed build-out lives in [`phase-1/`](phase-1/README.md).** This file is the phase-level plan (objective, workstreams, deliverables, metrics). The `phase-1/` subsystem holds the working materials:
> - **`phase-1/remediation-procedures/`** — a cited SOP per file type (decision tree, born-digital PDF, scanned/OCR PDF, Word, PowerPoint, Excel, images/alt text, HTML/Canvas Pages, STEM escalation).
> - **`phase-1/training/`** — the verified training-resource catalog, curriculum map, and per-student onboarding checklist with certification gates.
> - **`phase-1/process-documentation/`** — the system + templates for capturing SF-State-specific local process knowledge.

## Objective

Stand up a standardized, teachable, measurable document remediation operation (PDF + Microsoft Office) run by student assistants under AT, with a defined escalation path for complex content.

## Why documents first

- PDFs dominate every campus's problem data (UW: 55,939 scanned PDFs, 1M+ PDF issue occurrences in one year).
- Workflows are the most mature and teachable — ideal for student labor.
- Kick-off already categorized the work: AI-suitable / manual tagging (Equidox/Acrobat) / OCR-needed (ABBYY) / STEM.

## Workstreams

### 1.1 Standard operating procedures (Daniel + Cristian lead, per kick-off)
Write one SOP per document category. Base the PDF SOP on Clemson's 9-step sequence:
1. Contrast + descriptive links → 2. OCR if scanned (ABBYY) → 3. Auto-tag if untagged → 4. Reading order → 5. Tag correction (Equidox or Acrobat) → 6. Alt text → 7. Metadata (title, language, security) → 8. Forms → 9. Acrobat automated check as final QA gate.

Principles to encode in every SOP:
- **Source-first:** if the Word/PPT source exists, fix it there — PDF-level fixes die on re-export.
- **Prefer conversion over remediation** where content allows: HTML/Canvas Pages are easier to keep accessible than PDFs (UDOIT's PDF→Page conversion; watch copyright on course readings).
- **Never remediate unused content:** TidyUP-style cleanup / usage check before any document enters the queue.

Categories needing SOPs: (a) born-digital PDF, manual tag; (b) scanned PDF, OCR-first; (c) Word/PowerPoint source available; (d) AI-assisted first pass + human QA; (e) STEM/math — **escalation, not student work** (define handoff: specialist, outsource, or defer).

### 1.2 Complexity tiering & escalation boundary
- **Tier A (student, basic):** simple articles, syllabi, handouts, clean scans.
- **Tier B (student, trained):** multi-column layouts, tables, forms.
- **Tier C (escalate):** math/STEM notation, complex data viz, multilingual, braille/tactile requests (route accommodation-driven items via DPRC/AIMHub; check ATPC-equivalent options).
- CCC minimum-capacity benchmark: the shop should at least produce short, simple, error-free e-text reliably before scaling.

### 1.3 Training curriculum (reuse, don't build)
Full detail in [`phase-1/training/`](phase-1/training/README.md); verified catalog in `training-resource-catalog.md`.
- Skeleton: Clemson's prerequisite sequence (Fundamentals → Checking → Remediating). Public, no license issues.
- **⚠️ Access correction:** SFSU is **CSU, not CCC** — the CCC Accessibility Center catalog is gated to CCC employees and is **not** directly available to us. **Our channel is CSU ATI**, which may already license the WebAIM Accessible Documents course and CCC micro-courses systemwide. **Action (Daniel): confirm with the SFSU ATI coordinator what's licensed (WebAIM course, CCC micro-courses, LinkedIn Learning, Deque, ABBYY/Equidox/UDOIT) before paying for anything.** This supersedes the earlier "resolve CCC access" note.
- Free/authoritative backbone available to anyone: WebAIM articles, Section508 video modules, Microsoft in-app guides, Adobe Acrobat tutorials.
- Certification gate: student must pass a QA'd sample document per tier before working that tier live (see `onboarding-checklist.md`).

### 1.4 QA process
- 100% QA on each student's first N documents per tier, then sampling.
- **Two-gate standard on every document** (detailed in the SOPs): (1) automated — Acrobat Full Check clean **and PAC 2024 (PDF/UA + WCAG 2.1) clean** for PDFs / Office Accessibility Checker clean for source files; (2) human — reading order, heading logic, meaningful alt text, table-header logic, with **NVDA** screen-reader spot-checks for Tier B.
- Log QA results per student per tier — feeds training loop and progress reporting.

### 1.5 Intake & tracking (minimal viable — full system is Phase 5)
Adopt the CCC lifecycle rules from day one, even if the tracker is a spreadsheet:
- **Every document logged at intake** (course, instructor, category, tier, requester, date).
- **Every document closed with production metrics** (time spent, pages, issues fixed, QA result, delivery date).
- These records are the raw material for Phase 5 dashboards and leadership reporting — don't skip them.

### 1.6 Sourcing the work queue
Until Phase 2/4 provide scan- and DPRC-driven queues:
- DPRC accommodation requests (immediate, highest priority — 4-week pre-term lead-time target per CCC standard).
- Faculty submissions (simple upload/intake form — UW-Whitewater pattern).
- CanvasBot document census of selected high-enrollment courses (early engineering win; see Phase 5).

## Deliverables

- [x] **SOP per file type** — drafted & cited in `phase-1/remediation-procedures/` (PDF born-digital, scanned/OCR, Word, PowerPoint, Excel, images/alt text, HTML/Canvas, STEM escalation). *Next: core-team review; validate menu paths against installed tool versions.*
- [x] **Tiering rubric + escalation decision tree** — `phase-1/remediation-procedures/00-decision-tree.md`.
- [x] **Training path + verified resource catalog** — `phase-1/training/`. *Next: confirm CSU ATI licensing; build practice-document sets.*
- [x] **Process-documentation system** — templates + log in `phase-1/process-documentation/`. *Next: write the starter local docs.*
- [ ] QA checklist + sampling policy formalized (two-gate standard defined in SOPs; sampling thresholds TBD)
- [ ] Intake form + tracking log (minimal viable — schema drives Phase 5)
- [ ] Tool decision recorded (Equidox vs Acrobat primary) + licenses/access set up
- [ ] First cohort of student assistants certified on Tier A
- [ ] First monthly production report (documents in/out, turnaround, QA pass rate)

## Metrics

Documents remediated per week (by tier) · median turnaround · QA first-pass rate · % source-first vs PDF-only fixes · escalation rate · DPRC-request turnaround vs 4-week standard.

## Open questions

- **Equidox vs Acrobat as the *primary* student tool.** Research favors Equidox for student usability (visual zone model vs. Acrobat's tag tree) on routine/volume work, with Acrobat retained for edge cases and final tag inspection. **FERPA caveat:** Equidox is cloud — files leave our environment, so resolve data-handling before uploading anything with student info. Decide and record in `phase-1/process-documentation/note-tool-decision.md`.
- Which AI-based PDF remediation tool (if any) for AI-assisted first pass, and what human-review protocol wraps it (AI-limited stance from background research: triage/first-pass only, mandatory human review, no-training-on-our-data clause).
- ~~CCC training access mechanics~~ → **Answered:** SFSU is CSU, not CCC; go through CSU ATI. Confirm licensed inventory with the ATI coordinator.
- Copyright review for PDF→Canvas Page conversions of course readings.
- Confirm the QA checker stack: Acrobat Full Check + **PAC 2024** (free, Windows) as the PDF gate; who installs/maintains.
