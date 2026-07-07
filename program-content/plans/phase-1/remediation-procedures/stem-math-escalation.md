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
   - **Specialist / senior remediator** (in-house, as the team matures) for math/STEM using proper tools.
   - **Outsource vendor** if we have one for STEM/braille (TBD in process docs).
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

---

## Program actions this SOP depends on (open items)
- [ ] Name the Tier-C destination(s): in-house specialist? outsource vendor? Which for math vs. braille vs. complex charts?
- [ ] Set the escalation-time threshold (how long before a student escalates).
- [ ] Establish the DPRC/AIMHub accommodation-driven path and who owns it (AT ↔ DPRC handoff — see Phase 4).
- [ ] Decide tooling for in-house STEM remediation if/when we build that capacity (MathType, etc.).

## Training
Tier-C is specialist work — see `../training/training-resource-catalog.md` → Advanced/Specialist (Deque, IAAP ADS) and math-specific resources (MathType/DAISY math guidance) to be added as we build this capacity.
