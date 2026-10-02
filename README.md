# Scoville Handoff

Scoville Handoff turns the current task into one copy-ready continuation
prompt: the goal, decisions, unfinished work, blockers and next action.
Another session can pick up the work without asking you to explain it all again.

Scoville measures chili heat. Handoff keeps the useful context from being
diluted between conversations. The next agent already has enough imagination.

## How it works

- Read the conversation and the task sources already named or established.
- Capture the facts needed to resume, including permissions and unfinished work.
- Produce one prompt in the requested language, otherwise the conversation
  language. The receiving agent checks current state before acting.

## What it enforces

- **Explicit transfer.** A handoff starts when you request one. Preparing it is
  read-only and does not advance the task.
- **Faithful context.** Decisions, permissions, ownership and blockers survive
  the transfer. Unknown results stay unknown, and secrets stay out.
- **A useful next action.** The prompt tells the next session where to resume
  and how to recognize completion.

A targeted GPT-6 Luna High test turned a preference into a requirement. Check
that distinction in a generated handoff. Later testing has not disproved the
observation.

See the [full instructions](https://github.com/benjaminstelzer/scoville-handoff/blob/main/scoville-handoff/SKILL.md).

## What it costs

- Preparing the prompt takes tokens and time once, so the next session has less context to reconstruct.

## How it was developed

Real transfers exposed lost blockers, decisions and ownership of unfinished
changes. Those cases shaped a compact template that preserves what the next
session needs to continue.

## Compatibility

Developed for Codex and Claude Code with read access to the task's relevant sources. Use a Fable, Astra, SOL or Opus model (5.0+).

## Install

This Skill works independently. Other Scoville Skills are optional.

### Install this Skill

Ask your agent host:

```text
Install this Skill for all my projects from this exact package directory:
https://github.com/benjaminstelzer/scoville-handoff/tree/main/scoville-handoff
Preserve personal settings and unrelated Skills. Report the installed location
and whether the host discovers the Skill.
```

The host needs permission to write to its Skills directory. The
[Codex Skills guide](https://learn.chatgpt.com/docs/build-skills) and the
[Claude Code Skills guide](https://code.claude.com/docs/en/skills)
list the locations for each host.

### Install the complete Scoville suite

The complete suite is in the
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

- [Code](https://github.com/benjaminstelzer/scoville-code) covers engineering scope, implementation, risk and validation.
- [Plan](https://github.com/benjaminstelzer/scoville-plan) keeps Plans, Work Items, Decisions and their status in the repository.
- [UI](https://github.com/benjaminstelzer/scoville-ui) covers UI implementation, information structure, accessibility and rendered checks, with an optional WordPress adapter.
- [Handoff](https://github.com/benjaminstelzer/scoville-handoff) passes active work to another agent or session.
- [Project Context Cleanup](https://github.com/benjaminstelzer/scoville-suite) keeps requested project rules and index text concise without losing required context.

## License

MIT. See [LICENSE](LICENSE).
