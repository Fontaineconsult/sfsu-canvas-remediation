# Phase 1 — Document Remediation Subsystem

*The detailed build-out of `../phase-1-document-remediation.md`. This folder holds everything the document remediation operation needs to run day-to-day.*

## What's in here

```
phase-1/
├── README.md                         ← you are here (index + how the pieces fit)
├── remediation-procedures/           ← one SOP per file type (the "how to fix it" library)
│   ├── 00-decision-tree.md           ← triage: identify the file type/condition → route to the right SOP + tier
│   ├── pdf-born-digital.md
│   ├── pdf-scanned-ocr.md
│   ├── microsoft-word.md
│   ├── microsoft-powerpoint.md
│   ├── microsoft-excel.md
│   ├── images-and-alt-text.md        ← cross-cutting; referenced by every other SOP
│   ├── html-canvas-pages.md          ← the "convert instead of remediate" path
│   └── stem-math-escalation.md       ← Tier C: what students DON'T do, and how to hand it off
├── training/                         ← how we bring a student worker from zero to certified
│   ├── README.md                     ← curriculum map (which resources, in what order, per skill)
│   ├── training-resource-catalog.md  ← the collected external resources (links, cost, access)
│   └── onboarding-checklist.md       ← the per-student path + certification gates
└── process-documentation/            ← how we capture OUR local, SF-State-specific process knowledge
    ├── README.md                     ← the system: what to document, when, where
    ├── TEMPLATE-sop.md               ← standard template every procedure doc uses
    ├── TEMPLATE-process-note.md      ← lightweight "how we actually handle X here" note
    ├── TEMPLATE-tool-setup.md        ← tool install/config/license/access docs
    └── process-log.md                ← running index of every local process doc we've written
```

## How the three parts relate

- **remediation-procedures/** is the *standard* — the correct, tool-agnostic-where-possible way to fix each file type, based on WCAG 2.1 AA / PDF-UA and authoritative sources. It changes slowly. Think "the textbook."
- **training/** is how a person *learns* to execute those procedures. Points mostly at existing external curricula (we reuse, we don't build) plus our own onboarding path.
- **process-documentation/** is where we write down *how it actually works at SF State* — the things no external guide can tell us: which Acrobat license to use, the exact intake mailbox, the naming convention for delivered files, the decision we made about Equidox vs Acrobat, the weird edge case someone solved last Tuesday. This is our institutional memory. **The SOPs are the map; the process docs are the local knowledge that keeps the map honest.**

## Operating principles (encoded in every procedure)

1. **Source-first.** If the original Word/PowerPoint/Excel exists, remediate *that* and re-export — never just patch the PDF, because PDF-level fixes are destroyed on the next re-export. Only remediate the PDF directly when the source is unavailable.
2. **Convert when it's cheaper than fixing.** Simple PDFs that are really just text often belong as native Canvas Pages or accessible HTML, which stay accessible and reflow on mobile. Weigh conversion against remediation (watch copyright on published readings).
3. **Never remediate unused content.** Confirm the item is actually in use (TidyUP / usage check) before spending a minute on it.
4. **Two gates on everything.** Automated check (Acrobat checker / Office Accessibility Checker) AND a human check (reading order, meaningful alt text, correct heading logic). Automated-clean ≠ accessible.
5. **Log at intake, close with metrics.** Every item enters the tracker on arrival and leaves it with time/pages/issues/QA recorded (CCC lifecycle rule). This is the raw data for Phase 5 reporting — no exceptions, even while the "tracker" is still a spreadsheet.

## Status

| Component | State |
|---|---|
| Decision tree | Draft written; validate with first real queue |
| Per-file-type SOPs | Draft written from standards; being enriched with cited tool-specific steps + training links |
| Training catalog | Being populated from research |
| Onboarding path | Draft |
| Process-doc system | Templates ready to use now |

See `../phase-1-document-remediation.md` for the phase-level objective, workstreams, deliverables checklist, and metrics.
