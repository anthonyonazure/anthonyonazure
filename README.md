# Anthony Clendenen

I build production-grade software with LLMs at the core — not chatbots, not demos, not slides. Real applications where Claude is doing structured work that ships, gets measured, and pays for itself.

Top-rated freelancer on Upwork (top 3%, 1000+ hours, 5-star). Based in Arizona.

## What I work on

- **AI-driven workflow automation** — lead pipelines, document extraction, classification, outreach personalization
- **HIPAA-compliant healthtech** — running [Patient Pulse Tracker](https://patientpulsetracker.com), a behavioral-health assessment platform
- **Practical full-stack** — TypeScript, React, Node/Express, Azure Functions, PostgreSQL, SQLite. I prefer one well-designed codebase over six SaaS subscriptions

## Selected open-source

| | What it is | Why look |
|---|---|---|
| **[signal-forge](https://github.com/anthonyonazure/signal-forge)** | Hybrid LLM + tool-use + source-span linking for extracting structured signals from messy documents | Demonstrates how to ground LLM output in source text and reject hallucinations rather than trust them |
| **[lead-engine](https://github.com/anthonyonazure/lead-engine)** | Single-codebase AI lead pipeline — capture, qualify, score, draft, send. Vite/React + Express + SQLite + Claude + Twilio + Postmark | What a small services business actually needs, without six SaaS subscriptions |
| **[claude-prompt-library](https://github.com/anthonyonazure/claude-prompt-library)** | Production-ready Claude prompts with structured outputs and a deterministic eval harness | Shows what "tested prompt engineering" looks like — measurable iteration, not vibes |

Each repo has CI badges, real eval results, security audits applied, and walkthrough docs.

## How I think about LLM products

- **Tool-use forcing over free-form generation.** Strict JSON schemas eliminate parsing failures and let you measure quality.
- **Verbatim grounding.** If the model says it found something in the source, the source must contain it. Hallucination has to be detectable, not assumed away.
- **Eval harnesses on day one.** Prompt changes need a measurement. Otherwise you're tuning by vibes.
- **Cost & latency observability.** Every Claude call should log tokens, cache reads, latency, and computed cost. You can't optimize what you don't measure.
- **Human-in-loop where it matters.** AI drafts, the human reviews and approves before send. The UI is the safety layer.
- **Defense against prompt injection.** Submitter-controlled fields go inside `<<UNTRUSTED>>...<</UNTRUSTED>>` markers; system prompts explicitly tell the model to treat them as data.

## Stack I reach for

**Day-to-day**: TypeScript · React · Tailwind · Node 20 · Express · better-sqlite3 · PostgreSQL · Vite
**AI**: Anthropic Claude (Sonnet for quality, Haiku for cheap) · prompt caching · tool-use schemas
**Cloud**: Azure Functions · Azure Postgres · Azure Key Vault · GitHub Actions
**Communication**: Twilio · Postmark · Stripe

## Contact

- Upwork: [hire me](https://www.upwork.com/freelancers/~anthonyclendenen)
- GitHub: you're here
- Email: in profile
