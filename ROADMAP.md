# ROADMAP

## 0.5.0 — Bitrix profile expansion
- Expand Bitrix module rules: structure, install and uninstall, components, admin, SEF, security, performance
- Define testing minimum and ops or release baseline for Bitrix modules
- Add checklist for applying the Bitrix profile in Codex tasks

## 0.6.0 — additional profiles and improved routing
- Implement iteration protocol (analysis-first gating) so review/spec and Codex tasks are separate turns.
- Add profile-specific compliance gates to diff-first review (starting with Bitrix: admin/proxy + localization).
- Add profiles for Laravel, Node.js, Python
- Update routing for new profiles and scenarios
- Expand priority and conflict rules
- Refine profile detection via archive context

## 0.7.0 — quality metrics and rituals
- Add measurable agent-flow metrics and quality indicators
- Formalize handoff rituals between chats and histories
- Add guidance for regular retrospectives and audits
- Update summary templates with measurement focus
- Add a fix-first feedback triage loop with an Issue Log to prevent repeated re-testing