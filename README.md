# Scoville Handoff

Continuing a task requires its current blocker, unfinished changes and relevant
decisions. Scoville Handoff gathers those facts into one compact, copy-ready
prompt with the objective, permissions and next action, so another session can
resume the work.

## How it works

- Read conversation facts and named sources, recovering incomplete reads within the user's limits.
- Capture decisions, ownership, evidence and blockers while excluding secrets.
- Organize and check one copy-ready prompt with Receiver Instructions, Objective, State and Resume Steps.
- Preserve necessary facts under length limits. The receiver checks current state before acting.

## What it enforces

- **Explicit transfer.** A requested handoff produces one continuation prompt.
- **Usable context.** Material facts from the conversation and named sources
  appear in the prompt, including blockers and incomplete work.
- **Preserved authority.** Permissions, file ownership, user changes and
  boundaries on commits, publication or destructive actions remain explicit.
- **Honest state.** Unobserved results remain unknown. Secrets stay out.
- **Actionable continuation.** The first Resume Step gives the next safe action;
  the last defines observable completion.
- **A faithful snapshot.** Creating the handoff reads and describes the task
  without editing, testing or advancing it.

The complete contract is in [SKILL.md](https://github.com/benjaminstelzer/scoville-handoff/blob/main/scoville-handoff/SKILL.md).

## What it costs

- Reading the task state and preparing the handoff use additional tokens and time.

## How it was developed

- Transfers between real sessions exposed missing blockers, decisions and ownership of local changes.
- Project histories, targeted simulations and optimization workflows informed the four-section template and checks for necessary continuation facts.
- Test results and limitations are retained in the development records.

## Compatibility

Requires a frontier LLM from the Fable, Astra, SOL or Opus families, version 5.0
or newer, in an Agent Skills host that can read named task sources. Read-only
version-control inspection is optional. Handoff uses no scripts, network or
subagents.

Developed for Codex and Claude Code. Other hosts are untested. The model
requirement does not establish successful tests across those model families.

This Skill works independently. Other Scoville Skills are optional.

## Install

### Install this Skill

This standalone package works independently. Ask your compatible agent host:

```text
Install this Skill for all my projects from this exact package directory:
https://github.com/benjaminstelzer/scoville-handoff/tree/main/scoville-handoff
Preserve personal settings and unrelated Skills. Report the installed location
and whether the host discovers the Skill.
```

The host needs permission to write to its Skills directory. See the
[Codex Skills guide](https://learn.chatgpt.com/docs/build-skills) or the
[Claude Code Skills guide](https://code.claude.com/docs/en/skills)
for host-specific locations.

### Install the complete Scoville suite

Get the complete suite from the
[Scoville Suite monorepo](https://github.com/benjaminstelzer/scoville-suite).
Install its released Skill packages, not development templates.

## How to use

```text
Use Scoville Handoff to transfer this active task to a new session. Include the current repository state and verified evidence.
```

```text
Create a compact handoff for another agent. Preserve the objective, decisions, changed files, blockers and next action. Do not continue the work.
```

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

## Family

- [Code](https://github.com/benjaminstelzer/scoville-code) owns engineering scope, implementation, risk, and validation.
- [Plan](https://github.com/benjaminstelzer/scoville-plan) owns durable Plans, Work Items, Decisions, and lifecycle state.
- [UI](https://github.com/benjaminstelzer/scoville-ui) owns UI implementation, information structure, accessibility and rendered evidence, with a conditional WordPress adapter.
- [Handoff](https://github.com/benjaminstelzer/scoville-handoff) transfers active work to another agent or session.

## License

MIT. See [LICENSE](LICENSE).
