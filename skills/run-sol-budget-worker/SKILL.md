---
name: run-sol-budget-worker
description: Run Yue's quota-aware Sol/Luna workflow. Let Luna Max complete most clear, verifiable work directly; use Sol selectively for framing, conflict resolution, risk gates, and high-risk acceptance. Use whenever the user invokes `$run-sol-budget-worker` or includes the exact phrase “省额度” in a task request. Terra is never an automatic fallback.
---

# Run Sol + Luna Budget Workflow

Original workflow by **Yue**. Treat scarce Sol usage as decision bandwidth, not default labor. Prefer the simplest route that can produce a verifiable outcome.

This Skill cannot switch the current task's model or force an unavailable child model. Inspect the capabilities exposed in the current task, choose a route honestly, and never simulate delegation with extra CLI processes.

## Choose the route

1. **Current task is Luna Max — `LUNA_DIRECT`:** execute Green and Yellow work end to end in the current task. Do not spawn another worker merely to follow an orchestration pattern. Pause only at a Red decision or authorization gate.
2. **Current task is Sol and native Luna is available — `SOL_PLAN_LUNA_EXEC`:** Sol makes the minimum necessary decisions, gives one Luna Max worker a self-contained task card, and verifies only to the level required by risk.
3. **Current task is Sol and Luna is rejected or unavailable — `LUNA_UNAVAILABLE`:** do not retry a stable rejection and do not automatically substitute Terra. Finish a small Green task directly only when that is cheaper than rerouting; otherwise recommend continuing in a fresh Luna Max task with a handoff card.
4. **Terra — `TERRA_EXPLICIT`:** use Terra only when the user explicitly asks for it. Never treat Terra as a cost-equivalent Luna fallback.

Do not require Sol xhigh. Sol medium is the normal planning controller; use high for genuine ambiguity or important tradeoffs, and xhigh only for exceptional Red work. If the current model or effort cannot be inspected, report the route without claiming the label was verified.

## Match the quota posture

- **Healthy weekly quota:** an ambiguous or high-value task may start with one Sol medium planning pass, then move to Luna Max for execution. Do not reserve a second Sol pass unless Yellow uncertainty remains or a Red acceptance gate exists.
- **Tight weekly quota:** default to `LUNA_DIRECT`. Spend Sol only on an unresolved Yellow decision or Red gate, not on Green planning or duplicate verification.
- **Emergency or paid-credit bridge:** keep the work in one Luna Max task when safe, avoid parallel agents and optional polish, and defer non-urgent Red work instead of consuming Sol continuously.
- **Quota unknown:** use the tighter posture. Do not ask about the percentage unless it would change an immediate model decision.

## Classify by risk

- **Green:** extraction, status audit, documentation, reports, repetitive checks, log review, fixed tests, browser data entry, and small mechanical edits with objective evidence. Luna may execute and self-verify fully; Sol must not repeat the work.
- **Yellow:** bounded multi-file implementation, diagnosis, browser or remote workflows, service integration, and reversible changes with explicit acceptance criteria. Luna normally executes end to end. Sol checks only locked decisions, critical evidence, and unresolved conflicts; it does not independently redo every step.
- **Red:** architecture commitments, host or runtime identity under conflicting evidence, canonical state transitions, production deployment or restart, security recovery, secrets, irreversible actions, consequential external communication, and final high-risk acceptance. Sol owns the decision and final acceptance. Luna may collect evidence, prepare changes, run reversible tests, and draft outputs within exact limits.

The label follows the riskiest unresolved step, not the size or length of the task.

## Run lean

1. Read applicable project instructions and enough current evidence to avoid wrong-host, wrong-project, or dirty-worktree mistakes.
2. Make one task card, no longer than six lines:

```text
Goal and done condition:
Known facts and locked decisions:
Allowed tools, files, host, and writes:
Forbidden actions and approval gates:
Evidence required at completion:
Stop or escalate when:
```

3. In `LUNA_DIRECT`, use the card internally and proceed. In `SOL_PLAN_LUNA_EXEC`, spawn one fresh Luna Max worker (`gpt-5.6-luna`, `max`) with the card. Use a second worker only for a genuinely independent scope that saves meaningful time; never use more than two.
4. Permit writes only when the user requested implementation, the target is exact, and the change is recoverable. Preserve unrelated user work. Never widen inherited permissions.
5. Verify with the cheapest decisive evidence: current files, focused tests, Git diff, execution receipts, or visible runtime state. Green requires objective self-verification; Yellow requires targeted Sol spot-checking when Sol is present; Red requires independent Sol verification.
6. Retry only real tool, transport, or path failures. Do not rerun a wrong answer to manufacture a pass.
7. Stop when the stated acceptance criteria pass. Do not add abstractions, process files, broad audits, or optional polish unless they are required for the outcome.

## Communication budget

- Do not narrate every tool call or repeat the Skill explanation.
- Send an update only when the route is chosen, the state materially changes, user action is needed, a blocker appears, or a risk gate is reached.
- Keep plans short and outcome-facing. Separate required work from optional improvement.
- Return one consolidated result, not raw worker transcripts.

## Reporting

Lead with what is now usable and what remains unsafe or unverified. Then state briefly:

- route: `LUNA_DIRECT`, `SOL_PLAN_LUNA_EXEC`, `LUNA_UNAVAILABLE`, or `TERRA_EXPLICIT`;
- what Luna completed and what evidence passed;
- which narrow judgment or check Sol retained, if any;
- result: `PASS`, `PARTIAL`, `NOT_VERIFIED`, or blocked.

Never promote `NOT_VERIFIED`, `PARTIAL`, `HOLD`, or similar states. A local or test result is not production deployment, and a child completion message is not proof by itself.
