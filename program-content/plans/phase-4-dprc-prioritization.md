# Phase 4 — DPRC-Coordinated Course Prioritization

*Status: Pending — requires DPRC relationship maturity (kick-off: Christina/DPRC phased in as program matures) and Phase 5 data plumbing.*
*Research basis: background-research.md §8, §12.*

## Objective

Build the triage system that ranks Canvas courses for proactive remediation using DPRC enrollment data — remediate courses with registered disabled students **before** the student hits a barrier, then fall back to impact/usage ranking for everything else.

## Why this is the program's signature piece

No peer campus publishes a systematic enrollment-driven triage model — published frameworks rank by issue severity (MSU), impact/usage (Cal State LA), or faculty request (CSUF). The components all have precedent; the assembly is novel:

| Component | Precedent |
|---|---|
| DPRC→AT data link per accommodated student | CSU Fullerton: AIM Specialist added as TA to approved students' Canvas courses |
| Pre-term lead time | CCC standard: DSPS students notified ≥4 weeks before term; requests front-load the queue |
| Accommodation = top tier | UW captioning framework |
| Severity SLAs within a course | MSU: Critical 2mo / Significant 4mo / Minor 6mo (tune windows to our throughput) |
| Impact/usage ranking for the rest | Cal State LA: "prioritized based on impact and usage" |
| Accommodation-triggered outreach machinery | **Cal State LA "AIM for Student Success"** (CSU ATI framework appendices): provost announcement → dean amplification → **personalized request-form links in notification waves** (~2-week cadence, two dean follow-ups) to faculty whose course has an accommodation request → course copied & remediated on consent → "Accessible All-Star" recognition (RTP-citable). **Still request-gated — the faculty form is the bottleneck our enrollment triage removes.** |
| Official criteria menu for ranking | CSU ATI framework §1.5: enrollment, GE/core, **DFW/incomplete rates**, **gatekeeper courses**, accommodation history, **instructor readiness**, **cross-section/semester reuse**, issue complexity from scans |

## Proposed priority stack

1. **P0 — Accommodation-triggered:** DPRC request in an active course. SLA-bound; reactive; should shrink over time as P1 coverage grows.
2. **P1 — DPRC-enrollment proactive:** courses with registered DPRC students next term, ranked by (accommodation types × content risk score from Phase 2 scans/CanvasBot census). Target: remediated **before term start** (4-week standard).
3. **P2 — Impact/usage:** high-enrollment, recurring, high-content-volume courses. Refine with the framework's criteria: GE/core and **gatekeeper** courses, **high-DFW** courses, materials **reused across sections/terms**, and instructor willingness as a tiebreaker.
4. **P3 — Request-driven:** faculty who ask (never below the line — goodwill matters).

## Data & privacy design (engineering + policy)

- **Minimum viable data from DPRC:** course sections containing ≥1 registered student needing content accommodations, plus accommodation *category* (vision/hearing/print/etc. → drives what gets remediated first in the course). Not names; not diagnoses. Category also drives the **delivery format** for accommodation-driven output — e.g., a print/vision accommodation in a math-heavy course means **EPUB 3 + MathML or HTML** consumable by math-capable readers (Kurzweil 3000, Central Access Reader), not a tagged PDF; see the format hierarchy in `../research/accessible-math-reading.md`. Work with DPRC + registrar on FERPA-appropriate flow — aggregate course-level flags avoid most disclosure issues.
- Term-by-term feed, delivered ≥6 weeks before term start to honor the 4-week remediation lead.
- Content risk score per course: UDOIT score + CanvasBot census (document counts/types, video minutes uncaptioned, scan blind-spot content).
- Output: ranked queue into the Phase 5 tracking system; capacity line drawn per term based on measured throughput.

## Governance

- Joint AT–DPRC operating agreement: who flags, who prioritizes, who remediates, escalation path, shared metrics. (Kick-off context: role confusion between AT and DPRC is an open organizational issue — this agreement is where it gets settled for remediation work. EDUCAUSE framing supports the split: institution/AT owns systemic accessibility; DPRC owns individual accommodations.)
- Christina/DPRC join the working group at this phase (per kick-off long-term goals).

## Deliverables

- [ ] Data-sharing agreement + FERPA review (aggregate course flags)
- [ ] Priority-stack algorithm documented and ratified by AT + DPRC
- [ ] Term-cycle calendar (feed date, triage date, remediation window, term start)
- [ ] Ranked queue integrated into tracking system
- [ ] First proactive term: report % of P1 courses remediated before day one

## Metrics

% P1 courses ready by term start · P0 request volume trend (goal: down) · P0 turnaround time · barrier reports from DPRC students in remediated vs unremediated courses.
