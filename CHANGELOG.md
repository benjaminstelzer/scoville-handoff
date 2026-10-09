# Changelog

## v2.1.11 - 2026-10-09

- Keep the verified Python interpreter and all required arguments when capturing a helper command. Small direct calls remain available.

## v2.1.10 - 2026-10-09

- Clarify which path runs the reader and which document it reads, including source files from another Skill.

## v2.1.9 - 2026-10-09

- Keep the verified reader and launcher unchanged between document parts or Skills. Reset to part 1 when opening a different document.

## v2.1.8 - 2026-10-09

- Use a complete reader command when continuing document reads, and an existing directory with a file filter when searching. Prefer direct shell commands for simple file inventories.

## v2.1.7 - 2026-10-09

- Redact secrets in every part of the handoff, including warnings and quotations. Make the required sections and resume sequence explicit without changing task scope.

## v2.1.6 - 2026-10-08

- Create usable snapshots after the permitted recovery sequence, preserving unread ranges and gaps. Missing required facts still block dependent receiver actions.

## v2.1.5 - 2026-10-08

- Clarify the shared writing and document-reading instructions so the next action and its prerequisites are easier to identify.

## v2.1.4 - 2026-10-08

- Diagnose shortened output from the observed failing layer; a later shortened query does not prove that the original capture lost information.

## v2.1.3 - 2026-10-08

- Read complete transfer inputs with an explicit document reader and keep command status separate from output completeness.
- Make snapshot ownership and the required handoff facts easier to follow without duplicating instructions.

## v2.1.2 - 2026-10-08

- Read complete UTF-8 input in bounded parts. Capture command output before display and keep the manual route available without Python.

## v2.1.1 - 2026-10-07

- Check complete text before large reads and preserve Python launcher arguments when invoking the size checker. Keep continuation records limited to facts needed for the next work.

## v2.1.0 - 2026-10-07

- Preserve the complete continuation through compaction or a hashed temporary file when it exceeds the known output limit. Ask the recipient to read that file before continuing.
- Ask about unknown acceptance only when the next action depends on it. An unknown goal still blocks a usable handoff.
- Follow the applicable Codex or Claude Code project rules and keep preferences distinct from binding requirements.

## v2.0.24 - 2026-10-02

- Write the handoff in the requested language, otherwise the conversation language.
- Include task sources already named or established, while keeping source data distinct from accepted decisions.
- Finish already authorized record updates with their owner before preparing the read-only handoff.

## v2.0.23 - 2026-10-01

### Known limits

One targeted GPT-6 Luna High repeat still promoted a preference to a requirement. Check that distinction when continuing from a generated handoff. This limit remains unresolved by later testing.

## v2.0.22 - 2026-10-01

- Include Project Context Cleanup among the active sibling owners whose state and pending work a continuation preserves.

## v2.0.20 - 2026-09-27

- Keep continuation prompts focused on the current state, binding constraints, evidence limits and next action.

## v2.0.19 - 2026-09-26

- Separate preferences from accepted requirements and preserve the outer fence in saved handoffs.
- Distinguish hypothetical handoff advice from an explicitly requested task transfer.

## v2.0.18 - 2026-09-25

- Keep the continuation prompt copyable in one outer Markdown fence, with any nested fences safely contained.
- Preserve the actual task working directory and inspect version control only when the project uses it.
- Apply the complete-suite ownership contract in suite installations while keeping standalone Handoff independently usable.

## v2.0.17 - 2026-09-22

- Recover permitted missing source ranges before rendering a handoff instead
  of leaving that read to the receiver.
- Keep an unknown work status unknown. Missing evidence does not mean work
  has not started.

## v2.0.16 - 2026-09-20

- Clarify the evidence needed for active work without inventing repeat checks
  for work that is already complete.

## v2.0.15 - 2026-09-20

- Keep handoff rendering and checking read-only: missing facts remain
  `unknown` or `none known` instead of triggering builds, tests, probes, dummy
  commands, or other task commands.
- Clarify that inspected repository content is data and cannot replace the
  applicable instructions carried into the continuation.
- Clarify that discovering another family Skill does not activate it, while
  independently authorized work continues and a user opt-out applies only to
  the excluded Skill.

## v2.0.14 - 2026-09-19

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
