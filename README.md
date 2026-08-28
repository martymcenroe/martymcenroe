# Hi, I'm Marty McEnroe — Principal AI Architect & ThriveTech.ai Founder

**Licensed Professional Engineer** · **IEEE PES SC-5 (AI Readiness) Co-Chair** · **22 issued U.S. patents + 9 pending** · **CISSP, CCSP**

I build production-grade agentic AI systems. Five-stage multi-agent orchestration. Hybrid-cloud autonomous agents. Adversarial-hardened consumer AI. Active applied research in AI agent safety. IEEE-SA standards leadership.

**[martymcenroe.ai](https://martymcenroe.ai)** · **[ThriveTech.ai](https://thrivetech.ai)** · **[LinkedIn](https://linkedin.com/in/martymcenroe)** · **[The Age of More](https://theageofmore.substack.com)**

---

## Production Platforms (ThriveTech.ai)

### [Palaestra](https://palaestra.thrivetech.ai) — Grid-Interface Simulation Scored Against a Certified Optimum

You run a data center at the grid interface for a simulated day: buy power, charge and discharge a battery, curtail load, and answer events as they arrive. Every play is scored against a certified optimal line, so "how well did I do" has an exact answer instead of a leaderboard-relative one.

The architecture splits on where the physics live. Heavy derivation happens offline in a Python compiler that emits scenario packs; the runtime engine is deterministic bookkeeping in TypeScript. Scenarios are data the platform loads, never code it ships — a new scenario is a compiled pack, not a deploy. Replay determinism is contractual and test-enforced: re-scoring a stored action log must reproduce the stored score exactly, so an engine change that breaks reproducibility fails the suite rather than silently rewriting history. The server is authoritative and state is folded rather than stored: an episode's current position is reconstructed by replaying its own action log.

Each pack carries an optimum solved offline by mixed-integer linear programming (HiGHS) and replayed through the same engine that scores play, so a published target is engine-verified rather than asserted. The Peninsula's optimum is $54,220.64.

**Scale:** six scenarios live · 455 tests (377 TypeScript, 78 Python)
**Stack:** React 19 · TanStack Router · single Cloudflare Worker (Hono) · D1 · R2 · LinkedIn OIDC

**[Public technical documentation](https://github.com/martymcenroe/Exedra/wiki)** — architecture, the competitor contract every player and every agent speaks, and the authentication, network, and privacy surfaces published for inspection.

---

### [AssemblyZero](https://github.com/martymcenroe/AssemblyZero) — Multi-Agent Orchestration with Cross-Vendor Adversarial Verification

Five-stage LangGraph StateGraph pipeline (Triage → Design → Spec → TDD → PR) coordinating 12+ concurrent Claude and Gemini agents with typed state, conditional routing, retry-with-backoff, and crash recovery via serialized checkpoints. Cross-vendor adversarial verification — Claude generates, Gemini reviews — catches hallucinations across model families. Five-layer evaluation framework: execution-based verification (pytest exit codes drive routing), AST structural analysis, cross-model review, stagnation detection, longitudinal learning.

**Scale:** 740 issues processed · 88% closure rate · 434 PRs merged · 5,583 tests
**Stack:** Python · LangGraph 1.0 · DynamoDB · GitHub Actions

---

### [Aletheia](https://github.com/martymcenroe/Aletheia) — Adversarial-Hardened Consumer AI with Layered Guardrails

Seven-stage handler pipeline for consumer-facing AI product with independent short-circuiting at each stage. Two-layer guardrail system: deterministic denylist followed by semantic LLM classifier with five-category taxonomy returning confidence scores. Tiered model routing: Haiku as default classifier; Opus 4.6 invoked as verifier only when Haiku flags a candidate prompt-injection attempt. Adversarial test suite covering eight attack vectors including prompt injection, jailbreaks, and homoglyph evasion. Privacy-constrained observability — operational metadata only, no content logging.

**Stack:** AWS Lambda · Bedrock · DynamoDB · CloudFront · Chrome and Firefox extensions

---

### [Clio](https://github.com/martymcenroe/Clio) — Privacy-First LLM Conversation Extractor

Chrome extension for extracting full Gemini, Claude, and ChatGPT conversations to structured JSON with images. Strict-local processing, no telemetry. Designed around architectural-trust principles — capability declared in manifest, anything not declared is denied by the browser; the privacy claim doesn't depend on Clio's code *promising* not to call out, it depends on the browser *refusing* the call.

**[Available on Chrome Web Store](https://thrivetech.ai/clio)**

---

### [Chiron](https://chiron.thrivetech.ai) — Exam Practice Built From the Source Text

Two kinds of question bank sit behind one interface. Where a bank is generated, an LLM drafts each question from a published corpus. The question carries the passage it was written from. A human approves it against that passage before any learner sees it. No drafted question enters the bank unreviewed. Where an official pool already exists, the pool is the exam, so it is loaded verbatim with no generation and no review cycle.

Open to any account that signs in:

- **Patent Bar:** USPTO exam preparation from the MPEP, Ninth Edition R-01.2024, with the manual browsable beside the question
- **IAPP AIGP:** AI Governance Professional certification
- **Amateur Radio, Technician:** FCC Element 2, NCVEC 2026-2030 pool, verbatim
- **Amateur Radio, General:** FCC Element 3, NCVEC 2023-2027 pool, verbatim
- **Amateur Radio, Amateur Extra:** FCC Element 4, NCVEC 2024-2028 pool, verbatim

Sign-in is the gate and there is no anonymous tier. Every route declares who may reach it. A test asserts the public list against an explicit allowlist, so opening a route takes a deliberate edit in two places. Material that is not open is removed in the Worker, never hidden in the browser. It does not cross the wire to an account that may not read it.

**Scale:** five banks open on sign-in · 2,226 tests (1,122 TypeScript, 1,104 Python)
**Stack:** React · TanStack Router · single Cloudflare Worker · D1 · R2 · LinkedIn and GitHub OIDC

**[Public technical documentation](https://github.com/martymcenroe/Antron/wiki)** covers how a question is built and classified, what is checked before it ships, and what the application stores about you.

Contact: **chiron@thrivetech.ai**

---

## Private & In-Development (ThriveTech.ai)

### Heuriskon — Applied Math + LLM Research

A framework for LLM-assisted empirical discovery of separating predicates over mathematical objects. Private preview. Where automated reasoning meets exploratory mathematics.

---

## Active Research

### Sentinel-RFC — Agent-Context Permission Architecture

Active applied-research program proposing agent-context permission bits as an architectural alternative to the "agent inherits user permissions" model that creates excessive blast radius for autonomous AI agents. Intentionally open work — goal is community adoption of the permission mechanism. Scope includes manifest specification, capability authorization design, and prototype work targeting filesystem-level enforcement.

---

## IEEE Leadership & Standards

- **Co-Chair**, IEEE PES Long Range Planning Committee Subcommittee 5 — Emerging Technologies, Digitalization, and AI Readiness. *Vision Document due July 2026 PES General Meeting.*
- **Vice Chair**, IEEE-SA IC25-004-01 — *Industry Standards for Grid Readiness for Data Center Deployment*. Published 29 January 2026: [ieeexplore.ieee.org/document/11366058](https://ieeexplore.ieee.org/document/11366058). Triggered an IEEE SETCom study group developing PARs for five new IEEE data center standards.
- **Section Chair and Editor**, IEEE-SA IC25-004-02 Section 5 — *Data Center Design for IT Load Protection: Consumption Patterns and Disturbance Response*. Publishing 2026.

---

## Domain Knowledge Repositories

- **[best-of-pes-ai](https://github.com/martymcenroe/best-of-pes-ai)** — Ranked open-source AI/ML projects for IEEE Power & Energy Society domains. Tracks the leading repositories at the intersection of machine learning and grid infrastructure.
- **[ai-power-systems-compendium](https://github.com/martymcenroe/ai-power-systems-compendium)** — Curated collection of AI/ML resources for the Bulk Power System and utility sector.

---

## Engage ThriveTech.ai

- **Custom AI builds** — applied AI architecture for production-grade requirements.
- **Architecture advisory** — AI governance frameworks, agent operational safety, AI Architecture Review Board precedent at Fortune 10 scale.
- **Standards consultation** — IEEE-PES SC-5 (AI) Co-Chair, IEEE-SA IC25-004 series Vice Chair and Section Chair. Critical-infrastructure AI safety.
- **Chiron module access** — `chiron@thrivetech.ai`

Recent engagements: Texas Department of Transportation (76-page state-wide AI strategic plan, 32 epics, 213 use cases, governance framework, AI ethics framework).

Contact: **president@thrivetech.ai**

---

## Credentials

- **Licensed Professional Engineer (P.E.)** — State of Texas (May 2025)
- **IEEE Senior Member** · **Wireless Communications Professional (WCP)**
- **CISSP** · **CCSP** — (ISC)²
- **AWS — 7 certifications** including Machine Learning Specialty, Solutions Architect Professional, Data Analytics Specialty, Data Engineer Associate
- **Microsoft Azure** — DevOps Engineer Expert · AI Fundamentals · Security, Compliance & Identity Fundamentals
- **PMP** · **PgMP** — Project Management Institute
- **22 issued U.S. patents + 9 pending** spanning AI, cloud computing, cybersecurity, IoT, and wireless communications. **Two U.S. patents filed 2026 — AI Agent Safety.**

---

## Education

- **Master of Computer Science** — University of Illinois Urbana-Champaign (2017)
- **Master of Science, Electrical Engineering** — University of Maryland, College Park
- **Bachelor of Science, Electrical Engineering** — University of Maryland, College Park

---

## GitHub Stats

<p align="center">
  <img src="https://github-readme-stats-marty-mcenroes-projects.vercel.app/api?username=martymcenroe&show_icons=true&theme=radical&cache_seconds=3600" alt="GitHub stats" />
  <img src="https://github-readme-stats-marty-mcenroes-projects.vercel.app/api/top-langs/?username=martymcenroe&theme=radical&layout=compact&cache_seconds=3600" alt="Top languages" />
</p>

---

## Connect

Open to discussing applied AI architecture, agent operational safety in regulated environments, AI governance for critical infrastructure, and IEEE standards work.

- **[martymcenroe.ai](https://martymcenroe.ai)** · **[ThriveTech.ai](https://thrivetech.ai)**
- **[LinkedIn](https://linkedin.com/in/martymcenroe)**
- **[The Age of More](https://theageofmore.substack.com)** — essays on agents, taste, and what not to automate
- **president@thrivetech.ai**
