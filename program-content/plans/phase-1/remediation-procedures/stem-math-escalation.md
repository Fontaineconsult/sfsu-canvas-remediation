# SOP — STEM / Math & Tier-C Escalation

*Use when: content contains real mathematical, scientific, or other specialized notation, or any Tier-C trigger. **This is primarily a "what students do NOT do, and how to hand it off" document.** The goal is a clean, fast escalation — not a student struggling with content beyond the standard toolset.*

**Why this is separate:** Math and scientific notation are *not* remediable with the standard PDF/Office toolchain. Alt-texting an equation as prose loses rigor; OCR mangles notation; screen readers need real math markup (MathML) to read equations correctly. This requires specialized tools, skills, and often more time than the whole rest of a document.

---

## Tier-C triggers (stop and escalate)

Escalate immediately if the item contains:
- **Mathematical notation** beyond trivial inline symbols (fractions, integrals, matrices, summations, subscripts/superscripts with meaning, equations).
- **Scientific notation:** chemistry structures/formulas, physics notation, engineering diagrams.
- **Music notation.**
- **Complex data visualizations** where the data/relationships must be conveyed (needs substantial long description) — see `images-and-alt-text.md`.
- **Handwriting** (OCR can't read it).
- **Languages** the student can't verify well enough to judge reading order/alt text/OCR accuracy.
- **Braille or tactile graphics** production requests.
- **Complex fillable forms** with conditional logic.
- Anything a student has spent **more than the escalation-time threshold** [TBD — set in process docs] on without a clear path.

---

## What to do (the handoff)

1. **Stop working.** Don't spend Tier-A/B time on Tier-C content — it's inefficient and produces poor results.
2. **In the tracker, mark the item `Escalated — Tier C`** with the reason (math / complex chart / language / braille / form / other).
3. **Route to the correct destination:**
   - **Specialist / senior remediator** (in-house, as the team matures) for math/STEM using proper tools — **the specialist workflow now exists**: see "The specialist workflow" below and the full reading at `../../../research/accessible-math-reading.md`.
   - **Outsource vendor** — default lane: **Allyant (CommonLook)** under the in-progress CSU Master Procurement Agreement (framework-recommended for complex/scientific documents); confirm status via the ATI coordinator.
   - **CSU STEM Accessibility WG** for math-workflow questions and hard cases — the systemwide group building the LaTeX/Quarto accessible pipelines (see field-evidence section below).
   - **DPRC / AIMHub** for accommodation-driven alternate media (braille, tactile, e-text for a specific student) — the CSU/CCC exchange may already have an accessible version. This is the accommodation path, coordinated with disability services.
   - **Defer** if the item isn't urgently needed and no path exists yet — but log it so it's not lost.
4. **Capture what you learned** in a process note (`../process-documentation/`) if you discovered a reusable handling approach.

---

## Reference: how math accessibility actually works (for specialists)

*(Background so the escalation destination is understood — not a student procedure.)*

- **Real math needs MathML** (or an equivalent) so screen readers (with tools like MathPlayer/native support) can read and let users navigate expressions.
- **Authoring-side tools:** MathType (exports MathML, integrates with Word), LaTeX → MathML pipelines, and if the *source* is available (LaTeX, Word+MathType), regenerating accessible math is far better than remediating a flattened PDF.
- **Equations baked into a PDF as images** are the hard case — often the right answer is to obtain or recreate the source, not to patch the PDF.
- **Complex diagrams** may need a written long description authored by someone who understands the subject matter.

The practical program rule: **for STEM, get the source or a properly-authored accessible version; don't try to tag flattened math.**

### The specialist workflow (Accessible Math guide)

*Full reading: `../../../research/accessible-math-reading.md` (source: `research/Accessible Math.docx`). This is what the in-house Tier-C destination does — still specialist work, never Tier-A/B.*

**Target formats, in order of preference:** HTML+MathML (Canvas/LMS content) → EPUB 3+MathML (textbooks) → Word with native equations (handouts) → tagged PDF 2.0 (only when PDF is genuinely required).

1. **Decide:** mostly text + a few simple equations → remediate the PDF in place. STEM textbook / problem set / research article / *any scanned math PDF* → **recreate from scratch**.
2. **Extract with math-aware OCR** — ordinary ABBYY/Acrobat OCR mangles notation. **Mathpix** webapp for full-PDF conversion (exports Word / HTML / LaTeX / Markdown); MathKicker AI and EquatIO are alternatives. ⚠️ Cloud tools — FERPA/data-handling review before uploading student content (same gate as Equidox).
3. **Rebuild the accessibility skeleton** like any other document: title, headings, lists, tables.
4. **Verify and fix every equation by hand** — conversion is never trusted. Word lane: Word Equation Editor (supports LaTeX input — see U. Houston AutoCorrect codes) + MathType; **Mathpix Snip** for stragglers (screenshot → verify the LaTeX → copy **"MathML for Word"** → paste). LaTeX lane (when the student needs TEX source): TeXstudio, Overleaf.
5. **Graphs/diagrams:** alt text + long descriptions (see `images-and-alt-text.md`; science-description guides in the reading).
6. **Checkers, then export via a markup-preserving lane:**
   - **Word → PDF:** File → **Save As** → PDF → More options → check **"Document structure tags for accessibility"** — per the guide, the *only* Word export route that produces correct `Formula` tags (Print-to-PDF and other routes fail).
   - **Word → EPUB 3 / HTML:** free DAISY **WordToEPUB** add-in — Math tab → MathML for EPUB; HTML tab → "Include MathJax reference" for HTML.
7. **Listening check — the gate.** NVDA/JAWS pass on the actual math (see field evidence below). Math-capable readers for QA and alternate-media delivery: **Central Access Reader** (free), **Kurzweil 3000** (EPUB w/ MathML), EquatIO.

### ⚠️ Field evidence: even "correct" pipelines fail (CSU STEM WG, Dec 2025)

NVDA testing of real faculty files by the CSU STEM Course Materials Accessibility Working Group (`../../../research/STEM_WG_Summary12_2_25.docx`; digest: background-research.md §13) found:
- **Complex math was garbled in every pipeline tested** — LaTeX→Pandoc HTML, MathML output, R/Quarto HTML. Faculty couldn't reconstruct their own formulas from the audio. Simple math, text, and tables read fine.
- **Files that pass tag checks in Canvas still failed to read math correctly** → an automated-checker pass is *never* the QA gate for math. **The gate is a human listening check with NVDA (or equivalent).**
- HTML output beats PDF but does not solve complex expressions; R-generated HTML reads object references as "dollar sign" repeatedly; **RStudio is not screen-reader usable** (blind students need e.g. VS Code — see Dr. Jonathan Godfrey's resources on R for blind statisticians).
- WG interim guidance: author in source (Overleaf/TEX, `.qmd`/`.Rmd`), output HTML or DOCX, **avoid PDF for student-facing math/code**; equations-as-alt-text images only within character limits and never as a long-term strategy.

Consequences for this SOP: (1) the escalation rule stands even for skilled remediators — checker-clean math is unverified math; (2) the **CSU STEM WG is an escalation/coordination destination** — it is building the standard LaTeX→accessible HTML/DOCX workflow, an accessible Quarto template, and R-course guidance; don't solve these locally.

---

## Program actions this SOP depends on (open items)
- [ ] Name the Tier-C destination(s): in-house specialist? outsource vendor? Which for math vs. braille vs. complex charts?
- [ ] Set the escalation-time threshold (how long before a student escalates).
- [ ] Establish the DPRC/AIMHub accommodation-driven path and who owns it (AT ↔ DPRC handoff — see Phase 4).
- [ ] Decide tooling for in-house STEM remediation if/when we build that capacity — **shortlist now concrete** (from the Accessible Math guide): Mathpix license (webapp + Snip), MathType, WordToEPUB (free, DAISY), a LaTeX editor (TeXstudio/Overleaf), Central Access Reader (free) for listening QA; evaluate EquatIO, MathKicker, JamA11y. FERPA review for the cloud OCR tools.

## Training
Tier-C is specialist work — see `../training/training-resource-catalog.md` → Advanced/Specialist (Deque, IAAP ADS) and **§F STEM/Math specialist track** (from the Accessible Math guide: Accessibility Guy intro, DAISY webinar + WordToEPUB guides, LaTeX resources, U. Houston Word-math typing, video playlists).
