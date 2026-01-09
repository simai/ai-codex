# 80_DOCS
Keywords: documentation, user guide, developer guide, architecture docs, release process, security docs, documentation as product, doc updates, changelog alignment, onboarding docs


## When to use
- Always when behavior, interfaces, APIs, or processes change.
- Before releases and after audits or tests.

## Inputs
- Change list and impact on users, developers, and operations.
- Current documentation state and missing sections.

## Outputs
- Updated descriptions for user, dev, testing, release, and roadmap documentation.
- Plan for documentation updates in target projects.
- Notes on missing materials and risks.

## Procedure (steps)
#1
Apply `01_CORE.md` and active profiles. Identify affected audiences (user, dev, ops, QA, product).
end of step #1
#2
For target projects, remind the minimal documentation set as a concept: overview, install and deploy, configuration, operations and support, testing, releases, roadmap. This repo does not create folders, it defines rules only.
end of step #2
#3
For every behavior change, record updates: what changed, why, how to verify, how to roll back. Update relevant sections and link the changelog.
end of step #3
#4
Confirm no secrets or PII in docs or examples. Add references to smoke and regression in `60_TESTING_REGRESSION.md`.
end of step #4

## Checklists or message templates
- "Changed: <CHANGE>. Behavior or interfaces: <DETAILS>. Documentation updated for user, dev, testing, release, roadmap. Required checks: <CHECKS>."
- "Missing materials for <TOPIC>, propose adding to backlog."

## Related files
- [00_ROUTER.md](00_ROUTER.md)
- [01_CORE.md](01_CORE.md)
- [70_AUDITS.md](70_AUDITS.md)
- [90_LONG_CHAT_HANDOFF.md](90_LONG_CHAT_HANDOFF.md)
