# ultrakit

A structured software delivery system for AI coding agents. Drop it into any project to get a discover → plan → execute pipeline with worker delegation, parallel code review, and documentation maintenance.

## How It Works

When you ask your coding agent to build something non-trivial, the ultrakit orchestrator activates automatically and drives a three-stage pipeline:

1. **Discover** — The orchestrator asks Socratic questions and launches parallel exploration agents to understand the problem. It gathers codebase context, reads documentation, reads `.ultrakit/notes.md` for durable project and user preferences, and resolves all architectural decisions before any code is written. If ambiguity remains, it explores further recursively until every design question is answered.

2. **Plan** — The orchestrator writes a detailed execution plan with all design decisions resolved and phase boundaries defined. Each phase is small enough for a single agent to complete. The plan is a checked-in markdown file — the single source of truth for what is happening and why.

3. **Execute** — For each phase, the orchestrator spawns one powerful implementation agent, then launches parallel review agents (spec compliance, test quality, code quality, regression safety, integration coherence), then spawns a fix agent if needed. This execute-review-fix loop continues until reviews come back clean. The final phases address documentation.

## What's Inside

### Orchestrator Pipeline

| Skill | Purpose |
|-------|---------|
| `ultrakit:orchestrator` | Pipeline brain — drives discover → plan → execute |
| `references/discover.md` | Socratic discovery with parallel exploration agents |
| `references/plan.md` | Writes execution plans with all decisions resolved |
| `references/execute.md` | Execute-review-fix loop per phase |

### Worker Skills

| Skill | Purpose |
|-------|---------|
| `ultrakit:worker:implement` | Execute one phase from an execution plan |
| `ultrakit:worker:review` | Review one quality dimension of a completed phase |
| `ultrakit:worker:fix` | Apply targeted fixes based on review findings |
| `ultrakit:worker:resume` | Regather context after compaction or handoff |

### Documentation Audit (Ad-Hoc)

| Skill | Purpose |
|-------|---------|
| `ultrakit:audit:docs` | Orchestrate a documentation accuracy audit |
| `ultrakit:audit:doc-worker` | Verify docs against code |
| `ultrakit:audit:code-worker` | Find undocumented code |
| `ultrakit:audit:doc-fixer` | Apply doc fixes |

### Setup

| Skill | Purpose |
|-------|---------|
| `ultrakit:init` | Initialize `.ultrakit/` directory in your project |

### Project Structure (created by init)

| Path | Purpose |
|------|---------|
| `.ultrakit/exec-plans/plan-contract.md` | What a valid execution plan must contain |
| `.ultrakit/exec-plans/active/` | Plans currently in progress |
| `.ultrakit/exec-plans/completed/` | Archived plans |
| `.ultrakit/exec-plans/tech-debt-tracker.md` | Known gaps and deferred work |
| `.ultrakit/notes.md` | Lightweight cross-session project and user preferences for non-audit agents |
| `.ultrakit/developer-docs/` | Internal architecture documentation |

## How to Adopt

1. Copy `.agents/skills/ultrakit-*/` into your project's `.agents/skills/` directory.
2. Run `ultrakit:init` (or `bash .agents/skills/ultrakit-init/init.sh`) to create the `.ultrakit/` directory.
3. Start a conversation with your coding agent and describe what you want to build. The `ultrakit:orchestrator` skill triggers automatically for non-trivial work.

That's it. No configuration files to fill in. The discovery phase explores your project and figures out the context it needs.

## Philosophy

- **All decisions before execution.** The orchestrator resolves every architectural question during discovery and planning. Workers implement — they do not design.
- **The plan is the source of truth.** Not chat history, not memory, not external docs. If it matters, it is in the plan.
- **Notes capture durable preferences.** `.ultrakit/notes.md` is for lightweight cross-session project and user preferences, not execution state.
- **Every phase gets reviewed.** Five quality dimensions, every time. Reviews are cheap and catch real problems.
- **Documentation is architecture.** Developer docs describe system structure and contracts, not implementation details. User docs describe behavior, not internals.
- **Plans survive interruption.** Any contributor — human or agent — can open the plan and continue from where work stopped.

## Contributing

Skills live in `.agents/skills/`. The plan contract lives in `.agents/skills/ultrakit-init/scaffold/exec-plans/plan-contract.md`. To contribute:

1. Fork the repository
2. Make your changes
3. Ensure skill descriptions accurately reflect skill behavior
4. Submit a PR
