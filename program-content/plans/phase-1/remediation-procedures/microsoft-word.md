# SOP — Microsoft Word (.docx)

*Use when: the deliverable is a Word file, OR a PDF whose Word source is available (remediate here, then export). This is the highest-value SOP because **source-first** fixes are durable and Word is where most course documents originate.*

**Standard:** WCAG 2.1 AA. **Tool:** Microsoft Word (built-in Accessibility Checker). **Tier:** A for linear docs; B for tables/columns/figures.

---

## Before you start
- [ ] Logged in tracker with a Tier.
- [ ] Working copy made.
- [ ] Decide the deliverable: does it stay a Word doc, or get exported to PDF, or become a Canvas Page? (See decision tree.)

## The procedure

### 1. Headings via Styles (not manual formatting)
- Apply real **Styles** (Home → Styles): Heading 1, Heading 2, etc., in logical nested order. **Manually bolded/enlarged text is not a heading** and gives screen-reader users no navigation.
- One Title/H1 concept per document; don't skip levels.
- Use the **Navigation Pane** (View → Navigation Pane) to see the heading outline — if it's empty or wrong, the headings aren't real.

### 2. Alt text for images/objects
- Right-click image → **View Alt Text** (or Format → Alt Text). Write meaningful alt text (see `images-and-alt-text.md`).
- Mark purely **decorative** images as decorative (checkbox in the Alt Text pane) so they're skipped.
- Avoid images of text; if text must be an image, put the same text in the alt or nearby.

### 3. Accessible tables
- Insert real tables (Insert → Table) — never fake them with tabs/spaces.
- Set a **header row:** select the top row → Table Design → check **Header Row**; and Table Layout → **Repeat Header Rows**. Also Table Properties → Row → check "Repeat as header row at the top of each page."
- **Avoid merged/split cells and blank cells** used for layout — they break navigation. Keep tables simple and rectangular.
- Complex multi-level-header tables → consider Tier C or redesign into simpler tables.

### 4. Lists
- Use real **bulleted/numbered list** formatting (Home → Lists), not manually typed dashes or numbers.

### 5. Links
- Meaningful link text describing the destination — not a bare URL and not "click here." (Insert → Link → Text to display.)

### 6. Reading order & layout
- Keep a **single linear flow.** **Text boxes and floating objects are read unpredictably** by screen readers — avoid them; put content in the main body. If a floating object must stay, verify it's in the reading order.
- Use Word **columns** (Layout → Columns), not tables or tabs, for multi-column text.
- Don't use empty paragraphs/returns for spacing — use paragraph spacing settings.

### 7. Color & contrast
- Don't convey meaning by **color alone** (add text/symbols). Ensure text contrast meets AA (4.5:1 normal, 3:1 large). The Accessibility Checker flags some contrast issues.

### 8. Document metadata & language
- Set the document **Title** (File → Info → Properties, or Backstage).
- Set the **language** (Review → Language → Set Proofing Language) so PDF export carries it.

### 9. Export correctly (if delivering a PDF)
- **File → Save As / Export → PDF**, and in Options ensure **"Document structure tags for accessibility"** is checked. This carries your headings/alt text/tables into a tagged PDF.
- **Never "Print to PDF"** — it strips all tags and structure, undoing your work.
- After export, run the born-digital PDF checks (`pdf-born-digital.md` QA) — export is good but not perfect.

---

## QA — two gates

### Gate 1 — Automated
- **Review → Check Accessibility.** Resolve all Errors and Warnings. (Newer Office also has the **Accessibility Assistant**.)

### Gate 2 — Human
- Navigation Pane shows a correct heading outline.
- Tables have real header rows; no layout-only merged cells.
- Alt text is meaningful; decorative images marked.
- Reading order is linear (no stray text boxes).
- If exported to PDF: tags carried over, PDF QA passed.

Record: time, pages, issues fixed, checker result, QA reviewer.

## Common pitfalls
- Bold text used as fake headings (no Styles).
- Tables built with tabs/spaces, or with merged cells for layout.
- Text boxes holding important content.
- "Print to PDF" destroying tags on export.
- Color-only meaning (e.g., "items in red are required").

## Google Docs note (important export caveat)
Google Docs supports real headings (Format → Paragraph styles; verify with View → Show outline), alt text (right-click image → Alt text, or Ctrl+Alt+Y), real lists, and link text. **But two gaps matter:**
- **No "mark as decorative" option** — avoid purely decorative images in Google files, or remediate in Office where you can mark them.
- **⚠️ Google's native PDF export is NOT tagged.** "File → Download → PDF" produces an *untagged, non-conformant* PDF. To deliver a tagged PDF: either (a) Download as **.docx**, run Word's checker, and export a tagged PDF from Word (this SOP); or (b) use the **Grackle Docs** add-on to export a tagged PDF directly. Do the structural work in the Google editor first regardless.

## Common alt-text trap (all Office apps)
Do **not** accept Office's "Generate a description for me" auto-alt — its quality is usually poor. Delete the auto string (and the "automatically generated" note) and write your own. See `images-and-alt-text.md`.

## Training
`../training/training-resource-catalog.md` → Office section (WebAIM Word techniques, Section508 Word modules, Microsoft support, WebAIM Accessible Documents course).

## Sources
- Microsoft — Make Word documents accessible: https://support.microsoft.com/en-us/office/make-your-word-documents-accessible-to-people-with-disabilities-d9bf3683-87ac-47ea-b91a-78dcacb3c66d
- Microsoft — Create accessible PDFs: https://support.microsoft.com/en-us/office/create-accessible-pdfs-064625e0-56ea-4e16-ad71-3aa33bb4b7ed
- WebAIM — Microsoft Word (365/Windows): https://webaim.org/techniques/word/word365win
- UW — Tagged PDF (why Google export is untagged): https://www.washington.edu/accesstech/documents/tagged-pdf/
