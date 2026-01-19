# 60_TESTING_REGRESSION
Keywords: testing strategy, smoke test, regression testing, unit tests, integration tests, linting, static analysis, coverage, test plan, reproducible checks, bugfix requires test


## When to use
- Any new feature requires smoke testing and a regression minimum.
- Every bug fix must be accompanied by a test or a regression item.

## Inputs
- Change description and available tests or scripts.
- Environment requirements and constraints.

## Outputs
- Smoke and regression plan agreed with the user.
- Test results: what was run and outcomes.
- Updated regression checklist for future releases.
- Traceability between AC/DoD and smoke or regression checks.
- If user feedback is provided: updated Issue Log and mapping of issue IDs to focused re-test steps.

## Procedure (steps)
#1
Apply `01_CORE.md` and active profiles. Identify critical scenarios and risks.
end of step #1
#2
Define smoke: the minimal actions to confirm the main function using `TEMPLATES.md`. Clarify inputs and expected outcomes.
end of step #2
#3
Define regression: negative cases, compatibility, configurations, and data. Map smoke and regression checks to AC and DoD for traceability.
end of step #3
#4
For bug fixes, add a test or regression item. Record what runs and the expected behavior.
If the user provides manual test feedback, route to `16_FEEDBACK_TRIAGE.md` and ensure every reported item becomes either:
- an Issue Log entry, or
- a regression item (or both).
end of step #4
#5
Report results: what ran, conclusions, and what remains uncovered. Propose automation when possible and safe.
end of step #5

## Checklists or message templates
- "Smoke: actions <ACTIONS>, expected <EXPECTED>. If failure occurs, provide logs or screenshots with the step and expectation. Regression: <CHECKS>."
- "Bug fix <ID>: added test or regression item, run results: <RESULTS>."
- "AC/DoD mapping: <AC_TO_CHECKS_MAP>. Gaps: <GAPS>."

## Related files
- [00_ROUTER.md](00_ROUTER.md)
- [01_CORE.md](01_CORE.md)
- [16_FEEDBACK_TRIAGE.md](16_FEEDBACK_TRIAGE.md)
- [50_REVIEW_DIFF_FIRST.md](50_REVIEW_DIFF_FIRST.md)
- [70_AUDITS.md](70_AUDITS.md)
- [TEMPLATES.md](TEMPLATES.md)
