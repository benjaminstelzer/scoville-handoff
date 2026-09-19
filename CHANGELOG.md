# Changelog

## v2.0.14 - 2026-09-19

- Copy the continuation record from a packaged template instead of embedding a
  nested fenced template in the core instructions.
- State the complete eight-Skill ownership boundary in suite order while
  keeping every sibling optional and independently activated.

## v2.0.8 - 2026-09-05

- Added bounded recovery when a named source is truncated or fails
  transiently, while preserving explicit read limits and visible source gaps.
- Defined the facts that must survive a compact handoff and their order under a
  tight limit. Explicit lossless requests remain lossless except for secret
  redaction.

## v2.0.2 - 2026-08-11

- Made Scoville Handoff independently usable. Discovering another Scoville
  Skill does not install or activate it.

## v2.0.0 - 2026-08-10

- Renamed Compact Handoff to Scoville Handoff and made
  `$scoville-handoff` the canonical invocation.
- Replaced the large conditional template with one compact continuation record
  covering receiver instructions, objective, state, and resume steps.
- Preserve binding constraints, decisions, ownership, dirty changes, evidence,
  rejected approaches, blockers, in-flight work, hazards, unknowns, and the
  next safe action when they matter.
- Keep transfer separate from active task execution and from a durable Plan.

### Migration

- Replace an installed `compact-handoff/` directory with
  `scoville-handoff/`. Do not keep both packages installed.
- Replace explicit `$compact-handoff` invocations with `$scoville-handoff`.
  Natural-language transfer requests remain supported.

## v1.0.0 - 2026-07-26

- Require an explicit transfer request. Low context, a long conversation,
  compaction, or a finished task does not activate the Skill by itself.
- Added rejected approaches with their observed outcome and reason, so the next
  session does not repeat failed work.
- Added conditional sections and a two-minute reading target instead of
  emitting empty labels.
- Redact secrets even inside otherwise verbatim user instructions.
- Allow read-only version-control inspection for branch, HEAD, and staged state
  while keeping edits and task continuation forbidden.
- Record only observed timestamps, ask about ambiguous transfer intent, and
  honour a user-selected output language.
