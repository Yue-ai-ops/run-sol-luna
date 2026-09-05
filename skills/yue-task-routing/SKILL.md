---
name: yue-task-routing
description: Choose a quota-aware execution, delegation, or focused-advice route for Yue's current task; recover continuity after model switches and use explicitly expiring quota. Use for “省额度”, explicit model-routing requests, “额度即将重置”, or the former run-sol-budget-worker/run-sol-luna workflow. Not a mandatory planner or reviewer for ordinary work.
---

# Yue Task Routing

Original workflow by **Yue**. Optimize for a completed user outcome and total cost, including coordination and rework. Preserve the selected model and real goal; a new release alone is not a reason to migrate every task.

## Choose the shortest useful route

- **Direct execution:** the current model continues the authorized goal. This is the default, including Astra; do not require a cheaper child or stronger reviewer merely because one exists.
- **Budget choice (“省额度”):** consult [model-choices.md](references/model-choices.md). Prefer a proven economical configuration for separable work; do not split tightly coupled tasks solely for a lower advertised model price.
- **Bounded delegation:** use a native child only when authorized and an independent contribution improves completion time, context use, or total cost. Keep overlapping edits with one writer.
- **Focused advice:** obtain one material decision or independent milestone review when it will change the next action, not for every edit.
- **Optional Astra / Sol / Luna combination:** when Yue requests this combination, read the recipe in [model-choices.md](references/model-choices.md). Keep one continuing execution owner; planning, delegation, and final review are conditional help, not four mandatory stages.
- **Model switch or continuity gap:** read [handoff-recovery.md](references/handoff-recovery.md) for `MODEL_SWITCH_RECOVERY` or `SWITCHBACK_GAP_RECOVERY`.
- **Reset sprint:** read [reset-window-sprint.md](references/reset-window-sprint.md) when Yue requests “额度即将重置” or otherwise explicitly asks to use expiring capacity. A quotation, hypothetical discussion, or “额度有点少怎么办” does not start a sprint.

Keep routing internal unless it changes the user's next action or consumption. Do not print a mandatory route/state form every response.

## Ownership and actual capability

A bounded child returns its result to the parent; the parent remains accountable for the user's outcome. A real handoff to another task/model changes ownership only when explicitly arranged. Spawning a child does not automatically transfer the conversation.

Send the goal, relevant facts, allowed write scope, and completion condition. Reuse existing authorization. Do not shrink a repair or delivery request into read-only auditing unless auditing is the user's goal. Inspect returned artifacts; do not duplicate ordinary checks without a material gap or conflict.

Respect explicit model/effort selections. Set both when requesting a specific child, because defaults may inherit the parent. The economical Luna configuration means exactly `gpt-5.6-luna` + `max`; do not silently substitute another Luna effort. Terra has no fixed effort requirement: honor the requested supported setting, and never silently use it as Luna fallback.

This Skill cannot change the current selector, provide missing tools, override native rejections, or activate Fast. An accepted spawn request is not independent proof of backend execution identity; use runtime metadata if available and state the evidence level in comparisons. Missing metadata does not block ordinary current-model work.

Do not enable a paid speed option or redeem a reset without explicit authorization. Check actual account limits when timing matters; missing data is unknown, not an estimated entitlement.

If a requested model is rejected, explain the specific limitation once. Continue unaffected work when consistent with the budget request; otherwise offer a manual switch or an explicitly accepted alternative. Do not repeat stable rejections or launch a second CLI to simulate native delegation.

## One focused advice pass

Select an adviser by the problem and evidence, not a permanent Sol/Astra hierarchy. Send only:

- goal and acceptance;
- decisive changed artifacts or facts;
- validation already completed;
- the unresolved choice or review target.

For review, request `PASS / CHANGES_REQUIRED` with at most three substantive findings. For a decision, request a recommendation, reasoning, and material uncertainty. The adviser is read-only: no ordinary retesting, adjacent redesign, or execution takeover. The owner assesses findings and continues; review does not grant production or external-action permission.

Repeat only when new evidence or a genuinely new question justifies it. Ordinary coding, reports, logs, and browser actions do not automatically require review. Production risk requires appropriate judgment and authorization, not necessarily another model when the owner can handle it.

## Keep the protocol small

Stable rules belong here; dated recommendations and small test findings belong in `model-choices.md`. Switch/sprint details load only when needed. Do not accumulate incident-specific gates, benchmark frameworks, recurring audits, or per-model procedure files. Recommendations can change without renaming the Skill again.

Reasoning effort and parallelism are separate decisions. Use the lowest adequate effort; high/max/ultra are not daily defaults and do not require inventing parallel work. Preserve the user's chosen supported setting.

Compare routes on the same inputs and acceptance. Record outcomes, corrections, observable time, and cost only when attributable. Distinguish a local exercise from deployment or a long workload. Public dollars per task and shared quota movement are not measured task cost.

Finish with the user-visible result and remaining uncertainty. No new file, process, review, or switch is needed when direct execution already meets the goal.
