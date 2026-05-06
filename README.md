# Anthony Clendenen

I build production-grade software with LLMs at the core — not chatbots, not demos, not slides. Real applications where Claude is doing structured work that ships, gets measured, and pays for itself.

Top-rated freelancer on Upwork (top 3%, 1000+ hours, 5-star). Based in Arizona.

## What I work on

- **AI-driven workflow automation** — lead pipelines, document extraction, classification, outreach personalization
- **Multi-system B2B agent orchestration** — agents that work across HubSpot, Microsoft 365, Zendesk, Slack, Teams, internal portals; replacing manual ops handoffs with provable end-to-end runs
- **HIPAA-compliant healthtech** — running [Patient Pulse Tracker](https://patientpulsetracker.com), a behavioral-health assessment platform
- **Practical full-stack** — TypeScript, React, Node/Express, Azure Functions, PostgreSQL, SQLite. I prefer one well-designed codebase over six SaaS subscriptions

## Selected open-source

| | What it is | Why look |
|---|---|---|
| **[signal-forge](https://github.com/anthonyonazure/signal-forge)** | Hybrid LLM + tool-use + source-span linking for extracting structured signals from messy documents | Demonstrates how to ground LLM output in source text and reject hallucinations rather than trust them |
| **[lead-engine](https://github.com/anthonyonazure/lead-engine)** | Single-codebase AI lead pipeline — capture, qualify, score, draft, send. Vite/React + Express + SQLite + Claude + Twilio + Postmark | What a small services business actually needs, without six SaaS subscriptions |
| **[claude-prompt-library](https://github.com/anthonyonazure/claude-prompt-library)** | Production-ready Claude prompts with structured outputs and a deterministic eval harness | Shows what "tested prompt engineering" looks like — measurable iteration, not vibes |

Each repo has CI badges, real eval results, security audits applied, and walkthrough docs.

### B2B integration agents (Python · LangGraph · Anthropic)

For B2B services companies whose ops are split across HubSpot / M365 / Entra / Azure / Zendesk / Slack / Teams / a custom portal. Eight production-grade agents, a shared adapter library, and a fleet observability dashboard. Verified end-to-end against a live Microsoft 365 + Azure tenant; the AAM bot runs 24/7 in Azure Container Apps.

| | What it is | Why look |
|---|---|---|
| **[partner-onboarding-agent](https://github.com/anthonyonazure/partner-onboarding-agent)** | **Provisioning.** HubSpot Closed-Won → operational in <2 hrs: M365 mailbox + SharePoint + Planner, Zendesk org with SLA, internal portal account, co-branded PDF welcome packet, post-back to the deal | Real M365 readback in the README — every resource ID is Graph-addressable, not mocked. Parallel fan-out + barrier-join state graph |
| **[ai-account-manager](https://github.com/anthonyonazure/ai-account-manager)** | **Revenue ops.** Always-on per-AM briefing — ranks churn / expansion / co-sell signals; delivers via Slack DM, Teams channel, Teams 1:1 DM. **Deployed to Azure Container Apps** | 3 real delivery screenshots; deterministic math (signals = pure Python); LLM only writes the narrative |
| **[compliance-evidence-agent](https://github.com/anthonyonazure/compliance-evidence-agent)** | **Audit.** SOC 2 evidence collector. Pulls Entra (CA policies, audit log, roles) + Azure Resource Graph; deterministic Python predicates emit a hash-stamped PDF audit pack | Real-tenant verified — 207 audit events pulled, 3 actual gaps detected. YAML-driven control catalog → ISO 27001 / HIPAA / NIST CSF are sibling files |
| **[marketing-automation-agent](https://github.com/anthonyonazure/marketing-automation-agent)** | **Cold outreach.** Per-target enrichment + LLM draft anchored on a real public signal + LLM reviewer enforcing hard brand rules (no tropes, one CTA, signal-anchored). Lands as **drafts** in Outlook — never sends | Real-tenant verified — 5 personalized drafts in a real M365 mailbox. Eval harness with 20-target test set scores draft quality against deterministic rules |
| **[security-questionnaire-responder](https://github.com/anthonyonazure/security-questionnaire-responder)** | **Vendor questionnaires.** Auto-answers CAIQ / SIG / Excel from a YAML knowledge base, with citations + confidence per answer. Yellow-highlights cells below the human-review threshold in the output XLSX | The agent refuses to fabricate — when retrieval surfaces nothing, the answer is "open a policy ticket." Reviewer's workflow becomes "scan yellow rows, fix or sign off" |
| **[vciso-assistant](https://github.com/anthonyonazure/vciso-assistant)** | **vCISO.** Slack-first bot answering policy Q&A from KB + open-risk register; monthly board-update PDF generator with SHA-256 sidecar | Risk register feeds output: Q&A surfaces both the policy answer AND the open risk it touches. Same KB reused with `security-questionnaire-responder` |
| **[renewal-forecasting-agent](https://github.com/anthonyonazure/renewal-forecasting-agent)** | **Forecasting.** Per-account renewal probability + ARR-at-risk via deterministic logistic regression on the same signals AAM collects | Math is reproducible; coefficients are versioned in `model/coefficients.json`. Per-feature contribution map per account ("Acme is at 56% because: -1.4 from engagement decay, ...") |
| **[pen-test-reporter](https://github.com/anthonyonazure/pen-test-reporter)** | **Red-team reports.** Raw `nuclei` JSONL + `nmap` XML → polished pen-test PDF. Dedups by template-id, groups affected hosts inline, generates per-finding remediation, severity-orders the index | Severity is the scanner's, never the LLM's. SHA-256 sidecar; reviewers can re-run the scanner and verify any finding |
| **[observability-dashboard](https://github.com/anthonyonazure/observability-dashboard)** | **Fleet ops.** Single-pane FastAPI + SQLite dashboard that surfaces all 8 agents' run history, OK rate, p50/p95 latency, token spend. Agents `POST /v1/runs` to record themselves | One screenshot for the whole portfolio. No log shipping, no Datadog, no Sentry. The fleet is self-aware |
| **[b2b-agent-toolkit](https://github.com/anthonyonazure/b2b-agent-toolkit)** | **Shared library.** 7 adapter families with real Graph / ARM / HTTP clients + matching mocks. Protocol-based — swap real ↔ mock with one env flag | Every agent above imports this. Demonstrates how to keep multi-vendor integrations testable when half the stack is third-party |

Each agent runs end-to-end **without an API key** thanks to deterministic stub fallbacks — clone, `pip install -e .`, run the CLI, see the agent work. CI green on every push; topics + badges on every repo.

## How I think about LLM products

- **Tool-use forcing over free-form generation.** Strict JSON schemas eliminate parsing failures and let you measure quality.
- **Verbatim grounding.** If the model says it found something in the source, the source must contain it. Hallucination has to be detectable, not assumed away.
- **Eval harnesses on day one.** Prompt changes need a measurement. Otherwise you're tuning by vibes.
- **Cost & latency observability.** Every Claude call should log tokens, cache reads, latency, and computed cost. You can't optimize what you don't measure.
- **Human-in-loop where it matters.** AI drafts, the human reviews and approves before send. The UI is the safety layer.
- **Defense against prompt injection.** Submitter-controlled fields go inside `<<UNTRUSTED>>...<</UNTRUSTED>>` markers; system prompts explicitly tell the model to treat them as data.

## Stack I reach for

**Day-to-day**: TypeScript · React · Tailwind · Node 20 · Express · Python 3.12 · FastAPI · SQLAlchemy · better-sqlite3 · PostgreSQL · Vite
**AI / agents**: Anthropic Claude (Sonnet for quality, Haiku for cheap) · LangGraph state machines · prompt caching · tool-use schemas · Langfuse tracing
**Cloud**: Azure Functions · Azure Bot Service · Azure Postgres · Azure Key Vault · GitHub Actions · Microsoft Graph (app-only auth)
**Comms / integrations**: Slack (bot tokens, Block Kit) · Microsoft Teams (Bot Framework + Power Automate) · HubSpot · Zendesk · Twilio · Postmark · Stripe

## Contact

- Upwork: [hire me](https://www.upwork.com/freelancers/~anthonyclendenen)
- GitHub: you're here
- Email: in profile
