# idea-validation skill

An end-to-end agent skill that takes any app / startup idea and produces everything needed to validate and build it:

1. **Research** — searches the web, Product Hunt, Reddit, Indie Hackers, G2/Capterra, Alternatives.to, and trend signals for the idea and its market.
2. **Evaluate** — judges whether the problem is real, maps the competition, and finds the idea's wedge.
3. **Earning potential** — revenue models, pricing benchmarks, TAM/SAM/SOM, and 12/36-month scenarios (conservative / base / optimistic), backed by sourced benchmarks.
4. **Build plan** — with the user's chosen stack (Laravel, Next.js, etc.): a PRD, backend architecture, **AI token-usage management**, and a **memory system design** (short-term / long-term / vector memory).
5. **Design** — a ready-to-paste **Google Stitch** prompt pack (master prompt, per-page prompts, design tokens, iteration prompts, export steps) to design the whole app at stitch.withgoogle.com.
6. **Implementation** — developer instructions and a phase-by-phase checkbox todo list using the chosen stack's real commands.
7. **Subagent audit** — a strict auditor pass reviews every deliverable for fabricated sources, optimism bias, and plan gaps, then delivers a final **GO / PROCEED WITH CAUTION / NO-GO** verdict with confidence level.
8. **Vibe coding studio** — after the plan is audited, the agent creates and manages the webapp through a disciplined loop (one vibe prompt → surgical edit → run → commit) with a **PROGRESS.md** handoff so any session can resume cheaply.
9. **Token saving** — always-on token discipline: targeted reads, surgical edits, batched questions, handoff files — plus the app-side token-usage plan from the build plan.
10. **Engagement** — healthy momentum mechanics (instant wins, progress markers, one clear next step) to keep users engaged and coming back.
11. **Subagent orchestration** — the Researcher (research), Auditor (audit), Vibe-coder (coding), and Usage Monitor (token watchdog) each work in their own context and return one compact handoff, keeping the main thread token-cheap (with role-switch fallbacks when no delegate tool exists). When the free-account token allowance runs out, the Usage Monitor stops the build gracefully, writes a session checkpoint to PROGRESS.md, and resumes from it after the quota refills.
12. **Existing project mode** — point the skill at a repo you already have: it detects the stack, maps the codebase into PROGRESS.md, audits the existing code (architecture, auth, payments, security, token tracking, tech debt), and runs the vibe loop directly on it — no starting over.

## How to use

The skill lives at `.agents/skills/idea-validation/SKILL.md`. It loads automatically when you describe an idea, e.g.:

> I want to build an AI webapp that turns product screenshots into code, using Next.js. Validate the idea, research demand and competitors, estimate earning potential, give me a PRD, backend architecture with token usage tracking and memory, Google Stitch prompts for the whole design, and a phase-by-phase todo list to build it.

When the skill runs, it prints the **DEEPAK** banner at the start of every response.

Outputs are saved under `idea-validation-reports/<idea-slug>-/`:

- `<idea-slug>-market-report.md` — validation report + verdict
- `<idea-slug>-build-plan.md` — PRD, architecture, token usage, memory, dev todos
- `<idea-slug>-stitch-prompts.md` — Google Stitch design prompt pack

## Notes

- Every claim is sourced; "no evidence found" is used rather than inventing data.
- All revenue figures are estimates from public data, not guarantees.
- Stack commands in the build plan match the user's chosen stack.
