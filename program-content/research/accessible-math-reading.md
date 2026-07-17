# Full Reading — Accessible Math (Practical Creation & Remediation Guide)

*Knowledge-base entry for the SFSU AT Canvas Remediation Program · added July 2026*
*Source: `Accessible Math.docx` (this folder). Author/origin not recorded in the file — the content appears assembled from an email/webinar context (it links the DAISY "Accessible Math Unlocks STEM Education and Careers" event assets via Outlook safelinks). Confirm provenance with the team; treat the workflow as community practice, not vendor documentation.*

---

## TL;DR for SF State

This guide supplies **the piece the CSU STEM WG findings left open: an actual production workflow for math content.** The WG proved that checker-clean math is unverified math (`background-research.md` §13); this document describes **how a trained specialist rebuilds math content accessibly**: pick the right target format (HTML+MathML, EPUB 3, Word native equations, tagged PDF 2.0) → extract with **math-aware OCR (Mathpix)** → rebuild structure in Word or LaTeX → insert real equations (Word Equation Editor / MathType / Mathpix Snip "MathML for Word") → export through the **specific lanes that preserve math markup** (Word "Save As PDF" with structure tags = the only Word export that produces correct `Formula` tags; DAISY **WordToEPUB** for EPUB 3 with MathML or HTML with MathJax). It turns our Tier-C "escalate math" rule from *"escalate because we have no path"* into *"escalate to a specialist lane with a defined SOP basis."* The NVDA/listening-check QA gate from the STEM WG still applies to every output of this workflow, and the cloud OCR tools (Mathpix, MathKicker) need the same FERPA/data-handling review as Equidox.

---

## 1. Target formats — the accessible-math hierarchy

The guide names four target formats, each matched to a use case:

| Format | Use case | Why it works |
|---|---|---|
| **HTML + MathML** | OER content, LMS/Canvas content | Native MathML support; works well with screen readers; refreshable braille; reflow/zoom without loss; **semantic math navigation** (users can step through an expression) |
| **EPUB 3 + MathML** | Textbooks | Excellent screen-reader support; MathML embedded in the XHTML content files; reflowable |
| **Word (.docx) with native equations** | Course handouts | Easiest for faculty to author; native equation objects; converts onward to the other formats; "works reasonably well with modern screen readers" (the guide's own hedge — listening check still required) |
| **Tagged PDF 2.0 with accessible math** | Published/fixed-layout content | PDF 2.0 supports real math in the tag structure (`Formula` tags; see PDF Association's "accessible math in PDF" below) — the lane for when PDF is genuinely required |

This ordering is consistent with the STEM WG's "HTML > PDF, avoid student-facing PDF for math" guidance: **PDF is the last resort, not the default**, and Word/HTML/EPUB are the working formats.

## 2. Creating born-accessible math (authoring side)

Condensed per format — the recurring rules are: **semantic structure first** (title, headings, lists, tables, landmarks), **real math markup, never screenshots**, alt text/long descriptions for graphs and diagrams, and **test with a screen reader**.

- **HTML:** author equations directly in MathML or convert from LaTeX/MathType; use the `<math>` element; represent fractions, radicals, matrices, summations as MathML structure, not plain text or images; verify reflow, contrast, keyboard, and screen-reader reading.
- **EPUB 3:** build to EPUB 3 standards; embed MathML in the XHTML; complete navigation document/TOC; accessibility metadata; test in MathML-capable reading systems.
- **Word:** accessible document skeleton + **built-in Equation Editor, Mathpix, or MathType** for equations — *never pasted images of equations*; LaTeX input inside Word's Equation Editor where helpful (Word supports LaTeX entry natively — see the UH AutoCorrect codes and Microsoft's LaTeX/MathML support docs below); set language; run the Accessibility Checker; test with AT.
- **Tagged PDF:** start from an accessible **source** (Word, HTML, or LaTeX with structured math), export preserving tags, confirm equations are not flattened to images, verify tags/reading order/language, run Acrobat's checker + screen-reader review.

**Faculty-facing takeaway (Phase 6):** the authoring rules are simple enough to teach — native equation editor, no equation screenshots, alt-text the graphs — and they make everything downstream cheap.

## 3. The remediation workflow (the core of the document)

*(Step numbering follows the source, which has no "Step 3" — nothing is missing, the numbering just skips.)*

**Step 1 — Decide on approach.** Source-first, as always. Then:
- Mostly text with a few simple equations → **remediate the PDF** in place.
- STEM textbook, problem set, research article, engineering manual → **recreate from scratch**.
- Scanned PDF with equations → **recreate from scratch**.

This matches and sharpens our SOP rule (*"don't tag flattened math"*) — the guide's threshold is explicit: anything beyond "a few simple equations" is a rebuild, not a repair.

**Step 2 — Extract text with math-aware OCR.** Ordinary OCR (ABBYY/Acrobat) mangles notation; use OCR that recognizes math: **Mathpix**, **MathKicker AI**, **EquatIO**.
- **Mathpix webapp/desktop — full-PDF conversion:** upload the PDF (multiple at once supported), let it process, then **export to Word, HTML, LaTeX, or Markdown**.

**Step 4 — Rebuild the document.** Standard accessibility skeleton like any other document: title, headings, lists, tables.

**Step 5 — Edit the math content.** Walk the document **equation by equation**, verifying each conversion (the guide is emphatic: conversions must be human-checked). Editors by lane:
- **Word lane:** Word Equation Editor + MathType; **Mathpix Snip** for the stragglers — screenshot the equation, verify/edit the recognized LaTeX, copy **"MathML for Word"** and paste into the document. More symbols via the symbol pane; LaTeX-style entry via the University of Houston AutoCorrect codes.
- **LaTeX lane:** TeXstudio, Overleaf, etc. — for the rare case a student needs LaTeX source or a PDF with properly tagged equations plus an accompanying MathML file.

**Step 6 — Accessible graphs and diagrams.** Alt text + long descriptions where needed (see the image-description guides in Resources — these also feed our `images-and-alt-text.md` SOP).

**Step 7 — Run accessibility checkers.** Review equations *and* all standard document accessibility. Per the STEM WG: the checker pass is necessary, **the listening check is the gate**.

**Step 8 — Export to final format.**
- **Word → PDF:** File → **Save As** → PDF → **More options** → check **"Document structure tags for accessibility"** and headings-as-bookmarks. ⚠️ The guide's key finding: **other export/print-to-PDF routes do not produce correct `Formula` tags for equations.** (Extends our existing "never Print-to-PDF" rule with a math-specific reason.)
- **Word → EPUB 3 (DAISY WordToEPUB add-in, free):** set metadata/cover/language/TOC/page numbers in Advanced settings; on the **Math tab, select MathML**; validate in an EPUB reader.
- **Word → HTML (same add-in):** on the HTML tab check **"Include MathJax reference"**, create the HTML version, verify.

## 4. QA and delivery — math-capable TTS/reading tools

The guide lists reading tools that can actually voice math — useful both for **QA listening checks** and for **DPRC alternate-media delivery** (Phase 4):
- **Central Access Reader** (Central Washington University) — free TTS reader built for math content.
- **Kurzweil 3000** — reads EPUB with MathML; has an OCR lasso tool.
- **EquatIO** — OCR lasso; more of an authoring tool.
- **Microsoft Read Aloud** — simple documents only.

NVDA/JAWS remain the compliance gate (what a blind student actually hears); these tools widen the delivery options for accommodation-driven output.

## 5. How this sits with the CSU STEM WG findings (§13)

The two documents are complementary, with one tension to manage:

- **Agreement:** source-first; never images-of-equations as strategy; HTML/DOCX over PDF; human verification of every equation; math is specialist work.
- **The WG is the warning, this is the workflow:** the WG showed *conversion pipelines* (LaTeX→Pandoc, R/Quarto, even MathML output) garble complex math in NVDA — so **no output of this workflow is done until it passes a listening check**. "Mathpix converted it" and "the checker passed" are both non-evidence for math.
- **The PDF lane is conditional:** the WG says avoid student-facing PDF for math; this guide's tagged-PDF-2.0 lane is for when PDF is genuinely required (published/fixed-layout content) — and note real-world **reader support for math in PDF is still maturing** (PDF Association coverage below), which is another reason the listening check is non-negotiable.
- **Escalation still stands:** nothing here makes math Tier-A/B work. It defines what the **Tier-C in-house specialist** does instead of "we have no path — outsource or defer."

## 6. Program implications for SF State

1. **The Tier-C math lane now has an SOP basis** — `stem-math-escalation.md` gains a real specialist workflow (decide → math-OCR → rebuild → verify equations → export → listening check) instead of only routing rules.
2. **Tooling decision list for in-house STEM capacity** (Phase 1 open item, now concrete): **Mathpix** license (webapp + Snip; per-seat, cheap), **MathType**, **WordToEPUB** (free, DAISY), LaTeX editor (TeXstudio/Overleaf), **Central Access Reader** (free) for listening QA alongside NVDA. EquatIO and MathKicker as evaluation candidates. JamA11y (remediation tool with MathType built in) worth a look.
3. **FERPA/data-handling gate:** Mathpix webapp and MathKicker are **cloud services — course files leave our environment**, same review needed as Equidox and the AI PDF lanes before uploading anything with student data.
4. **Bulk-AI lane stays math-free:** the ASU pipeline produces no MathML (`asu-pdf-accessibility-reading.md` §8) — math content must be filtered out of any bulk lane and routed here.
5. **Training (specialist track):** the Resources section below is effectively the syllabus for training a senior student/specialist on math remediation — added to `training-resource-catalog.md` §F.
6. **DPRC/alternate media (Phase 4):** EPUB 3 + MathML is the textbook-accommodation format; math-capable readers (Kurzweil, Central Access Reader) shape what "delivered" means for a math accommodation.
7. **Faculty guidance (Phase 6):** authoring rules (native equation editors, LaTeX input in Word, no screenshots) belong in the STEM faculty guidance next to the WG's Quarto/LaTeX templates.

## 7. Resource catalog (from the guide — URLs as listed, not yet independently verified)

**Overviews**
- Introduction to Math Accessibility — The Accessibility Guy: https://theaccessibilityguy.com/introduction-to-math-accessibility/
- Accessible Math Unlocks STEM Education and Careers — DAISY Consortium: https://dl.daisy.org/web/event/ability2026assets/index.html

**Software**
- Mathpix: https://mathpix.com/
- MathKicker: https://mathkicker.ai/
- MathType (Wiris): https://www.wiris.com/en/mathtype/
- EquatIO: https://www.everway.com/products/equatio/features/
- Pandoc conversion utility (PSU guide): https://accessibility.psu.edu/math/pandoc/
- WordToEPUB (DAISY): https://daisy.org/activities/software/wordtoepub/ · getting started: https://daisy.org/guidance/info-help/guidance-training/content-creation/getting-started-with-wordtoepub/
- MathML support in Microsoft 365: https://learn.microsoft.com/en-us/office/math/mathml · LaTeX support: https://learn.microsoft.com/en-us/office/math/latex
- Typing math in MS Word (U. Houston AutoCorrect codes): https://online.math.uh.edu/typing-math-in-ms-word/
- Accessible math in PDF — PDF Association: https://pdfa.org/accessible-math-in-pdf-finally/
- Math converter tool — Indiana University: https://accessibility.iu.edu/tools/math-converter-instructions.html
- JamA11y (Jamworks; remediation with MathType built in): https://help.jamworks.com/en/articles/13763405-jama11y
- Converting documents to PDF — WebAIM: https://webaim.org/techniques/acrobat/converting

**Image / diagram description** *(also feeds `images-and-alt-text.md`)*
- Charts & diagrams alt text — U. of South Carolina: https://sc.edu/about/offices_and_divisions/digital-accessibility/toolbox/best_practices/alternative_text/charts-diagrams/
- Effective practices for description of science content — NCAM/GBH: https://www.wgbh.org/foundation/services/ncam/tools-resources/effective-practices-for-description-of-science-content-example-i-complex-diagrams-and-illustrations
- Image description guidelines — DIAGRAM Center: http://diagramcenter.org/table-of-contents-2.html

**LaTeX**
- learnlatex.org: https://www.learnlatex.org/ · Overleaf Learn: https://www.overleaf.com/learn · mathematical expressions: https://www.overleaf.com/learn/latex/Mathematical_expressions
- Accessibility checklist for LaTeX — Lancaster: https://portal.lancaster.ac.uk/ask/checklist-latex
- Making accessible documents using LaTeX (AMS Notices): https://ww2.ams.org/journals/notices/202301/rnoti-p68.pdf
- Generating tagged PDF from LaTeX (LaTeX tagging project): https://latex3.github.io/tagging-project/documentation/wtpdf/
- Cheat sheets: UOregon https://pages.uoregon.edu/torrence/391/labs/LaTeX-cheat-sheet.pdf · Rice symbols https://www.cmor-faculty.rice.edu/~heinken/latex/symbols.pdf · Tilburg amsmath https://www.tilburgsciencehub.com/topics/research-skills/templates-dynamic-content/templates/amsmath-latex-cheatsheet/ · UChicago guide https://guides.lib.uchicago.edu/c.php?g=992088&p=7228301
- From LaTeX to accessible PDFs — Microsoft 365 blog: https://techcommunity.microsoft.com/blog/microsoft365insiderblog/from-latex-to-accessible-pdfs-transforming-math-workflows-in-microsoft-365/4523506

**TTS readers (math-capable)**
- Central Access Reader — CWU: https://www.cwu.edu/student-life/student-support/central-access/resources/reader.php
- Kurzweil 3000 math accessibility: https://accessinghigherground.org/math-accessibility-in-kurzweil-3000/

**Videos**
- Turning math into HTML: https://www.youtube.com/watch?v=ophpILKTVNI
- Using Pandoc: https://www.youtube.com/watch?v=N31E_NZYQQY · LaTeX Beamer→HTML: https://www.youtube.com/watch?v=ZlAuTc17Dno
- Math accessibility playlist: https://www.youtube.com/playlist?list=PL2GnpAhfNiFH47a-mqWk2JG9OnteAnqTJ
- Accessible math and science in digital publications: https://www.youtube.com/watch?v=ja7gjDCN8n8
- "Math in a PDF is now possible!": https://www.youtube.com/watch?v=W5xuS5_vaIE
- Accessible math in PDF — PDF Association: https://youtu.be/yb5QElBAr-Q
- Center for Assistive Technology Training (CATT-APH) channel: https://www.youtube.com/@CATT-APH/videos

---

## Sources
- `Accessible Math.docx` (this folder) — full workflow + resource list; provenance to confirm.
- Cross-references: `STEM_WG_Summary12_2_25.docx` + `background-research.md` §13 (the QA-gate evidence); `asu-pdf-accessibility-reading.md` (no-MathML limitation of the bulk AI lane); `../plans/phase-1/remediation-procedures/stem-math-escalation.md` (the SOP this feeds).
