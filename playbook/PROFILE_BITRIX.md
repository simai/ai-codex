# PROFILE_BITRIX
Keywords: bitrix, module structure, install uninstall, components, admin pages, sef, urlrewrite, security defaults, performance defaults, testing minimum, ops release, partner name, partner uri, versioning, audits, upload/tmp, temporary files, import export, export filename, timestamp, admin tabs, CAdminTabControl, admin ui, mail, notifications, Bitrix Mail::send, header array, Result, isSuccess, CEvent, EventMessage, diagnostics, recipients normalization, marketplace, partner_name, partner_uri, install/index.php, module constructor

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

## Module conventions
- Module ID and path: `local/modules/<MODULE_ID>/` with a clear namespace.
- Required files: `install/index.php`, `install/version.php`, `include.php`, `lang/<LANG>/` localization.
- Use `lang/<LANG>/<PATH>` placeholders when describing localization paths.
- Keep module configuration in `install` and runtime logic in module classes.
- Table naming: `module_name_table_name` with module code dots replaced by `_`.
- Initial module version on creation: `1.0.0` (SemVer).

### Partner name and URI
- `PARTNER_NAME` must be a plain text string, example: "SIMAI".
- `PARTNER_URI` must be "https://simai.ru".

### Marketplace requirement: PARTNER_NAME and PARTNER_URI
- `PARTNER_NAME` and `PARTNER_URI` must be assigned as plain strings.
- Assignment must be done inside `__construct()` in `/install/index.php`.
- Do not use constants, variables, configs, or dynamic expressions.
- Violations may cause Bitrix Marketplace rejection.

Example (correct):
```php
public function __construct()
{
    $this->PARTNER_NAME = 'SIMAI';
    $this->PARTNER_URI = 'https://simai.ru';
}
```

### Temporary files for import and export
- Temporary files created during import or export must be stored in: `/upload/tmp/<module_id>/`.
- Create the directory if missing.
- Use unique filenames to avoid collisions.
- Clean up temporary files on success and on failure.
- Do not store secrets or PII in temp files; use short retention.

### Export filename convention
- Export file name format: `<site_domain>_<export_entity>_<optional_scope>_<YYYY_MM_DD_HH_mm_ss>.<ext>`
- Sanitize `site_domain` for filesystem usage, for example replace dots with underscores.
- `export_entity` and `optional_scope` must be short, lowercase, and must not contain PII.
- Examples: `example_com_orders_full_2026_01_09_14_30_05.csv`, `store_net_products_2026_01_09_08_12_00.json`.

### Admin UI: standard Bitrix tabs and form layout
- Admin pages for settings or editing must use standard Bitrix tabs and forms (`CAdminTabControl` or equivalent).
- Layout requirement: header (navchain and title) then tabs then tab content then footer buttons.
- Do not build custom ad hoc HTML forms for typical admin edit and settings screens.

## Task Standard: Mail and Notifications (Bitrix PHP)

### A) Goal
- Compatibility with the Bitrix core, predictable behavior, and strong diagnostics.

### B) Mail::send rules (Bitrix\Main\Mail\Mail::send)
- `HEADER` must be an array only. String `HEADER` is forbidden.
- Example: `'HEADER' => ['From: noreply@site.ru']`
- Always set `CONTENT_TYPE` and `CHARSET`:
- `'CONTENT_TYPE' => 'text/plain'` (or `text/html` if required)
- `'CHARSET' => SITE_CHARSET ?: 'UTF-8'`
- `Mail::send()` can return bool or a `Result`-like object. Never cast it to bool blindly.
- If it is an object and has `isSuccess()`, use it.
- If it provides `getErrorMessages()` and or `getErrors()`, extract the most informative error text.
- If it is bool, check true or false.
- Do not swallow `Throwable` exceptions. Record them in diagnostics (log, module options, or diagnostics table).
- Sender `From` must come from settings:
- `Option::get('main', 'email_from')` and or `SITE_EMAIL`
- If empty, build `noreply@<server_name>`.
- On failure, return or record:
- attempt timestamp
- normalized recipients
- detailed error text

### C) Mail events rules (`CEvent` or `EventMessage`)
- Do not mix with `Mail::send` unless necessary.
- Prefer events for critical notifications (queue and templates), unless the task explicitly says no events.
- If the task says no events, strictly follow the `Mail::send` rules above.

### D) Recipient normalization (mandatory)
- Accept separators: comma, semicolon, spaces, line breaks.
- Output must be a unique array:
- trim
- strtolower
- `filter_var($email, FILTER_VALIDATE_EMAIL)`
- If there are no valid recipients, do not send and record a diagnostics error.

### E) Diagnostics is mandatory (traceability)
- Every notification attempt must leave a trace:
- `last_attempt_at`
- `last_success_at` (only on success)
- `last_error` (clear only on success)
- `last_recipients`
- Storage can be `Option::set(<module_id>, <name>, <value>)` or a dedicated table, depending on task requirements.

### F) No magic and scope control
- Do not add dependencies or change architecture without explicit instruction.
- Do not change unrelated business logic in notification tasks.
- Make changes minimal and localized.

### G) PHP code quality requirements
- `declare(strict_types=1)`
- PSR-12 formatting
- PHPDoc required for new or changed public methods and new private helpers, with typed `@param`, `@return`, and `@throws` when needed.
- Arrays: short syntax `[]`

### H) Delivery checklist (before closing a task)
- List changed files and what changed
- Explain how to verify (commands or admin actions)
- Explain what diagnostics will be visible and where it is stored

Critical checks (must fix)
- If you see `'HEADER' => 'From: noreply@site.ru'` as a string, fix it to an array.
- If you see `(bool)$result` or similar for `Mail::send()`, fix it to proper `Result` or bool handling.

## Install and Uninstall contract
- Install steps: register module, create database tables, add events, add agents, add urlrewrite rules, register options.
- Uninstall steps: remove agents, remove events, remove urlrewrite rules, unregister module, remove options.
- Database changes must be idempotent and safe for repeated runs.
- Provide uninstall checkboxes for data retention and respect user choice.
- If the module stores any data, uninstall must be two-step: show a first-step checkbox "Delete data" and only delete data when the user explicitly opts in.
- Install checklist: database changes idempotent, files present, events registered, agents registered, urlrewrite added, options set, rights and groups configured.
- Uninstall checklist: agents removed, events removed, urlrewrite removed, options cleaned, module unregistered.
- Keep data option: retain data tables and user content when selected, still remove agents, events, urlrewrite rules, and runtime options.

## Components and Admin pages
- Separate public components from admin pages and data access layers.
- Validate inputs and permissions for both component and admin entry points.
- Prefer admin pages as proxies to service classes, not as business logic holders.
- Proxy files under `/bitrix/admin` must include admin pages from `/local/modules/<module_id>/admin` first, then fall back to `/bitrix/modules/<module_id>/admin`.
- Admin pages must use admin prolog/epilog (`prolog_admin_before.php`, `prolog_admin_after.php`, `epilog_admin.php`) and must not include public `header.php`/`footer.php`.
- Every admin page must be attached to an admin menu section; child pages must be registered as nested (child) items under the parent menu entry that opens them.

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
- In `install/index.php`: `PARTNER_NAME` must be a plain text string, example "SIMAI", and `PARTNER_URI` must be "https://simai.ru".
- Module initial version on creation: `1.0.0` (SemVer).
- Regular security and performance audits; convert results into tasks and add to the roadmap.

## Admin/proxy publishing (portable, marketplace-friendly)
Preferred structure (keeps module clean and proxies explicit):
- Real admin page scripts: `local/modules/<MODULE_ID>/admin/*.php`
- Proxy scripts published into `/bitrix/admin/`: `local/modules/<MODULE_ID>/install/admin/*.php`

Install/uninstall rules:
- `DoInstall()` copies only `install/admin/*.php` into `/bitrix/admin/`.
- `DoUninstall()` deletes those proxy files from `/bitrix/admin/` by explicit list (never wildcard delete).

Proxy requirements:
- Must NOT hardcode `/local/...` paths.
- Must try to include the real admin page from:
  1) `/local/modules/<MODULE_ID>/admin/<page>.php`
  2) `/bitrix/modules/<MODULE_ID>/admin/<page>.php`
- Must include admin prolog/epilog and set module name:
  - `define('ADMIN_MODULE_NAME', '<MODULE_ID>');`
  - `require $_SERVER['DOCUMENT_ROOT'].'/bitrix/modules/main/include/prolog_admin_before.php';`
  - `\Bitrix\Main\Loader::includeModule('<MODULE_ID>')`
  - `require $_SERVER['DOCUMENT_ROOT'].'/bitrix/modules/main/include/epilog_admin.php';`

Template (proxy script skeleton):
```php
<?php
define('ADMIN_MODULE_NAME', '<MODULE_ID>');

require_once $_SERVER['DOCUMENT_ROOT'] . '/bitrix/modules/main/include/prolog_admin_before.php';

if (!\Bitrix\Main\Loader::includeModule('<MODULE_ID>')) {
    \CAdminMessage::ShowMessage('Module <MODULE_ID> is not installed.');
    require_once $_SERVER['DOCUMENT_ROOT'] . '/bitrix/modules/main/include/epilog_admin.php';
    return;
}

$local = $_SERVER['DOCUMENT_ROOT'] . '/local/modules/<MODULE_ID>/admin/<PAGE>.php';
$bitrix = $_SERVER['DOCUMENT_ROOT'] . '/bitrix/modules/<MODULE_ID>/admin/<PAGE>.php';
$target = file_exists($local) ? $local : $bitrix;

if (!file_exists($target)) {
    \CAdminMessage::ShowMessage('Admin page not found: <PAGE>.php');
    require_once $_SERVER['DOCUMENT_ROOT'] . '/bitrix/modules/main/include/epilog_admin.php';
    return;
}

require $target;

require_once $_SERVER['DOCUMENT_ROOT'] . '/bitrix/modules/main/include/epilog_admin.php';
```

Note: In this pattern, the real admin scripts under `module/admin/` should NOT include prolog/epilog again. They should render the page body and rely on the proxy to wrap prolog/epilog.

## Localization (mandatory)
- All UI strings in admin/menu/options/install/admin pages must be localized.
- Use `\Bitrix\Main\Localization\Loc`:
  - `Loc::loadMessages(__FILE__);`
  - `Loc::getMessage('KEY')`
- Store messages in `lang/<LANG>/<relative_path_to_file>.php`.

Minimum localization coverage:
- `install/index.php` (module name/description, install/uninstall messages)
- `admin/menu.php` (menu labels, titles)
- every admin page in `admin/*.php`
- `options.php` and any settings pages

Common failure gates:
- Hardcoded Russian/English UI strings in PHP.
- Missing `lang/ru/...` files for entry points.

Key naming suggestion:
- Prefix by module ID in uppercase with dots replaced by underscores, e.g. `SIMAI_AI_MENU_TITLE`, `SIMAI_AI_QUEUE_TITLE`.

