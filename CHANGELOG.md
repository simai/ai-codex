# CHANGELOG

Rule: cumulative log, newest versions on top. Keep sections Added, Changed, Fixed, Security, Docs for every version.

## [0.5.4] - 2026-01-09
### Added
- Suggested commit message line required in every Codex task.
### Changed
- Step numbers for Codex tasks increment by 1 and continue across handoff based on history.
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
