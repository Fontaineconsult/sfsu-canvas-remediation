# SOP — Microsoft Excel (.xlsx)

*Use when: the deliverable is a spreadsheet or data workbook. Excel accessibility is mostly about **data-table structure and navigation**, which is different from Word/PPT.*

**Standard:** WCAG 2.1 AA. **Tool:** Microsoft Excel (built-in Accessibility Checker). **Tier:** A for simple single-table sheets; B for multi-sheet/complex-data workbooks; C for dense analytical models or data viz needing description.

---

## Before you start
- [ ] Logged in tracker with a Tier.
- [ ] Working copy made.
- [ ] Ask: is a spreadsheet the right format for the audience? If it's really a *presentation of data* for reading (not interaction), an accessible Word/HTML table may serve better.

## The procedure

### 1. Use real table structure
- Format the data range as a **Table** (Insert → Table, check "My table has headers"). This gives Excel a defined header row that assistive tech can announce as you navigate.
- Give each Table a **meaningful name** (Table Design → Table Name) instead of "Table1."
- One data table per sheet where possible; separate distinct tables onto separate sheets or with clear spacing.

### 2. Header rows and cell relationships
- Ensure the header row genuinely labels its columns.
- **Avoid merged cells** — they break cell-by-cell navigation and header association. Un-merge and restructure.
- Avoid blank rows/columns inside a table used only for spacing (they signal "table ends" to AT).

### 3. Sheet tabs
- Give every worksheet tab a **unique, meaningful name** (right-click tab → Rename) — e.g., "2025 Enrollment," not "Sheet1."
- **Delete blank/unused sheets.**

### 4. Alt text
- Charts, images, and objects need **alt text** (right-click → View Alt Text). A chart's alt should describe what the data shows; for complex charts, provide the underlying data in an adjacent accessible table (the table *is* the accessible version of the chart).

### 5. Navigation aids
- Set a sensible **active cell** (save with cursor at A1 of each sheet).
- For large sheets, consider **named ranges** and a defined **print/reading area** so users can orient.
- Provide row/column freezing sparingly and only where it aids orientation.

### 6. Color & contrast
- Don't encode meaning by cell color alone (e.g., "red cells = over budget") — add a text indicator or a status column. Ensure contrast for text and chart elements (4.5:1 text, 3:1 chart marks).
- **Never use red-only formatting for negative numbers** — Excel's Accessibility Checker flags this as an *Error*. Add a minus sign or parentheses so the value is clear without color.
- To center a title across columns **without merging cells**, use Format Cells (Ctrl+1) → Alignment → **Horizontal: Center Across Selection** (merging breaks navigation).

### 7. Number/format clarity
- Use real number formatting (dates, currency) rather than text that looks like numbers; screen readers and sorting depend on it.

---

## QA — two gates

### Gate 1 — Automated
- **Review → Check Accessibility.** Resolve Errors/Warnings (missing alt text, default sheet names, merged cells, missing table headers).

### Gate 2 — Human
- Tab through the table — do headers announce and data cells make sense?
- Sheet tabs uniquely named; no orphan blank sheets.
- Charts have data descriptions / an accessible data table.
- No color-only meaning; contrast OK.

Record: time, sheet/table count, issues fixed, checker result, QA reviewer.

## Common pitfalls
- Merged cells everywhere (the #1 Excel accessibility killer).
- "Sheet1/Sheet2" left unnamed.
- Charts with no alt/data description.
- Color-coded cells with no text equivalent.
- Fake tables made by spacing values across cells without Table formatting.

## When to escalate to Tier C
Dense multi-table analytical workbooks, pivot-heavy models, or data visualizations that require substantial long-description work → specialist.

## Training
`../training/training-resource-catalog.md` → Office section (Section508 Excel modules — 11 videos; Microsoft support; WebAIM Accessible Documents course includes an Excel bonus module).

## Sources
- Microsoft — Accessibility best practices with Excel: https://support.microsoft.com/en-us/office/accessibility-best-practices-with-excel-spreadsheets-6cc05fc5-1314-48b5-8eb3-683e49b3e593
- Microsoft — Accessibility Checker rules: https://support.microsoft.com/en-us/office/rules-for-the-accessibility-checker-651e08f2-0fc3-4e10-aaca-74b4a67101c1
- Harvard — Accessible Excel: https://accessibility.huit.harvard.edu/creating-accessible-excel-spreadsheets · WebAIM — Excel: https://webaim.org/techniques/excel/
