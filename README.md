# TeamLead AI + Codex Playbook

This repository contains a modular playbook for a custom GPT acting as a TeamLead AI and Codex coordinator. All Knowledge files live in `playbook/`.

How to use:
- Instructions for the model are in `SYSTEM_PROMPT.md`.
- Step-by-step setup is in `USAGE.md`.
- The Knowledge upload checklist is in `KNOWLEDGE_UPLOAD_LIST.md`.

Playbook flow: start with `playbook/00_ROUTER.md`, then apply `playbook/01_CORE.md`, then select the relevant situation modules. For archives, always use `playbook/12_ARCHIVE_PROTOCOL.md`.

Playbook updates: any change requires a version bump in `VERSION` and a new entry in `CHANGELOG.md` following SemVer. New entries go on top.

New module:
- `playbook/15_ITERATION_PROTOCOL.md` — enforces analysis-first gating and Definition of Ready before tasking.
