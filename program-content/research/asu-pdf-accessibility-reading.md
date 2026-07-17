# Full Reading — ASU PDF_Accessibility (AI-Powered PDF Remediation)

*Knowledge-base entry for the SFSU AT Canvas Remediation Program · added July 2026*
*Repo: https://github.com/ASUCICREPO/PDF_Accessibility · Built by Arizona State University's AI Cloud Innovation Center (AI CIC), powered by AWS · License: MIT*

---

## TL;DR for SF State

An **open-source, AWS-native, batch PDF remediation pipeline** that auto-tags PDFs (via the Adobe Auto-Tag API), cleans metadata, and generates AI alt text (via Amazon Bedrock) to target **WCAG 2.1 AA** — at a reported **cents-per-page** vs. **$1–$4/page manual**. It has two lanes: **PDF→PDF** (preserve format) and **PDF→HTML** (convert to accessible HTML). It is best understood as a **high-volume "bulk lane"** for the legacy-PDF backlog that would **complement**, not replace, our careful interactive tools (Acrobat, Equidox) and still requires **human QA** and a **FERPA/data-governance review** before use on student content. It is explicitly a **rapid prototype, "as-is," not warranted for production** — a strong starting point our engineering team could harden, not a turnkey service.

---

## 1. Origin & why it exists

- Grew out of a real higher-ed challenge: **The Ohio State University Libraries** found many of their PDFs failed **WCAG 2.1 AA** (missing tags, structure, and image alt text) and estimated **manual remediation at ~$3–$4 per page** with external expertise they couldn't staff — untenable at library scale.
- ASU's **AI Cloud Innovation Center** (an AWS-powered public-sector innovation lab) built this automated solution in response, and open-sourced it.
- **Compliance driver is the same one driving our program:** the DOJ **ADA Title II** rule requiring public entities' digital content (including documents) to meet WCAG 2.1 AA. (See `../background-research.md` §2 for the SF State/CSU version, including the April 2027 deadline.)

## 2. What it does — two solution lanes

**Lane A — PDF→PDF (preserve original format).**
- Splits a PDF into chunks → orchestrates processing with **Step Functions** → merges results with **ECS/Fargate** tasks.
- **Structural tagging via the Adobe PDF Accessibility Auto-Tag API** (an enterprise Adobe PDF Services API).
- **AI alt-text generation for images/charts via Amazon Bedrock.**
- Also does metadata cleanup.
- Requires **Adobe PDF Services API** access (enterprise contract or trial credentials).

**Lane B — PDF→HTML (convert to accessible HTML).**
- Parses the PDF with **Amazon Bedrock Data Automation**, then produces accessible HTML preserving layout, using the **Bedrock `NOVA_PRO`** model.
- Output package includes the **remediated HTML, image alt text, and an accessibility-improvement report**.
- The HTML remediation is adapted from **AWS Labs' document/"Content Accessibility Utility,"** wired for backend integration.
- Requires **Bedrock Data Automation** service access.
- This lane echoes our own "**convert to HTML/Canvas Pages when cheaper than tagging**" principle (see `plans/phase-1/remediation-procedures/html-canvas-pages.md`).

## 3. Architecture & tech stack

- **AWS services:** S3 (storage), Lambda (triggers/processing), Step Functions (orchestration), ECS + Fargate (containerized processing/merge), CodeBuild, ECR (Docker images), CloudWatch (monitoring/dashboards), Secrets Manager (Adobe credentials), **Amazon Bedrock** (Bedrock Data Automation + Nova Pro; LLM alt-text).
- **External:** **Adobe PDF Services API** (Auto-Tag) for Lane A; Docker containers for processing utilities.
- Serverless-plus-containers pipeline; supports **bulk remediation, on-demand single-file remediation, and custom integration** with existing repositories.

## 4. Deployment & prerequisites

- **Deploy via AWS CDK** through a unified `deploy.sh` bash script with interactive prompts (solution selection, credential input); optional UI; runs from **AWS CloudShell**.
- **Prereqs:** an AWS account with appropriate IAM permissions; **Adobe PDF Services API** creds (Lane A); **Bedrock Data Automation** access (Lane B).
- Repo docs: `CONFIGURING_LIMITS.md`, `IAM_PERMISSIONS.md`, `MANUAL_DEPLOYMENT.md`, `TROUBLESHOOTING_CDK_DEPLOY.md`.
- **Repo layout:** `adobe-autotag-container/`, `alt-text-generator-container/`, `cdk/`, `lambda/`, `pdf2html/`, `policies/`, `docs/`, plus `app.py`, `deploy.sh`, `cdk.json`, `buildspec-unified.yml`, `requirements.txt`.

## 5. Cost & performance (as claimed)

- **~cents per page** (blog also says "a fraction of a penny per page") vs. **$1–$4/page manual** — the headline value proposition.
- **Seconds-to-minutes per document** vs. hours manually; designed for large repositories.
- ⚠️ **No accuracy/quality metrics, tested scale, or WCAG-validation methodology are published.** Cost/speed are cited; *correctness* is not benchmarked in the public materials.

## 6. Maturity, license, and the fine print

- **MIT license**; active repo (~200+ commits, ~120+ stars at time of reading).
- Also surfaced as an **AWS Marketplace** listing and a **remediate-pdf.com** demo/trial.
- **Explicit disclaimers:** code contains "**shortcuts in order to support rapid prototyping**," is provided "**as-is and without warranties**," and is "**not warranted for production environments**" on critical data. Users bear responsibility for testing, security hardening, and suitability assessment.

## 7. Strengths

- **Scale + cost:** genuinely attacks the big cost driver — the legacy-PDF backlog — at a fraction of manual cost.
- **Open source (MIT)** and **higher-ed origin** with the same ADA Title II driver → high transferability to a CSU context.
- **Two lanes** cover both "keep it a PDF" and "make it HTML," matching our own source-first/convert-when-cheaper philosophy.
- **Bedrock data posture:** AWS states Bedrock does **not** use customer inputs/outputs to train base models — a meaningful plus over generic public AI tools for a data-governance conversation (still must be verified against our FERPA needs).
- **Engineering-deployable:** CDK + containers suit a team like ours that can stand up and harden infrastructure.

## 8. Limitations & risks (read before piloting)

- **Human QA still required.** Auto-tag (Adobe) + AI alt text are a **first pass** — the same caveat our SOPs already encode (auto-tag is a starting point; never ship AI alt text unreviewed). Output must pass our two-gate QA (**PAC 2026 + human review**). This aligns with the program's "**AI for first-pass/triage, humans verify**" stance (`background-research.md` §7).
- **No published accuracy.** We'd need our own sample benchmark before trusting it on real course content — especially complex tables, multi-column, and **STEM/math (it won't produce MathML)**.
- **FERPA / data governance.** PDFs are uploaded to **AWS S3 + Bedrock + Adobe's API**. Course materials with student data or unpublished content need a data-handling review — the same gate we flagged for Equidox and the Fullerton AI tool. Adobe's API is a second external processor to vet.
- **Dependency + ops cost.** Requires an AWS account, **Bedrock access**, and an **Adobe PDF Services API contract** (Lane A). That's real setup, spend, and maintenance — not a desktop install.
- **Prototype, not product.** "Not warranted for production" means we'd own hardening, security, and reliability if we ran it for real.
- **Scanned PDFs:** the pipeline centers on tagging/alt-text; genuinely image-only scans still need **OCR first** (our ABBYY/Acrobat step) to have text to tag.

## 9. Relevance & recommendation for SF State

**Where it fits:** a **bulk/automated "first-pass lane"** for the high-volume legacy PDF backlog, running *ahead of* human QA — while Acrobat/Equidox/the Fullerton AI tool handle careful, complex, and accommodation-driven work. It operationalizes two themes already in our research: **AI as first-pass-with-human-review** and **scope/cost reduction at scale**.

**Suggested next step (low-commitment pilot):** have the engineering team stand up the PDF→PDF lane in a **test AWS account** and run a **representative sample** of our real PDFs (simple, multi-column, tables, a scan) through it, then **QA the output in PAC 2026 + NVDA/JAWS** and score it against our tiers. In parallel, run a **FERPA/data-handling review** of the S3/Bedrock/Adobe data path. That tells us cost-per-page *and* real quality on our content before any production decision.

**Guardrails to keep:** every AI/auto output still passes our two-gate QA; no student-data PDFs uploaded until the data review clears; treat it as infrastructure we'd harden, not a finished service.

**Watch item:** because it's MIT-licensed, higher-ed-born, and on AWS Marketplace, it's plausible CSU ATI or sister campuses evaluate it too — worth raising with the ATI coordinator (alongside the Fullerton AI tool) to avoid duplicate effort.

## 10. Quick comparison with our other PDF tools

| Tool | Type | Best for | Human-in-loop | Cost model | Where data lives |
|---|---|---|---|---|---|
| **ASU PDF_Accessibility** | AWS batch pipeline (Adobe Auto-Tag + Bedrock AI alt-text) | **Bulk legacy backlog**, first pass | QA *after* | AWS infra + ~cents/page + Adobe API | AWS cloud + Adobe API |
| **Equidox** | Cloud interactive, zone-based | Careful/complex docs; student production | In-loop | SaaS per-seat | Vendor cloud |
| **Adobe Acrobat Pro** | Desktop, manual tagging | Edge cases, final tag inspection, complex tables | Fully manual | Per-seat license | Local |
| **Fullerton AI PDF tool (CSU)** | AI web tool (evaluating) | TBD — evaluate | QA *after* | TBD | Web/cloud |
| **ABBYY FineReader** | Desktop OCR (+ tagging) | Scanned/image PDFs (OCR first) | In-loop | Per-seat license | Local |

*Takeaway: ASU's tool is the **batch/infrastructure** option — pair it with the interactive tools, don't swap them out.*

---

## Sources
- Repo: https://github.com/ASUCICREPO/PDF_Accessibility (README, `docs/`, MIT license)
- AWS Public Sector Blog — "From inaccessible to inclusive: How the new PDF accessibility remediation solution helps institutions compliantly address accessibility requirements": https://aws.amazon.com/blogs/publicsector/from-inaccessible-to-inclusive-how-the-new-pdf-accessibility-remediation-solution-helps-institutions-compliantly-address-accessibility-requirements/
- ASU AI CIC (challenge origin — Ohio State University): https://smartchallenges.asu.edu/challenges/pdf-accessibility-ohio-state-university
- AWS Marketplace listing: https://aws.amazon.com/marketplace/pp/prodview-hvqjpfphsec6y
- Demo/trial: https://www.remediate-pdf.com/

*Note: public materials do not disclose accuracy metrics or the exact Bedrock model used for alt-text on the PDF→PDF lane (the PDF→HTML lane uses Amazon Nova Pro). Treat cost/speed claims as vendor-reported and validate quality on our own sample.*
