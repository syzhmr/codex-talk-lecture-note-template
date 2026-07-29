# Talk/lecture-note ExecPlans

Create an ExecPlan under `work/plans/YYYY-MM-DD-short-topic.md` when work spans
several topics or page ranges, changes policy or tooling, has major unknowns,
or is likely to continue across sessions. Small localized edits do not need one.

`WORK_LEDGER.md` remains the canonical mathematical, source, and next-content
state. An ExecPlan records execution state only; copy durable decisions,
unresolved mathematics, and the next content step back to the ledger.

Use this structure:

```markdown
# Outcome

State the reader-visible or workflow-visible result.

## Scope and non-goals

Name exact lecture topics, handwritten pages, files, and exclusions.

## Source map

List handwritten pages, policy/ledger headings, reference pages, and existing
TeX. Record uncertainty and source differences rather than guessing.

## Progress

- [ ] YYYY-MM-DD HH:MM TZ — concrete milestone and next action.

## Surprises and discoveries

Record facts that changed the approach.

## Decision log

- YYYY-MM-DD — decision, reason, and consequences.

## Milestones

State end conditions and observable acceptance evidence.

## Implementation

Describe bounded edits in execution order.

## Validation and acceptance

Give commands and success conditions, including build checks for TeX changes,
exact-page PDF inspection, loss audit, and `git diff --check`.

## Recovery

State how to resume safely and preserve user changes.

## Outcome and retrospective

Summarize delivery, remaining gaps, and acceptance evidence.
```

A plan does not authorize network access, dependency installation, commits,
pushes, destructive actions, or broader edit scope.
