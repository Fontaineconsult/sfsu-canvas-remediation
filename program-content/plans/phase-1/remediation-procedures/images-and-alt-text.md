# SOP — Images & Alt Text (cross-cutting)

*Referenced by every other SOP. Writing good alt text is the single most common judgment call in document remediation, and the one automated tools cannot do for you. This is the "how to write it" reference.*

**Standard:** WCAG 2.1 AA (1.1.1 Non-text Content). **Tier:** A for simple images; B for figures needing careful description; C for complex data viz / diagrams needing long descriptions.

---

## First decision: what *kind* of image is it?

| Type | Definition | What to do |
|---|---|---|
| **Decorative** | Adds no information — dividers, borders, background textures, purely aesthetic stock photos | **Mark decorative / null alt** (`alt=""`, "artifact" in PDF, "decorative" checkbox in Office). Screen reader skips it. |
| **Informative** | Conveys meaning — a photo illustrating a concept, an icon with meaning, a chart | **Write alt text** conveying that meaning in context. |
| **Functional** | Does something — a linked image, a button | Alt describes the **action/destination** ("Search," "Download syllabus PDF"), not the picture. |
| **Text-in-image** | A picture of text (logos aside) | Alt contains the **same text**; better, avoid images of text entirely. |
| **Complex** | Charts, graphs, diagrams, maps, infographics | **Short alt + long description** (see below). Often Tier C. |

**If you can't tell whether it's decorative:** ask "if this image vanished, would the reader lose anything?" No → decorative. Yes → informative.

---

## How to write good alt text

**Do:**
- Be **concise** — usually a sentence or less (~a phrase to ~125 characters is a good norm; longer is fine when genuinely needed).
- Convey the image's **purpose in this context** — the same photo can need different alt in different documents.
- Be **specific and accurate** — "Bar chart: enrollment rose from 12,000 in 2020 to 18,000 in 2025," not "a chart."
- Consider **surrounding text** — don't repeat a caption verbatim; add what the image contributes.
- End with a period so screen readers pause.

**Don't:**
- Start with "image of…", "picture of…", "graphic of…" — the screen reader already announces it's an image.
- Dump the filename ("IMG_2043.png") — that's the failure state, not alt text.
- Write a paragraph for a simple image, or a novel where a phrase works.
- Include information not present in the image.

---

## Complex images (charts, graphs, diagrams, maps, infographics)

A short alt can't carry a data table or a process diagram. Use a **two-part** approach:
1. **Short alt** identifies the image and its topic ("Line graph of monthly rainfall, described below").
2. **Long description** conveys the full content, placed where sighted users can also benefit:
   - The **underlying data table** adjacent to or beneath the chart (best for quantitative charts — the table IS the accessible equivalent).
   - A **text description** in the body or a caption explaining the trend/relationship/structure.
   - For PDFs, a linked or adjacent long description; for Canvas, text on the page.

**This is frequently Tier C.** If conveying the image requires interpreting data relationships, escalate rather than guess — a wrong description of a chart is worse than a flagged one.

For per-image-type description templates and a free guided authoring tool, use the **DIAGRAM Center** guidance and **POET** tool (diagramcenter.org) — the authoritative reference for describing charts, diagrams, and infographics. For **scientific/STEM figures** specifically (complex diagrams, lab illustrations, quantitative charts), add: **NCAM/GBH — Effective Practices for Description of Science Content** and the **U. of South Carolina charts-and-diagrams alt-text guide** (links in `../../../research/accessible-math-reading.md` §7).

---

## Special cases
- **Logos:** alt = the organization name (e.g., "San Francisco State University").
- **Photos of people:** describe what's relevant to the context (role/action), not exhaustive appearance.
- **Groups of images** making one point: one alt on the group, or decorative on the rest.
- **Math/equations rendered as images:** these need real math handling → `stem-math-escalation.md`. Don't paraphrase equations in alt text.
- **Screenshots of text/UI:** provide the essential text/steps in accessible form, not just "screenshot."

---

## Where alt text lives (per format)
- **PDF:** `<Figure>` tag → Alternate Text (Reading Order tool / Tags panel). Decorative → artifact.
- **Word/PowerPoint/Excel:** right-click → View Alt Text; decorative checkbox for decorative.
- **Canvas/HTML:** the `alt` attribute (Canvas image dialog has an alt field; decorative = leave blank + mark decorative).

## ⚠️ Never use auto-generated alt text
Do not accept Office's "Generate a description for me" / auto-alt, or AI-generated alt, as-is — quality is usually poor and it often describes appearance instead of purpose. Delete it and write your own (a wrong-but-confident description is worse than none).

## QA check for alt text
- Read each alt aloud in context — does it replace the image for someone who can't see it?
- Decorative images confirmed skipped.
- No "image of," no filenames, no empty alt on informative images.
- Complex images have a real long description / data table.
- No leftover auto-generated / AI alt strings.

## Training
`../training/training-resource-catalog.md` → WebAIM alt text article; Section508 alt-text guidance; DIAGRAM Center/POET for complex images; DAISY image guidance.

## Sources
- W3C WAI — Images decision tree: https://www.w3.org/WAI/tutorials/images/decision-tree/
- WebAIM — Alternative Text: https://webaim.org/techniques/alttext/
- Microsoft — Write effective alt text: https://support.microsoft.com/en-us/office/everything-you-need-to-know-to-write-effective-alt-text-df98f884-ca3d-456c-807b-1a1fa82f5dc2
- Section508 — Alternative text: https://www.section508.gov/create/alternative-text/ · DIAGRAM Center: http://diagramcenter.org/making-images-accessible.html
