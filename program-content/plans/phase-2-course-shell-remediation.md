# Phase 2 — Course Shell Scanning & Remediation (UDOIT)

*Status: Pending — begins once Phase 1 SOPs and student certification are running.*
*Research basis: background-research.md §4, §12.*

## Objective

Move from per-document work to systematic course-shell remediation: batch-scan Canvas courses with UDOIT, triage findings by severity, and have student assistants remediate in-Canvas content (pages, headings, alt text, tables, links, contrast) at scale.

## Deployment decisions (informed by peers)

1. **Instance scope:** UDOIT enabled in every course (Cal State LA pattern) but with **central/batch scanning**, not opt-in-only — get **Cidiscape** (free with Cidi Labs) or UDOIT Advantage institutional scanning for batch coverage. Pure instructor-opt-in (the default CSU peer model) will not produce program-level coverage.
2. **Pre-clean before scan:** TidyUP (or equivalent cleanup) to remove unused content first — CSUN and Cal State LA both codify "clean up then scan." Consider an archiving policy for dead courses (UCR's scope-reduction lesson) so nobody remediates content that will never be used.
3. **Know the blind spots:** UDOIT does not scan classic quiz questions/banks or New Quizzes and does not cover all WCAG criteria; video is essentially uncovered by all scanners. CanvasBot census (Phase 5) supplies the missing inventory. UDOIT ≠ compliance audit.
4. **Advantage tier evaluation:** UDOIT Advantage adds PDF scanning, alternate-format generation, batch remediation, scorecards + historical trends — evaluate cost (FTE-priced) against building equivalent reporting on the open-source version + CanvasBot.

## Workflow

1. Batch scan target course set → UDOIT findings, High/Medium/Low impact (Cal State LA weighting: 60/30/10 → course score).
2. Course entered into tracking queue with score + issue inventory.
3. Student assistants work the queue: UFIXIT for in-Canvas fixes (alt text, headings, tables, contrast, links); documents found in the course route into the Phase 1 pipeline.
4. Rescan → verify score improvement → close with metrics (before/after score, issues fixed, time).
5. Severity SLAs, adapted from MSU: Critical (blocks task, no workaround) fast-tracked; Significant next; Minor batched. Set concrete windows once baseline throughput is known.

## Course targeting (until Phase 4 automates it)

1. DPRC-registered courses (manual list from DPRC — the Phase 4 preview)
2. High-enrollment, recurring courses (impact × usage — Cal State LA's stated frame)
3. Faculty who request help (Fullerton's opt-in stream — never turn away a willing instructor)

## Faculty-relations groundwork

- Check collective-bargaining/consultation constraints on centrally scanning individual instructors' courses **before** batch scanning (flagged in Canvas community practice).
- Message the service as help, not surveillance: UW's framing ("meet the minimums, we'll help with everything else") and Cal State LA's "not required to fix everything immediately" set the right tone. Formal minimum-requirements policy is Phase 6.

## Deliverables

- [ ] Batch scanning operational (Cidiscape or Advantage) with documented scan cadence
- [ ] Course-level severity/score triage rubric + SLA table
- [ ] Student SOP for UFIXIT-based shell remediation
- [ ] Course queue integrated with tracking system (Phase 5)
- [ ] Baseline scan of first target cohort; before/after scores reported
- [ ] CBA/consultation question resolved

## Metrics

Courses scanned / remediated per term · mean course score before/after · issues fixed by severity · % of active courses meeting threshold score · time per course by size.
