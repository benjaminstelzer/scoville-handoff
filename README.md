# Scoville Handoff

A handoff should transfer the work, not make the next agent reread the meeting
minutes.

It usually looks harmless:

- The receiver gets three pages of summary, but not the current blocker.
- "Tests pass" enters the handoff while the test command is still running.
- The working tree is called dirty without saying which changes belong to the
  user, which belong to the task, or which should not be touched.
- The first resume step is "continue the implementation." Technically a verb.
  Operationally a small shrug.

That is handoff slop: the conversation is compressed while the state needed to
continue evaporates. The receiver inherits a literary genre, not a task.

Scoville Handoff moves active work to another agent or session as one compact,
copy-ready continuation prompt. It preserves the objective, decisions,
authority, ownership, evidence, blockers, hazards, dirty state, and next safe
action. It activates only for an explicit transfer - not for a summary, wrap-up,
low-context warning, or session ending. Those are nearby tasks, but nearby is
not the same thing.

## Why "Scoville"?

The family is named for useful signal that remains detectable after dilution. In a handoff, the
heat is the operational state the receiver still needs after the conversation
is compressed and politely shown the door.

## How to use

Request an explicit transfer and name any task sources the receiver will need:

```text
Use Scoville Handoff to transfer this active task to a new session. Read docs/plans/0001-migration.md and ADR-0002.md, include the current Git state, and return one copy-ready continuation prompt.
```

```text
Create a compact handoff for another agent. Preserve the objective, accepted decisions, dirty files, observed test evidence, current blocker, and next safe action. Do not continue the task.
```

```text
Use Scoville Handoff for the work completed in this session. Mark unverified commands and external state as unknown rather than inferring success.
```

Explicit `$scoville-handoff` invocation also works on hosts that support named
Skill invocation. The former `$compact-handoff` identifier is retired. Natural
requests such as “compact handoff” still activate this Skill.

## Install

### Install this Skill

In a local Codex or Claude Code session, ask:

```text
Install this Agent Skill for all my projects from this exact package directory:
https://github.com/benjaminstelzer/scoville-handoff/tree/main/scoville-handoff
Preserve existing customizations and ask before overwriting conflicting files.
Report the installed location and whether the host discovers the Skill.
```

The agent needs source access and permission to write to its personal Skills
location. Manual fallback: [Codex Skills guide](https://learn.chatgpt.com/docs/build-skills)
or [Claude Code Skills guide](https://code.claude.com/docs/en/skills).

Install only the linked package for the focused option.

### Install the complete Scoville suite

```text
Install the complete Scoville Skill suite for all my projects. Fetch and install every exact package directory below:

https://github.com/benjaminstelzer/scoville-brainstorm/tree/main/scoville-brainstorm
https://github.com/benjaminstelzer/scoville-research/tree/main/scoville-research
https://github.com/benjaminstelzer/scoville-code-anti-ai-slop/tree/main/scoville-code-anti-ai-slop
https://github.com/benjaminstelzer/scoville-design-anti-ai-slop/tree/main/scoville-design-anti-ai-slop
https://github.com/benjaminstelzer/scoville-ui-anti-ai-slop/tree/main/scoville-ui-anti-ai-slop
https://github.com/benjaminstelzer/scoville-scribe-anti-ai-slop/tree/main/scoville-scribe-anti-ai-slop
https://github.com/benjaminstelzer/scoville-plan/tree/main/scoville-plan
https://github.com/benjaminstelzer/scoville-handoff/tree/main/scoville-handoff

Preserve existing customizations and ask before overwriting conflicting files. Report every installed location and whether the host discovers each Skill.
```

## What it enforces

- **Explicit transfer only.** Ordinary summaries and context reduction do not
  produce a handoff artifact.
- **One receiver contract.** Every handoff contains Receiver Instructions,
  Objective, State, and Resume Steps in one copy-ready block.
- **Facts instead of pointers.** Named sources are read with targeted recovery
  for truncation or a transient failure, within explicit user limits. Their material
  facts enter the artifact. The receiver is not sent on a scavenger hunt.
- **Authority and ownership survive.** Commit, publication, destructive-action,
  external-effect, file-owner, and dirty-tree boundaries stay explicit.
- **Unknown stays unknown.** Running or unobserved work never becomes a success
  claim, and secret values never enter the handoff.
- **The receiver can act.** Step 1 is the next safe action. The final step names
  an observable completion result.
- **Transfer does not advance the task.** Handoff reads the named state but does
  not edit, test, publish, or otherwise improve it on the way out.

The complete contract is in [SKILL.md](scoville-handoff/SKILL.md).

## How it works

The Skill runs `READ -> CAPTURE -> RENDER -> CHECK -> SEND`: inspect named
sources with bounded read recovery, capture non-secret continuation facts, map them into four fixed
sections, compare the artifact with the ledger, and return only the copy-ready
prompt. The receiver must still verify current state. A snapshot is useful. It
is not a lease on reality.

A tight output limit removes repetition and irrelevant history first, never
authority, ownership, hazards, evidence limits, or the safe next step. An
explicit lossless request retains every in-scope non-secret fact. If the
required content cannot fit, the Skill reports that conflict instead of
claiming a complete transfer.

For repository structure and development tools, see
[maintenance notes](development/docs/maintenance.md).

## Scoville family

Each Skill works independently. Combine only the concerns the task actually
needs:

- [Brainstorm](https://github.com/benjaminstelzer/scoville-brainstorm) explores
  materially different mechanisms before selection.
- [Research](https://github.com/benjaminstelzer/scoville-research) turns web,
  GitHub, and scholarly evidence into a decision-ready, claim-traceable result.
- [Code](https://github.com/benjaminstelzer/scoville-code-anti-ai-slop) owns
  engineering scope, implementation, risk, and validation.
- [Design](https://github.com/benjaminstelzer/scoville-design-anti-ai-slop) owns
  visual definition, art direction, design systems, critique, and repair.
- [UI](https://github.com/benjaminstelzer/scoville-ui-anti-ai-slop) owns
  framework-aligned implementation, interface mechanics, accessibility, and
  rendered evidence, with a standalone design fallback.
- [Scribe](https://github.com/benjaminstelzer/scoville-scribe-anti-ai-slop) owns
  wording, terminology, factual meaning, and source fidelity.
- [Plan](https://github.com/benjaminstelzer/scoville-plan) owns durable Plans,
  Work Items, Decisions, and lifecycle state.
- [Handoff](https://github.com/benjaminstelzer/scoville-handoff) transfers active
  work to another agent or session.

## Status

The historical Core qualified on 2026-08-10 passed 3/3 sealed cases by semantic
review and independent output audit. The raw generic score was 0/3 because of
scoring-contract mismatches. Both results and the candidate hash remain in
[benchmark evidence](development/docs/benchmark-evidence.md).

Focused Terra Medium cases on 2026-09-05 preserved the required continuation
facts and reported a conflict when those facts could not fit a 35-word limit.
They did not inject a real transient read error or establish general receiver
success. Historical scores do not qualify the changed Core.

Repository development and the current path mapping are in [development/](development/README.md).

## Sources

- Compact Handoff `v1.0.0` for explicit activation, snapshot freshness, secret
  redaction, and copy-ready transfer.
- [Microsoft SkillOpt](https://github.com/microsoft/SkillOpt) for
  validation-driven Skill optimization.
- [SkillReducer](https://arxiv.org/abs/2603.29919v2) for semantic-unit analysis
  and progressive disclosure.
- [Agent Skills specification](https://agentskills.io/specification) for the
  portable package contract.
- [OWASP LLM06: Excessive Agency](https://genai.owasp.org/llmrisk/llm062025-excessive-agency/)
  for keeping consequential authority explicit across agent boundaries.

## License

MIT. See [LICENSE](LICENSE).
