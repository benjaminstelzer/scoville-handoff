---
format_version: 1
id: ADR-0004
status: accepted
created: 2026-08-10
accepted: 2026-08-10
scope: project/publication
---

# Publish Scoville Handoff and remove the predecessor

## Decision

Rename the existing GitHub repository and local repository directory to `scoville-handoff`, publish the qualified package as `v2.0.0`, replace Compact Handoff in the GitHub profile pins, and permanently remove the old `compact-handoff` installations from Codex and Claude after validating the staged Scoville Handoff replacement. Retain no old-installation backup.

## Problem

The completed local candidate has the Scoville identity, but the active host installations, repository name, release history, and GitHub profile still expose Compact Handoff. The prior Work Item intentionally stopped before publication and required a recoverable backup, while the user has now explicitly authorized publication and permanent predecessor removal.

## Drivers

- Present one canonical Skill and repository identity across Codex, Claude, GitHub, and the Scoville family.
- Preserve the existing repository history instead of creating a parallel project.
- Avoid duplicate Skill discovery and a stale pinned Compact Handoff identity.
- Publish only the benchmark-qualified package and its factual evidence.
- Follow the user's explicit choice not to retain the old installed package or a rollback backup.

## Considered alternatives

- Keep the repository and active installations under Compact Handoff: avoids migration but contradicts the accepted Scoville identity.
- Keep a permanent backup or compatibility installation: improves rollback but retains the predecessor the user explicitly chose to remove.
- Create a new Scoville Handoff repository: gives a clean name but fragments history and leaves two project owners.
- Rename and release the existing repository while replacing both active installations: preserves history and establishes one canonical owner.

## Consequences

Explicit `$compact-handoff` invocations stop working and must use `$scoville-handoff`; established natural-language handoff phrases remain supported. GitHub's repository redirect may continue to resolve the former URL, but no separate Compact Handoff repository or package remains. The published release is a breaking identity migration and therefore uses major version `v2.0.0`. Removing the old local packages without a backup makes rollback depend on repository history rather than retained installation directories.

## Confirmation

Verify byte-identical installed packages on Codex and Claude, absence of both old active directories and old-installation staging data, one renamed GitHub repository with preserved history, a release and tag bound to the pushed commit, the updated profile pin, and a clean local tree under the renamed directory.

## Revisit when

A supported host provides one canonical package with a portable explicit-invocation alias or the release must be rolled back from repository history.
