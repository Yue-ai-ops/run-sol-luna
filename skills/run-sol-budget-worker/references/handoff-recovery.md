# Handoff and Recovery

Read this reference only when execution ownership changes, the model selector changes, or Sol → Luna → Sol continuity needs repair.

## Minimal reality refresh

Refresh only what may change the next action:

- current user outcome and acceptance condition;
- current project/worktree, branch, HEAD, and dirty state where relevant;
- relevant host/runtime identity and one decisive current observation;
- verified work, unknowns, and completed work that must not be repeated;
- next concrete action and the existing boundary that would require the user.

For a small textual task, keep this in context rather than creating a file.

## Handoff card

Prefer an existing `HANDOFF_CARD.md`, `PROJECT_STATE.md`, or equivalent section. For a long cross-session task with no suitable home, create at most one `AGENT_HANDOFF.md`; do not create a file per model switch. Keep it within 300–800 words, up to 1200 only for complex recovery.

```markdown
# Agent Handoff Card

## User Outcome and Acceptance
What the user wants and what counts as done.

## Current Reality (refreshed)
Project/worktree, host/runtime, verified facts, and date/commit where relevant.

## Completed and Verified
Finished work with the smallest useful evidence.

## In Progress / Not Verified
Open work; preserve PARTIAL, BLOCKED, NOT_VERIFIED, DEMO_ONLY, or equivalent labels.

## Locked Decisions and Constraints
Existing decisions, permissions, safety boundaries, and human-only gates.

## Do Not Repeat / Known Traps
Completed ordinary work, wrong-host risks, stale assumptions, and rejected approaches.

## Next Concrete Action
One next action, then only mechanically dependent authorized work.

## Human-only or Escalate
The exact action requiring the user, credentials, approval, or an irreversible decision.
```

The handoff is an index, not proof of current reality. Do not invent a restriction or report a narrow audit as completion of the larger outcome.

## Direct selector switch

For `MODEL_SWITCH_RECOVERY`:

1. Locate the latest handoff or derive a temporary one from the current goal and files.
2. Perform the minimal reality refresh.
3. `continue` if aligned, `recover` if context is incomplete, and stop only for a real authorization or material-state conflict.
4. Reuse completed work; do not restart project planning because the model changed.

## Sol → Luna → Sol switchback

For `SWITCHBACK_GAP_RECOVERY`, reconcile:

- **T0 — Last trusted Sol state:** accepted outcome, decisions, completed evidence, and boundaries before the switch.
- **T1 — Luna state:** what Luna actually ran, model/effort if known, outputs and receipts, and its real assigned scope.
- **T2 — Current reality:** fresh worktree/host/runtime and current user-visible state; the handoff alone is never T2.

Classify each material item as `KEEP`, `VERIFY`, `REWORK`, or `DROP`. Preserve valid work, recheck only changeable facts, repair a narrowed task definition, and discard stale assumptions or false completion claims. Issue one recovered handoff and name the next sole owner.
