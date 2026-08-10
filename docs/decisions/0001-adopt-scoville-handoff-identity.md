---
format_version: 1
id: ADR-0001
status: accepted
created: 2026-08-10
accepted: 2026-08-10
scope: project/identity
---

# Adopt Scoville Handoff as the canonical identity

## Decision

Use `Scoville Handoff` as the product title and `scoville-handoff` as the canonical Skill name, installable directory, and future repository name. Treat Compact Handoff as the predecessor rather than a parallel product.

## Problem

The current `compact-handoff` identity sits outside the Scoville naming and discovery pattern even though its transfer-snapshot behavior complements the family. A display-only rename would leave the runtime identifier, directory contract, installation paths, and agent-facing metadata inconsistent.

## Drivers

- Present one coherent Scoville family identity to users and agents.
- Keep the installable directory equal to the frontmatter `name`.
- Preserve the explicit-request activation boundary and the existing handoff semantics.
- Separate local implementation from later GitHub repository mutation or publication.

## Considered alternatives

- Keep Compact Handoff unchanged: avoids migration but does not create a recognizable Scoville sibling.
- Change only the display name: minimizes file movement but leaves contradictory runtime and installation identities.
- Rename the complete local contract to Scoville Handoff: creates one coherent identity and makes the migration surface explicit.

## Consequences

The local Skill directory, frontmatter, heading, display metadata, examples, tests, documentation, and installation paths must use `scoville-handoff`. Existing natural-language trigger phrases can remain compatible, but explicit `$compact-handoff` invocation and installed-directory compatibility require a separate migration decision. GitHub repository renaming, pushing, tagging, releasing, and remote installation remain outside the current local phase.

## Confirmation

Inspect the final local package and isolated agent catalogs: the directory, frontmatter name, display metadata, invocation examples, and repository documentation all identify Scoville Handoff, while behavioral tests preserve the explicit-request handoff contract.

## Revisit when

A supported host requires the old runtime identifier, provides a first-class alias mechanism, or cannot discover the renamed installable directory.
