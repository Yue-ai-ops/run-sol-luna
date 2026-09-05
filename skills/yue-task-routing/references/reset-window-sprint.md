# Reset-window Sprint

Read this reference when Yue explicitly asks to use expiring capacity, including “额度即将重置”, not when quoting or discussing the phrase. Aim for valuable completed work before the stated reset, not maximum token burn.

## Preconditions

- Treat the user's stated reset window as the trigger; do not browse rumors or infer a reset.
- Use only work already requested, already authorized, or explicitly selected by the user.
- Preserve all project, host, Git, safety, external-send, and human-only gates.
- If timing, model availability, or Fast availability cannot be confirmed, state that rather than pretending.
- Check actual account limits when timing matters. Do not redeem a reset or enable paid speed without explicit authorization.

## Triage the existing backlog

Classify each candidate once:

- `READY`: high-value, authorized, unblocked, with a clear acceptance condition.
- `BLOCKED`: needs credentials, user input, external authority, unavailable infrastructure, or a preceding dependency.
- `LOW_VALUE`: speculative cleanup, duplicate testing, optional documentation, invented abstractions, or work whose only purpose is consuming quota.

Execute `READY` work only. Prioritize by business value, time-to-completion before reset, reversibility, and verifiability. Do not lower safety standards to fit the window.

## Choose investment by task shape

- Keep the current capable model unless a different choice offers material benefit; consult [model-choices.md](model-choices.md) when needed.
- Choose reasoning effort by difficulty and observed quality, separately from worker count. Ultra does not require multiple streams, nor does expiring quota automatically justify Ultra.
- Parallelize only genuinely independent `READY` workstreams when authorized and likely to improve completion. Shared state and sequential dependencies do not qualify merely because a stronger effort is selected.
- Fast: enable only when the user explicitly asks to spend the expiring quota faster and the interface visibly supports it. Fast changes speed and quota rate, not the quality tier.

## Stop conditions

Stop when the reset time arrives, no `READY` work remains, the next action hits an existing boundary, or additional work would be lower value than preserving a clean handoff. Do not start speculative projects, generate unused engineering packages, add redundant tests, or expand architecture merely because quota remains.

Report completed results, meaningful blockers, and remaining handoff in plain language. Mention confirmed model or timing only when useful.
