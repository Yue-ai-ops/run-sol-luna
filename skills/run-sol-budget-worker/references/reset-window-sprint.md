# Reset-window Sprint

Read this reference only when the user includes the exact phrase “额度即将重置”. The goal is to convert genuinely expiring capacity into valuable completed work, not to maximize token burn.

## Preconditions

- Treat the user's stated reset window as the trigger; do not browse rumors or infer a reset.
- Use only work already requested, already authorized, or explicitly selected by the user.
- Preserve all project, host, Git, safety, external-send, and human-only gates.
- If timing, model availability, or Fast availability cannot be confirmed, state that rather than pretending.

## Triage the existing backlog

Classify each candidate once:

- `READY`: high-value, authorized, unblocked, with a clear acceptance condition.
- `BLOCKED`: needs credentials, user input, external authority, unavailable infrastructure, or a preceding dependency.
- `LOW_VALUE`: speculative cleanup, duplicate testing, optional documentation, invented abstractions, or work whose only purpose is consuming quota.

Execute `READY` work only. Prioritize by business value, time-to-completion before reset, reversibility, and verifiability. Do not lower safety standards to fit the window.

## Choose investment by task shape

- One clear execution task: keep Luna Max when it can meet acceptance.
- One difficult quality-first plan, decision, or focused review: use Sol high; use max only when the difficulty or consequence justifies it.
- Two or more genuinely independent `READY` workstreams: Ultra may be proposed or used when supported and likely to improve wall-clock completion. Shared state, sequential dependencies, or one task split into ceremonial pieces do not qualify.
- Fast: enable only when the user explicitly asks to spend the expiring quota faster and the interface visibly supports it. Fast changes speed and quota rate, not the quality tier.

## Stop conditions

Stop when the reset time arrives, no `READY` work remains, the next action hits an existing boundary, or additional work would be lower value than preserving a clean handoff. Do not start speculative projects, generate unused engineering packages, add redundant tests, or expand architecture merely because quota remains.

Report:

```text
Route: RESET_WINDOW_SPRINT
Ready work completed:
Blocked or deliberately skipped:
Model / effort / speed actually confirmed:
Remaining handoff:
```
