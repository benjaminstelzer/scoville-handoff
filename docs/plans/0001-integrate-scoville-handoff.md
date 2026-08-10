---
format_version: 1
id: PLAN-0001
status: active
created: 2026-08-10
updated: 2026-08-10
current_item: W-006
---

# Integrate Scoville Handoff into the Scoville suite

## Goal

Transform the current local Compact Handoff repository into a behaviorally reliable, token-efficient Scoville Handoff sibling whose runtime identity, composition boundaries, repository structure, documentation, benchmarks, and Codex and Claude installations match the Scoville suite while preserving truthful, explicit-request-only task transfer.

## Non-goals

- Do not rewrite history, create a parallel repository, or retain a second Compact Handoff runtime after the authorized Scoville Handoff publication.
- Do not weaken explicit activation, snapshot freshness, authority, secret handling, dirty-tree ownership, in-flight operation, or continuation-critical facts to simplify the output or reduce tokens.
- Do not make Scoville Handoff require another Scoville Skill, replace Scoville Plan's durable repository state, or absorb Code, UI, Scribe, or Plan ownership.
- Do not change sibling Skill behavior or packages; publication updates are limited to factual README family links, family totals, changelogs, and patch releases.

## Work items

### W-001 Establish the canonical Skill identity and behavior contract
Status: done
Depends on: []
Blocked by: []
Decisions: [ADR-0001, ADR-0002]
Outcome: One locally reviewable `scoville-handoff` package expresses the new Scoville identity, returns a compact and continuation-useful transfer artifact, preserves the existing transfer semantics, and defines non-overlapping ownership with Plan, Code, UI, and Scribe.
Acceptance: The installable directory and frontmatter name are `scoville-handoff`; the heading and OpenAI display metadata say `Scoville Handoff`; the frontmatter description stays within 1,024 characters, passes the Skill validator, and covers explicit English and German transfer requests, negative summary and wrap-up cases, and legacy natural-language phrases; a Fable-reviewed field audit classifies every current output section as required, conditional, mergeable, or removable and traces every retained field to a concrete receiver decision or safety boundary; the candidate starts from exactly four required headings—`Receiver Instructions`, `Objective`, `State`, and `Resume Steps`—and its output contract enumerates the exact spelling and objective trigger of every conditional heading, including canonical sources, binding user decisions and constraints, authorization when side-effect work exists, dirty-tree ownership when changes exist, validation evidence, tried and rejected approaches, external state, assumptions and unknowns, blockers, in-flight operations and hazards, and time-sensitive observations; no conditional section appears without content and every declared trigger makes its section mandatory; the semantic map preserves objective, acceptance, current state, ownership, authority, binding user decisions and constraints, assumptions, unknowns, decisive evidence, failed approaches, first safe resume action, freshness, secrets, dirty-tree, in-flight, and no-side-effect boundaries for W-003 to verify; family composition treats Handoff as a portable snapshot, Plan as durable repository state, and every sibling as optional; the accepted outcome of ADR-0002 is implemented without duplicate ownership.
Steps:
1. Freeze the released `compact-handoff` package and enumerate every operational invariant and trigger boundary.
2. Ask Fable to audit the current returned handoff for continuation value, redundancy, missing facts, conditional fields, and the smallest safe output shape.
3. Design the renamed package, selected output contract, and any conditional reference split without losing a continuation-critical fact.
4. Apply the identity, metadata, output, composition, and migration changes locally.
5. Validate the Skill package, field-to-invariant map, and complete semantic diff before behavioral qualification.
Evidence: [released baseline frozen at commit e6d9970 and 1689 Core tokens, behavior contract maps activation output safety and sibling ownership, Skill quick validator passed for scoville-handoff, Fable 5 High semantic review returned READY, static identity and trigger contract passed 11 of 11 checks, uncompressed candidate uses 1481 Core tokens]

### W-003 Qualify reliability first and then reduce loaded Skill tokens
Status: cancelled
Depends on: [W-001]
Blocked by: []
Decisions: [ADR-0001, ADR-0002]
Outcome: A frozen paired SkillOpt evaluation selects a Scoville Handoff candidate only when it improves or preserves every declared behavior and then minimizes observed loaded Skill instructions using the local SkillReducer strategy.
Acceptance: The Luna pilot and its observed Test cases remain historical and are never reused as promotion evidence; a fresh Terra 5.6 Medium released baseline from commit `e6d9970e7d081f322050ae8cf3b6d1e37ab561e4` establishes real original behavior, while Sol 5.6 xhigh analyzes failures; the benchmark adds new hash-bound Test cases never exposed to the optimizer and covers direct and indirect positive activation, English and German transfer, negative summary and wrap-up, ambiguity, dirty-tree ownership, secret redaction, authorization, in-flight state, empty state, Plan composition, optional sibling composition, renamed real-catalog discovery, and fresh-receiver continuation; a frozen coverage matrix maps every behavior category and every conditional-output trigger to one or more cases and splits, permits multi-category cases, and leaves no declared invariant unmapped; fixture reads are explicit scored preconditions; deterministic scoring checks the selected fenced Markdown headings, semantic facts, and receiver actions rather than analyzer key spelling; six distinct Train cases run three times for 18 observations and three distinct Validation cases run three times for 9 observations; the strengthened uncompressed candidate must reach 18/18 Train and 9/9 Validation before becoming the reliability-matched reducer control; only then may SkillReducer-style classification, progressive disclosure, selective restore, and expected loaded-token cost create a reduced candidate, which must also reach 18/18 Train and 9/9 Validation with no candidate-only hard failure, unauthorized mutation, missing provider evidence, or retained field unsupported by the Fable field audit; after a reduced candidate hash is sealed, three new opaque Test cases run once per arm with independent fresh agents and both reliability-matched control and candidate must reach 3/3; if only the reduced candidate fails a genuine held-out criterion while control passes, reject the reduction and retain the qualified uncompressed control; if no reduced candidate reaches the open gates, run the qualified uncompressed control alone on the new opaque Test set and retain it only at 3/3; if both paired arms reach 3/3 but the reduced candidate does not lower expected loaded tokens, retain the qualified uncompressed control; if control fails, both paired arms fail, or a Test contract or infrastructure defect prevents a valid comparison, promote neither tested candidate, preserve the raw results, return to open development, and mint an entirely new opaque Test set after correction; never retry, remint, or reuse an exposed Test case for qualification; benchmark, harness, and infrastructure defects remain raw evidence but count neither as Skill passes nor Skill failures after narrow documented adjudication; discovery claims use real catalog probes only; when references are introduced, token comparison measures Core plus actually routed references across representative routes; promote the lower-cost reduced candidate only after every stated gate, otherwise retain the Test-qualified uncompressed control only through one of the explicit fallback branches.
Steps:
1. Repair and extend the existing `benchmarks/compact-handoff` contract, require fixture reads, and replace every exposed held-out case before candidate optimization.
2. Freeze package, controller, fixtures, scorers, split hashes, execution models, counterbalanced order, real catalog probes, and promotion gates.
3. Run the released baseline and repeated open reliability candidate, repairing only the smallest causal Skill unit for real failures and stopping on unresolved benchmark ambiguity.
4. Freeze the perfect uncompressed candidate as reducer control, apply the local SkillReducer method, and rerun all affected open gates after every reduction.
5. Seal the selected candidate hash and execute each new held-out arm once with independent fresh agents, including fresh receivers that lack the old conversation.
6. Recompute pass rates, receiver actions, loaded Core and reference tokens, provider usage, retries, reads, shell calls, and run counts from raw artifacts.
Evidence: [original paired gate cancelled after wrong comparator binding and contradictory scorer contract, exposed v1 holdout retained as diagnostic evidence, ADR-0003 selects a fresh candidate-only qualification]

### W-005 Qualify the frozen candidate with a fresh sealed Test
Status: done
Depends on: [W-001]
Blocked by: []
Decisions: [ADR-0003]
Outcome: One fresh opaque Candidate-only Test establishes whether the final frozen Scoville Handoff candidate safely transfers unseen tasks without reusing or relabeling the invalid paired run.
Acceptance: A fresh author that has read no Skill candidate open case prior Test run or project Plan creates three new schema-valid cases; a separate fresh Terra 5.6 Medium agent executes the bound candidate hash once with network and prediction reuse disabled; direct review and Fable both find 3/3 semantic passes across two positive transfers and one negative request; provider usage exact-once named reads command prohibitions shell budgets and Skill isolation are complete; no retry remint reuse or post-Test candidate edit occurs; the raw scorer result and every contract defect remain preserved separately from the Skill score.
Steps:
1. Author and seal three new opaque cases against the validated Studio schema without exposing the candidate or previous suites.
2. Bind the final Skill hash and execute the Candidate once through a fresh Terra 5.6 Medium agent.
3. Inspect results only after the run is terminal and separate real semantic failures from benchmark-contract defects.
4. Obtain a final short Fable review of the actual outputs and publish only the supported qualification claim.
Evidence: [sealed v2 Candidate-only Test passed 3 of 3 by direct and Fable semantic audit, no Test retry remint reuse or post-Test candidate edit occurred, final Skill hash D9D92F1131C99CE72654FCA7BB57E9E0C2D9497947DFB07DB00FE1360E9490C9 uses 1086 tokens, discarded v1 paired run retained after wrong comparator and scorer-contract diagnosis]

### W-002 Align repository documentation and Scoville-family recognition
Status: done
Depends on: [W-001, W-005]
Blocked by: []
Decisions: [ADR-0001, ADR-0002, ADR-0003]
Outcome: The Handoff repository presents the benchmark-qualified Scoville Handoff with the same public structure, terminology, installation guidance, cost explanation, and optional-sibling model as Code, UI, Scribe, and Plan.
Acceptance: The Handoff README uses the suite section order `Why`, `Install`, `What it enforces`, `Use with the Scoville family`, `Design`, `Sources and inspirations`, `Repository contents`, `Status`, and `License`; installation names Terra 5.6 Medium or comparable such as Opus 4.8 as the minimum; `What it costs` distinguishes provider usage from literal loaded Skill instructions, uses only W-005 qualification and direct token measurements, and explains when safe transfer justifies the overhead; the repository contains root README, CHANGELOG, LICENSE, installable package, evaluation cases, and benchmark evidence in the same ownership pattern as its siblings; its family section links the existing four sibling repositories and states non-overlapping optional ownership; no published sibling repository is edited during this phase; all repository-content claims, status figures, terminology, and local Markdown links are verified against the final local tree and W-005 artifacts.
Steps:
1. Map each current Handoff document and family statement to the released Scoville repository pattern.
2. Rewrite Handoff documentation and add evaluation and evidence surfaces from the final W-005 artifacts without copying internal optimization history into user-facing prose.
3. Describe Handoff's ownership beside existing Scoville siblings without adding reciprocal unpublished links or hard dependencies.
4. Verify terminology, status numbers, links, repository contents, and independent sibling operation.
Evidence: [README suite section order and cost guidance verified, public status reconciled to 222 runs 620 cases 3 of 3 sealed and 35.70 percent token reduction, Skill validator local links JSON diff encoding and repository inventory passed, Scoville family links and optional ownership verified]

### W-004 Migrate local installations and prove publication readiness
Status: cancelled
Depends on: [W-002, W-005]
Blocked by: []
Decisions: [ADR-0001, ADR-0002, ADR-0003]
Outcome: Codex and Claude use the exact validated Scoville Handoff package locally as one optional Scoville sibling, while the repositories remain uncommitted and no remote state changes.
Acceptance: The exact active paths are `C:/Users/benja/.codex/skills/compact-handoff`, `C:/Users/benja/.codex/skills/scoville-handoff`, `C:/Users/benja/.claude/skills/compact-handoff`, and `C:/Users/benja/.claude/skills/scoville-handoff`; a recoverable staging copy and SHA-256 inventory cover each old installation before cutover; for each host, the new package is validated outside the active Skills directory, explicit approval is obtained immediately before moving the old installation to its exact backup path, and the staged replacement is moved into the active path without a duplicate-discovery interval; the installed `scoville-handoff` trees are byte-identical to the promoted candidate; old runtime paths are handled exactly as the accepted ADR-0002 requires and no duplicate Handoff Skill remains; isolated discovery and representative positive, negative, Plan-composition, and sibling-composition checks pass on both hosts; Skill quick validation, repository evaluation cases, benchmark-evidence links, Markdown links, `git diff --check`, package inventory, and full scoped diffs pass; every touched repository remains on its original branch with no commit, push, tag, release, remote rename, sibling-repository edit, or GitHub mutation.
Steps:
1. Stage the promoted package outside active Skill directories and record source, old-installation, and staged-tree hashes without exposing secrets or unrelated files.
2. For Codex, obtain immediate cutover approval, move the old installation to the enumerated backup, activate the staged replacement, refresh discovery, verify it, and roll back on failure.
3. Repeat the same bounded cutover and verification for Claude after separate immediate approval.
4. Run representative cross-host and family-composition checks, audit every local repository diff, and prepare a publication report without publishing it.
Evidence: [Codex and Claude staging packages validated byte-identical to final Skill hash D9D92F1131C99CE72654FCA7BB57E9E0C2D9497947DFB07DB00FE1360E9490C9, old active installations inventoried without mutation, cutover inventory SHA256 71B87D214C47AC3BA2CFB8EE8AAC98CCDFF8725FE68CB1EBE19B030592F7D5E3, user replaced the recoverable local-only cutover with permanent removal and GitHub publication]

### W-006 Publish Scoville Handoff and complete the permanent cutover
Status: in_progress
Depends on: [W-002, W-005]
Blocked by: []
Decisions: [ADR-0001, ADR-0002, ADR-0003, ADR-0004]
Outcome: Codex and Claude use only the validated Scoville Handoff package and the existing GitHub repository is published under the Scoville Handoff identity with a verified release and profile pin.
Acceptance: The active Codex and Claude `scoville-handoff` packages are byte-identical to the qualified candidate; both old active `compact-handoff` directories and their staged old-installation backup are absent; isolated package validation and representative activation boundaries pass; the local repository directory and Git remote use `scoville-handoff`; README installation guidance names the public repository; the existing GitHub repository is renamed rather than replaced; main contains one intentional release commit; the immutable `v2.0.0` tag and GitHub Release point to that commit; every published Scoville sibling README links Scoville Handoff in its family section and reports the reconciled five-Skill run total without changing a sibling Skill package; Code `v1.0.9`, UI `v1.0.9`, Scribe `v1.0.9`, and Plan `v1.2.5` releases point to their respective README-only publication commits; the `BenjaminStelzer` profile README replaces Compact Handoff with Scoville Handoff; the GitHub profile pins `benjaminstelzer/scoville-handoff` and no longer pins `benjaminstelzer/compact-handoff`; the final repository and Plan checks pass.
Steps:
1. Reconcile the publication decision with the repository records and public installation guidance.
2. Replace both active host packages from the validated staging copies and permanently remove the predecessor directories and old-installation staging data.
3. Validate both installed packages and the final repository tree before publication.
4. Commit the exact reviewed tree and rename the existing GitHub repository to `scoville-handoff`.
5. Publish the four sibling README links and patch releases plus the updated GitHub profile README.
6. Push main, create and verify release `v2.0.0`, verify the profile pin, rename the local repository directory, and complete the Plan.
Evidence: []
Next action: Update the accepted publication record and public repository text before the authorized local cutover.
