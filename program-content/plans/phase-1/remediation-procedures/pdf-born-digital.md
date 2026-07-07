# SOP — Born-Digital PDF (Tagging & Structure)

*Use when: the PDF has a real text layer (you can select text) but is untagged, mis-tagged, or missing structure. If text won't select, do `pdf-scanned-ocr.md` FIRST, then return here.*

**Standard:** WCAG 2.1 AA + PDF/UA (ISO 14289). **Primary tool:** Adobe Acrobat Pro (Equidox is an easier alternative for students on routine/volume work — see the tool note at the bottom and `../process-documentation/`). **Tier:** A–B depending on layout complexity.

> **Source-first reminder:** If a Word/PowerPoint source exists, remediate that instead (`microsoft-word.md` / `-powerpoint.md`) and re-export. Only tag the PDF directly when there is no source.

> **Acrobat UI note (important):** Adobe redesigned Acrobat in October 2023. Accessibility work now lives under **All tools → Prepare for accessibility** (which replaced the old "Tools → Accessibility → Make Accessible" wizard). Older guides that say "Make Accessible" or "TouchUp Reading Order" describe the pre-2023 UI — same operations, different names. *Confirm the exact labels on our installed build and record in a process note.*

> **The three panels you work in** (add them via right-click the left nav → Accessibility Tags, Order, Content):
> - **Accessibility Tags panel** — the logical structure tree (`<H1>`, `<P>`, `<Table>`, `<Figure>`…). **This is what a screen reader actually reads — the source of truth.**
> - **Order panel** — the reading order of content blocks per page.
> - **Content panel** — raw physical objects; used to find stray/untagged content.
> **Critical rule:** when you reorder in the **Order** panel, you must *also* verify/repair the **Tags** tree — the two are not kept in sync automatically, and the Tags tree wins for AT.

---

## Before you start
- [ ] Item is logged in the tracker with a Tier.
- [ ] You have the working copy (never edit the only copy — keep the original).
- [ ] Confirm text selects (Ctrl+A, or try to highlight a line). If not → OCR SOP first.

## The procedure (Acrobat Pro)

Work top-to-bottom. Each step builds on the last; doing them out of order creates rework.

### 1. Document properties (fast wins)
1. **File → Properties → Description:** set a meaningful **Title** (not "Microsoft Word - final_v3.docx").
2. **Properties → Initial View → Show:** set to **Document Title** (so the title, not the filename, shows in the window).
3. **Properties → Advanced → Reading Options → Language:** set the document **Language** (e.g., English). Screen readers use this to pick pronunciation.
4. **Properties → Security:** confirm security does **not** block "Content copying for accessibility." If it does, remove the restriction (we have rights to remediate).

### 2. Add tags if missing
- Open the **Tags** panel (Accessibility tools → Reading Order / Tags, or the left-nav Tags icon).
- If it says "No Tags available," run **auto-tag** (Accessibility → *Autotag Document*, or "Add Tags to Document").
- Auto-tag is a *starting point*, not the finish. It will get headings, tables, and reading order wrong. You fix those next.

### 3. Set reading order and structure (the core work)
Use the **Reading Order tool** (Accessibility → Reading Order) and the **Tags panel** together:
- **Headings:** tag the real document headings as H1–H6 in a logical, nested order. One H1 (the title) is typical; don't skip levels (no H2 → H4). Manual bold text is *not* a heading — it must carry a heading tag.
- **Body text:** paragraphs tagged `<P>`.
- **Lists:** real list tags (`<L>`, `<LI>`, `<Lbl>`, `<LBody>`) — not paragraphs with manual bullets.
- **Reading order:** verify with the **Order panel** (left nav) that content flows the way a person reads it — especially multi-column pages (each column in sequence, not left-half/right-half interleaved).
- **Links:** ensure hyperlinks are tagged `<Link>` with the visible text as the accessible name; avoid bare URLs and "click here."

### 4. Tables
Tables are the most common failure point — Tier B skill. Structure: `<Table>` → `<TR>` rows → `<TH>` header cells / `<TD>` data cells.
1. **Remove non-table content first** — captions/titles must NOT live inside the `<Table>` tag; re-tag them as `<Caption>` or `<P>` outside it. (This is the "Table Regularity" checker error.)
2. **Open the Table Editor** — with the Reading Order tool open, click the table's region → **Table Editor**. **Header cells highlight red, data cells gray** — a fast visual check.
3. **Set header cells** — select the top row / left column → right-click → **Table Cell Properties → Type = Header Cell** (`<TH>`).
4. **Set scope on every `<TH>`** — **Column** for column headers, **Row** for row headers, **Both** for a corner cell that is both. Never leave scope "None." (This is the "Table Header" checker error.)
5. **Spanned cells** — set correct **Row Span / Column Span** for any merged header.
6. **Multi-level headers** where scope isn't enough → assign explicit **Header IDs** so each `<TD>` references the right `<TH>` — or escalate to **Tier C**.
- Layout tables (positioning only) should not be tagged as data tables — ideally re-flow as real content.

### 5. Figures and images
- Every meaningful image needs **alt text** (`<Figure>` tag with Alternate Text). See `images-and-alt-text.md` for *how to write it*.
- **Decorative** images (dividers, spacers, purely aesthetic) → mark as **artifact** (Reading Order tool → "Background/Artifact") so screen readers skip them.

### 6. Reading order details & tab order
- **Tab order:** Page Thumbnails → select all pages → Page Properties → Tab Order → **Use Document Structure**. This makes keyboard tabbing follow the tags.
- Remove page headers/footers/decorative rules from the reading order (artifact them) unless they carry needed info.

### 7. Bookmarks (longer documents)
- For documents longer than ~a few pages with sections, add **Bookmarks** from the headings so screen-reader and keyboard users can navigate.

---

## QA — two gates (required on every document)

### Gate 1 — Automated
- **Acrobat: Prepare for accessibility → Check for accessibility (Full Check).** Ensure all 32 rule options are on; resolve every Failed item and review every "Needs manual check." Right-click an issue → Fix / Explain / Check Again. It's necessary but not sufficient — a file can pass Acrobat and still be inaccessible.
- **PAC 2024 (PDF Accessibility Checker):** the stricter final gate. Free, **Windows-only**, from the PDF Association. It validates **PDF/UA (ISO 14289) + WCAG 2.1** using the Matterhorn Protocol and catches low-level structure errors Acrobat doesn't. Drag-drop the file; aim for **0 errors**. Use its **Screen Reader Preview** to see what AT will read and in what order. *(Confirm PAC is installed/approved — process note.)*

### Gate 2 — Human (the part tools can't do)
- **Logical reading order:** read the tag tree / use the Order panel — does it match how a sighted person reads the page?
- **Heading logic:** are heading *levels* semantically correct (not just "big text = H1")?
- **Alt text quality:** does each alt text convey the image's purpose in context? (Not "image1.png," not a novel.)
- **Table headers:** do row/column headers actually associate with the right data?
- **Screen-reader spot check** (required for Tier B and anything uncertain): with **NVDA** (free, Windows) — `Insert+↓` "Say All" to hear reading order; `H` to jump headings; `Insert+F7` for the Elements List of headings/links; `Tab` through links/fields. Automated tools verify *presence* of structure; the screen reader verifies the *experience*.

Only after **both** gates pass does the item move to "delivered." Record in the tracker: time spent, page count, issues fixed, checker result, QA reviewer.

---

## Common pitfalls
- Trusting auto-tag and skipping reading-order review → jumbled screen-reader output.
- "Big bold line" left as a paragraph instead of a heading → no navigation.
- Manual bullets/numbers instead of real list tags.
- Multi-column reading order interleaved.
- Alt text that's a filename, or that starts with "image of…", or that restates adjacent caption text.
- Data tables with no `<TH>`/scope.
- Remediating a PDF when the Word source was available (wasted, non-durable work).

## When to escalate to Tier C
Real math notation, complex multi-level tables, charts/diagrams needing long descriptions, non-Latin scripts you can't verify, or fillable forms with complex logic → `stem-math-escalation.md` or specialist queue.

## Tool note — Acrobat vs. Equidox for students
**Equidox** (cloud, zone-based) is markedly easier for student workers than Acrobat's abstract tag-tree: you label visual zones (heading, paragraph, list, image, table) on the page, AI pre-detects zones, and "Zone Transfer/Page Match" reuse patterns across similar pages — good for volume. Trade-off: it's a paid cloud subscription and **the file leaves our environment when uploaded — check FERPA/data-handling before uploading anything with student information.** Recommended split: Equidox as primary production tool for routine/volume docs; Acrobat Pro for edge cases, quick fixes, and final tag inspection; **PAC + NVDA for QA either way.** (Record the final tool decision in `../process-documentation/note-tool-decision.md`.)

## Training for this SOP
See `../training/training-resource-catalog.md` → PDF section (WebAIM "Reviewing/Repairing PDFs in Acrobat," Adobe Acrobat accessibility tutorials, Clemson workflow, Section508 PDF Module 3). New students complete the PDF-fundamentals → checking → remediating sequence before working live Tier-A PDFs.

## Sources
- WebAIM — Reviewing/Repairing PDFs in Acrobat: https://webaim.org/techniques/acrobat/reviewing · Setting up Acrobat: https://webaim.org/techniques/acrobat/acrobat
- Adobe — Create & verify PDF accessibility: https://helpx.adobe.com/acrobat/using/create-verify-pdf-accessibility.html
- Section508 — Remediating PDFs (Module 3): https://www.section508.gov/training/pdfs/aed-cop-pdf03/
- PAC 2024: https://pac.pdf-accessibility.org/en · W3C PDF techniques: https://www.w3.org/TR/WCAG20-TECHS/pdf · WCAG vs PDF/UA: https://www.buffalo.edu/access/digital/content/documents/pdf/wcagvspdfua.html

---
*Menu paths reflect current (post-Oct-2023) Acrobat Pro; verify against our installed version and record differences in a process note (`../process-documentation/`).*
