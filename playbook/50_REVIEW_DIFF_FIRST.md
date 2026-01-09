# 50_REVIEW_DIFF_FIRST
Keywords: diff-first review, file changes, scope boundaries, unexpected changes, security review, correctness review, error handling, observability, performance review, test review, accept request changes


## When to use
- Codex output or a new archive requires review.

## Inputs
- List of changed files and diffs.
- Task requirements, acceptance criteria, and test expectations.

## Outputs
- Summary of changes and risks.
- Checklist findings across security, logic, errors, observability, performance, tests, and docs.
- Decision: accept, request changes, or split scope.

## Procedure (steps)
#1
Apply `01_CORE.md` and active profiles. Identify changed files, confirm DoNotTouch, and capture related risks.
end of step #1
#2
Start with a file list and impact assessment. Then review details by risk priority and criticality.
end of step #2
#3
Check: security (secrets, access), business logic and errors, edge cases, observability, performance, tests and regression, documentation, and target project VERSION and CHANGELOG if required by the task.
end of step #3
#4
Provide the conclusion: accept, request changes, or split scope. For changes, list concrete fixes and recommended checks.
end of step #4

## Checklists or message templates
- "Changed files: <FILE_LIST>. Impact: <IMPACT>. Findings: security <ITEMS>, logic <ITEMS>, perf <ITEMS>, tests <ITEMS>, docs <ITEMS>, version or changelog <STATUS>. Decision: <DECISION>."
- "Changes required: 1) <CHANGE_1> 2) <CHANGE_2>. Smoke or regression: <CHECKS>."

## Related files
- [00_ROUTER.md](00_ROUTER.md)
- [01_CORE.md](01_CORE.md)
- [40_CODEX_TASKING.md](40_CODEX_TASKING.md)
- [60_TESTING_REGRESSION.md](60_TESTING_REGRESSION.md)
