# CHANGELOG

Rule: cumulative log, newest versions on top. Keep sections Added, Changed, Fixed, Security, Docs for every version.

## [0.7.1] - 2026-01-18
### Added
- Added a mandatory “Issue Log footer” mini-ritual: once triage starts, every assistant reply must end with a compact Issue Log snapshot to prevent forgetting feedback.

### Changed
- Clarified in the iteration protocol and Codex tasking guidance how to keep the Issue Log snapshot visible even when producing a Codex task.

### Fixed
- N/A

### Security
- N/A

### Docs
- Updated triage and templates documentation to enforce the Issue Log snapshot footer.

## [0.7.0] - 2026-01-18
### Added
- Added `playbook/16_FEEDBACK_TRIAGE.md` to convert user test feedback into a categorized, prioritized Issue Log and to enforce a fix-first iteration loop.
- Added Issue Log and User Test Feedback templates to `playbook/TEMPLATES.md`.

### Changed
- Router now routes “user test feedback / bug reports” to triage before any new planning or tasking.
- CORE + Iteration Protocol now include a bugfix-first gate: do not move to new functionality while OPEN issues exist unless explicitly deferred.
- Codex tasking now requires issue references when test feedback exists and enforces fix-only iterations by default.
- Long chat handoff now includes an Issue Log snapshot so context isn’t lost between chats.

### Fixed
- N/A

### Security
- Security and data-loss issues are explicitly treated as P0 in triage to avoid accidental deprioritization.

### Docs
- Updated Knowledge upload list, README, USAGE, and ROADMAP for the feedback triage loop.

## [0.6.0] - 2026-01-18
### Added
- Added `playbook/15_ITERATION_PROTOCOL.md` to enforce analysis-first gating (spec/review vs Codex task separation) and Definition of Ready (DoR).
- Expanded Bitrix profile with a concrete admin/proxy + localization compliance checklist and a portable proxy template.
- Added a `PROJECT_STANDARDS.md` template to capture stack-specific non-negotiables early.

### Changed
- Router and SYSTEM_PROMPT now require explicit profile detection from context and forbid mixing archive review/spec discovery with a Codex task in the same reply.
- Diff-first review now includes profile-specific compliance gates (Bitrix: admin proxy layout, localization, path portability) and evidence-driven checks.

### Fixed
- N/A

### Security
- Strengthened default gates against hardcoded paths and direct UI strings that bypass localization review.

### Docs
- Updated templates and knowledge upload list for the new iteration protocol.

## [0.5.8] - 2026-01-17
### Added
- Roadmap cadence prompt after MINOR releases.
- Decision log field in state summary template.
- AC/DoD to checks traceability item in testing guidance.
### Changed
- Codex tasking now requires Definition of Ready, task splitting for large or risky scope, and UI UX intent for UI tasks.
- Codex task template includes dependencies, environment access, Definition of Ready, risk or rollback, and observability expectations.
- Review guidance now requires requirement to change traceability.
- Bitrix profile adds admin prolog or epilog usage, admin menu attachment, and delete data checkbox on uninstall.
### Fixed
- N/A
### Security
- N/A
### Docs
- N/A

## [0.5.7] - 2026-01-09
### Added
- Bitrix Marketplace requirement for PARTNER_NAME and PARTNER_URI assignment.
### Changed
- N/A
### Fixed
- N/A
### Security
- N/A
### Docs
- N/A

## [0.5.6] - 2026-01-09
### Added
- N/A
### Changed
- Bitrix profile adds Mail and Notifications task standard with mandatory diagnostics and critical checks.
### Fixed
- N/A
### Security
- N/A
### Docs
- N/A

## [0.5.5] - 2026-01-09
### Added
- N/A
### Changed
- Bitrix profile adds mail and notifications task standard with diagnostics and critical rules.
### Fixed
- N/A
### Security
- N/A
### Docs
- N/A

## [0.5.4] - 2026-01-09
### Added
- Codex task tracking tag usage and suggested commit message requirement.
### Changed
- Bitrix profile updated with temp files, export filename convention, admin UI tabs, and partner name rule without SVG.
### Fixed
- N/A
### Security
- N/A
### Docs
- Updated system prompt and templates with tracking and commit message guidance.

## [0.5.3] - 2026-01-09
### Added
- N/A
### Changed
- Step tags are used only inside Codex task code blocks for tracking; normal assistant messages must not be step-formatted.
### Fixed
- N/A
### Security
- N/A
### Docs
- Updated system prompt and templates to reflect tracking tag usage.

## [0.5.2] - 2026-01-09
### Added
- Added Bitrix profile rules for temp import and export files and export filename convention.
### Changed
- N/A
### Fixed
- N/A
### Security
- N/A
### Docs
- N/A

## [0.5.1] - 2026-01-09
### Added
- Added install and uninstall checklist, security details, and testing checklists to the Bitrix profile.
### Changed
- N/A
### Fixed
- N/A
### Security
- N/A
### Docs
- N/A

## [0.5.0] - 2026-01-09
### Added
- Expanded Bitrix profile to cover module structure, install and uninstall, components, admin pages, SEF, security, performance, testing, and ops.
### Changed
- Updated Bitrix profile keywords and organization.
### Fixed
- N/A
### Security
- N/A
### Docs
- N/A

## [0.4.3] - 2026-01-09
### Added
- N/A
### Changed
- Removed remaining non-English examples and updated templates to use <LOCAL_LABEL> placeholders.
### Fixed
- N/A
### Security
- N/A
### Docs
- N/A

## [0.4.2] - 2026-01-09
### Added
- Rule: Codex tasks are written in the user’s language, with bilingual field labels.
### Changed
- Translated `KNOWLEDGE_UPLOAD_LIST.md` to English.
### Fixed
- N/A
### Security
- N/A
### Docs
- Updated system prompt and templates with language and bilingual label rules.

## [0.4.1] - 2026-01-09
### Added
- N/A
### Changed
- Added Keywords lines to all playbook files to improve Knowledge retrieval.
### Fixed
- N/A
### Security
- N/A
### Docs
- N/A

## [0.4.0] - 2026-01-09
### Added
- Language policy: reply in the user language.
### Changed
- Translated playbook and repository docs to English.
### Fixed
- N/A
### Security
- N/A
### Docs
- Updated system prompt and usage instructions.

## [0.3.0] - 2026-01-09
### Added
- Added `playbook/` folder for Knowledge files.
- Added `SYSTEM_PROMPT.md`, `USAGE.md`, `KNOWLEDGE_UPLOAD_LIST.md`.
### Changed
- Updated links after moving playbook into `playbook/`.
### Fixed
- N/A
### Security
- N/A
### Docs
- README and ROADMAP updated for the new structure and usage flow.

## [0.2.0] - 2026-01-08
### Added
- Added `12_ARCHIVE_PROTOCOL.md` with archiving rules and safety.
- Added target version and archive fields to templates and handoff.
### Changed
- Clarified planning and tasking rules: each Codex task requires a target version and target project CHANGELOG update.
- Router includes archiving scenario and links.
### Fixed
- N/A
### Security
- Strengthened the rule prohibiting secrets and PII in archives without explicit permission.
### Docs
- README and ROADMAP updated for the release; modules expanded for archives and handoff.

## [0.1.1] - 2026-01-08
### Added
- N/A
### Changed
- Clarified instruction wording for self-contained guidance.
### Fixed
- Removed placeholders and truncations, restored exact filenames and router table.
### Security
- N/A
### Docs
- Improved readability and completeness for modules, Bitrix profile, and templates.

## [0.1.0] - 2026-01-08
### Added
- Initial modular playbook: router (`00_ROUTER.md`), core (`01_CORE.md`), situation modules 10..90, profiles (`PROFILES_OVERVIEW.md`, `PROFILE_BITRIX.md`), templates (`TEMPLATES.md`), and meta files (`README.md`, `VERSION`, `ROADMAP.md`).
### Changed
- N/A
### Fixed
- N/A
### Security
- N/A
### Docs
- Described usage, reading order, routing, profiles, templates, and roadmap.
