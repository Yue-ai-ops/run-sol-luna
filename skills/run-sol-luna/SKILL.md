---
name: run-sol-luna
description: Run a budget-aware Sol-plans, Luna-executes, Sol-verifies Codex workflow created by Yue. Use whenever the user invokes `$run-sol-luna` or includes the exact phrase “省额度” in a task request. Do not infer other natural-language triggers.
---

# Run Sol + Luna

Original workflow by **Yue**. Use the current main task as the controller: understand the goal, protect project boundaries, delegate only bounded work to Luna Max, and independently verify the returned result.

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
5. Spawn one Luna worker by default. Use a second only when there are two genuinely independent scopes, parallel execution saves meaningful time, and the parent can verify both without duplicated work. Never use more than two. Use only the native subagent collaboration tools exposed to the current parent task. Never launch Codex CLI processes or shell commands as a delegation workaround. If native delegation tools are unavailable, report `PARTIAL` or `NOT_VERIFIED` and do not simulate a Luna run.
6. Explicitly use `gpt-5.6-luna` with `max` reasoning. If that model is unavailable, report the compatibility limitation instead of silently substituting another model.
7. Give each Luna worker:
   - one concrete objective and objective acceptance criteria;
   - exact allowed files, commands, and write scope;
   - explicit forbidden actions and stop conditions;
   - a disjoint scope when another worker runs in parallel;
   - an output contract of at most 10 lines or one compact table.
8. Do not reveal hidden evaluation answers to Luna. Do not retry a wrong model answer merely to obtain a passing result; retry only a genuine tool or path failure.
9. While workers run, perform non-overlapping controller work. Do not duplicate their assigned tasks.
10. Independently verify every material worker claim against current files, Git state, tests, receipts, or runtime evidence. Treat subagent completion as a claim, not verification.
11. Close completed subagents. Return one consolidated answer; do not dump raw worker transcripts.

## Write discipline

- Permit Luna to edit only when the user asked for implementation, the change is reversible, and the write scope is exact and disjoint.
- Keep shared handoffs, canonical state, deployment controls, and final integration under one parent writer.
- Preserve user-owned dirty work and unrelated changes.
- Inherit the parent sandbox and approval boundaries; never widen authority for a child.
- Stop for any required approval, secret, production action, external send, evidence conflict, or scope expansion.

## Reporting

Lead with the verified outcome, what the user can do now, and the actual remaining risk. Then state briefly:

- what Luna handled;
- what the parent independently verified;
- whether the result is `PASS`, `PARTIAL`, `NOT_VERIFIED`, or blocked;
- the next safe action, only when one remains.

Do not call internal evidence production-ready, do not promote `NOT_VERIFIED`, `PARTIAL`, `HOLD`, or similar states, and do not equate a passing child result with completed delivery.
