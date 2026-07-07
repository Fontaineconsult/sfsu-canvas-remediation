# SOP — Scanned / Image-Only PDF (OCR First)

*Use when: the PDF is a picture of pages — text will not select, or selecting grabs the whole page as an image. This is extremely common for course readings scanned from books/journals.*

**Standard:** WCAG 2.1 AA + PDF/UA. **Primary tools:** ABBYY FineReader PDF (preferred for OCR quality), Adobe Acrobat Pro (OCR + tagging). **Tier:** A for clean single-column scans; B for multi-column/poor scans; C for handwriting, math, or unreadable scans.

> A scanned PDF has **no text at all** for a screen reader — it's an image. OCR (optical character recognition) creates the text layer. **You cannot tag what isn't there, so OCR always comes first.** After OCR, the document is treated like a born-digital PDF (`pdf-born-digital.md`).

---

## Before you start
- [ ] Logged in tracker with a Tier.
- [ ] Working copy made.
- [ ] Confirm it's truly image-only (text won't select).
- [ ] **Quality check the scan:** **Scan at 300 DPI for best OCR** — 150 DPI gives noticeably worse accuracy; ~72 DPI is the floor below which OCR fails. Is it straight, not too faint/speckled? A bad scan = bad OCR = more work. If it's crooked/faint, **deskew and despeckle** (ABBYY image editor / Acrobat's Enhance) or re-scan; don't accept bad output.
- [ ] **Is there handwriting, math, or a language you can't verify?** → Tier C, escalate. OCR does not handle these reliably.

## The procedure

### Path A — ABBYY FineReader PDF (preferred for anything non-trivial)
1. Open the scan in ABBYY FineReader PDF.
2. **Set the recognition language(s)** to match the document (critical for accuracy; multi-language docs need all languages selected).
3. **Preprocess:** apply deskew, despeckle, and correct orientation. Good preprocessing dramatically improves recognition.
4. Run **Recognize / OCR**.
5. **Verify recognition:** use the verification view to catch mis-recognized characters, especially in headings, tables, numbers, and proper nouns. Correct errors — OCR is never 100%.
6. Check that ABBYY correctly identified the document areas (text vs. table vs. image zones). Fix zoning where columns/tables were mis-detected.
7. **Export as a tagged/accessible PDF** (PDF/UA or "PDF (accessible)" output). ABBYY can produce a first pass of tags.

### Path B — Adobe Acrobat Pro (for simple, clean scans)
1. **Scan & OCR → Recognize Text → In This File.** Choose the correct language; output "Searchable Image" (keeps the visual, adds text underneath).
2. Review recognized text quality (Acrobat's OCR is decent for clean scans, weaker than ABBYY on poor ones).
3. Proceed to tagging.

### After OCR (both paths) — tag and structure
The document now has text. **Switch to `pdf-born-digital.md` and do the full tagging procedure**: document properties/language/title, add tags, reading order, headings, lists, tables, figures/alt text, tab order, bookmarks.

Do **not** skip this — a searchable-but-untagged PDF is still inaccessible. OCR gives you *text*; tagging gives you *structure*.

---

## QA — two gates
Same as `pdf-born-digital.md`, plus scan-specific checks:

### Gate 1 — Automated
- Acrobat Full Check + PAC clean.
- Confirm no lingering "image-only" / "scanned text" flags.

### Gate 2 — Human
- **OCR accuracy spot-check:** read several passages against the image — are words, numbers, and especially table figures correct? Wrong numbers in a data table are worse than no text.
- Reading order, heading logic, alt text, table headers (as in the born-digital SOP).
- Confirm the visible image and the text layer match (no misaligned "ghost text").

Record: time spent, pages, OCR tool used, issues fixed, checker result, QA reviewer.

---

## Common pitfalls
- **Stopping at OCR.** Searchable ≠ accessible. It still needs tags.
- Wrong OCR language → garbled text, especially accented characters.
- Not verifying numbers in tables/figures — silent data corruption.
- OCR-ing a crooked/low-res scan and accepting bad output instead of getting a better source.
- Treating a scan of a math/chemistry page as Tier A — escalate.

## When to escalate to Tier C
Handwriting, mathematical/scientific notation, music/chemistry notation, heavily degraded scans, complex multi-column journals with figures, or any language the student can't verify → `stem-math-escalation.md` or specialist queue.

## Why ABBYY over Acrobat (when it matters)
ABBYY FineReader publishes ~99.8% OCR accuracy and better preserves columns, tables, and reading structure — use it for **poor/degraded scans, complex multi-column layouts, tables, mixed-language docs, and batch jobs.** Acrobat's OCR is fine for **clean, high-resolution, single-column** scans when you're already in Acrobat and volume is low. ABBYY can export **PDF/UA** directly; still validate in PAC and finish tag corrections (headings, alt text quality, tables) in Acrobat.

## Training for this SOP
`../training/training-resource-catalog.md` → OCR + PDF sections (ABBYY FineReader guides; "The Accessibility Guy" ABBYY OCR walkthrough; WebAIM; Section508 PDF Module 3). Students must be signed off on the born-digital PDF SOP before doing scanned PDFs, since scanned work *includes* the full tagging procedure.

## Sources
- Adobe — Recognize text (Scan & OCR): https://helpx.adobe.com/acrobat/desktop/create-documents/scan-documents-to-pdfs/recognize-text.html
- ABBYY — PDF/UA workflow: https://pdf.abbyy.com/blog/pdf-ua/ · ABBYY vs Acrobat OCR: https://www.documentsnap.com/ocr-smackdown-abbyy-finereader-vs-adobe-acrobat/
- Section508 — Remediating PDFs (Module 3): https://www.section508.gov/training/pdfs/aed-cop-pdf03/

---
*Verify ABBYY/Acrobat menu paths against our installed versions; record deviations as a process note.*
