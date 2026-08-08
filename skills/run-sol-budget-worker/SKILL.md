---
name: run-sol-budget-worker
description: Run Yue's quota-aware Sol/Luna workflow with Luna Max as the execution owner, explicit mid-task handoff and switchback recovery, and optional Sol advice for genuine high-risk decisions. Use whenever the user invokes `$run-sol-budget-worker` or includes the exact phrase “省额度”. Luna Max means exactly `gpt-5.6-luna` with `max` reasoning; never substitute another Luna effort or Terra.
---

# Run Sol + Luna Budget Workflow

Original workflow by **Yue**. Treat scarce Sol usage as decision bandwidth, not default labor. Prefer the shortest route that can produce a real, verifiable outcome. Existing project, permission, safety, host, and human-approval boundaries remain fully in force; this Skill must not turn them into a second workflow or a wall of artificial evidence gates.

This Skill guides routing and handoff. It cannot force the current task's model to change, bypass a native model rejection, or create a second agent through an unrelated CLI process. Confirm model identity and reasoning effort from runtime metadata, the model selector, native spawn settings, or the user's explicit selection. If they cannot be confirmed, say so.

## Core invariants

1. **One execution owner.** At any moment either Luna Max or Sol owns the next action. An adviser may recommend, but does not silently become a second executor.
2. **Luna Max is the default worker.** The valid Luna route is exactly `gpt-5.6-luna` with `max` reasoning. Do not use another Luna effort to imitate Max.
3. **Handoff is about state, not a new plan.** Preserve the user's actual outcome, completed work, constraints, decisions, unknowns, and next action. Do not replace the goal with a smaller checklist merely because another model is starting.
4. **Reality beats memory.** A handoff is an index, not proof that the world still looks the same. On ownership change, perform a minimal current-state refresh.
5. **No duplicate ordinary work.** The previous owner does not repeat the new owner's normal checks merely to reassure itself. Recheck only a concrete high-risk conflict or a required acceptance condition.

## Routes

Use exactly one route label in the internal decision and final report:

1. **`LUNA_MAX_DIRECT`** — the current task is already confirmed Luna Max; let it execute the user's goal end to end.
2. **`SOL_HANDOFF_TO_LUNA_MAX`** — Sol is the current owner, the work is execution-shaped, and native Luna Max is available; create a handoff and transfer ownership once.
3. **`LUNA_WITH_SOL_ADVICE`** — Luna remains owner and asks Sol one narrow decision question; Sol returns advice only.
4. **`MODEL_SWITCH_RECOVERY`** — the user changed the model in the selector or explicitly says the model was changed; recover state before continuing.
5. **`SWITCHBACK_GAP_RECOVERY`** — ownership moved Sol → Luna → Sol, or the user reports drift, missing context, or a broken continuation; reconcile T0/T1/T2 before choosing the next owner.
6. **`LUNA_MAX_UNAVAILABLE`** — exact Luna Max is rejected, unavailable, or unconfirmable; do not silently downgrade or substitute Terra.
7. **`TERRA_EXPLICIT`** — use Terra only when the user explicitly requests it. Terra is not an automatic fallback and not part of the default route.

## Minimal reality refresh

Run this only on an ownership change, a recovery, or when the current evidence may be stale. Do not turn it into a universal preflight:

- current user outcome and acceptance condition;
- current project/repository and worktree, branch, HEAD, and dirty state;
- relevant host/runtime/service identity and the one decisive current observation;
- what is verified, what is still unknown, and what the handoff says not to repeat;
- the next concrete action and the boundary that would require Yue.

If the task is a small isolated answer or a purely textual job, keep the refresh in the current task context and do not create a file.

## Handoff protocol

Create or update a handoff when ownership changes, a meaningful milestone completes, a major fact or decision changes, or the user pauses/compacts a long task. Prefer the existing project `HANDOFF_CARD.md`, `PROJECT_STATE.md`, or equivalent current handoff section. For a genuinely long cross-session task with no suitable home, create at most one persistent `AGENT_HANDOFF.md`; do not create one file per model switch. For short tasks, keep it in the current task block.

Keep the handoff normally within 300–800 words (maximum 1200 for a complex recovery) and never use a full transcript or raw log as the handoff. Use this shape:

```markdown
# Agent Handoff Card

## User Outcome and Acceptance
What the user actually wants and what counts as done.

## Current Reality (refreshed)
Project/worktree, host/runtime, verified facts, and date/commit where relevant.

## Completed and Verified
What is actually finished, with the smallest useful evidence.

## In Progress / Not Verified
What remains open; preserve PARTIAL, BLOCKED, NOT_VERIFIED, DEMO_ONLY, or equivalent labels.

## Locked Decisions and Constraints
Decisions already made, existing permissions, safety boundaries, and human-only gates.

## Do Not Repeat / Known Traps
Completed ordinary work, wrong-host risks, stale assumptions, and rejected approaches.

## Next Concrete Action
One next action, followed by the next only if it is already authorized and mechanically dependent.

## Human-only or Escalate
The exact action that requires Yue, credentials, approval, or an irreversible decision.
```

The handoff must not invent a restriction that the user or project did not impose. A temporary read-only audit can remain a scoped subtask, but it must not be reported as completion of the larger user outcome.

## Sol → Luna Max

When the current Sol owner is doing execution-shaped work, or the user asks to save quota:

1. Identify the user's actual outcome and write the handoff above before transfer.
2. Refresh only the current reality needed to prevent wrong-project, wrong-host, or dirty-worktree mistakes.
3. Start one native child with `model="gpt-5.6-luna"` and `reasoning_effort="max"`. Prefer inherited current context when the interface supports it; if context inheritance is unavailable, the handoff is mandatory. Do not use `fork_context=false` as a reason to shrink the goal into a local checklist.
4. Give Luna a short continuation brief: “Continue the user's current outcome end to end. Use the handoff as an index, refresh current reality, reuse valid work, and stop only at an existing project, permission, safety, or human-only boundary.”
5. Luna becomes the sole execution owner. Sol stops ordinary execution and does not repeat Luna's routine validation.

## Luna Max direct execution

If the current task is already confirmed `gpt-5.6-luna + max`, use `LUNA_MAX_DIRECT`. Do not spawn another worker, add a Sol review layer, or create a handoff solely to make the route look sophisticated. Luna may write, test, use the browser, or operate a runtime only when the user's request and existing project boundaries authorize it. It must report reality honestly: a lab result is not production, and `NOT_VERIFIED` stays `NOT_VERIFIED`.

## Luna → Sol advice

Use `LUNA_WITH_SOL_ADVICE` only for one concrete unresolved decision that Luna cannot reliably settle from current evidence, such as a consequential architecture choice, a genuine host/runtime conflict, a security-recovery choice, or a high-risk irreversible action. Do not call Sol for ordinary coding, tests, logs, browser operations, document cleanup, fixed questions, or a clearly authorized reversible task.

The advice request is a minimal decision package, not a full transcript:

```yaml
Question: one decision only
Current facts: only verified facts needed for this decision
Options: A / B (and C only if genuinely live)
Constraints: existing project and permission boundaries
Need from Sol: recommend one, explain the decisive reason, name the main risk, state what not to do
```

Sol is an adviser: when a native child override is available, request `model="gpt-5.6-sol"` with `reasoning_effort="medium"`; use high or xhigh only when the actual decision justifies it. Sol must not edit files, run commands, deploy, send, create a replacement architecture, or expand the user's goal. Luna remains owner, evaluates the advice, verifies the affected fact if needed, and continues. Use at most one Sol advice call per task unless Yue explicitly asks a new independent decision.

If the user explicitly asks Sol to take over, or Luna reaches a genuinely irreversible/high-risk decision that cannot be safely deferred, use the reverse handoff: Luna writes a handoff, Sol becomes the sole owner for that decision, and Sol writes a new handoff before returning execution to Luna. Do not let the adviser quietly become the executor or add a separate default route.

## Direct model-selector switch recovery

Use `MODEL_SWITCH_RECOVERY` when the user says they switched models or the selector/runtime shows a new model. A Skill cannot detect every UI switch; if metadata is unavailable, state that model identity is unconfirmed rather than pretending.

Before continuing:

1. Locate the latest handoff, or derive a temporary one from the most recent user goal and current files/state.
2. Perform the minimal reality refresh.
3. Compare the new owner with the handoff: `continue` if aligned, `recover` if context is incomplete, and stop for Yue only if there is a real authorization or material state conflict.
4. Reuse completed work. Do not restart project planning just because the model changed.

## Sol → Luna → Sol switchback recovery

Use `SWITCHBACK_GAP_RECOVERY` when a Sol task was handed to Luna, then returned to Sol, or when the user reports that the continuation lost context. Build one recovered handoff and reconcile:

- **T0 — Last trusted Sol state:** the last accepted user outcome, decisions, completed evidence, and boundaries before the first switch.
- **T1 — Luna state:** what Luna actually ran, exact model/effort if known, outputs and receipts, and the scope it was really given.
- **T2 — Current reality:** a fresh minimal check of the actual worktree/host/runtime and current user-visible state. The handoff alone is never T2.

Classify every material item as `KEEP`, `VERIFY`, `REWORK`, or `DROP`. Keep valid evidence; verify facts that may have changed; rework a narrowed or mis-scoped task definition; drop stale assumptions, duplicate work, and false completion/outage claims. Then issue one new handoff with the restored outcome and select the next owner. Never discard all Luna work and never trust all Luna work without T2.

## Unavailable models and Terra

If the native interface rejects exact Luna Max, use `LUNA_MAX_UNAVAILABLE`: do not retry a stable rejection, downgrade to another Luna effort, or automatically route to Terra. The user may manually switch the current task or explicitly authorize another route. If Luna cannot call a Sol adviser, do not emulate it with a second CLI process; continue only when safe, otherwise report `PARTIAL`/`NOT_VERIFIED`.

Use `TERRA_EXPLICIT` only after the user explicitly names Terra. Do not add Terra to the normal Sol/Luna handoff chain merely because a native interface limitation exists.

## Validation and reporting

Validate this protocol against these minimal cases without starting unrelated long work:

1. Luna Max direct work → `LUNA_MAX_DIRECT`.
2. Sol mid-task to Luna → handoff, one exact Luna Max child, one owner, no narrowed replacement goal.
3. Luna asks Sol → minimal decision package, Sol advice only, Luna remains owner.
4. Sol → Luna → Sol → T0/T1/T2 reconciliation, `KEEP/VERIFY/REWORK/DROP`, recovered handoff, explicit next owner.
5. User explicitly requests Terra → `TERRA_EXPLICIT` only.

Report one route label, the confirmed model/effort, what was completed, what remains unverified, and any narrow Sol judgment. Use `PASS`, `PARTIAL`, `NOT_VERIFIED`, or blocked honestly. Never claim a model switch was successful when the interface rejected it; never claim a child completion proves the parent outcome.
