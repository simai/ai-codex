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
- If an Issue Log exists: map each addressed issue ID to concrete file changes and list what remains OPEN or FIXED_PENDING_VERIFY.

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
## Mandatory review depth
- When a project archive is provided, reconstruct the behavior end-to-end from the code and identify potential issues and gaps.
- When a task specifies required functionality, verify the implementation section-by-section, building a full picture of how the feature works.
- When requirements exist, map each requirement to concrete changes and verification steps, and record any gaps.
- If a user Issue Log exists, map each fixed issue ID to evidence (file paths or code snippets) and list the focused re-test steps.

## Checklists or message templates
- "Changed files: <FILE_LIST>. Impact: <IMPACT>. Findings: security <ITEMS>, logic <ITEMS>, perf <ITEMS>, tests <ITEMS>, docs <ITEMS>, version or changelog <STATUS>. Decision: <DECISION>."
- "Changes required: 1) <CHANGE_1> 2) <CHANGE_2>. Smoke or regression: <CHECKS>."
- "Requirements trace: <REQ_TO_CHANGE_MAP>. Gaps: <GAPS>."

## Related files
- [00_ROUTER.md](00_ROUTER.md)
- [01_CORE.md](01_CORE.md)
- [40_CODEX_TASKING.md](40_CODEX_TASKING.md)
- [60_TESTING_REGRESSION.md](60_TESTING_REGRESSION.md)

## Profile compliance gates (mandatory)
In every review, after summarizing changed files, run a profile-specific compliance check:
- Use the active `PROFILE_*.md` checklist.
- Record evidence (file paths, code snippets, grep patterns) for each gate.

Bitrix compliance gates (when Bitrix profile is active):
- Admin/proxy technology:
  - Real admin pages live under `module/admin/`.
  - Proxy files to be copied into `/bitrix/admin/` live under `module/install/admin/`.
  - Install copies only `install/admin/*.php` to `/bitrix/admin/`; uninstall removes them by explicit list.
  - Proxy scripts do NOT hardcode `/local/...`; they locate admin pages in `/local/modules/<id>/admin/` first and fall back to `/bitrix/modules/<id>/admin/`.
- Localization:
  - `lang/<LANG>/...` exists for install, menu, options, and each admin page.
  - No UI text is hardcoded in PHP; use `Loc::getMessage()` and load messages.
- Security / permissions:
  - Admin entry points guard access (prolog admin, rights checks).
  - No secrets in repo/logs; no unsafe output.
If any gate fails: decision must be "Request changes" (or "Split scope" if mixed).

## Suggested evidence helpers
- Search for hardcoded paths: `/local/modules/` or `/bitrix/modules/`.
- Search for hardcoded Cyrillic UI strings in PHP.
- Check that every menu label has a localization key.
