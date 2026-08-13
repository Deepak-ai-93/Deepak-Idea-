---
name: idea-validation
description: "End-to-end product skill. Takes any app/startup idea and produces (1) a validated market report — researched across Product Hunt, Reddit, Indie Hackers, G2/Capterra, Alternatives.to, and trend signals — with competition analysis and sourced earning-potential estimates; (2) a full build plan using the user's chosen stack (Laravel, Next.js, etc.): PRD, backend architecture, AI token-usage management, and memory system design; (3) a Google Stitch prompt pack to design the whole app; (4) developer instructions with a phase-by-phase implementation todo list; (5) a vibe-coding studio that creates and manages the webapp with a disciplined, token-saving build loop — heavy work runs through dedicated subagents (Researcher, Auditor, Vibe-coder), each returning one compact handoff; and (6) a strict auditor subagent pass over everything before delivering a GO / PROCEED WITH CAUTION / NO-GO verdict. Uses healthy momentum mechanics — instant wins, progress markers, one clear next step — to keep users engaged and coming back. Use whenever the user shares an idea and wants market validation, earning potential, a build plan, design prompts, implementation todos, or hands-on vibe coding."
---

# Idea Validation → Build Plan → Design → Implementation

Turn a raw idea into an evidence-backed market report, a ready-to-build plan (PRD, stack, architecture, token usage, memory), Google Stitch design prompts, and a phased implementation todo list — all audited by a strict subagent pass before delivery.

## Banner (mandatory — print first, every time)

Whenever this skill runs, print the banner below at the very start of your first response. It must be the first thing the user sees, in any language. Do not skip it, shorten it, or bury it after other text.

```
██████╗ ███████╗███████╗██████╗  █████╗ ██╗  ██╗
██╔══██╗██╔════╝██╔════╝██╔══██╗██╔══██╗██║ ██╔╝
██║  ██║█████╗  █████╗  ██████╔╝███████║█████╔╝ 
██║  ██║██╔══╝  ██╔══╝  ██╔═══╝ ██╔══██║██╔═██╗ 
██████╔╝███████╗███████╗██║     ██║  ██║██║  ██╗
╚═════╝ ╚══════╝╚══════╝╚═╝     ╚═╝  ╚═╝╚═╝  ╚═╝
```

You may follow it with a one-line tagline (e.g. "Idea Validation • Build Plan • Design • Implementation"). The banner appears in the chat/terminal output only — it does not need to be embedded in the saved report files.

## Engagement — keep momentum (healthy addiction)

Make using this skill feel rewarding so users come back. Never use dark patterns — this is about momentum and quick wins, not manipulation:

- **Instant win**: deliver something visible within the first minute (banner → one-line verdict → first artifact). Never bury the user under long preamble.
- **Momentum markers**: show phase progress as you go — "✅ Research done · ⏳ Earning potential next". End every response with the single best next step.
- **Quick-wins ladder**: always point to the smallest achievable win first (MVP slice, one Stitch screen, one working endpoint) before the big picture.
- **Celebrate milestones**: mark completed phases and big moments (verdict, first build, first commit) with a short celebratory line — not walls of emoji.
- **One decision at a time**: ask one focused question per turn, or batch several into a single ask_user — never overwhelm with five questions.
- **Streaks & goals**: encourage a simple rhythm (e.g., "ship one vibe session a day") and track it in PROGRESS.md.
- **Always end with a hook**: the last line of every response is a clear, clickable next action ("Say 'build phase 1' to start").

## When to use

- The user shares a startup / app / side-project idea and wants validation, market research, competition analysis, or earning potential.
- The user wants to actually build it: PRD, stack choice, backend architecture, design, implementation todos.

## Inputs

- **Idea**: what they want to build, who it's for, and constraints (budget, timeline, solo vs. team, platform).
- **Stack preference**: ask which stack they want — Laravel, Next.js, etc. If they don't care, recommend one (see Phase 4.1) and state it as a decision in the report.
- If the idea is vague, ask up to 3 clarifying questions, then proceed. If the user doesn't answer, state your assumptions explicitly and proceed.
- **Language**: write all outputs in the user's language (default: English), in plain, easy-to-read language. Technical terms (TAM, MRR, CAC, PRD) can stay in English with a short explanation.

## Subagents & handoffs (orchestration pattern)

This skill uses three subagents — **Researcher**, **Auditor**, **Vibe-coder** — for the heavy, isolated work. Spawn them with the `delegate` tool when available; if the runtime has no delegate tool, achieve the same effect by switching roles with strict handoffs.

Every subagent follows the same contract:

1. **Brief in** — give it a focused task: what to produce, the inputs (or where to find them), and the exact deliverable format.
2. **Own context** — it does its work in its own context; you never hold its raw intermediate state.
3. **Deliverable out** — it returns ONE compact, structured deliverable (evidence pack / findings list / commit summary). No raw dumps.

This is what keeps the skill token-cheap: the main thread only ever holds the compact deliverables.

## Phase 1 — Research (Researcher subagent)

Spawn the **Researcher** subagent to run this phase. Give it the idea and the source playbook below as its brief; it works in its own context and returns an **Evidence Pack** (format below). If no delegate tool is available, run the research yourself with the same discipline: record every claim with its source URL, and if you can't find evidence write "no evidence found" — never fabricate a source, number, or quote.

**Evidence Pack format** (the only thing that returns to the main thread):

- Problem & demand — pain points, user quotes, demand signals (each with source URL)
- Competitor table — name / positioning / pricing / gaps (sourced)
- Earning benchmarks — MRR/revenue figures with dates (sourced)
- Trends — growth/saturation signals (sourced)
- Research gaps — what could not be verified ("no evidence found")

### Source playbook — run each source type that applies

1. **Product Hunt** — search `producthunt.com <keyword>`. Similar products: launch date, upvotes, maker, current status (many are dead or pivoted). Hundreds of upvotes = validated demand AND established competition.
2. **Reddit** — search `reddit <keyword>` and `site:reddit.com <keyword>`. Check r/SaaS, r/Entrepreneur, r/startups, r/indiehackers, plus niche subs for the domain. Extract: recurring pain points, people asking "is there a tool that…", complaints about existing tools, willingness-to-pay signals. Reuse users' actual words verbatim in the report.
3. **Indie Hackers** — search `indiehackers.com <keyword>`. Similar products' MRR/revenue stories; cite actual figures and dates. Your best earning benchmarks.
4. **Competitors & pricing** — search `<keyword> alternative`, `<keyword> pricing`, plus G2 and Capterra pages. Competitor table: name, positioning, pricing (cite), strengths, weaknesses, gaps.
5. **Trend & market signals** — Google Trends, search interest, funding news, market-size reports. Growing, saturated, or just hyped?
6. **Niche communities** — Hacker News (hn.algolia.com), X/Twitter, Discord/Facebook groups, niche forums for the target user.

## Phase 2 — Analyze: is the problem real and the space winnable?

- **Problem validation**: How real, frequent, and painful is the problem? Who feels it most? Would they pay, or is it a nice-to-have?
- **Demand signals**: search volume, community mentions, traction of existing products. Strong demand + bad existing options = opportunity; weak demand = warning.
- **Competition matrix**: direct competitors vs. indirect (spreadsheets, manual work, generic tools). What do incumbents do badly? What's the idea's wedge?
- **Differentiation & moat**: what the idea does better and why it's hard to copy (data, distribution, integrations, community, brand).
- **Risks**: execution difficulty, market timing, regulation, platform dependence, big-company threat.

## Phase 3 — Earning potential: numbers with sources and assumptions

- **Revenue models**: subscription (SaaS), one-time, usage-based, ads, marketplace fee, affiliate, B2B licensing. Score each for fit.
- **Pricing benchmarks**: real competitor prices (cite sources). Position the idea's price within that range and justify it.
- **Market sizing (TAM/SAM/SOM)**: explicit assumptions per layer. Example: "2M people search X/month (source) × 5% could pay = 100K addressable × 2% reachable in 2 years = 2K customers."
- **Scenarios (12-month and 36-month MRR)**: conservative / base / optimistic, showing the math (customers × ARPU).
- **Unit economics**: rough CAC, churn, LTV — stated as assumptions.
- **Benchmarks**: MRR figures from similar indie products; compare the idea against them.
- **Reality check**: most indie products fail or earn under $1K/month. The conservative case must reflect that honestly. Never present only the rosy case.
- Label ALL numbers as estimates with the assumptions that produced them.

## Phase 4 — Build plan

### 4.1 Stack selection

Ask the user which stack they want. Present real options and, if they're undecided, recommend one based on the product:

| Product type | Recommended stack | Why |
|---|---|---|
| AI webapp (chat, generation, agents) | Next.js + Vercel AI SDK + Postgres | streaming UI, AI SDK, serverless, fastest to ship |
| CRUD / business / admin-heavy app | Laravel + Inertia (Vue/React) or Filament | auth, queues, payments, admin out of the box |
| Marketplace / community / API-first | Laravel API + Next.js frontend | robust backend + rich frontend |
| Landing page + simple tool | Next.js (static + API routes) | simplest possible |

State the chosen stack and the reasoning in the plan. If the user picked a stack that's a poor fit, say so honestly and suggest an alternative, but build the plan around their choice.

### 4.2 PRD (Product Requirements Document)

Write these sections:

- **Overview & goals** — one paragraph: what it is, who it's for, the core problem it solves.
- **Personas** — 2–3 concrete personas with goals and frustrations.
- **User stories** — "As a [persona], I want [feature], so that [outcome]" for every feature.
- **Feature list** — split **MVP** (must-have to launch) vs. **V2** (later). Keep MVP genuinely small.
- **Success metrics** — 3–5 measurable metrics (activation, retention, MRR, cost per user).
- **Non-functional requirements** — performance targets, security, privacy, cost limits per user.

### 4.3 Backend architecture

Design it for the chosen stack. Cover:

- **Layers**: routes → controllers → services → repositories → models (or the stack's idiomatic equivalent, e.g., Next.js App Router route handlers + server actions).
- **Folder structure**: a concrete tree for the chosen stack.
- **API design**: endpoints or server actions for every user story; auth (sessions/JWT); input validation; error handling.
- **Database schema**: tables for users, projects, conversations/messages, usage, subscriptions (plus the stack's migration tool).
- **Auth**: registration, login, password reset, OAuth options (Google/GitHub), role model if needed.
- **Payments** (if the product charges): Stripe (or stack-native, e.g., Laravel Cashier), plan tiers, webhooks for subscription events.
- **Jobs/queues** (if needed): email, background AI work, report generation (Laravel queues / BullMQ).
- **AI integration layer**: provider abstraction (OpenAI / Anthropic / Gemini), streaming, retries, timeouts, structured output.

### 4.4 Token usage management (for AI apps — always include)

- **Tracking**: log every model call — model, input tokens, output tokens, cost — in a `usage` table, keyed by user.
- **Quotas**: free tier gets a monthly token allowance; paid tiers get more. Enforce at the API layer, not just the UI.
- **Cost control**: prompt caching (OpenAI/Anthropic), model routing (cheap/fast model for simple tasks, frontier model only for complex ones), caching repeated results (Redis), batching.
- **Rate limiting**: per-user request/token limits; 429s with clear messaging.
- **Dashboard & alerts**: per-user and global cost view; alert when a user or the app exceeds budget.
- Include the per-model price table with current list prices (cite sources) so the plan has real cost math.

### 4.5 Memory system (for AI apps — always include)

Design a layered memory model:

- **Short-term (working) memory**: recent conversation turns in the request context window.
- **Long-term (episodic) memory**: full session history stored in Postgres (messages, timestamps, metadata); loaded on demand.
- **Semantic (vector) memory**: embeddings + vector store (pgvector / Chroma) for "what did the user say about X" recall; top-k retrieval into context.
- **User profile (facts)**: extracted preferences/facts stored in a structured table, injected into system prompt.
- **Memory ops**: write (extract facts from each turn), retrieve (top-k by relevance), summarize (compress old sessions to stay in context), prune/expire (TTL, size caps).
- **Privacy**: what's stored, what the user can delete, opt-out.

## Phase 5 — Google Stitch design prompt pack

**What Stitch is**: Google Labs' free AI UI design tool at stitch.withgoogle.com (free with a Google account). It turns text prompts into responsive UI and front-end code for web and mobile, can extract a design system from any URL, generates multi-page prototypes with consistent design tokens, and exports to React or Google AI Studio. The user pastes these prompts into Stitch; you produce the prompts.

Produce a prompt pack covering the whole app:

1. **Master prompt** — the whole app in one prompt. Be specific: product one-liner, target users, vibe, layout, device priority, color tone. Example shape:
   ```
   [Name] is a [one-line description] for [target users].
   Design a complete responsive web app with a [adjective] aesthetic.
   Design system: primary color #XXXXXX, accent #XXXXXX, [font vibe],
   [style: e.g. clean SaaS, dark sidebar + card layout, rounded corners].
   Pages: 1. Landing (hero + value proposition + features grid + pricing + CTA),
   2. Auth (sign up / log in), 3. Dashboard (overview with [metrics]),
   4. [Core feature page: describe the main interaction, e.g. chat interface],
   5. Settings (profile, plan, billing). Mobile + desktop layouts, consistent tokens.
   ```
2. **Per-page prompts** — one focused prompt per page/screen so the user can generate them one by one and keep visual consistency (Stitch reuses the project's design tokens).
3. **Design tokens** — the color palette, typography, spacing, and component style to pin down (so every page matches).
4. **Iteration prompts** — ready-to-paste refinements: "make the header more compact", "change the card grid to a list view", "switch to dark mode", "shift colors warmer", "add a mobile bottom nav".
5. **Export steps** — from Stitch: export to React (adapt components to the chosen stack, e.g. Tailwind/component library) or send to Google AI Studio to wire in logic. Give 3–5 bullet instructions.

## Phase 6 — Developer instructions & phased todo list

Write a phase-by-phase build plan with actionable, checkbox-style todos for the **chosen stack**. Use the stack's real commands (e.g., `laravel new app` vs. `npx create-next-app`, Composer vs. npm, `php artisan migrate` vs. Prisma). Standard phases:

- **Phase 0 — Setup & design handoff**: scaffold the app, install deps, env vars, run Stitch export → component base.
- **Phase 1 — Auth & users**: registration/login, profiles, roles.
- **Phase 2 — Core data & CRUD**: schema migrations, models, the main feature endpoints.
- **Phase 3 — AI integration**: provider SDK, streaming, structured output, token usage tracking (4.4).
- **Phase 4 — Memory system** (AI apps): sessions, vector store, summarization (4.5).
- **Phase 5 — Payments & plans**: checkout, webhooks, quotas enforcement.
- **Phase 6 — Polish & launch**: testing, error handling, rate limits, analytics, deploy.

Each phase: 5–10 concrete todos written as `- [ ] do this specific thing`. Mark dependencies (e.g., payments depends on auth). Estimate effort per phase (hours/days) so the user can plan.

## Phase 7 — Auditor subagent: two-pass review (mandatory)

The user explicitly wants a subagent to audit the work, so the audit runs as a true subagent. Spawn the **Auditor** with a brief containing the drafts (or their file paths) plus this skill's audit checklist; it audits in its own context and returns only its findings. If no delegate tool is available, switch roles: finish the drafts as the analyst, then become the Auditor.

### Pass A — Draft

Produce all deliverables from Phases 1–6 (market report, build plan, Stitch prompts, todos).

### Pass B — Audit the drafts (as the Auditor)

Be adversarial. Check, in order:

1. **Source integrity**: every factual claim sourced? Any fabricated URLs, numbers, quotes, or pricing? Anything marked "no evidence found" that actually has evidence — or missing that flag?
2. **Optimism bias**: revenue estimates inflated? Conservative case actually conservative? Survivorship-bias benchmark passed off as typical?
3. **Market gaps**: missed competitors, segments, regions, or threats? Unresearched source type from Phase 1?
4. **Build-plan soundness**: PRD complete (personas, MVP/v2, metrics)? Architecture holes — missing auth, payments, validation, error handling, rate limits, security? Token-usage guardrails present? Memory model covers storage + privacy? Todos actionable and stack-correct (right commands, right deps)? Any phase with no clear definition of done? Token-saving practices and a PROGRESS.md handoff defined for the vibe loop?
5. **Assumptions**: stated, reasonable, flagged as assumptions?
6. **Verdict honesty**: would the verdict change under the auditor's worst-case reading?

Record findings as **CRITICAL / MAJOR / MINOR** with a one-line fix for each — this findings list is the Auditor's single deliverable.

### Pass C — Merge & verdict

Revise all deliverables to resolve every CRITICAL and MAJOR finding (list what changed). Add the final section:

**Audit & Verdict**
- Verdict: **GO** / **PROCEED WITH CAUTION** / **NO-GO** (one line of reasoning)
- Confidence: LOW / MEDIUM / HIGH — based on evidence quality, not optimism
- Top 3 risks (from the audit)
- Recommended next step: the single highest-leverage, cheapest action (pre-sales/landing page, customer interviews, MVP scope, Stitch design pass, pricing test)

## Phase 8 — Vibe coding studio (Vibe-coder subagent)

Once the plan is audited and the user says go, run the build as a vibe-coding loop. The user directs with plain language ("vibe prompts"); the **Vibe-coder** subagent does the code work. It owns the codebase context (reads files, makes edits, runs the dev server) and returns only a short commit summary per loop, so the main thread stays lean and token-cheap. If no delegate tool is available, run the loop in the main thread with the token discipline in 8.4.

### 8.1 Kickoff (one session)

- Scaffold the chosen stack; wire the Stitch export as the UI base.
- Create **PROGRESS.md** in the repo: current phase, what works, what's broken, next up, token log. This file is the handoff — any future session can continue by reading PROGRESS.md alone (this is the single biggest token saver).
- Run the app locally so the user sees something real on screen immediately (instant win).

### 8.2 The vibe loop (repeat per feature)

1. **Prompt**: the user describes ONE change in plain language.
2. **Plan (cheap)**: state the plan in one line, then edit surgically — targeted changes, never rewrite whole files.
3. **Build**: make the minimal change for the chosen stack.
4. **Run**: start/refresh the dev server and check it works.
5. **Commit**: one tiny commit per working feature (e.g., "feat: chat sends first message").
6. **Update PROGRESS.md** (check the todo item off).

Rules: one change per loop; split big changes into 2–3 loops; never leave the app broken at the end of a loop; if something breaks, fix or revert before moving on.

Deliverable per loop: one short summary — what changed, the commit hash, and one thing for the user to check.

### 8.3 Manage & iterate

- Keep the build-plan todo list as the backlog; check items off in PROGRESS.md as they ship.
- End each session with a short **vibe review** (3 bullets into PROGRESS.md): what shipped, what broke, what's next.
- Deploy early (after Phase 0–1), then iterate on real feedback.
- When the user returns, read PROGRESS.md — not the whole codebase — and continue.

### 8.4 Token-saving mode (always on)

- **Context discipline**: read only what's needed (code_search + targeted windows) — never dump whole files back into the conversation.
- **Batch decisions**: collect all answers in one ask_user; avoid back-and-forth round trips.
- **Plan before generating**: one short plan line, then one edit — no speculative rewrites.
- **Surgical edits**: targeted replacements; never regenerate an entire file to change one line.
- **Handoff files**: PROGRESS.md lets a fresh session resume cheaply — prefer fresh short sessions over long ones (long chats burn tokens).
- **Cache & reuse**: reuse earlier research instead of re-searching; cache repeated results.
- **Model routing**: mechanical edits → cheap/fast model; complex reasoning → strong model.
- **App-side costs**: the built app enforces the token-usage plan from Phase 4.4 (quotas, caching, model routing) so running it stays cheap.
- Log tokens per session in PROGRESS.md so the user sees the savings.

## Output

Write three files to `idea-validation-reports/<idea-slug>-/`:

1. **`<slug>-market-report.md`** — Phases 1–3 + audit verdict: idea, problem & demand, competition, differentiation, earning potential, risks, Audit & Verdict, sources.
2. **`<slug>-build-plan.md`** — Phase 4 (stack decision, PRD, backend architecture, token usage management, memory) + Phase 6 (developer instructions and phased todo list) + the audit fixes that changed the plan.
3. **`<slug>-stitch-prompts.md`** — the full Google Stitch prompt pack (Phase 5).

When the user starts building (Phase 8), create and maintain **PROGRESS.md** in the project repo as the live status + handoff file.

Then a short chat summary:
- Verdict + confidence
- 3 strongest findings (with sources)
- Earning potential range (conservative–optimistic, 12-month)
- Chosen stack + why, and the single best next step

Remind the user: revenue figures are estimates from public data, not guarantees.

## Guardrails

- Never invent sources, prices, revenue figures, quotes, or stack commands. "No evidence found" is a valid answer.
- Cite a URL inline for every factual claim.
- Every estimate ships with its assumptions.
- The auditor pass is mandatory for this skill — skipping it is not an option.
- The Deepak banner must be printed at the start of every response when using this skill — never skip it.
- Keep momentum: always end with one clear next action, celebrate milestones briefly, and never overwhelm the user with many questions at once.
- Run the vibe loop in small steps — one change, one commit; never leave the app broken at the end of a loop.
- Token discipline is always on: targeted reads, surgical edits, batched questions, PROGRESS.md handoffs — never dump whole files into context unnecessarily.
- Subagent contract: every subagent gets a focused brief and returns one compact deliverable — never raw dumps back into the main thread.
- Use the stack's real commands and idioms — never generic placeholder commands for a specific framework.
- Keep everything readable: tables, short bullets, plain language in the user's language.
