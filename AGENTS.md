# AGENTS

Purpose: this file is the entry map for repository knowledge.

Treat this file as a table of contents, not an encyclopedia. Start here, then load only the smallest set of docs needed for the task.

## Canonical Sources (In Order)

<!-- PROJECT-SPECIFIC: replace this list with your project's actual canonical docs in priority order -->
1. `PLANS.md`
2. `docs/product-specs/index.md`
3. `docs/exec-plans/active/`
4. `docs/exec-plans/completed/`
5. `docs/exec-plans/tech-debt-tracker.md`

## Operating Model

1. Repository markdown is the system of record for product, design, architecture, and execution state.
2. External context (chat, memory, ad hoc notes) is non-authoritative unless captured in-repo.
3. Keep docs short, cross-linked, and layered for progressive disclosure.
4. If it is important for future execution, encode it into repository docs.

## Delivery Stance

<!-- PROJECT-SPECIFIC: adjust these stances to match your project's maturity and compatibility requirements -->
1. Do not preserve legacy UI or backend behavior for backward compatibility by default.
2. Backward compatibility is required only when a spec, execution plan, or explicit instruction says it is required.
3. Optimize for the best current user experience, backend contract clarity, and product correctness, even when that breaks legacy implementation patterns.
4. Treat legacy behavior as migration context, not a binding constraint.
5. Prefer deleting, replacing, or simplifying obsolete implementation patterns over carrying them forward.

## Read Order by Task Type

1. User-facing behavior and acceptance: `docs/product-specs/index.md`, then specific spec.
2. Multi-step execution planning and plan maintenance: `PLANS.md`, then `docs/exec-plans/active/`.
3. Delivery status and sequencing: `docs/exec-plans/active/`.

<!-- PROJECT-SPECIFIC: add more task-type read orders for your project's own canonical docs (vision, design, architecture, specs, etc.) -->

## Execution Plan Lifecycle

1. Multi-step work must have a checked-in plan under `docs/exec-plans/active/`.
2. `PLANS.md` is the canonical contract for what an execution plan must contain and how it must be maintained.
3. Active plans are living documents; keep `Progress`, `Surprises & Discoveries`, `Decision Log`, and `Outcomes & Retrospective` current during execution.
4. Plan completion requires acceptance criteria to be met and recorded.
5. Completed plans move to `docs/exec-plans/completed/`.
6. Known gaps or intentionally deferred work go to `docs/exec-plans/tech-debt-tracker.md`.

## Documentation Update Matrix

When behavior changes, update the matching source of truth in the same change:

<!-- PROJECT-SPECIFIC: map behavior change categories to your own canonical docs -->
1. Milestones, sequencing, execution status: `docs/exec-plans/active/*`.
2. Deferred cleanup or known limitations: `docs/exec-plans/tech-debt-tracker.md`.

## PR/Change Enforcement Checklist

Every meaningful change should satisfy this checklist:

1. Docs impact evaluated: either docs updated or explicitly marked "no-doc-impact" with reason.
2. Any execution status change is reflected in the relevant active/completed plan.
3. Index files remain accurate when docs are added, renamed, or moved.
4. Links and references in touched docs remain valid.

## Commit Message Standard

1. Commit subject must state what changed in clear, concrete terms.
2. Commit body is required for non-trivial changes.
3. Commit body should be high-level but detailed enough to explain:
   - what was implemented or modified,
   - why the change was made,
   - key impact areas (API, data model, UI, docs, ops) when relevant.
4. Avoid vague subjects like "updates", "fix stuff", or "misc changes".
5. Prefer commit messages that are understandable without opening the diff.

## Mechanical Enforcement Intent

These checks should be automated as repository tooling matures:

1. Validate required docs exist and core indexes reference current files.
2. Flag broken internal markdown links.
3. Flag plans in `active/` that do not conform to `PLANS.md` required sections or have stale status/progress metadata.
4. Flag specs/design docs not indexed by their corresponding index files.
5. Run recurring doc-gardening passes to reduce stale guidance drift.

## Repository Layout Intent

<!-- PROJECT-SPECIFIC: replace with your actual top-level directory structure -->
1. `docs/exec-plans/`
2. `docs/product-specs/`
3. `.agents/skills/`

## Agent Skills

1. Skills are loaded from `.agents/skills/`.
2. Use `plan-and-execute` when a request asks to plan work and execute it end-to-end.
3. `plan-and-execute` must operate against `PLANS.md` and the relevant execution-plan docs under `docs/exec-plans/active/`.
4. When executing a single phase in an existing plan, use the `execute-phase` skill together with `PLANS.md`.
