# 10_ONBOARDING
Keywords: onboarding, kickoff, discovery questions, context recovery, new project, existing project, brownfield, project brief, assumptions, constraints, stakeholders, next steps


## When to use
- New project, vague idea, or context recovery after a break.
- Archive or code received without descriptions, need a quick state assessment.

## Inputs
- Initial information: goals, links, archive, requirement snippets.
- Active profile details (if applicable) and safety constraints.

## Outputs
- Short state summary and identified gaps.
- List of clarifying questions and explicit ASSUMPTIONS.
- Suggested next step via `00_ROUTER.md`.

## Procedure (steps)
#1
Check `01_CORE.md` and active profiles. Record constraints, DoNotTouch, and safety requirements. Prepare questions if data is missing.
end of step #1
#2
Collect known goals, inputs, and artifacts. Identify risks and uncertainties. Record ASSUMPTIONS as a separate list.
end of step #2
#3
Produce a short summary: current understanding, gaps, required confirmations. Propose a route via `00_ROUTER.md` such as `20_PROJECT_SPEC_GUIDE.md` or `50_REVIEW_DIFF_FIRST.md`.
end of step #3

## Checklists or message templates
- Summary message: "Understanding: <SHORT_SUMMARY>. Missing data: <DATA_REQUEST>. ASSUMPTIONS: <LIST>. Proposed next step: <MODULE_OR_ACTION>."
- If archive: "Ready to report findings and risks. Please provide environment, secrets handling, and dependency details to keep safety intact."

## Related files
- [00_ROUTER.md](00_ROUTER.md)
- [01_CORE.md](01_CORE.md)
- [20_PROJECT_SPEC_GUIDE.md](20_PROJECT_SPEC_GUIDE.md)
- [50_REVIEW_DIFF_FIRST.md](50_REVIEW_DIFF_FIRST.md)
