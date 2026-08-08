---
name: run-sol-budget-worker
description: Run Yue's quota-aware Sol/Luna workflow with Luna Max as the execution owner and Sol only for genuine high-risk decisions. Use whenever the user invokes `$run-sol-budget-worker` or includes the exact phrase “省额度”. A valid Luna route must be exactly `gpt-5.6-luna` with `max` reasoning; never substitute another Luna effort or Terra.
---

# Run Sol + Luna Budget Workflow

Original workflow by **Yue**. Treat scarce Sol usage as decision bandwidth, not default labor. Prefer the simplest route that can produce a verifiable outcome. Existing project, permission, safety, and human-approval boundaries remain fully in force; do not duplicate them as a new control system.

This Skill cannot switch the current task's model or force an unavailable child model. Inspect the capabilities exposed in the current task, choose a route honestly, and never simulate delegation with extra CLI processes.

## Choose the route

1. **Current task is confirmed Luna Max — `LUNA_MAX_DIRECT`:** execute the current goal end to end. Do not spawn another worker or add a Sol review layer merely to follow an orchestration pattern.
2. **Current task is Sol and native Luna Max is available — `SOL_TO_LUNA_MAX`:** spawn one worker with explicit model `gpt-5.6-luna`, explicit reasoning `max`, and inherited current context. Let it own execution.
3. **Luna Max is rejected or unavailable — `LUNA_MAX_UNAVAILABLE`:** do not retry a stable rejection, use another Luna reasoning level, or automatically substitute Terra. Recommend switching the current task to Luna Max rather than continuing a long Sol workflow.
4. **Terra — `TERRA_EXPLICIT`:** use Terra only when the user explicitly asks for it. Never treat Terra as a cost-equivalent Luna fallback.

Do not require Sol xhigh. Sol medium is enough when a controller is genuinely needed; use high or xhigh only for an actual difficult high-risk decision. Confirm Luna Max from runtime metadata, the model selector, the explicit spawn settings, or the user's explicit selection. If model or effort cannot be confirmed, do not claim that Luna Max ran.

Default to Luna Max whether quota is healthy, tight, or unknown. Sol may re-enter only for a concrete unresolved architecture commitment, conflicting host or runtime identity, canonical state transition, production or destructive action, security recovery, secret or human-only step, consequential external communication, or final high-risk acceptance. This is a safety boundary, not a request to classify every task or build evidence gates.

## Run lean

1. Read applicable project instructions and enough current evidence to avoid wrong-host, wrong-project, or dirty-worktree mistakes.
2. Do not create a fixed task card. In `LUNA_MAX_DIRECT`, proceed from the current context. In `SOL_TO_LUNA_MAX`, fork the current context and use one short execution brief: continue the latest user goal end to end, reuse the existing implementation, and stop only at an applicable project, permission, safety, or human-only boundary.
3. Spawn exactly one Luna worker with `model="gpt-5.6-luna"` and `reasoning_effort="max"`. Do not use another Luna effort. Use a second worker only when the user explicitly asks for parallel agents and the scopes are independent.
4. Permit writes only when the user requested implementation, the target is exact, and the change is recoverable. Preserve unrelated user work. Never widen inherited permissions.
5. Let Luna perform normal outcome verification with the cheapest decisive evidence: current files, focused tests, Git diff, execution receipts, or visible runtime state. Sol must not repeat ordinary work. It checks only a concrete high-risk conflict surfaced by Luna.
6. Retry only real tool, transport, or path failures. Do not rerun a wrong answer to manufacture a pass.
7. Stop when the stated acceptance criteria pass. Do not add abstractions, process files, broad audits, or optional polish unless they are required for the outcome.

## Communication budget

- Do not narrate every tool call or repeat the Skill explanation.
- Send an update only when the route is chosen, the state materially changes, user action is needed, a blocker appears, or a risk gate is reached.
- Keep plans short and outcome-facing. Separate required work from optional improvement.
- Return one consolidated result, not raw worker transcripts.

## Reporting

Lead with what is now usable and what remains unsafe or unverified. Then state briefly:

- route: `LUNA_MAX_DIRECT`, `SOL_TO_LUNA_MAX`, `LUNA_MAX_UNAVAILABLE`, or `TERRA_EXPLICIT`;
- what Luna completed and what evidence passed;
- confirmation that Luna used `max`, or an honest statement that it could not be confirmed;
- which narrow judgment or check Sol retained, if any;
- result: `PASS`, `PARTIAL`, `NOT_VERIFIED`, or blocked.

Never promote `NOT_VERIFIED`, `PARTIAL`, `HOLD`, or similar states. A local or test result is not production deployment, and a child completion message is not proof by itself.
