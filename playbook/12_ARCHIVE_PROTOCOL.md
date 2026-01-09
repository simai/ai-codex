# 12_ARCHIVE_PROTOCOL
Keywords: archive protocol, timestamped archive, zip, exclusions, git, node_modules, vendor, secrets, env files, pii, macos, linux, powershell, handoff


## When to use
- Need to prepare, send, or receive a project archive for Codex or review.
- Need to lock down naming, exclusions, and safety rules for archiving.

## Inputs
- Project path and desired archive name.
- Exclusion list and confirmed safety constraints.
- Active profile information (if applicable).

## Outputs
- Archive with a unique name and recorded exclusions.
- Short instruction for the archive recipient.
- Confirmed list of exclusions and safety rules.

## Procedure (steps)
#1
Apply `01_CORE.md` and active profiles. Confirm the archive purpose and recipients. Verify there are no data transfer restrictions.
end of step #1
#2
Assign a unique archive name with a timestamp: `<PROJECT_NAME>_<YYYYMMDD_HHMMSS>.zip`. Store the archive outside the project folder, for example one level above the root.
end of step #2
#3
Define exclusions: `.git`, `node_modules`, `vendor`, `dist` if rebuildable, `build`, caches (`.cache`, `tmp`), system files (`.DS_Store`, `__MACOSX`), temporary files, and logs. Confirm that `.env`, secrets, private keys, and PII dumps are not included without explicit approval. Prefer `.env.example` or sanitized samples.
end of step #3
#4
Build the archive with exclusions and an external destination.
- macOS and Linux from project root:
```
TS=$(date +%Y%m%d_%H%M%S)
ARCHIVE="../<PROJECT_NAME>_${TS}.zip"
zip -r "$ARCHIVE" . -x "*/.git/*" "*/node_modules/*" "*/vendor/*" "*/dist/*" "*/build/*" "*/tmp/*" "*/.cache/*" "*__MACOSX*" "*.DS_Store" "*.log" "*.swp" "*.tmp"
```
- Windows PowerShell from project root, ensure the destination folder exists:
```
$ts = Get-Date -Format "yyyyMMdd_HHmmss"
$archive = "..\<PROJECT_NAME>_$ts.zip"
$exclude = @('.git','node_modules','vendor','dist','build','tmp','.cache','__MACOSX','.DS_Store','*.log','*.tmp')
Get-ChildItem -Force | Where-Object { $exclude -notcontains $_.Name } | Compress-Archive -DestinationPath $archive -Force
```
end of step #4
#5
Verify archive size and contents. Confirm there are no secrets or PII. Record the exclusion list and archive path in the state summary.
end of step #5

## Checklists or message templates
- "Archive ready: name `<PROJECT_NAME>_<YYYYMMDD_HHMMSS>.zip`, stored outside the root. Exclusions: `.git`, `node_modules`, `vendor`, `dist`, `build`, caches, temporary files. Secrets and PII are excluded."
- "To reproduce the archive: use the zip command with exclusions on macOS/Linux or Compress-Archive on Windows. Any additional exclusions required?"

## Related files
- [00_ROUTER.md](00_ROUTER.md)
- [01_CORE.md](01_CORE.md)
- [10_ONBOARDING.md](10_ONBOARDING.md)
- [50_REVIEW_DIFF_FIRST.md](50_REVIEW_DIFF_FIRST.md)
- [90_LONG_CHAT_HANDOFF.md](90_LONG_CHAT_HANDOFF.md)
