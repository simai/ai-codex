# 20_PROJECT_SPEC_GUIDE
Keywords: requirements gathering, project specification, scope, out of scope, roles, user stories, functional requirements, non-functional requirements, data privacy, acceptance criteria, definition of done


## When to use
- Need to gather or refine a project specification for greenfield or brownfield work.
- Need to define scope, out-of-scope, AC, DoD, and risks before planning.

## Inputs
- Product goals, audience, and constraints.
- Known artifacts: designs, APIs, existing code, or an archive.

## Outputs
- Draft specification with goals, functionality, and constraints.
- List of open questions and assumptions for confirmation.
- AC and DoD for key features.

## Procedure (steps)
#1
Apply `01_CORE.md` and active profiles. Clarify context such as domain, platforms, and delivery environment. Record DoNotTouch and constraints.
end of step #1
#2
Build the spec structure: goals, users, scenarios, non-functional requirements, integrations, data, security, localization, risks, AC, DoD, exclusions.
end of step #2
#2.1
If the scope includes a user interface, outline the UX approach before writing tasks: user goals, core workflows, required functionality, and a draft layout based on available UI components and constraints.
end of step #2.1
#3
Request missing information: inputs, constraints, sources of truth, access, deadlines. If not provided, record ASSUMPTIONS explicitly.
end of step #3
#4
Produce the draft spec using `TEMPLATES.md`, separate scope and out-of-scope, and state risks and regression requirements.
end of step #4
#5
Propose the next step: planning in `30_PLANNING_ROADMAP.md` or tasking in `40_CODEX_TASKING.md`.
end of step #5

## Checklists or message templates
- "Needed inputs: goals, audience, platforms, integrations, data, constraints, deadlines, AC, DoD. Please confirm or correct."
- "Scope: <SCOPE_LIST>. Out of scope: <OUT_LIST>. Risks: <RISK_LIST>. Assumptions: <ASSUMPTIONS_LIST>."

## Related files
- [00_ROUTER.md](00_ROUTER.md)
- [01_CORE.md](01_CORE.md)
- [10_ONBOARDING.md](10_ONBOARDING.md)
- [30_PLANNING_ROADMAP.md](30_PLANNING_ROADMAP.md)

## Standards Contract (mandatory)
In every spec draft, include a section "Standards & Non‑negotiables":
- Active profile (e.g., Bitrix) and why.
- Project structure conventions (folders, entry points, install/uninstall behavior).
- Localization rules (what must be localized; key naming).
- Security defaults (permissions, CSRF/session, safe logging).
- UX/admin usability expectations (navigation, error handling, confirmations).
- Verification plan: smoke steps + regression minimum.
- Feedback loop: how test feedback is collected and tracked (Issue Log), and the bugfix-first gate before new features.

If a standard is not known or is project-specific:
- Ask the user to provide it (as a short bullet list or a file) and record it in `PROJECT_STANDARDS.md`.
- Do NOT guess.

Bitrix prompt (if Bitrix profile is active):
- Confirm admin/proxy technology expectations (where real admin pages live, where proxies live, how they include local/bitrix modules).
- Confirm localization baseline (all admin UI strings via `Loc::getMessage()` + `lang/ru/...`).
