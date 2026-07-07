# SOP — Convert to HTML / Canvas Pages (instead of remediating)

*Use when: a document is essentially linear text (an article, a syllabus, a handout, a reading) and would be **cheaper to convert into a native Canvas Page than to tag as a PDF** — and copyright allows it.*

**Standard:** WCAG 2.1 AA. **Tool:** Canvas Rich Content Editor (RCE) + its built-in accessibility checker; UDOIT's PDF→Page conversion. **Tier:** A–B.

> **Why convert?** Native Canvas Pages/HTML are accessible by default (real headings, reflow on mobile, resize without breaking, work with every screen reader), and they **stay** accessible — no re-export to undo. For simple text content, conversion is often faster and more durable than PDF tagging. This is the "prefer conversion over remediation" principle in action.

---

## When to convert vs. remediate the PDF

**Convert to a Canvas Page when:**
- The content is mostly text (with a few images/tables that convert cleanly).
- It lives in a Canvas course anyway.
- **Copyright permits** reproducing it as web content (see below).
- No fixed layout/pagination is required.

**Keep it a (tagged) PDF when:**
- It's a **published copyright work** (journal article, book chapter) where converting/re-hosting exceeds fair-use/licensed terms — remediate the PDF instead.
- Exact pagination matters (legal forms, citations to page numbers).
- It's a fillable form.
- It's heavily formatted / complex layout that won't survive conversion.

**⚠️ Copyright gate:** Course readings are frequently published works. Converting a PDF into a Canvas Page reproduces it. Do **not** convert copyrighted readings without confirming rights (library reserves / licensed terms / fair use). When in doubt, remediate the PDF in place. *Record the copyright decision in the tracker.*

---

## The procedure

### Option A — UDOIT PDF→Page conversion (fast start)
1. In the Canvas course, use UDOIT's convert-scanned-PDF-to-Page feature to generate a first-pass Canvas Page from the PDF.
2. Then clean up the result using Option B steps — auto-conversion is a starting point, not the finish.

### Option B — Build/clean the Canvas Page in the RCE
1. Paste or import the text into a new Canvas **Page**.
2. **Headings:** apply real heading styles in the RCE (Paragraph → Heading 2/3/… — note Canvas reserves H1 for the page title, so start content headings at H2). Logical nesting, no skipped levels.
3. **Lists:** use the RCE's real bullet/number list buttons.
4. **Links:** meaningful link text (not raw URLs / "click here"). Use the link tool's text field.
5. **Images:** add alt text in the image dialog; mark decorative images as decorative. (See `images-and-alt-text.md`.)
6. **Tables:** use the RCE table tool; set a header row (Table → Row/Cell header options). Keep simple.
7. **No color-only meaning; check contrast.** Don't paste in fixed font colors that fail contrast.
8. Remove pasted-in junk markup (paste as plain text if formatting comes in messy, then re-apply structure).

---

## QA — two gates

### Gate 1 — Automated
- **Canvas RCE accessibility checker** (the little checkmark icon in the editor) — resolve all issues.
- Optionally re-scan the course/page with **UDOIT** and confirm the page is clean.

### Gate 2 — Human
- Heading outline is logical (content starts at H2 under the page title).
- Links are descriptive; images have alt; tables have headers.
- Reads top-to-bottom sensibly; reflows on a narrow window.
- Copyright decision recorded.

Record: time, source pages, issues fixed, checker result, QA reviewer, **copyright disposition**.

## Common pitfalls
- Converting a copyrighted reading without checking rights.
- Using H1 for content headings (H1 is the Canvas page title).
- Pasting styled text that carries bad contrast / fake headings.
- Converting something that really needed fixed pagination or was a form.

## Training
`../training/training-resource-catalog.md` → WebAIM (semantic structure), UDOIT/Cidi Labs docs (conversion + Canvas checking). Canvas's own accessibility guides for the RCE.
