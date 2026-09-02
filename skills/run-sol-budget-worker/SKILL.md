---
name: run-sol-budget-worker
description: Run Yue's quota-aware Sol/Luna/Terra workflow with Luna Max as the default execution owner, optional Terra xhigh when Yue explicitly chooses it, focused Sol judgment, model-switch recovery, and an explicit reset-window sprint. Use whenever the user invokes `$run-sol-budget-worker` or includes the exact phrase “省额度” or “额度即将重置”. Luna Max means exactly `gpt-5.6-luna` with `max` reasoning; Terra means exactly `gpt-5.6-terra` with `xhigh` reasoning and is never a silent fallback.
---

# Run Sol + Luna Budget Workflow

Original workflow by **Yue**. Treat scarce Sol usage as decision bandwidth, not default labor. Prefer the shortest route that produces a real, verifiable outcome. Existing project, permission, safety, host, and human-approval boundaries remain authoritative; do not turn them into a second workflow or a wall of artificial evidence gates.

This Skill guides routing and handoff. It cannot force the current model to change, bypass a native model rejection, enable Fast, or create a second agent through an unrelated CLI process. Confirm model and effort from runtime metadata, the selector, native spawn settings, or the user's explicit selection. If they cannot be confirmed, say so.

## Core invariants

1. **One execution owner.** Luna Max, Terra xhigh, or Sol owns the next action. An adviser or reviewer does not silently become a second executor.
2. **Luna Max is the default worker.** The valid Luna route is exactly `gpt-5.6-luna` with `max` reasoning.
3. **Terra xhigh is an explicit alternative worker.** Use exactly `gpt-5.6-terra` with `xhigh` only when Yue names Terra or the current task is already confirmed Terra xhigh and Yue asks it to continue; do not treat it as a cheaper Luna route.
4. **Sol is judgment bandwidth.** Use it for a consequential unresolved decision, a high-value plan, or one focused milestone review—not routine execution.
5. **Handoff preserves the outcome.** Keep completed work, decisions, constraints, unknowns, and the next action; never replace the user's goal with a smaller checklist.
6. **No duplicate ordinary work.** Recheck only a concrete high-risk conflict or required acceptance condition.
7. **Use the lowest adequate investment.** Max is for the hardest single tasks; Ultra is only for work that genuinely divides into independent streams.

## Routes

Use exactly one route label in the internal decision and final report:

1. **`LUNA_MAX_DIRECT`** — confirmed Luna Max owns the clear execution task end to end.
2. **`SOL_HANDOFF_TO_LUNA_MAX`** — Sol owns execution-shaped work and native Luna Max is available; hand off once.
3. **`LUNA_WITH_SOL_ADVICE`** — Luna remains owner while Sol answers one narrow decision or performs one focused high-value review.
4. **`MODEL_SWITCH_RECOVERY`** — the user changed the model; recover state before continuing.
5. **`SWITCHBACK_GAP_RECOVERY`** — Sol → Luna → Sol or reported context drift; reconcile trusted, executed, and current state.
6. **`RESET_WINDOW_SPRINT`** — the user says exactly “额度即将重置”; spend expiring capacity only on existing authorized high-value work.
7. **`LUNA_MAX_UNAVAILABLE`** — exact Luna Max is rejected, unavailable, or unconfirmable; do not silently downgrade.
8. **`TERRA_EXPLICIT`** — confirmed Terra xhigh is the sole worker after Yue explicitly requests Terra or asks an already-selected Terra xhigh task to continue.

## Normal execution

### Luna Max direct

When the current task is confirmed `gpt-5.6-luna + max`, let it execute the user's goal. Do not spawn another worker, add a ceremonial Sol layer, or create a handoff merely to make the route look sophisticated. Luna performs the normal validation authorized by the task and reports reality honestly: a lab result is not production, and `NOT_VERIFIED` stays `NOT_VERIFIED`.

### Sol to Luna Max

When Sol owns execution-shaped work or the user says “省额度”:

1. Preserve the real outcome in the handoff protocol.
2. Refresh only the facts needed to prevent wrong-project, wrong-host, or dirty-worktree mistakes.
3. Start one native child with `model="gpt-5.6-luna"` and `reasoning_effort="max"` when supported.
4. Tell Luna to continue the current outcome end to end, reuse valid work, and stop only at an existing authorization, safety, or human-only boundary.
5. Luna becomes the sole execution owner; Sol stops routine work and duplicate checks.

For handoff, selector-switch, and switchback recovery, read [handoff-recovery.md](references/handoff-recovery.md). Do not load it for an ordinary Luna-direct task.

### Luna with focused Sol judgment

Use `LUNA_WITH_SOL_ADVICE` only when Luna cannot safely settle one consequential decision from current evidence, or when a completed medium-to-large milestone, architecture commitment, or high-risk acceptance genuinely benefits from independent judgment. Ordinary edits, tests, logs, browser operations, and fixed questions do not qualify.

Send a minimal package:

```yaml
Goal and acceptance: what must be true
Verified facts or changed artifacts: only the decisive material
Existing validation: what already ran; do not repeat it
Open decision or risk: one question or review target
Need from Sol: recommendation, or PASS/CHANGES_REQUIRED with at most 3 material findings
```

When a native override is available, use `gpt-5.6-sol` with `high` for a qualified review or decision; use `max` only when difficulty or consequence clearly warrants it. If Sol is unavailable, Luna keeps ownership and reports the unperformed review instead of emulating it. Do not use Ultra in the normal route. Sol is read-only: it does not edit, deploy, send, rerun ordinary tests, redesign adjacent systems, or take ownership. Luna evaluates actionable findings and continues. Use at most one Sol judgment pass per milestone unless the user asks a new independent question.

## Reset-window sprint

The phrase “额度即将重置” is an explicit request for `RESET_WINDOW_SPRINT`; similar wording such as “额度有点少” is not. Read [reset-window-sprint.md](references/reset-window-sprint.md) only for this route.

Do not infer reset timing from rumors, manufacture work, expand scope, or treat spending quota as success. Fast is optional speed, costs more quota, and must be explicitly requested and visibly available. Ultra is allowed only for at least two genuinely independent ready workstreams.

## Unavailable models and Terra

If native Luna Max is stably rejected, use `LUNA_MAX_UNAVAILABLE`: do not retry for appearance, downgrade Luna, automatically route to Terra, or emulate a child with a second CLI process. Yue may manually switch the task or explicitly authorize Terra xhigh.

Use `TERRA_EXPLICIT` only after Yue names Terra or confirms that an already-selected Terra xhigh task should continue. Confirm exactly `gpt-5.6-terra + xhigh`; if model or effort cannot be confirmed, report `NOT_VERIFIED` rather than silently using another Terra effort. Terra becomes the sole execution owner, performs normal task validation, and does not automatically add Luna or Sol. Terra is not a hidden fallback in the Sol/Luna chain and is not assumed to save more quota than Luna Max.

## Validation and reporting

Validate this protocol without starting unrelated long work:

1. “省额度” keeps Luna Max as execution owner.
2. “额度即将重置” selects only existing `READY` high-value work; no ready work means stop.
3. “额度有点少怎么办” does not activate the reset sprint.
4. One task never justifies Ultra; a normal small edit never triggers Sol review.
5. A qualified milestone gets one read-only Sol pass, at most three material findings, and Luna remains owner.
6. Terra remains explicit-only and exactly xhigh; model rejection or unconfirmed effort is reported honestly.

Report the route label, confirmed model/effort, completed outcome, remaining unknowns, and any narrow Sol judgment. Use `PASS`, `PARTIAL`, `NOT_VERIFIED`, or blocked honestly. A child completion does not by itself prove the parent outcome.
