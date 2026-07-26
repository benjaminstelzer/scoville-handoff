# Changelog

## 2026-07-26: Explicit activation, usable anchor fields, failed approaches

### Added

- An `Activation` section that refuses to produce a handoff without an explicit
  user request to transfer work. Low remaining context, a finished task, a long
  conversation, an approaching session end, and compaction warnings are named
  as non-requests. A frontmatter description can only influence whether a skill
  triggers; once it has triggered, only a rule inside the body can stop it, and
  self-initiated handoffs were the failure worth stopping.
- `Tried and Rejected` in the prompt template, plus the rule behind it: record
  abandoned approaches with their observed outcome and the reason they were
  dropped. Without this the receiving session's first move is often the
  approach that already failed, and neither `Decisions` nor
  `Assumptions and Unknowns` covered it.
- A soft length target: a prompt the receiver can read in under two minutes,
  cut in reverse priority order when it exceeds that. The compression
  priorities were already ordered but had nothing to trigger them.
- Conditional sections. Receiver Instructions, Objective, Continuation Anchor,
  Work State, and Resume Steps are always emitted; every other section and
  subsection appears only when it has content. A handoff after a short session
  previously produced a skeleton of `none known` labels, which is the process
  artifact this skill otherwise avoids.
- A boundary against workflow skills that define their own in-place compaction
  record: this skill produces the separate transfer prompt and does not merge
  the two shapes.
- Secret redaction inside verbatim quotes. The template asks for the latest
  user instruction verbatim, which is the one place the no-secrets rule could
  be overridden by a more specific instruction.

### Changed

- Read-only inspection of version-control state is now allowed and expected.
  The template asks for branch, HEAD, and per-file staged state while the rules
  forbade inspecting anything, so those fields resolved to `unknown` in exactly
  the sessions where nobody happened to run `git status`. Side-effecting
  commands, edits, and continuing the task remain forbidden.
- Observation times are recorded only when they appear in the conversation or a
  tool result, never as a guessed wall-clock time. A wrong timestamp in a
  handoff is worse than an absent one.
- The no-questions rule is scoped to questions about missing facts. Asking
  whether a handoff is wanted at all is now required when the request is
  ambiguous.
- English output gained an override for a user-named target language.
- `Trigger Handling` became `Edge Cases`. Its first two bullets restated the
  frontmatter description, which cannot affect a decision that has already been
  made by the time the body is read.
- The Codex `short_description` in `agents/openai.yaml` states the constraint
  instead of describing an unconditional capability. It was the last surface
  still presenting the skill as available on its own.

### Removed

- `Project/workspace` from the Continuation Anchor; `Working directory` already
  carried it.

### Note

- `SKILL.md` grew from 973 to 1,282 words, of which 309 are the prompt
  template. The README now states the measured count.
