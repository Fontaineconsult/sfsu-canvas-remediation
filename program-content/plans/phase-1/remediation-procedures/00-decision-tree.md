# Document Remediation Decision Tree

*Start here for every incoming item. This routes a file to the right procedure and the right complexity tier before any work begins.*

## Step 0 — Should we touch this at all?

- **Is it actually in use?** If the item isn't in an active/upcoming course (or a confirmed accommodation request), stop — flag for archive/removal instead (see the "never remediate unused content" principle). Do not remediate dead content.
- **Does an accessible version already exist?** Check with the publisher, AIMHub (for accommodation-driven alternate media), or a prior remediation. Acquiring an accessible source beats remediating every time.
- **Is there a source file?** If the Word/PowerPoint/Excel original exists, route to the **source SOP**, not the PDF SOP. Fixing the source and re-exporting is durable; patching the PDF is not.

## Step 1 — Identify the file type and condition

```
What is the delivered file?
│
├─ PDF
│   ├─ Does selecting text work / is there a real text layer?
│   │   ├─ NO  → image-only scan ........... → pdf-scanned-ocr.md      (OCR FIRST, then tag)
│   │   └─ YES → born-digital / has text .... → pdf-born-digital.md    (tag / fix tags)
│   └─ Is a source file (Word/PPT) available? → use the source SOP instead, re-export to PDF
│
├─ Microsoft Word (.docx) ................... → microsoft-word.md
├─ Microsoft PowerPoint (.pptx) ............. → microsoft-powerpoint.md
├─ Microsoft Excel (.xlsx) .................. → microsoft-excel.md
├─ Google Doc/Slide ........................ → microsoft-word.md / -powerpoint.md (see Google notes)
├─ Image file (PNG/JPG) or image inside a doc → images-and-alt-text.md
├─ Mostly-text PDF that could be a web page . → consider html-canvas-pages.md (convert, don't tag)
└─ Audio / video ........................... → NOT Phase 1 — route to Phase 3 (captioning)
```

## Step 2 — Assign a complexity tier

The tier decides **who** works it and **how much QA** it gets. When in doubt, tier up.

| Tier | Who | Typical content | QA |
|---|---|---|---|
| **A — Basic** | New-certified student | Linear text: articles, syllabi, handouts, simple letters, clean single-column scans, slides from standard layouts | 100% reviewed until student is proven, then sampled |
| **B — Intermediate** | Student certified on Tier A + trained on B | Multi-column layouts, data tables with headers, forms, figures needing real alt text, longer documents needing bookmarks, mixed content | 100% until proven on B, then sampled |
| **C — Escalate (not student work)** | Specialist / outsource / defer | Math & STEM notation, complex data visualizations needing long descriptions, chemistry/music notation, heavily multilingual, braille/tactile requests, scanned handwriting, complex fillable forms | Specialist QA |

### Tier-C escalation triggers (memorize these — stop and hand off)
- Any real mathematical/scientific notation beyond trivial inline symbols → `stem-math-escalation.md`
- Charts/graphs/diagrams where the *data or relationships* must be conveyed (not just a caption) → needs a long description; escalate if unsure
- Content in a language the student can't read well enough to judge reading order/alt text
- A request that names braille, tactile graphics, or large-print production
- Anything a student has spent >[threshold TBD] minutes on without a clear path — escalate rather than churn

## Step 3 — Pick the remediation path (source-first, convert-when-cheaper)

```
Source file available?
├─ YES → remediate source (Word/PPT/Excel SOP) → export tagged PDF → QA
└─ NO  → Is the PDF basically linear text with no complex layout?
          ├─ YES → is it a course reading with copyright limits?
          │        ├─ NO  → consider converting to Canvas Page/HTML (html-canvas-pages.md)
          │        └─ YES → remediate the PDF in place (pdf-born-digital.md)
          └─ NO  → remediate the PDF in place (pdf-born-digital.md), OCR first if scanned
```

## Step 4 — Log it

Before starting work, create the tracker row: item ID, course, instructor, source (DPRC / faculty / scan / census), file type, tier, assignee, intake date. Nothing gets worked before it's logged. (See `../../phase-1-document-remediation.md` §1.5 and the Phase 5 tracker.)

---

### Quick reference: which SOP for which symptom

| Symptom | SOP |
|---|---|
| "Can't select the text / it's a picture of a page" | pdf-scanned-ocr.md |
| "Text selects but screen reader reads it wrong / no headings" | pdf-born-digital.md |
| "I have the original Word file" | microsoft-word.md |
| "It's a slide deck" | microsoft-powerpoint.md |
| "It's a spreadsheet / data table" | microsoft-excel.md |
| "There's a chart/photo/diagram and I don't know what to write" | images-and-alt-text.md |
| "It's just text and would be better as a web page" | html-canvas-pages.md |
| "There's math / it's a STEM PDF" | stem-math-escalation.md |
