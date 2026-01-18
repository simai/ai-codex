# 40_CODEX_TASKING
Keywords: codex task, task specification, single code block, tracking tags, suggested commit message, allowed scope, do not touch, acceptance criteria, checks, tests, smoke test, version bump, changelog update, no drive-by improvements

## When to use
- Need to formulate a Codex task with clear constraints and checks.

## Inputs
- Confirmed scope, current repository or archive state.
- Constraints and DoNotTouch, checks and smoke requirements.
- Target project version to set after the task.

## Outputs
- Self-contained Codex task in a single code block with a target version.
- Checks list (smoke and regression) and acceptance criteria.
- Tracking tags only inside the code block and a Suggested commit message line included.
- Clarifying questions when ambiguity is detected.
- Definition of Ready and risk/rollback details when applicable.

## Procedure (steps)
#1
Apply `01_CORE.md` and active profiles. Check for ambiguity and ask questions before drafting the task.
end of step #1
#2
Collect inputs: goal, context, target version, files and directories in scope, DoNotTouch, constraints on time and tests, logging and secret requirements.
end of step #2
#2.1
If the task is UI-related, include a brief UX intent block: user goals, key flows, required UI elements, and a high-level layout plan aligned with available tools.
end of step #2.1
#2.2
Confirm Definition of Ready: environment, access, dependencies, test data, CI limits, and secrets handling. If any are missing, ask before drafting.
end of step #2.2
#2.3
If the scope is large or risky, split into smaller tasks with clear boundaries and dependencies. Avoid multi-domain bundles.
end of step #2.3
#3
Draft the task in one code block using `TEMPLATES.md`. Include tasks, steps, expectations, checks, smoke, no drive-by improvements, expected response format, target version, and requirement to update target project VERSION and CHANGELOG if part of the task.
end of step #3
#4
Reinforce rules: write the Codex task in the user’s language, use bilingual field labels with the local label followed by the English canonical label in parentheses. Add tracking tags inside the code block only: first line `#N`, last line `end of step #N`. The number N increments by 1 for each new Codex task and continues after handoff based on the last task in history. Include a "Suggested commit message:" line inside the code block near the end, before the final tracking tag. Do not use these tags in normal assistant explanations.
end of step #4

Commit message guidance:
- Use Conventional Commits types: feat, fix, docs, chore, refactor, test, perf, security.
- Optional scope is recommended, for example playbook, profile-bitrix, docs, system-prompt.
- Use a short imperative subject in English.

## Checklists or message templates
- "Codex task is ready and includes scope, DoNotTouch, checks, smoke, and target version <VERSION>. Confirm before sending."
- "Ambiguity found in <FRAGMENT>. Clarification needed: <QUESTION>."

## Related files
- [00_ROUTER.md](00_ROUTER.md)
- [01_CORE.md](01_CORE.md)
- [30_PLANNING_ROADMAP.md](30_PLANNING_ROADMAP.md)
- [50_REVIEW_DIFF_FIRST.md](50_REVIEW_DIFF_FIRST.md)
- [TEMPLATES.md](TEMPLATES.md)

## Definition of Ready (DoR) gate (mandatory)
Before emitting a Codex task, confirm all are present:
- Active profile (or explicit ASSUMPTION with rationale).
- Scope/out-of-scope + AC + Checks/Smoke.
- DoNotTouch boundaries + constraints.
- Target version + CHANGELOG update requirement.
If anything is missing or ambiguous: ask questions and do NOT emit a Codex task.

## Profile rules in tasks (mandatory)
- Every Codex task must restate the active profile's non-negotiables in the constraints section.
- For Bitrix tasks, include a micro-checklist in Acceptance Criteria that covers:
  - module structure (admin vs install/admin)
  - localization (`lang/` + `Loc::getMessage`)
  - path portability (no hardcoded `/local/` in proxies)
