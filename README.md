# Compact Handoff

A small Agent Skill for handing unfinished work to another session without dragging the whole conversation along.

Its output is one copy-ready English Markdown prompt. The prompt keeps the goal, working state, decisions, evidence, blockers, and next safe action together. It also tells the receiving agent not to trust it: a handoff is a claim about the past, and the working tree has had time to disagree. Verify first, then continue.

## Install

Use an agent that supports the Agent Skills format: a `SKILL.md` file with name and description frontmatter.

Usually, the simplest option is to send your agent this prompt:

```text
Install this Agent Skill from GitHub and make it available for my work:
https://github.com/benjaminstelzer/compact-handoff/tree/main/compact-handoff
```

Add `for all my projects` or `only for this project` when the installation scope matters. The agent should use its supported skills directory, keep the repository name `compact-handoff`, and refresh its skill list.

For a manual installation, copy the repository's `compact-handoff/` directory
so the final path is:

```text
<skills-dir>/compact-handoff/SKILL.md
```

Skill directories vary between agents. Check your agent's documentation if it cannot choose the location itself.

## Use

Ask for a `compact handoff`, `context handoff`, `session handoff`, or `Übergabe an neue Session`. The skill returns the fenced Markdown prompt and nothing else; the output contract does not let it so much as wish the next agent luck.

**It only runs when you ask.** The skill never produces a handoff on its own initiative. Low remaining context, a finished task, or an approaching session end are not requests, and a request to shorten or summarize is not one either. If it activates without an explicit handoff request, it says so in one sentence and gets back to work.

Asking in your own words is enough. "Hand this over to a new session" triggers the skill exactly as `$compact-handoff` does, because that is a request. The line the skill will not cross is producing a handoff nobody asked for.

It reads version-control state to fill the anchor fields, which is the one thing it does beyond reading the conversation. That inspection is read-only: current branch, HEAD, and working-tree status. Anything it cannot observe is marked `unknown` rather than guessed, and that includes timestamps.

**What it costs.** `SKILL.md` is about 1,300 words, including a roughly
300-word prompt template. It loads when the skill triggers; exact context
accounting depends on the agent.

It complements workflow guardrails such as [Scoville](https://github.com/benjaminstelzer/scoville-anti-ai-coding-slop): their internal handoff rules govern minimal in-place records that survive context compaction, while this skill produces the explicit transfer prompt for handing work to another session.

## License

MIT. See [LICENSE](LICENSE).
