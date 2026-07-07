# SOP — Microsoft PowerPoint (.pptx)

*Use when: the deliverable is a slide deck, or a PDF exported from one whose source is available.*

**Standard:** WCAG 2.1 AA. **Tool:** Microsoft PowerPoint (built-in Accessibility Checker + Reading Order pane). **Tier:** A for standard-layout decks; B for heavy diagrams/tables.

---

## Before you start
- [ ] Logged in tracker with a Tier.
- [ ] Working copy made.

## The procedure

### 1. Use built-in slide layouts
- Build slides from **Home → Layout** placeholders, not free-floating text boxes. Placeholders have a defined reading order and title; loose text boxes do not.
- If a deck is all free-floating boxes, the fastest durable fix is often to rebuild slides on proper layouts.

### 2. Unique, meaningful slide titles
- **Every slide needs a title** (it's how screen-reader users navigate between slides). Use the layout's title placeholder.
- Titles should be **unique** ("Results: 2025 Survey," not five slides all titled "Results").
- If a title shouldn't be visible, don't delete it — move it off-slide or set it via **Accessibility Checker → Slide Title** / Outline view, so it exists for AT but isn't shown.

### 3. Reading order per slide
Two different panes control this and **they list in opposite directions** — this is the single most common trainee mistake, so memorize it:
- **Reading Order Pane** (Review → Check Accessibility ▾ → **Reading Order Pane**): lists **top-to-bottom = reading order**. The item at the **TOP is read FIRST**. Title should be at the **top** (position 1). Reorder by dragging or the Move Up/Down arrows (Up = earlier). Uncheck an item to mark it decorative / remove from reading order. *(Not available in PowerPoint for the web.)*
- **Selection Pane** (Home → Arrange → **Selection Pane**, or Alt+F10): lists **z-order (reversed)**. The item at the **BOTTOM is read FIRST** (Send to Back = read first). Use this on Mac and the web.
- Set the flow to: title first, then content in logical order. Remove/skip decorative items.
- **Verify with Outline View** (View → Outline View): it shows only text that's in real title/content placeholders. If body text you see on the slide is missing from the outline, it's trapped in a free-floating text box — move it into a placeholder.

### 4. Alt text
- Right-click image/chart/SmartArt/icon → **View Alt Text.** Write meaningful alt (see `images-and-alt-text.md`); mark decorative items decorative.
- **Charts/graphs/SmartArt** conveying data → need a real description of the data/relationship, not just a label. Complex data viz → Tier C long-description handling.

### 5. Tables
- Real tables (Insert → Table) with a **header row** (Table Design → Header Row). Keep them simple; avoid merged cells. Complex tables → consider moving to an accompanying accessible document.

### 6. Links & contrast
- Meaningful link text (not raw URLs).
- Sufficient contrast (projected slides are often low-contrast — check text against background); don't rely on color alone.

### 7. Embedded audio/video
- If slides contain media, that media needs captions/transcripts — **route the media to Phase 3 (captioning)**; note it in the tracker. The slide deck SOP covers the slides, not the video.

### 8. Export (if delivering PDF)
- **File → Save As / Export → PDF** with **"Document structure tags for accessibility"** checked. Not "Print to PDF."
- Run PDF QA after export.

---

## QA — two gates

### Gate 1 — Automated
- **Review → Check Accessibility.** Resolve Errors/Warnings, especially "missing slide title" and "check reading order."

### Gate 2 — Human
- Every slide has a unique, meaningful title (check Outline view).
- Reading order pane flows logically on each slide.
- Alt text meaningful; decorative marked; data charts described.
- Contrast OK; no color-only meaning.
- Any media flagged for Phase 3.

Record: time, slide count, issues fixed, checker result, QA reviewer.

## Common pitfalls
- Missing or duplicate slide titles.
- Content in free-floating text boxes with scrambled reading order.
- Charts with a label but no data description.
- Low-contrast text over busy backgrounds.
- Embedded video shipped without routing to captioning.

## Google Slides note
Add alt text (right-click → Alt text, or Ctrl+Alt+Y); give every slide a unique title (Slide → Apply layout). **Reading order is more limited than PowerPoint** — Slides has *no* reading-order/selection pane; screen readers read objects in the order added, and the only lever is layering (Arrange → Order). Keep slides simple, add objects in intended order, prefer placeholders. **Native PDF export is untagged** — route through PowerPoint (download as .pptx) or the **Grackle Slides** add-on for a tagged PDF.

## Training
`../training/training-resource-catalog.md` → Office section (Section508 PowerPoint modules, Microsoft support, WebAIM Accessible Documents course).

## Sources
- Microsoft — Make PowerPoint accessible: https://support.microsoft.com/en-us/office/make-your-powerpoint-presentations-accessible-to-people-with-disabilities-6f7772b2-2f33-4bd2-8ca7-dae3b2b3ef25
- Microsoft — Reading Order Pane: https://support.microsoft.com/en-us/office/make-slides-easier-to-read-by-using-the-reading-order-pane-863b5c1c-4f19-45ec-96e6-93a6457f5e1c
- WebAIM — PowerPoint accessibility: https://webaim.org/techniques/powerpoint/
