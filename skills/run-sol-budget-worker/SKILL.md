---
name: run-sol-budget-worker
description: Run a budget-aware Sol-plans, bounded-worker-executes, Sol-verifies Codex workflow created by Yue. Prefer Luna Max; when the current native interface does not expose Luna, use Terra medium as an explicit fallback. Use whenever the user invokes `$run-sol-budget-worker` or includes the exact phrase “省额度” in a task request. Do not infer other natural-language triggers.
---

# Run Sol + Budget Worker

Original workflow by **Yue**. Use the current main task as the controller: understand the goal, protect project boundaries, delegate only bounded work to a capability-selected worker, and independently verify the returned result.

This Skill does not change the main task's model. Rely on the user's model selection for the parent Sol role. If the parent model cannot be inspected, do not claim that it was technically verified and do not add a separate Sol reviewer merely to prove the label.

## Choose the parent effort

Treat the parent effort as routing guidance, not a hard launch requirement:

- **Sol medium:** use for Green work with objective evidence, such as read-only scans, extraction, report inputs, and repetitive checks.
- **Sol high:** use as the default for routine Green and Yellow work, including bounded coding, diagnosis, tests, and evidence-backed reporting.
- **Sol xhigh:** reserve for Red work, long or conflicting context, cross-host or runtime identity, architecture, production, and final high-risk acceptance.

Do not require xhigh merely to run this Skill. If the current parent is weaker than the recommended tier, narrow the delegated scope and keep uncertain or high-risk judgment unverified; do not stop only to prove a model label.

## Run the workflow

1. Read the applicable project instructions and inspect the current checkout, host, dirty state, and authoritative evidence needed for the request.
2. Define the goal, acceptance criteria, locked decisions, allowed writes, forbidden actions, and the one next action before delegating.
3. Classify the work:
   - **Green:** read-only exploration, evidence extraction, status reconciliation, log analysis, report drafts, repetitive tests, or small mechanical edits with objective verification.
   - **Yellow:** multi-file implementation, ambiguous diagnosis, shared-state work, or tasks where a wrong result is costly. Delegate only independent supporting slices; keep integration and judgment in the parent.
   - **Red:** architecture decisions, host or runtime identity, canonical state transitions, production, deployment, restart, security recovery, secrets, irreversible actions, real external communication, or final acceptance. Keep decisions and writes in the parent; delegate only clearly separable read-only evidence work when useful.
4. Skip delegation when the task is trivial, tightly coupled, or the next parent action depends immediately on the same work.
5. Spawn one worker by default. Use a second only when there are two genuinely independent scopes, parallel execution saves meaningful time, and the parent can verify both without duplicated work. Never use more than two. For trivial or tightly coupled work, complete it directly under the parent even though the Skill was triggered. Use only the native subagent collaboration tools exposed to the current parent task. Never launch Codex CLI processes or shell commands as a delegation workaround.
6. Apply the capability gate before delegation:
   - If the native subagent interface exposes `gpt-5.6-luna`, use **Luna Max** (`gpt-5.6-luna`, `max`) and mark the route `LUNA_ACTIVE`.
   - If Luna is absent or the interface rejects it while explicitly listing only Sol/Terra, use **Terra medium** (`gpt-5.6-terra`, `medium`) and mark the route `TERRA_FALLBACK`.
   - Never use Terra high, xhigh, max, or ultra as a Luna substitute. Terra fallback preserves a bounded execution lane; it does not imply Luna-level cost savings.
   - When the parent is Sol medium, use Terra fallback only when independent parallel work has clear value; otherwise keep the bounded task in the parent rather than paying for a second mid-tier worker.
   - Do not retry a stable Luna model-rejection. If neither Luna nor Terra is available, report `ROUTE_UNAVAILABLE` with `PARTIAL` or `NOT_VERIFIED`; do not simulate delegation.
7. Start workers without prior conversation context when supported and provide a self-contained task card.
8. Give each worker:
   - one concrete objective and objective acceptance criteria;
   - exact allowed files, commands, and write scope;
   - explicit forbidden actions and stop conditions;
   - a disjoint scope when another worker runs in parallel;
   - an output contract of at most 10 lines or one compact table.
9. Do not reveal hidden evaluation answers to a worker. Do not retry a wrong model answer merely to obtain a passing result; retry only a genuine tool or path failure.
10. While workers run, perform non-overlapping controller work. Do not duplicate their assigned tasks.
11. Independently verify every material worker claim against current files, Git state, tests, receipts, or runtime evidence. Treat subagent completion as a claim, not verification.
12. Close completed subagents. Return one consolidated answer; do not dump raw worker transcripts.

## Write discipline

- Permit the selected worker to edit only when the user asked for implementation, the change is reversible, and the write scope is exact and disjoint.
- Keep shared handoffs, canonical state, deployment controls, and final integration under one parent writer.
- Preserve user-owned dirty work and unrelated changes.
- Inherit the parent sandbox and approval boundaries; never widen authority for a child.
- Stop for any required approval, secret, production action, external send, evidence conflict, or scope expansion.

## Reporting

Lead with the verified outcome, what the user can do now, and the actual remaining risk. Then state briefly:

- what the selected worker handled;
- which route was used: `LUNA_ACTIVE`, `TERRA_FALLBACK`, or `ROUTE_UNAVAILABLE`;
- what the parent independently verified;
- whether the result is `PASS`, `PARTIAL`, `NOT_VERIFIED`, or blocked;
- the next safe action, only when one remains.

Do not call internal evidence production-ready, do not promote `NOT_VERIFIED`, `PARTIAL`, `HOLD`, or similar states, and do not equate a passing child result with completed delivery.
