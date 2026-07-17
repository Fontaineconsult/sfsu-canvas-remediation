# Phase 5 — Lifecycle Tooling, Tracking & Reporting

*Status: Parallel track — minimal viable tracker required by Phase 1; full build as engineering capacity allows.*
*Research basis: background-research.md §9, §10.*

## Objective

Build the data backbone that makes the program lifecycle-driven and progress-reportable: item-level tracking from intake to delivery, a CanvasBot-powered content census, and a leadership dashboard. This is where the engineering team earns its keep — AIMHub's own rationale notes campuses waste remediation time reinventing tracking systems ad hoc; we build ours once, deliberately.

## Components

### 5.1 Lifecycle tracker (the core)
CCC lifecycle rules as invariants:
- **Every work item logged at intake** — id, type (document/shell/video), course, source (DPRC/scan/faculty/census), tier, priority (P0–P3), assignee.
- **State machine:** intake → triage → assigned → in-progress → QA → delivered/closed (+ escalated, deferred, blocked-on-faculty).
- **Every close records production metrics:** time spent, pages/minutes/issues, QA outcome, delivery info.
- Options: ServiceNow (CSUF pattern — check campus instance/licensing) vs custom build. Decide on integration needs: custom wins if the DPRC feed, CanvasBot census, and UDOIT scores need to flow in programmatically; ServiceNow wins on procurement/maintenance. **Start with the Phase 1 spreadsheet schema either way — its columns are the data model.**

### 5.2 CanvasBot content census
CanvasBot v2 (https://github.com/Fontaineconsult/canvas-bot-v2) as the inventory engine commercial scanners don't provide:
- Per-course census: documents (type, count, source), video (platform, minutes, caption status), external links, quiz content (UDOIT blind spot).
- Feeds: Phase 1 queue seeding · Phase 2 risk scores · Phase 3 caption-coverage baseline · Phase 4 course risk ranking.
- Engineering tasks: scheduled census runs across active courses; normalized store; caption-status detection for Studio/YouTube/embedded sources; diff between terms (what's new/reused — reuse triggers Medium captioning tier).

### 5.3 Program dashboard (MSU Power BI pattern)
- **Audience-first design:** leadership view (trend lines, % coverage, deadline runway to April 2027), operations view (queue depth, throughput, SLA breaches), college/department view (Canvas sub-account level — Ally-shop pattern for dept reports).
- Content: course scores + trends (UDOIT), document production (tracker), caption coverage (census), DPRC readiness (% P1 courses ready by term start), training completions.
- Refresh weekly (MSU cadence). Role-gate department views.
- Feeds ATI annual reporting and any CO ATI asks — one source of truth. **Mirror the CSU ATI framework's per-section KPI checklists** (baseline data, request response rates, turnaround, courses/files remediated, student hours, training completions, cost avoidance) — that vocabulary is what the CO reads, and **round-2 student-assistant funding is allocated on demonstrated progress**, so the dashboard is also the funding case.

### 5.4 Integration map
```
DPRC feed ──┐
UDOIT/Cidiscape scores ──┤
CanvasBot census ──┼──► Lifecycle tracker ──► Dashboard ──► Leadership / ATI reports
Faculty intake form ──┤
Vendor captioning API/exports ──┘
```

## Build order

1. Phase 1 spreadsheet schema (now — free)
2. CanvasBot census MVP on a pilot course set (early, high value, de-risks everything downstream)
3. Tracker decision (ServiceNow vs custom) + v1
4. Dashboard v1 (even a static weekly report page counts)
5. DPRC feed + risk scoring (unblocks Phase 4)

## Deliverables

- [ ] Data model / schema doc (work item, course, census record)
- [ ] CanvasBot census running on pilot courses with caption-status output
- [ ] Tracker v1 in production; Phase 1 log migrated
- [ ] Dashboard v1 shipped to core team; leadership view by first quarterly report
- [ ] Written quarterly reporting cadence (what, to whom, from which queries)

## Metrics (about the system itself)

% of work items with complete lifecycle records (target 100%) · census freshness · dashboard weekly refresh reliability · time from intake to triage.
