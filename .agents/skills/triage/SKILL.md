---
name: triage
description: Reconcile scheduling-product requests and backlog against their specs into a complete issue tracker, marking open issues agent-ready or needs-human with actionable briefs, explicit decisions, dependencies and source evidence. Use for intake and retriage, not implementation or deciding for product owners.
---

# Triage requests into a marked tracker

Read the repository's AGENTS.md, tracker README, all specs and accepted decisions before classifying requests. Their actual issue format and authority rules win over generic templates. In this tracker the source rules are PRD-1..4, DES-1..5, ADR-0001..2 and AUT-1..3; reread their current text rather than assuming the ids mean the same thing elsewhere.

Use the supplied collectors and cursor store instead of recreating their intake. Collect a local review copy before publishing. Keep an immutable raw-source snapshot and a ledger linking each request id, exact wording, channel and response-history record to its resulting issue and disposition. Reuse the existing capture workflow when sources conflict or require reconciliation. Log each course request and full response immediately in local, ignored challenge-history.jsonl; stop further course calls if a response cannot be saved. Collector state may contain session proofs and must never enter Git or a public artifact.

## Decide the disposition

- Account for every backlog key and every request id, including requests that need no new work. Compare the meaning, not just matching words. Merge requests for the same outcome into the existing issue's sources; retain all source ids. A new request can be evidence against a proposed change.
- Preserve shipped backlog work as done. A stale report of that same defect can be attached to its shipped issue with the shipped key as evidence. Do not label a newly rejected request done: close it with duplicate, obsolete, contradicts-spec or not-planned and cite the deciding spec, shipped issue or request. A duplicate points to a real canonical issue, with its sources retained there; never use a closed duplicate as a dependency target.
- Close an exact request that contradicts an accepted invariant, citing its rule. Do not quietly implement a preferred replacement or rewrite a spec to satisfy it. If a separate safe outcome is warranted, give that outcome its own sourced scope.
- AUT-1 permits bounded spec-conforming bugs, copy, additive features and token-based variants. AUT-2 overrides that permission for anything involving client reliance, pricing/invoices/terms, or deleting/rewriting stored data. Urgency and the requester's title do not grant authority.
- Look for cross-channel counterevidence before marking a superficially simple change ready: export date order, API formats, vocabulary clients rely on, historical-data cleanup, financial changes, or replacing existing data columns. Distinguish an additive option from switching an existing default. Preserve competing evidence in one decision issue; do not ask the student to decide for the product's people.

## Write the issue for its next worker

Every open issue has exactly one authority label: agent-ready or needs-human. Preserve origin labels and source ids. Use the README's key, sources, blocked-by, duplicate-of, status and reason representations for the selected tracker.

An agent-ready body includes Intent, Acceptance and Boundaries; observable Given/When/Then cases or checkboxes; at least one meaningful negative case; a regression test/evidence requirement; and the specific AUT-1 permission. Cite the relevant product/design/decision rules. Preserve current client-facing behavior outside its stated scope. Do not invent a new product policy, rate limit, retention period, colour palette or security model merely to make the brief complete.

A needs-human body follows AUT-3: Question, at least two Options, Recommendation and Why, citing the exact rule/request/issue that requires the decision. Name the product decision owner by role when the evidence identifies one; otherwise leave ownership unassigned rather than inventing a person. Leave it open until the authoritative decision arrives; a recommendation is not that decision.

Dependency reasoning is part of triage. Colour-token migration must precede a colour scheme; type-scale migration precedes larger text; spacing-scale migration precedes density. Use the actual backlog keys and blocked-by fields, preserve transitive prerequisites, and check for missing targets and cycles. A scoped additive fix must not wait on an unrelated broad proposal. An agent must not start blocked work until its prerequisites are done, even if it needs no human decision.

## Check and publish

Check request coverage against all collected channel pages and preserve every backlog key; one open issue must never carry both authority labels. Review the semantics of every ready/closed/human disposition against its cited sources, not merely headings or label counts. Recheck the current source catalog/channels before publishing and claiming; report new evidence and retriage affected work. Bound freshness review to the agreed number of rounds and pause for review when exhausted.

For GitHub, reuse the installed gh routine and its help; name the approved owner/repo on every command. Read auth status, create labels before issues, use body files, retain returned issue numbers, and translate dependency keys to actual references if needed. Use the README's close reason/labels: shipped is completed, rejection is not planned, and obsolete/contradicts-spec additionally carry their reason labels. With older gh, keep blocked-by lines in bodies instead of assuming native blockedBy support. Read the resulting tracker back from GitHub, including closed states and reasons.

Before any external mutation, show the concrete issue table/bodies, target repository, visibility and undo plan and obtain the required approval. Keep raw history, cursors, session proofs and private snapshots out of publication. Export the actual GitHub tracker with the README's documented fields, validate source coverage and payload size, and submit the actual skill text used. A local pass means verified, not course-accepted; claim acceptance is the final external proof.
