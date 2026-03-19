# agent-harness

A portable planning and documentation system for agentic software delivery.

Drop this into any repository to give AI agents (and human contributors) a structured way to plan multi-step work, delegate to worker agents, track decisions and discoveries, and safely archive completed plans.

## What is in Here

| Path | Purpose |
|---|---|
| `PLANS.md` | Canonical contract for what a valid execution plan must contain and how it stays current |
| `AGENTS.md` | Agent operating model — how to navigate repository knowledge, commit, and update docs |
| `docs/exec-plans/active/` | Plans currently in progress |
| `docs/exec-plans/completed/` | Archived plans with met acceptance criteria |
| `docs/exec-plans/tech-debt-tracker.md` | Inventory of known gaps and deferred work |
| `.agents/skills/plan-and-execute/` | Controller skill: create plan, sequence phases, delegate workers |
| `.agents/skills/execute-phase/` | Worker skill: execute one bounded phase from an existing plan |

## How to Adopt in a New Project

1. Copy this repo's contents into your project root (or add it as a git subtree/submodule).
2. Replace placeholder text in `AGENTS.md` with your project's canonical source list and repository layout.
3. Symlink or copy `.agents/skills/` into your project's agent skill directory.
4. Start creating plans under `docs/exec-plans/active/` following the contract in `PLANS.md`.

## Quickstart

```
# Create a new plan for a multi-step feature
docs/exec-plans/active/my-feature.md   ← write the plan here following PLANS.md
docs/exec-plans/active/index.md        ← register the plan

# Use the skills
.agents/skills/plan-and-execute/   ← controller: plan + orchestrate
.agents/skills/execute-phase/      ← worker: execute one phase

# When done
docs/exec-plans/completed/         ← move finished plan here
```

## Core Idea

Execution plans are checked-in markdown documents. They are the single source of truth for what is happening, why decisions were made, and how another contributor (human or agent) can resume safely from the working tree alone — without relying on chat history or external memory.
# agent-harness
