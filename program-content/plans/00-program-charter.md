# SFSU Canvas Remediation Service — Program Charter & Roadmap

*Owner: Academic Technology (Daniel Fontaine) · Last updated: July 2026*

## Mission

Build a comprehensive, lifecycle-driven Canvas LMS digital accessibility remediation service at SF State that makes course content WCAG 2.1 AA conformant, coordinates with DPRC to serve enrolled disabled students first, and produces reportable progress toward the ADA Title II deadline.

## Regulatory anchor

- **WCAG 2.1 Level AA** is the required standard (ADA Title II, DOJ final rule April 2024).
- **Legacy-content compliance deadline: April 26, 2027** (DOJ Interim Final Rule, April 2026 — extended from April 2026).
- New content is expected to be **born-accessible now** (Cal State LA reads the new-content obligation as effective April 24, 2026 — confirm with CO ATI).
- CSU CO ATI directive: the extension changes nothing strategically — use the time for **quality, sustainable practices, consistent outcomes**.
- Canvas course content is fully covered (password-protected course-content exemption was removed from the final rule). Legacy documents still used in active courses are NOT exempt.

## Program model (from background research §3, §12)

Three-element structure validated at peer institutions:
1. **Central remediation service** (this program) — hub-and-spoke: student assistants on basic documents/course shells at scale; specialists/outsourcing for complex content (STEM, math notation, forms, braille); college liaisons as the program matures.
2. **Faculty support & training** — reuse CCC/Clemson/Cidi Labs curricula; help faculty stop creating inaccessible content.
3. **Minimum faculty requirements** — future policy work (e.g., UDOIT score threshold paired with a support guarantee); not a Phase 1 concern.

## Toolchain

| Layer | Tool |
|---|---|
| Course scanning | UDOIT (+ TidyUP cleanup; Cidiscape or UDOIT Advantage for batch/institutional scans) |
| Content census & inventory | CanvasBot v2 (custom — fills UDOIT's gaps: video sources, file inventory, quizzes) |
| Document remediation | Adobe Acrobat Pro, Equidox, ABBYY FineReader (OCR); source-first where possible |
| Video | Canvas Studio (platform of record) + outsourced professional captioning vendor |
| Alternate media exchange | AIMHub (CSU/CCC exchange — for accommodation-driven conversions) |
| Tracking/reporting | Custom lifecycle queue + dashboard (engineering team); see Phase 5 |
| AI | Triage and first-pass only; mandatory human review; no-training-on-our-data vendor clauses |

## Phases

| # | Plan file | Focus | Status |
|---|---|---|---|
| 1 | `phase-1-document-remediation.md` | Document remediation service (PDF/Office) with the existing student team | **ACTIVE — top priority** |
| 2 | `phase-2-course-shell-remediation.md` | UDOIT-driven course shell scanning & remediation at scale | Pending |
| 3 | `phase-3-video-captioning.md` | Canvas Studio + captioning vendor pipeline, tiered accuracy standards | Pending |
| 4 | `phase-4-dprc-prioritization.md` | DPRC enrollment-driven course triage (the novel piece) | Pending — needs DPRC relationship maturity |
| 5 | `phase-5-lifecycle-tooling-reporting.md` | Intake/tracking system, CanvasBot census, program dashboard | Runs parallel to 1–4; minimal viable tracker needed in Phase 1 |
| 6 | `phase-6-faculty-engagement-training.md` | Faculty training program, minimum-requirements policy, liaisons | Long-term (per kick-off: after standardized practices exist) |

## Stakeholders

- **Core team:** Amanda, Andrew, Daniel, Cristian (kick-off 2026). Daniel + Cristian lead technical documentation; Andrew owns doc reorganization & Box setup; Amanda owns scheduling.
- **DPRC / Christina:** phased in as program matures; Daniel maintains communication on captioning/accommodations meanwhile.
- **SFBRN:** program designed holistically for SFSU + SFBRN needs.
- **External:** John Lynch, East Bay team (practice sharing); CCC Accessibility Center (training reuse); CO ATI (reporting line).

## Program-level success metrics

- % of active course shells scanned; % remediated to threshold
- Documents remediated per term (by type/complexity tier); average turnaround time
- Caption coverage: % of course video with compliant captions (by tier)
- DPRC-registered courses: % proactively remediated before term start
- Reactive accommodation-request volume trending **down** as proactive coverage rises (UW's $2M/year reactive operation is the anti-pattern)
- Quarterly trend reports to leadership; ATI annual report inputs
