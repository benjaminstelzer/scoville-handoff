# Scoville Handoff

A handoff should transfer the work, not make the next agent reread the meeting
minutes.

It usually looks harmless:

- The receiver gets three pages of summary, but not the current blocker.
- "Tests pass" enters the handoff while the test command is still running.
- The working tree is called dirty without saying which changes belong to the
  user, which belong to the task, or which should not be touched.
- The first resume step is "continue the implementation." Technically a verb;
  operationally a small shrug.

That is handoff slop: the conversation is compressed while the state needed to
continue evaporates. The receiver inherits a literary genre, not a task.

Scoville Handoff moves active work to another agent or session as one compact,
copy-ready continuation prompt. It preserves the objective, decisions,
authority, ownership, evidence, blockers, hazards, dirty state, and next safe
action. It activates only for an explicit transfer—not for a summary, wrap-up,
low-context warning, or session ending. Those are nearby tasks, but nearby is
not the same thing.

## Why "Scoville"?

The family is named for useful signal that survives dilution. In a handoff, the
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
Skill invocation. The former `$compact-handoff` identifier is retired; natural
requests such as “compact handoff” still activate this Skill.

## Install

Use an Agent Skills-compatible host and Terra 5.6 Medium or a comparably
capable executor such as Opus 4.8. Ask the agent to install:

```text
Install this Agent Skill and refresh the available Skill list:
https://github.com/benjaminstelzer/scoville-handoff/tree/main/scoville-handoff
Keep the installed directory name scoville-handoff. Use Terra 5.6 Medium or a comparably capable executor such as Opus 4.8.
```

The final path must end in `<skills-dir>/scoville-handoff/SKILL.md`. For Claude
Code, use `~/.claude/skills/` globally or `.claude/skills/` inside one project.
Other hosts use their supported Skills directory.

**What it costs.** The 1,086-token Core is 35.70% smaller than Compact Handoff
`v1.0.0`. That context buys a safer transfer of authority, dirty state,
evidence, hazards, and the next action. Use it for real session transfers; skip
it for a brief task that needs no continuation snapshot. See
[benchmark evidence](docs/benchmark-evidence.md).

## What it enforces

- **Explicit transfer only.** Ordinary summaries and context reduction do not
  produce a handoff artifact.
- **One receiver contract.** Every handoff contains Receiver Instructions,
  Objective, State, and Resume Steps in one copy-ready block.
- **Facts instead of pointers.** Named sources are read once and their material
  facts enter the artifact; the receiver is not sent on a scavenger hunt.
- **Authority and ownership survive.** Commit, publication, destructive-action,
  external-effect, file-owner, and dirty-tree boundaries stay explicit.
- **Unknown stays unknown.** Running or unobserved work never becomes a success
  claim, and secret values never enter the handoff.
- **The receiver can act.** Step 1 is the next safe action; the final step names
  an observable completion result.
- **Transfer does not advance the task.** Handoff reads the named state but does
  not edit, test, publish, or otherwise improve it on the way out.

The complete contract is in [SKILL.md](scoville-handoff/SKILL.md).

## How it works

The Skill runs `READ -> CAPTURE -> RENDER -> CHECK -> SEND`: read each named
source once, capture non-secret continuation facts, map them into four fixed
sections, compare the artifact with the ledger, and return only the copy-ready
prompt. The receiver must still verify current state. A snapshot is useful; it
is not a lease on reality.

## Scoville family

Each Skill works independently. Combine only the concerns the task actually
needs:

- [Brainstorm](https://github.com/benjaminstelzer/scoville-brainstorm) explores
  materially different mechanisms before selection.
- [Code](https://github.com/benjaminstelzer/scoville-code-anti-ai-slop) owns
  engineering scope, implementation, risk, and validation.
- [UI](https://github.com/benjaminstelzer/scoville-ui-anti-ai-slop) owns
  interface hierarchy, framework fit, accessibility, and rendered evidence.
- [Scribe](https://github.com/benjaminstelzer/scoville-scribe-anti-ai-slop) owns
  wording, terminology, factual meaning, and source fidelity.
- [Plan](https://github.com/benjaminstelzer/scoville-plan) owns durable Plans,
  Work Items, Decisions, and lifecycle state.
- [Handoff](https://github.com/benjaminstelzer/scoville-handoff) transfers active
  work to another agent or session.

## Status

A reliability-first extension of
[Microsoft SkillOpt](https://github.com/microsoft/SkillOpt), combined with
SkillReducer-style reduction, tested the six Scoville Skills across **1,201
optimization and evaluation runs**. Scoville Handoff accounts for **222 runs
and 620 benchmark case executions**, passed **3/3 new sealed qualification
cases**, and uses **35.70% fewer loaded instruction tokens than Compact Handoff
v1.0.0**. See [benchmark evidence](docs/benchmark-evidence.md).
The [family run ledger](docs/optimization-history.md) shows the complete count.

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

MIT - see [LICENSE](LICENSE).
