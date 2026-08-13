# idea-validation skill

An end-to-end agent skill that takes any app / startup idea — or an existing project — and produces everything needed to validate and build it:

1. **Research** — searches the web, Product Hunt, Reddit, Indie Hackers, G2/Capterra, Alternatives.to, and trend signals (run by the **Researcher** subagent).
2. **Evaluate** — judges whether the problem is real, maps the competition, and finds the idea's wedge.
3. **Earning potential** — revenue models, pricing benchmarks, TAM/SAM/SOM, and 12/36-month scenarios (conservative / base / optimistic), all sourced.
4. **Build plan** — with your chosen stack (Laravel, Next.js, etc.): PRD, backend architecture, AI token-usage management, and memory system design.
5. **Design** — a ready-to-paste **Google Stitch** prompt pack (master prompt, per-page prompts, design tokens, iteration prompts, export steps) for stitch.withgoogle.com.
6. **Implementation** — developer instructions and a phase-by-phase checkbox todo list using your stack's real commands.
7. **Subagent audit** — a strict **Auditor** pass reviews every deliverable, then a final **GO / PROCEED WITH CAUTION / NO-GO** verdict with confidence level.
8. **Vibe coding studio** — builds and manages the webapp through a disciplined loop (one vibe prompt → surgical edit → run → commit) with a `PROGRESS.md` handoff.
9. **Usage Monitor** — pauses the build gracefully when your free-account token allowance runs out, writes a session checkpoint, and resumes after the quota refills.
10. **Existing project mode** — point it at a repo you already have: it detects the stack, maps the codebase, audits it, and keeps vibe-coding without starting over.
11. **Engagement & token saving** — healthy momentum (instant wins, progress markers, one clear next step) plus always-on token discipline.

## Installation

The skill is a standard **Agent Skill**: a folder named `idea-validation` containing a `SKILL.md` file. Any AI coding tool that supports agent skills can load it. This repo ships it at `.agents/skills/idea-validation/SKILL.md`.

### Option A — Install with the skills CLI (recommended, installs across all tools)

```bash
# preview what this repo contains
npx skills add Deepak-ai-93/Deepak-Idea- --list

# install into the current project (.agents/skills/)
npx skills add Deepak-ai-93/Deepak-Idea- --skill idea-validation --yes

# install globally for all your projects (add -g)
npx skills add Deepak-ai-93/Deepak-Idea- --skill idea-validation --yes -g
```

### Option B — Manual copy (per tool)

Copy the skill folder into your tool's skill directory. Project-level = available in one repo; global = available everywhere.

```bash
# opencode (project or global)
cp -r .agents/skills/idea-validation <your-project>/.opencode/skills/
cp -r .agents/skills/idea-validation ~/.config/opencode/skills/

# Codex CLI — OpenAI (project or global)
cp -r .agents/skills/idea-validation <your-project>/.codex/skills/
cp -r .agents/skills/idea-validation ~/.codex/skills/

# Antigravity — Google (workspace or global)
cp -r .agents/skills/idea-validation <your-project>/.agents/skills/
cp -r .agents/skills/idea-validation ~/.gemini/config/skills/

# Claude Code — Anthropic (project or global)
cp -r .agents/skills/idea-validation <your-project>/.claude/skills/
cp -r .agents/skills/idea-validation ~/.claude/skills/

# Gemini CLI — Google (project or global)
cp -r .agents/skills/idea-validation <your-project>/.gemini/skills/
cp -r .agents/skills/idea-validation ~/.gemini/config/skills/
```

### Where each tool looks for skills

| Tool | Project-level path | Global path |
|---|---|---|
| opencode | `.opencode/skills/` | `~/.config/opencode/skills/` |
| Codex CLI (OpenAI) | `.codex/skills/` | `~/.codex/skills/` |
| Antigravity (Google) | `.agents/skills/` (default) | `~/.gemini/config/skills/` |
| Claude Code (Anthropic) | `.claude/skills/` | `~/.claude/skills/` |
| Gemini CLI (Google) | `.gemini/skills/` (also `.agents/skills/`) | `~/.gemini/config/skills/` |

> `.agents/skills/` is the open cross-tool standard — opencode, Antigravity, and Gemini CLI pick it up automatically. Cloning this repo into your project makes the skill available to those tools with zero extra setup.

### Verify it's installed

Start a session in the project and say: *"use the idea-validation skill to validate [your idea]"*. The first thing you should see is the **DEEPAK banner**, then the validation flow.

If the skill doesn't appear:
- the folder must be named exactly `idea-validation` (lowercase, hyphens);
- the file must be `SKILL.md` (all caps);
- the frontmatter must include `name` and `description` (description ≤ 1024 characters).

## How to use

Example prompts:

- **New idea:** "I want to build an AI webapp that turns product screenshots into code, using Next.js. Validate it, estimate earning potential, then give me the PRD, backend architecture, Google Stitch prompts, and the phased todo list."
- **Existing project:** "Use the skill on this repo — audit the code, create PROGRESS.md, and start vibe-coding the missing features."

## What it produces

Outputs are saved under `idea-validation-reports/<idea-slug>-/`:

- `<idea-slug>-market-report.md` — validation report + verdict
- `<idea-slug>-build-plan.md` — PRD, architecture, token usage, memory, dev todos
- `<idea-slug>-stitch-prompts.md` — Google Stitch design prompt pack

During building (Phase 8), the project keeps a `PROGRESS.md` as its live status + handoff file.

## Notes

- Every claim is sourced; "no evidence found" is used rather than inventing data.
- All revenue figures are estimates from public data, not guarantees.
- Stack commands in the build plan match your chosen stack.
