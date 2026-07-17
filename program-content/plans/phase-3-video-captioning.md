# Phase 3 — Video & Captioning Pipeline

*Status: Pending. Depends on: Canvas Studio adoption decisions; captioning vendor contract; legal review of external-video capture (kick-off action item, Andrew).*
*Research basis: background-research.md §6, §7.*

## Objective

Route all course video through Canvas Studio with tiered caption quality standards, professional vendor captioning where accuracy matters, student QA of vendor/ASR output, and caption-coverage tracking independent of UDOIT/Ally (which cannot see most video).

## Tiered accuracy standard (adapt UW's framework)

| Tier | Trigger | Standard | Path |
|---|---|---|---|
| **High** | DPRC captioning accommodation in the course | **99%+, human-verified** | Professional vendor; student QA on receipt |
| **Medium** | Reused/recurring recordings; reported bad captions; high-enrollment courses | **97%+** | Vendor or ASR + mandatory student edit pass |
| **Low** | Single-use, one-course, low-audience recordings | Unedited ASR acceptable | Canvas Studio auto-captions |

Rationale: machine captions alone are "rarely accurate enough" for compliance (UW). Vendor accuracy estimates serve as the routing threshold for human review. Budget reference points (UW vendor quotes): ASR ~$0.10/min · ASR+human ~$0.45/min · full manual $1.00–1.85/min — the blended tiered model is several times cheaper than captioning everything manually.

## Policy direction (from kick-off, validated by research)

- **Faculty upload video to Canvas Studio, full stop.** CSUN (YouTube/Panopto) and UW-Whitewater (Kaltura) made the same consolidation move with their platforms; training focuses on this workflow. The CSU ATI framework endorses the same consolidation: assess moving stray media (Zoom recordings, instructor YouTube, embedded Canvas media) onto the central platform, prefer vendor captioning via platform integration, and names **Verbit and Echo Labs** as the systemwide vendor lane (SFSU is exiting Verbit — pattern, not prescription).
- External/YouTube-linked video: pipeline to detect links (CanvasBot detects video sources), then either (a) faculty re-uploads/replaces, or (b) capture-caption-reintegrate **pending the legal opinion** on scraping public content (open kick-off item — do not build ahead of counsel).

## Workflows

1. **Proactive (new content):** Studio upload → auto-ASR → tier assignment → route Medium/High to vendor/edit queue → publish.
2. **Accommodation-driven (High tier):** DPRC request → course video inventory (CanvasBot) → vendor submission → student QA against 99% standard → delivery; log lead time against the 4-week pre-term target.
3. **Legacy backlog:** CanvasBot census of video across active courses → coverage report (total videos, minutes, caption status — MSU dashboard pattern) → prioritize by Phase 4 rules.

## Student assistant role (UW "Student Accessibility Team" pattern)

Submit recordings to the vendor, receive output, **review/edit captions before publication**, log metrics. Captioning QA is a distinct skill track from document work — separate training/certification (CCCAC has a captions micro-course).

## Deliverables

- [ ] Tier rubric ratified with DPRC (they define accommodation triggers)
- [ ] Vendor contract with turnaround + accuracy SLAs, and a no-AI-training-on-our-content clause
- [ ] Canvas Studio faculty workflow guide + training module
- [ ] External-video legal opinion documented; capture pipeline built or shelved accordingly
- [ ] CanvasBot video census + caption-coverage baseline report
- [ ] Student captioning-QA SOP and certification

## Metrics

% of course video minutes captioned (by tier) · vendor turnaround vs SLA · QA correction rate on vendor/ASR output · accommodation lead time vs 4-week standard · % new video entering via Studio vs external links (should trend up).
