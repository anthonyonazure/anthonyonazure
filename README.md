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

For B2B services companies whose ops are split across HubSpot / M365 / Entra / Azure / Zendesk / Slack / Teams / a custom portal. Four distinct competencies — provisioning, monitoring, audit, marketing — all verified end-to-end against a real Microsoft 365 + Azure tenant.

| | What it is | Why look |
|---|---|---|
| **[partner-onboarding-agent](https://github.com/anthonyonazure/partner-onboarding-agent)** | Provisioning agent. Takes a closed-won HubSpot deal to fully operational in <2 hours: provisions M365 (mailbox, SharePoint, Planner), Zendesk org with SLA, internal portal account; generates a co-branded PDF welcome packet (Jinja2 + WeasyPrint), uploads to SharePoint + portal, posts back to the deal | Real M365 readback in the README — every resource ID is Graph-addressable, not a mock. Demonstrates parallel fan-out with a barrier-join state graph and idempotent provisioning |
| **[ai-account-manager](https://github.com/anthonyonazure/ai-account-manager)** | Revenue co-pilot. Watches every active partner account, ranks churn / expansion / co-sell signals, briefs each AM daily with a ranked action list. Three delivery channels working live: Slack DM (Block Kit), Teams channel (Adaptive Card via Power Automate), Teams 1:1 DM (Bot Framework with proactive messaging) | Three real screenshots in the README — same briefing, three channels, all live. Math is deterministic (signals are pure Python, no LLM); LLM only generates the narrative |
| **[compliance-evidence-agent](https://github.com/anthonyonazure/compliance-evidence-agent)** | SOC 2 evidence collector. Pulls Entra (conditional access, audit log, role memberships) + Azure Resource Graph (storage, key vaults, app services, diagnostic settings); validates against a YAML control catalog with deterministic Python predicates; emits a hash-stamped multi-page PDF audit pack | Real-tenant verified — 207 audit events pulled, 3 actual SOC 2 gaps detected. YAML-driven control catalog so ISO 27001 / HIPAA / NIST CSF are sibling files, not separate codebases. PDF SHA-256 sidecar as tamper-evidence anchor |
| **[marketing-automation-agent](https://github.com/anthonyonazure/marketing-automation-agent)** | Cold-outreach agent with a brand-voice firewall. Per-target enrichment + LLM draft anchored on a specific public signal + LLM reviewer pass enforcing hard rules (no marketing tropes, one CTA, signal-anchored). Lands as a DRAFT in Outlook — never sends autonomously | Real-tenant verified — 5 personalized drafts created in a real M365 mailbox, read back via Graph. Compliance-friendly architecture: humans review and click Send |
| **[b2b-agent-toolkit](https://github.com/anthonyonazure/b2b-agent-toolkit)** | Shared Python adapter library. Microsoft Graph (M365, Entra, mailer), Azure Resource Graph, HubSpot, Zendesk, custom portal API. Protocol-based abstractions so real ↔ mock swap with one env flag | All four agents above import this. Demonstrates how to keep multi-vendor integrations testable when half your stack is third-party |

Each repo runs end-to-end **without an API key** thanks to deterministic stub fallbacks — clone, `pip install -e .`, run the CLI, see the agent work.

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
