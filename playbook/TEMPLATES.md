# TEMPLATES
Keywords: templates, project brief template, project spec template, codex task template, changelog template, smoke test template, state summary template, copy paste, placeholders

## Project Brief template (1–2 pages)
```
Project name and version: <NAME>
Goal and value: <GOAL>
Target audience and personas: <PERSONAS>
Key scenarios (3–7): <SCENARIOS>
Platforms and channels: <WEB_MOBILE_BACKOFFICE_OTHER>
Technical constraints: <CONSTRAINTS>
Integrations and data: <SYSTEMS_AND_DATA>
Risks and unknowns: <RISKS>
Success metrics: <METRICS>
Next steps and decisions: <NEXT_STEPS>
```

## Project Specification template
```
Spec name and version: <NAME>
Context and goals: <CONTEXT_AND_GOALS>
Users and personas: <PERSONAS>
Scope (functions): <SCOPE_LIST>
Out of scope: <OUT_LIST>
Functional requirements (by scenario): <REQUIREMENTS>
Non-functional: perf, security, observability, UX, l10n, accessibility, SEO, ops <DETAILS>
Data and storage: <DATA_STRUCTURES>
Integrations and API (contracts, constraints): <INTEGRATIONS>
UI and UX inputs (if any): <LINKS_OR_MOCKS>
Security and privacy assumptions: <ASSUMPTIONS>
Localization and currencies: <L10N>
AC and DoD for key functions: <AC_DOD_LIST>
Risks and mitigation plan: <RISKS_AND_MITIGATIONS>
Regression and testing (smoke plus minimum): <CHECKS>
Open questions: <QUESTIONS>
Assumptions: <ASSUMPTIONS_LIST>
Attachments and links: <LINKS>
```

## Codex task template (strict format)
```
#N
Instruction: write this task in the user’s language. Use bilingual field labels.
Replace <LOCAL_LABEL> with the user-language label when you produce the actual Codex task.
Tracking tags are only for the Codex task code block and must not be used in normal assistant explanations.
The number N increments by 1 for each new Codex task and continues after handoff based on the last task in history.

# Task
- <LOCAL_LABEL> (Context): <CONTEXT>
- <LOCAL_LABEL> (Goal): <GOAL>
- <LOCAL_LABEL> (Active profile): <PROFILE_OR_NONE>
- <LOCAL_LABEL> (Target version): <X_Y_Z>

# Scope
- <LOCAL_LABEL> (Work to do): <WORK_LIST>
- <LOCAL_LABEL> (DoNotTouch): <LIMITS>
- <LOCAL_LABEL> (Constraints): <WORK_CONSTRAINTS>

# Inputs
- <LOCAL_LABEL> (Files and directories): <LIST>
- <LOCAL_LABEL> (Commands or scripts): <COMMANDS>
- <LOCAL_LABEL> (Additional materials): <MATERIALS>

# Expected result
- <LOCAL_LABEL> (Expected outcomes): <CRITERIA>
- <LOCAL_LABEL> (Response must include): changed file list, short change summary, check results, updated target project VERSION and CHANGELOG when required.

# Checks
- <LOCAL_LABEL> (Smoke): <SMOKE_STEPS>
- <LOCAL_LABEL> (Regression minimum): <REGRESSION_STEPS>
- <LOCAL_LABEL> (Additional checks): <CHECK_COMMANDS>

# Rules
- Ask questions if unclear, do not guess.
- No drive-by improvements.
- Record ASSUMPTIONS explicitly.

Suggested commit message: <COMMIT_MESSAGE_EN>
Commit message guidance: use Conventional Commits with an optional scope and a short imperative subject in English.
Commit message examples: feat(playbook): refine codex task tracking, docs(system-prompt): clarify tracking tags, chore(profile-bitrix): update export file rules.
end of step #N
```

## CHANGELOG entry template
```
## [X.Y.Z] - YYYY-MM-DD
### Added
- <ADDED>
### Changed
- <CHANGED>
### Fixed
- <FIXED>
### Security
- <SECURITY>
### Docs
- <DOCS>
```

## Smoke Test template
```
Goal: <GOAL>
Environment or conditions: <ENV>
Step 1: action <ACTION_1> → expected <EXPECTED_1>
Step 2: action <ACTION_2> → expected <EXPECTED_2>
Step 3: action <ACTION_3> → expected <EXPECTED_3>
If a failure occurs, capture logs or screenshots and note the step and expected outcome.
```

## Project State Summary template
```
Date and context version: <DATE>
Project goal: <GOAL>
Done: <DONE_LIST>
In progress: <IN_PROGRESS_LIST>
Open questions: <QUESTIONS>
ASSUMPTIONS: <ASSUMPTIONS_LIST>
Risks and blockers: <RISKS>
Next steps: <NEXT_STEPS>
Checks and tests in focus: <CHECKS>
Archive or snapshot: <ARCHIVE_NAME_WITH_TIMESTAMP>
Links to spec, roadmap, tasks: <LINKS>
```

Note: do not use tracking tags outside Codex task code blocks.
