# Document Remediation Checklist & Readiness — Working Group Review

*Purpose: give the working group one page to review before we remediate our first documents. It covers (1) how ready our infrastructure is, (2) which tools we're using for each task, (3) the actual per-file-type remediation checklist, and (4) the open decisions we need to make together. **Draft for discussion — mark it up.***

*Owner: Daniel · Last updated: 2026-07-06 · Status: for working-group review*

**Status legend:** ✅ Ready · 🟡 In progress / drafted · ⬜ Not started · ❓ Needs a group decision

---

## Part 1 — Infrastructure Readiness at a Glance

| Component | Status | Notes / what's needed |
|---|---|---|
| **Remediation SOPs** (per file type) | 🟡 | Drafted & cited in `remediation-procedures/`. Need: group review + validate menu paths against our *installed* tool versions. |
| **Triage / decision tree** | 🟡 | Drafted (`00-decision-tree.md`). Confirm tier boundaries with the group. |
| **Adobe Acrobat Pro** | ❓ | Confirm license count, version, and how a student gets it. |
| **ABBYY FineReader** (OCR) | ❓ | Likely available via CSU ATI — confirm access. |
| **Equidox** (PDF remediation) | ❓ | Decision needed as primary vs. fallback + **FERPA/data-handling review** (cloud — files leave our environment). |
| **PAC 2024** (QA checker) | ⬜ | Free, Windows-only. Confirm who installs; make it the PDF sign-off gate. |
| **NVDA** (screen-reader QA) | ✅ | Free; can install now for spot-checks. |
| **UDOIT** (course scanning) | ⏭️ | Licensed, but this is **Phase 2** (course shells), not document intake. |
| **Training resources** | 🟡 | Catalog built. Need: confirm CSU ATI licensing (WebAIM course, micro-courses); build practice-document sets. |
| **Intake process** (how work arrives) | ⬜ | Mailbox / form / Box folder — undecided. |
| **Tracking log** (minimal viable) | ⬜ | Schema needed; even a spreadsheet is fine to start (feeds Phase 5). |
| **QA / sign-off policy** | 🟡 | Two-gate standard defined; need sampling thresholds + who reviews. |
| **Process-documentation system** | ✅ | Templates + log ready to use now (`process-documentation/`). |
| **Student staffing** | 🟡 | Team exists (per kick-off); not yet trained/certified. |
| **Tier-C escalation destination** | ❓ | Where do math/STEM/braille/complex items go? (specialist / outsource / DPRC + AIMHub) |
| **Delivery convention** | ❓ | File-naming + where remediated files are returned. |

**One-line read:** the *knowledge* layer (SOPs, training map, process system) is drafted; the *operational* layer (tool decisions, licenses, intake, tracker, certified students) is what this meeting needs to move.

---

## Part 2 — Tools We're Using, by Task

| Task | Proposed primary tool | Fallback | QA tool(s) | Decision status |
|---|---|---|---|---|
| **OCR** (scanned/image PDFs) | ABBYY FineReader | Acrobat Scan & OCR | — | Confirm ABBYY access |
| **PDF tagging/remediation** | **Equidox** (easier for students, volume work) | Adobe Acrobat Pro | PAC 2024 + NVDA | ❓ **Decision needed** (+ FERPA review) |
| **Word / PowerPoint / Excel** | Native Office app + built-in Accessibility Checker | — | Office checker → verify exported PDF | ✅ Office available |
| **Alt text** (incl. complex charts) | Manual; DIAGRAM Center / POET for complex | — | Human review | ✅ Ready |
| **Convert to Canvas Page / HTML** | Canvas RCE + UDOIT convert | — | Canvas checker + UDOIT | ⏭️ UDOIT = Phase 2 |
| **STEM / math** | Escalate (MathType / specialist) | — | Specialist | ❓ **Decision needed** |
| **Automated QA gate** | Acrobat Full Check **+ PAC 2024** | — | — | Confirm PAC install |
| **Screen-reader QA** | NVDA (Windows) | VoiceOver (Mac) | — | ✅ Ready |

**Recommendation to discuss:** make **Equidox the primary student tool** (visual, zone-based, easier to learn than Acrobat's tag tree, good for volume) with **Acrobat Pro retained** for edge cases and final tag inspection — **pending a FERPA/data-handling review**, since Equidox is cloud and uploaded files leave our environment. QA is tool-independent: **PAC 2024 + NVDA** either way.

---

## Part 3 — Per-File-Type Remediation Checklists

*Condensed working checklists. Full step-by-step + sources are in each `remediation-procedures/` SOP. Every item also passes the cross-cutting QA gate in Part 4.*

### First, for every item (triage)
- [ ] Confirm it's actually **in use** (don't remediate dead content)
- [ ] Check for an **existing accessible version** (publisher / AIMHub / prior work)
- [ ] **Source file available?** If yes → use the source SOP, not the PDF SOP
- [ ] Assign a **tier** (A basic / B intermediate / C escalate)
- [ ] **Log it** in the tracker (course, instructor, source, type, tier, assignee, date)

### Born-digital PDF (`pdf-born-digital.md`)
- [ ] Set Title, show Title in window, set Language, clear security blocks
- [ ] Auto-tag, then **correct** (never trust auto-tag)
- [ ] Headings H1–H6 logical, no skipped levels (bold text ≠ heading)
- [ ] Real lists; descriptive link text
- [ ] Tables: `<TH>` + scope (Table Editor — header cells red, data gray)
- [ ] Figures: meaningful alt text; decorative → artifact
- [ ] Reading order verified; tab order = Use Document Structure
- [ ] Bookmarks for long docs

### Scanned / image-only PDF (`pdf-scanned-ocr.md`)
- [ ] Confirm it's image-only (text won't select)
- [ ] Scan quality OK (**300 DPI**, deskew/despeckle) — else get a better copy
- [ ] **OCR first** (ABBYY preferred for tough scans), set correct language
- [ ] **Verify OCR accuracy** — especially numbers/tables
- [ ] Then do the **full born-digital tagging** checklist above
- [ ] ⚠️ Handwriting / math / unreadable → **Tier C escalate**

### Microsoft Word (`microsoft-word.md`) — *source-first, highest value*
- [ ] Headings via **Styles** (verify in Navigation Pane)
- [ ] Alt text; mark decorative; **don't use auto-generated alt**
- [ ] Tables: header row + Repeat Header Rows; no merged/layout cells
- [ ] Real lists; descriptive links; no important content in text boxes
- [ ] Contrast OK; no color-only meaning; set Title + Language
- [ ] Export: **Save As PDF with "Document structure tags"** — **never Print-to-PDF**

### PowerPoint (`microsoft-powerpoint.md`)
- [ ] Built-in **layouts** (not free-floating text boxes)
- [ ] Unique, meaningful **slide titles** (check Outline View)
- [ ] **Reading order** (Reading Order Pane: top = read first)
- [ ] Alt text; charts/SmartArt described; decorative marked
- [ ] Simple tables w/ header row; link text; contrast
- [ ] Embedded media → **route to Phase 3 captioning**
- [ ] Export tagged PDF (not Print-to-PDF)

### Excel (`microsoft-excel.md`)
- [ ] Format data as a real **Table** ("My table has headers"); name it
- [ ] No merged cells (use Center Across Selection); no blank spacer rows
- [ ] Unique sheet-tab names; delete blank sheets; A1 populated
- [ ] Alt text on charts + underlying data accessible
- [ ] No color-only meaning; **no red-only negatives**; contrast OK

### Images / alt text (`images-and-alt-text.md`) — *cross-cutting*
- [ ] Classify: decorative / informative / functional / complex
- [ ] Decorative → marked/skipped; informative → concise meaningful alt
- [ ] No "image of…", no filenames, no auto-generated alt
- [ ] Complex (charts/diagrams) → short alt **+ long description / data table** (often Tier C)

### Convert to Canvas Page / HTML (`html-canvas-pages.md`)
- [ ] Content is mostly linear text **and copyright allows** conversion
- [ ] Headings start at H2 (H1 = page title); real lists; link text
- [ ] Image alt; simple tables w/ headers; contrast
- [ ] Canvas RCE checker clean; **record copyright decision**

### STEM / math & Tier-C (`stem-math-escalation.md`)
- [ ] **Stop** — don't do Tier-C with the standard toolset
- [ ] Mark `Escalated — Tier C` in the tracker with reason
- [ ] Route to the agreed destination (❓ to be decided — Part 5)

---

## Part 4 — Cross-Cutting QA Gate (every document)

**Gate 1 — Automated:** Office Accessibility Checker (source files) / **Acrobat Full Check + PAC 2024** (PDFs) → 0 errors.
**Gate 2 — Human:** logical reading order · correct heading levels · meaningful alt text · table-header logic · **NVDA** spot-check (required for Tier B).
**Close-out:** record time, pages, issues fixed, checker result, QA reviewer in the tracker.

*Automated-clean ≠ accessible. Both gates are required.*

---

## Part 5 — Open Decisions for the Group (discussion agenda)

1. **Primary PDF tool** — Equidox vs. Acrobat as the student default? → triggers a **FERPA/data-handling review** for Equidox (cloud).
2. **Confirm CSU ATI licensed inventory** — WebAIM Accessible Documents course, CCC micro-courses, ABBYY, Equidox, UDOIT. *(Reminder: SFSU is CSU, not CCC — CCC's own catalog is not directly open to us; ATI is our channel.)*
3. **Tier-C escalation destination** — in-house specialist? outsource vendor? DPRC + AIMHub for accommodation-driven items? Who owns the handoff?
4. **QA ownership** — who signs off, initial 100%-QA count per student, and sampling rate after.
5. **Tracker** — build the minimal spreadsheet now (define columns) or wait for Phase 5? Recommend: start the spreadsheet now.
6. **Intake & delivery** — how does work arrive (mailbox / form / Box), what's the file-naming convention, where do remediated files go back?
7. **AI first-pass** — do we use an AI-assisted first pass for any type, and what human-review protocol wraps it? (Program stance: triage/first-pass only, mandatory human review, no-training-on-our-data clause.)
8. **Copyright review** — process for PDF→Canvas-Page conversions of published readings.
9. **Source-first policy** — can/should we ask faculty to provide original Word/PPT files rather than PDFs?
10. **Pilot scope** — which courses/documents do we remediate *first* to shake out the workflow?

---

### Related documents
- Per-type SOPs: `remediation-procedures/`
- Training catalog & onboarding: `training/`
- Local process docs & templates: `process-documentation/`
- Phase plan: `../phase-1-document-remediation.md` · Program context: `../background-research.md`
