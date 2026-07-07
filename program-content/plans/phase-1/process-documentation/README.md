# Local Process Documentation — The System

*How the SFSU document remediation team captures its own institutional knowledge as it works. This is where "how it actually works here" gets written down, so it isn't trapped in one student's head.*

## Why this exists

The remediation SOPs (`../remediation-procedures/`) tell you the *standard* way to fix a file type — they're based on WCAG/PDF-UA and apply anywhere. But every real operation accumulates **local knowledge** that no external guide covers:

- Which Acrobat license/version we use and how a student gets it.
- The exact intake mailbox / form / Box folder where work arrives and gets delivered.
- Our file-naming convention for delivered files.
- The decision we made about Equidox vs. Acrobat and *why*.
- The weird edge case someone solved last Tuesday and how.
- Who to ask when X breaks.

If this lives only in people's memory, it walks out the door when a student graduates. **This folder is our institutional memory.** Writing it down is part of the job, not overhead.

## What to document (and which template)

| You have… | Use | Example |
|---|---|---|
| A repeatable local procedure with steps | **TEMPLATE-sop.md** | "How we intake a document and log it in the tracker" |
| A quick fact, decision, gotcha, or "how we handle X here" | **TEMPLATE-process-note.md** | "We deliver files as `CourseID_OrigName_ACC.pdf`" · "Equidox is our primary tool because…" |
| Tool install / configuration / license / access steps | **TEMPLATE-tool-setup.md** | "Installing and configuring ABBYY FineReader on a lab machine" |

When in doubt, write a **process note** — it's the lightweight option. Promote it to a full SOP later if it turns out to be a core repeatable procedure.

## The rules (keep it usable)

1. **One topic per file.** Small and findable beats one giant document.
2. **Name files clearly:** `sop-<topic>.md`, `note-<topic>.md`, `tool-<toolname>.md` (kebab-case). Example: `sop-intake-logging.md`, `note-file-naming.md`, `tool-abbyy-setup.md`.
3. **Fill the frontmatter** (owner + last-updated + status) so we know if it's current.
4. **Add one line to `process-log.md`** whenever you create a doc — that's the index everyone scans.
5. **Date decisions.** "We chose X on 2026-08-01 because Y." Future-you needs the *why*.
6. **Update, don't duplicate.** If a doc exists on the topic, edit it. Note the change date.
7. **Capture the gotcha the moment you solve it.** The five minutes right after you figure something out is when it's cheapest to write down.

## Where this feeds

- **Onboarding:** new students read the relevant process docs to learn our local setup (paired with `../training/`).
- **QA & consistency:** everyone follows the same local conventions.
- **Phase 5:** stable, proven local SOPs graduate into the formal tracking-system documentation and the program's operating manual.
- **Resilience:** when a student leaves, their knowledge stays.

## Starter docs to write first (checklist)

These are the local docs the operation needs on day one — assign and write them as the process solidifies:

- [ ] `sop-intake-logging.md` — how an item arrives, gets logged in the tracker, and is assigned
- [ ] `sop-delivery.md` — how a finished file is named, where it's delivered, how the tracker is closed
- [ ] `note-file-naming.md` — the delivered-file naming convention
- [ ] `note-tool-decision.md` — Equidox vs. Acrobat (and other tool choices) with the reasoning + date
- [ ] `tool-acrobat-setup.md` — Acrobat Pro access/version/config for students
- [ ] `tool-abbyy-setup.md` — ABBYY FineReader access/config
- [ ] `tool-equidox-setup.md` — Equidox account access (if used)
- [ ] `note-checkers.md` — which checkers we use as gates (Acrobat Full Check + PAC version) and where to get them
- [ ] `note-escalation-routing.md` — where Tier-C items actually go (fills the open items in `stem-math-escalation.md`)
- [ ] `sop-qa-signoff.md` — our local QA/sampling procedure and who signs off

*(This checklist mirrors the "open questions" in `../../phase-1-document-remediation.md` — writing these docs is how those questions get answered and recorded.)*
