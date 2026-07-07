# Training — Curriculum Map

*How a student assistant goes from zero to certified remediator. We reuse existing external curricula (`training-resource-catalog.md`) and gate progress with certification checkpoints; the per-student path lives in `onboarding-checklist.md`.*

## Philosophy

- **Reuse, don't build.** The catalog has enough free/licensed material to train the whole team; we assemble a path through it rather than writing courses.
- **Learn by tier.** Students train and certify on Tier A before touching Tier B, and never do Tier C. Training maps to the same tiers as `../remediation-procedures/00-decision-tree.md`.
- **Certify before live work.** Each tier has a sign-off gate: a QA'd practice document the student must pass before working that tier on real course content.
- **Standards before tools.** Understand *why* (headings, reading order, alt text, WCAG) before *which button* — so skills transfer across Acrobat, Equidox, and Office.

## The learning path (sequence)

### Stage 0 — Foundations (everyone, before any live work)
Goal: understand what accessibility is, who it's for, and the core concepts.
- WCAG 2.1 AA in plain terms; how screen-reader users navigate (headings, reading order, alt text, tables).
- Resources: WebAIM articles → Section508 "Create Accessible Documents" intro → one AccessibilityOnline webinar.
- **Concept check** (short quiz/discussion) before moving on.

### Stage 1 — Tier A skills (basic documents)
Goal: remediate linear text — simple PDFs, Word docs, slides, clean scans.
- **Standards + checker use:** Microsoft Accessibility Checker (Word/PPT/Excel); Acrobat Full Check.
- **Per-type SOPs:** read and practice `../remediation-procedures/` for Word, PowerPoint, born-digital PDF, scanned PDF (OCR), images/alt text.
- **Core course:** WebAIM Accessible Documents (if licensed via CSU ATI) — covers Office + PDF + Excel with a certificate.
- **PDF depth:** Adobe Acrobat accessibility tutorials + Clemson workflow + Section508 PDF Module 3.
- **→ Tier A certification gate** (see onboarding checklist).

### Stage 2 — Tier B skills (intermediate)
Goal: tables, multi-column layouts, forms, figures needing real alt text, longer documents, OCR of tougher scans.
- **Table remediation** (Acrobat Table Editor: TH/scope/spans); complex reading order; bookmarks; PDF/UA validation with **PAC 2024**; **NVDA** screen-reader spot-checks.
- **Tool proficiency:** Equidox (if adopted) for volume work; ABBYY FineReader for tougher OCR.
- Resources: WebAIM "Reviewing/Repairing PDFs in Acrobat"; LinkedIn Learning "Advanced Accessible PDFs" (if SFSU has access); Section508 spreadsheets/PDF series.
- **→ Tier B certification gate.**

### Stage 3 — Growth / specialist (selected students, program leads)
Goal: deeper expertise, QA reviewer role, and the boundary of Tier C.
- Deque University; IAAP **ADS (Accessible Document Specialist)** credential as a stretch goal.
- Screen-reader fluency; QA/sign-off responsibility; mentoring new students.

## Tool-specific training (as we adopt each tool)
- **UDOIT / Cidi Labs** — for Phase 2 course-shell work (knowledgebase + vendor video series).
- **Equidox** — vendor guides (zone-based remediation).
- **ABBYY FineReader** — OCR verification and PDF/UA export.
- **PAC 2024** — the QA gate; free, Windows.
- **NVDA** — free screen reader for spot-checks.

## Open action items
- [ ] **Confirm with SFSU ATI coordinator what's licensed** (WebAIM course, CCC micro-courses, LinkedIn Learning, Deque) — this determines the exact path and cost. *(Owner: Daniel)*
- [ ] Decide primary PDF tool (Equidox vs Acrobat) so Stage 1–2 training standardizes on it. *(See `../process-documentation/note-tool-decision.md`.)*
- [ ] Build the Tier A and Tier B **practice-document sets** with known issues for certification.
- [ ] Set the concept-check and gate rubrics.

See `training-resource-catalog.md` for every resource (links, cost, access) and `onboarding-checklist.md` for the trackable per-student path.
