# PROFILE_BITRIX
Keywords: bitrix, module structure, install uninstall, components, admin pages, sef, urlrewrite, security defaults, performance defaults, testing minimum, ops release, partner name, partner uri, versioning, audits, upload/tmp, temporary files, import export, export filename, timestamp

Profile for Bitrix projects. Active when the user explicitly asks, the archive contains Bitrix structures such as `bitrix/`, `local/modules/`, `install/index.php`, or the task is clearly about a Bitrix module or site.

## Activation signals
- User explicitly requests Bitrix guidance or module development.
- Archive contains `local/modules/<MODULE_ID>/`, `bitrix/`, or `install/index.php`.
- Task mentions Bitrix components, admin pages, SEF, or urlrewrite rules.

## Non-negotiables
- Do not modify Bitrix core files; work inside `local/` and the module folder.
- Use official APIs and follow Bitrix module conventions.
- Guard direct access with prolog checks in all entry points.
- Always use `Loader::includeModule('<MODULE_ID>')` before module usage.
- Step format is mandatory: each step starts with `#N` and ends with `end of step #N`.

## Module conventions
- Module ID and path: `local/modules/<MODULE_ID>/` with a clear namespace.
- Required files: `install/index.php`, `install/version.php`, `include.php`, `lang/<LANG>/` localization.
- Use `lang/<LANG>/<PATH>` placeholders when describing localization paths.
- Keep module configuration in `install` and runtime logic in module classes.
- Table naming: `module_name_table_name` with module code dots replaced by `_`.
- Initial module version on creation: `1.0.0` (SemVer).

### Temporary files for import and export
- Temporary files created during import or export must be stored in `/upload/tmp/<module_id>/`.
- Create the directory if missing and ensure it is not publicly indexed.
- Use unique filenames to avoid collisions and concurrent overwrite.
- Always clean up temporary files on success and failure.
- Do not store secrets or PII in temp files; if sensitive data is unavoidable, require access protection and short retention.

### Export filename convention
- Format: `<site_domain>_<export_entity>_<optional_scope>_<YYYY_MM_DD_HH_mm_ss>.<ext>`
- Sanitize `site_domain` for filesystem usage, for example replace dots with underscores.
- `export_entity` and `optional_scope` must be short, lowercase, and must not contain PII.
- Examples: `example_com_orders_full_2026_01_09_14_30_05.csv`, `store_net_products_2026_01_09_08_12_00.json`.

## Install and Uninstall contract
- Install steps: register module, create database tables, add events, add agents, add urlrewrite rules, register options.
- Uninstall steps: remove agents, remove events, remove urlrewrite rules, unregister module, remove options.
- Database changes must be idempotent and safe for repeated runs.
- Provide uninstall checkboxes for data retention and respect user choice.
- Install checklist: database changes idempotent, files present, events registered, agents registered, urlrewrite added, options set, rights and groups configured.
- Uninstall checklist: agents removed, events removed, urlrewrite removed, options cleaned, module unregistered.
- Keep data option: retain data tables and user content when selected, still remove agents, events, urlrewrite rules, and runtime options.

## Components and Admin pages
- Separate public components from admin pages and data access layers.
- Validate inputs and permissions for both component and admin entry points.
- Prefer admin pages as proxies to service classes, not as business logic holders.

## SEF and urlrewrite rules
- Define SEF templates in components and keep urlrewrite rules minimal and scoped.
- Add urlrewrite rules during install and remove them during uninstall.
- Avoid global rewrite pollution; use module-specific paths.

## Security defaults
- Enforce CSRF checks and session ID validation for admin and public actions.
- Validate and sanitize input for all endpoints and component parameters.
- Use safe logging with no secrets or PII.
- Use permissions-aware caching and avoid leaking data across roles.
- Require explicit authorization and role checks for admin endpoints.
- Never cache responses across roles without separation or access checks.

## Performance defaults
- Use cache and composite where appropriate; avoid heavy work in request handlers.
- Avoid N+1 queries; add indexes and use pagination for lists.
- Move expensive jobs to agents or cron, not user requests.

## Testing minimum
- Smoke test is mandatory after every functional change.
- Define a regression minimum checklist for critical flows.
- Optional tooling: PHPUnit, PHPStan, CS-Fixer, Deptrac when available.
- Mandatory smoke test checklist: install succeeds, uninstall succeeds, admin pages load, component renders, SEF routes resolve, permissions enforced, no PHP errors in logs, basic data create and read works.
- Regression minimum checklist: install and uninstall idempotent, options persistence, permissions boundaries, cache behavior by role, urlrewrite add and remove, agent execution safety, module version bump and changelog update.

## Ops and Release minimum
- Store environment-specific configuration in module settings.
- Require backups before destructive migrations.
- Use staging for verification when possible.
- Add monitoring for key failures and slow operations.
- Follow update discipline: version bump and CHANGELOG update per task.

## How to apply the profile in Codex tasks
- State "Profile: Bitrix" explicitly and include the non-negotiables.
- Include the target version and required CHANGELOG updates.
- Require smoke test steps and regression minimum.
- Note any module structure, install or uninstall, and urlrewrite changes.

Key rules to preserve:
- Smoke test is mandatory after every functional change.
- Table naming: `module_name_table_name` with module code dot replaced by `_`.
- In `install/index.php`: `PARTNER_NAME` uses the SVG below and `PARTNER_URI = https://simai.ru`.
- Module initial version on creation: `1.0.0` (SemVer).
- Regular security and performance audits; convert results into tasks and add to the roadmap.

SVG for PARTNER_NAME (use verbatim):
```xml
<svg xmlns="http://www.w3.org/2000/svg" width="89" height="30" fill="none"><path fill="#E81123" fill-rule="evenodd" d="m0 18.007 7.048-6.993 2.29 2.272-4.758 4.721 4.758 4.72L7.048 25 0 18.007Z" clip-rule="evenodd"/><path fill="#221F20" d="M29.275 6.93c0 1.066-.874 1.93-1.952 1.93a1.94 1.94 0 0 1-1.952-1.93A1.94 1.94 0 0 1 27.323 5c1.078 0 1.952.864 1.952 1.93ZM50.57 24.717v-7.612c0-1.646-1.352-2.982-3.017-2.982-1.665 0-3.016 1.336-3.016 2.982v7.612h-3.194v-7.612c-.002-1.644-1.353-2.979-3.017-2.979-1.665 0-3.016 1.337-3.016 2.983v7.608h-3.196l.002-13.467h3.194v.771c.822-.703 1.922-1.053 3.016-1.053 1.83 0 3.475.784 4.612 2.03a6.227 6.227 0 0 1 4.615-2.033c3.428 0 6.21 2.751 6.21 6.14v7.612H50.57ZM28.92 11.246h-3.194v13.47h3.194v-13.47Z"/><path fill="#221F20" fill-rule="evenodd" d="M66.894 23.573c-.836.802-2.462 1.427-3.903 1.427-3.918 0-7.098-3.144-7.098-7.017 0-3.874 3.18-7.018 7.098-7.018 1.441 0 2.854.636 3.903 1.438v-1.158h3.195v13.471h-3.195v-1.143Zm.142-5.59c0-2.13-1.749-3.86-3.903-3.86-2.155 0-3.904 1.73-3.904 3.86s1.749 3.86 3.904 3.86c2.154 0 3.903-1.73 3.903-3.86Z" clip-rule="evenodd"/><path fill="#221F20" d="M76.477 11.246h-3.194v13.47h3.194v-13.47ZM74.88 8.86a1.941 1.941 0 0 0 1.951-1.93c0-1.066-.874-1.93-1.951-1.93a1.94 1.94 0 0 0-1.952 1.93 1.94 1.94 0 0 0 1.952 1.93ZM11.886 22.53c1.453 1.717 3.893 2.47 5.746 2.47 1.617 0 2.897-.384 3.84-1.15.943-.768 1.415-1.807 1.415-3.117 0-1.384-.613-2.549-1.863-3.242-.643-.357-2.283-.846-3.221-1.127l-.314-.094a6.669 6.669 0 0 0-.053-.016c-.522-.156-1.847-.553-1.81-1.387.031-.71.78-1.095 1.992-1.095.89 0 2.267.271 3.177 1.46l2.021-1.965c-.866-1.118-2.334-2.302-5.111-2.302-1.059 0-2.39.201-3.162.716-1.202.802-1.949 1.806-1.949 3.438 0 1.086.679 2.345 1.863 3.018.76.432 2.55 1.05 3.752 1.39.905.254 1.683.633 1.646 1.459-.037.822-1.093 1.322-2.166 1.277-2.015-.085-3.3-1.155-3.782-1.698l-2.021 1.965Z"/><path fill="#E81123" fill-rule="evenodd" d="m89 18.007-7.048-6.993-2.29 2.272 4.757 4.721-4.757 4.72L81.952 25 89 18.007Z" clip-rule="evenodd"/></svg>
```xml
