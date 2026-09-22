# Scoville Handoff

The next session needs enough information to continue the work. A long account
of the conversation can still miss the current blocker, the uncommitted changes
or the reason an earlier approach failed.

Scoville Handoff turns active work into one compact continuation prompt. It
preserves the objective, decisions, permissions, file ownership, observed
results and next safe action. A test that is still running stays unresolved.
Changes belonging to the user remain identifiable.

Request it when you want to transfer work to another agent or session. Ordinary
summaries, low context and ending a conversation do not activate it.

## Why "Scoville"?

The family is named for useful signal that remains detectable after dilution.
In Handoff, that means preserving what the next session needs when the conversation is shortened.

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

## Compatibility

Any Agent Skills host that can read the named task sources. Optional read-only version-control inspection (git). No scripts, no network, no subagents. Developed for Codex and Claude Code; other hosts untested.

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

Get the complete suite from the
[Scoville Suite monorepo](https://github.com/benjaminstelzer/scoville-suite).
Install its released Skill packages, not development templates.

## What it enforces

- **Explicit transfer only.** Ordinary summaries and context reduction do not
  produce a handoff artifact.
- **One receiver contract.** Every handoff contains Receiver Instructions,
  Objective, State, and Resume Steps in one copy-ready block.
- **Facts instead of pointers.** Named sources are read with targeted recovery
  for truncation or a transient failure, within explicit user limits. Their material
  facts enter the artifact so the receiver has them when resuming.
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
prompt. The receiver checks the current state before acting on the handoff.

A tight output limit removes repetition and irrelevant history first, never
authority, ownership, hazards, evidence limits, or the safe next step. An
explicit lossless request retains every in-scope non-secret fact. If the
required content cannot fit, the Skill reports that conflict instead of
claiming a complete transfer.

## How it was developed

Handoff grew out of moving real work between sessions and seeing what the next
session was missing. A long summary could still omit the current blocker or
fail to say which local changes belonged to the user. The
[changelog](CHANGELOG.md) traces the move from a large conditional template to
four sections built around continuing the work.

I used [SkillOpt and reduction work](https://github.com/benjaminstelzer/scoville-handoff/blob/d319aa3291160a20d30baad5157b1ab5083ea0e1/CHANGELOG.md)
to refine that format. In ongoing use, I compare the task history with the
handoff to look for lost facts, repeated failed approaches and unnecessary
detail. A shorter handoff helps only if the next session can still act on it.

## Scoville family

Each Skill works independently. Combine only the concerns the task actually
needs:

- [Brainstorm](https://github.com/benjaminstelzer/scoville-brainstorm) explores materially different mechanisms before selection.
- [Research](https://github.com/benjaminstelzer/scoville-research) turns web, GitHub, and scholarly evidence into a decision-ready, claim-traceable result.
- [Code](https://github.com/benjaminstelzer/scoville-code-anti-ai-slop) owns engineering scope, implementation, risk, and validation.
- [Design](https://github.com/benjaminstelzer/scoville-design-anti-ai-slop) owns visual definition, art direction, design systems, critique, and repair.
- [UI](https://github.com/benjaminstelzer/scoville-ui-anti-ai-slop) owns framework-aligned implementation, interface mechanics, accessibility, and rendered evidence, with a standalone design fallback.
- [WordPress UI Backend](https://github.com/benjaminstelzer/scoville-wordpress-ui-backend-anti-ai-slop) owns plugin-owned WordPress admin interfaces, platform components, spacing, accessibility and internationalization.
- [Scribe](https://github.com/benjaminstelzer/scoville-scribe-anti-ai-slop) owns wording, terminology, factual meaning, and source fidelity.
- [Plan](https://github.com/benjaminstelzer/scoville-plan) owns durable Plans, Work Items, Decisions, and lifecycle state.
- [Handoff](https://github.com/benjaminstelzer/scoville-handoff) transfers active work to another agent or session.
- [Workflow Codex](https://github.com/benjaminstelzer/scoville-suite) coordinates explicit Plan execution through native Codex project tasks.

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

