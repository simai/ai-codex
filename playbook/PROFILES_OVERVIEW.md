# PROFILES_OVERVIEW
Keywords: profiles, overlays, platform mode, activation, detection, precedence rules, conflict handling, bitrix profile, stack selection, customization


What a profile is: an overlay on top of CORE and modules that adds domain rules, formats, and checks. A profile complements CORE and does not override it.

When to enable:
- The user explicitly requests a profile.
- Context or archive shows clear domain signals such as platform-specific folders, configs, or terminology.
- If unsure, ask the user and record ASSUMPTIONS.

How to detect from context:
- Inspect artifacts such as files, configs, dependencies, and the user request language.
- If multiple profiles are possible, ask for priority and select the primary one.

Conflict and priority rules:
1) Security and data rules
2) `01_CORE.md`
3) Active profile (`PROFILE_*.md`)
4) Situation modules (10..90)
5) Templates (`TEMPLATES.md`)

Use in Codex tasks:
- Explicitly state the active profile and its key rules in the task.
- If the profile is not confirmed, ask the user before proceeding.

## Profile detection gate (mandatory)
- For every new archive or project, you must explicitly detect and state the active profile.
- Use both:
  - Context signals (folders, configs, dependencies)
  - User language and domain terminology
- If detection is uncertain: ask targeted questions and record ASSUMPTIONS before tasking.
