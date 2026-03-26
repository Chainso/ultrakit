# Product Specs

This directory holds user-facing and operator-facing product specs.

A spec describes **what behavior exists or should exist** from the perspective of someone using the product. It is not an implementation plan. It defines acceptance expectations — what a human can observe and verify once the behavior is delivered.

## How To Use This Directory

1. A spec that is `completed` describes delivered, ratified behavior.
2. A spec that is `draft` captures intended product behavior not yet fully implemented.
3. When a draft spec enters active delivery, the tracking home is the relevant execution plan under `.ultrakit/exec-plans/active/`, not the spec itself.
4. Link specs to execution plans where implementation is in progress.
5. Keep specs focused on observable behavior and acceptance criteria. Avoid implementation detail unless it is truly user-visible.

## Index

See [index.md](./index.md).

## Spec Template

Each spec should include at minimum:

```markdown
# <Feature Name> Spec

**Status:** draft | completed
**Owner phase:** <link to exec-plan if in delivery>
**Last updated:** YYYY-MM-DD

---

## Purpose

Why this behavior exists and who it serves.

## Who Interacts With This

Personas and their roles.

## Primary Flows

What the user/operator does and what the system does in response.

## Acceptance Expectations

Observable, verifiable outcomes that prove the spec is met.

## Out of Scope

What is explicitly not covered.
```
