# Changelog

## 2026-08-11: Standalone family contract (v2.0.2)

### Changed

- Clarified that every Scoville Skill works independently and that family
  discovery does not imply installation, activation, applicability, or a
  dependency.
- Added all five current siblings with scoped ownership and kept sibling
  opt-out local to that sibling.
- Reduced repeated Core wording while retaining the existing activation
  metadata, fixed handoff artifact, source-read limits, and transfer boundary.

### Validation

- The central family-contract test passed all six packages and rejected all
  five synthetic drift cases; Agent Skill package validation also passed.
- No new model-behavior benchmark was run for this patch release.

## 2026-08-11: Scoville Brainstorm sibling (v2.0.1)

### Changed

- Added Scoville Brainstorm to the optional family composition guide and kept
  explicit session transfer separate from divergent exploration.
- Added copy-ready examples for explicit task and session transfers.
- Reduced installation, cost, mechanism, and family documentation while
  retaining the Scoville name rationale, sources, and benchmark evidence.
- Added a family run ledger and reconciled the public total across all six
  Scoville Skills.

## 2026-08-10: Scoville Handoff v2.0.0

### Changed

- Renamed the local Skill identity and installable directory from Compact
  Handoff to Scoville Handoff while preserving established natural-language
  transfer requests.
- Replaced the large conditional template with one four-section continuation
  artifact and a compact `READ -> CAPTURE -> RENDER -> CHECK -> SEND` transfer
  machine.
- Kept objective, acceptance, canonical sources, decisions, constraints,
  authorization, ownership, dirty changes, evidence, rejected approaches,
  blockers, in-flight work, hazards, unknowns, and the next safe action.
- Retired the explicit `$compact-handoff` identifier to avoid duplicate Skill
  discovery; `$scoville-handoff` is now canonical.

### Validation

- Microsoft SkillOpt at commit `ba820b5` ran with Sol 5.6 xhigh analysis and
  Terra 5.6 Medium execution; SkillReducer-style reduction removed redundant
  semantic units before the final reliability hardening.
- The final candidate passed 3/3 new one-shot sealed qualification cases
  reviewed by Fable 5 High. Repeated open development runs remained 26/27 and
  expose one nondeterministic family-ownership miss.
- The always-loaded Skill fell from 1,689 to 1,086 `o200k_base` tokens, a
  35.70% reduction from Compact Handoff v1.0.0.
- The canonical Agent Skill validator, Studio preflight, metadata checks, and
  local repository checks pass.

### Migration

- Replace an installed `compact-handoff/` directory with
  `scoville-handoff/`; do not keep both packages installed.
- Update explicit `$compact-handoff` invocations to `$scoville-handoff`.
  Natural-language requests such as `compact handoff` and `session handoff`
  remain supported.
- Renamed the existing GitHub repository to `scoville-handoff` so its history,
  issues, and releases remain under one canonical project.

## 2026-08-04: Canonical Scoville reference

### Fixed

- Updated the README to link directly to the renamed Scoville Code repository
  instead of relying on GitHub's redirect from its former name.

## 2026-07-26: Installable skill separated from repository documentation

### Changed

- Moved `SKILL.md` and `agents/openai.yaml` into the
  `compact-handoff/` directory. The installable directory now contains only
  runtime skill files, while README, changelog, and license remain repository
  documentation at the root.
- Updated installation instructions to target the named skill directory. Its
  parent directory continues to match the frontmatter name.

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

- `SKILL.md` grew substantially and now includes a roughly 300-word prompt
  template. The README states the approximate current size without implying a
  universal Markdown word-count method.
