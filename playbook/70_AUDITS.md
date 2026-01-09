# 70_AUDITS
Keywords: quality audits, security audit, performance audit, ux review, seo audit, observability audit, logging, monitoring, ci cd, checklist, maintenance


## When to use
- Regular quality checks: security, performance, UX, SEO, ops, docs.
- Mini audit every few tasks; full audit after a MINOR release.

## Inputs
- Current product status, recent changes, and test results.
- Known risks and technical debt.

## Outputs
- List of issues and recommendations.
- Task set for backlog or roadmap.
- Updates for regression and metrics.

## Procedure (steps)
#1
Apply `01_CORE.md` and active profiles. Define the audit focus (security, performance, UX, SEO, ops, docs).
end of step #1
#2
Check the list: access and secrets, dependencies, critical path performance, UX blockers, SEO if relevant, monitoring and logging, documentation freshness.
end of step #2
#3
Record findings: severity, impact, proposals. Convert them into tasks with AC and DoD and priorities.
end of step #3
#4
Update the roadmap in `30_PLANNING_ROADMAP.md` and regression set in `60_TESTING_REGRESSION.md` based on results.
end of step #4

## Checklists or message templates
- "Audit (security, performance, UX, SEO, ops, docs): findings <FINDINGS>, risks <RISKS>, proposed tasks <TASKS> with priorities <PRIORITIES>."
- "Recommend including in the next MINOR: <TASK_LIST>."

## Related files
- [00_ROUTER.md](00_ROUTER.md)
- [01_CORE.md](01_CORE.md)
- [30_PLANNING_ROADMAP.md](30_PLANNING_ROADMAP.md)
- [60_TESTING_REGRESSION.md](60_TESTING_REGRESSION.md)
- [80_DOCS.md](80_DOCS.md)
