# 00_ROUTER
Keywords: router, routing, situation detection, decision tree, module selection, priority rules, conflict resolution, missing information, assumptions, profiles, knowledge retrieval


Goal: quickly select the right modules and profiles for the user situation while keeping a consistent process.

Rule: always apply `01_CORE.md` regardless of situation.

Situations and routing:

| Situation | Signals | Files to use | Output to provide |
|---|---|---|---|
| New project or vague idea | No code or clear plan, needs a starting point | [01_CORE.md](01_CORE.md), [10_ONBOARDING.md](10_ONBOARDING.md), [20_PROJECT_SPEC_GUIDE.md](20_PROJECT_SPEC_GUIDE.md), [PROFILES_OVERVIEW.md](PROFILES_OVERVIEW.md) | Short status summary, clarifying questions, explicit ASSUMPTIONS, next steps proposal |
| Existing project archive (brownfield) | Archive or code link received, needs assessment | [01_CORE.md](01_CORE.md), [10_ONBOARDING.md](10_ONBOARDING.md), [12_ARCHIVE_PROTOCOL.md](12_ARCHIVE_PROTOCOL.md), [50_REVIEW_DIFF_FIRST.md](50_REVIEW_DIFF_FIRST.md), [PROFILES_OVERVIEW.md](PROFILES_OVERVIEW.md) | Summary of artifacts, risk list, missing data questions, proposed route |
| Requirements or project spec needed | Need a specification and boundaries | [01_CORE.md](01_CORE.md), [20_PROJECT_SPEC_GUIDE.md](20_PROJECT_SPEC_GUIDE.md), [30_PLANNING_ROADMAP.md](30_PLANNING_ROADMAP.md), [TEMPLATES.md](TEMPLATES.md) | Structured spec draft, missing info questions, agreed scope and out-of-scope |
| Codex task formulation needed | Need to craft a task for Codex | [01_CORE.md](01_CORE.md), [40_CODEX_TASKING.md](40_CODEX_TASKING.md), [PROFILES_OVERVIEW.md](PROFILES_OVERVIEW.md), [TEMPLATES.md](TEMPLATES.md) | Self-contained task in one code block, checks and smoke, DoNotTouch list and expected response |
| Codex result or new archive requires review | Diff or archive needs quality review | [01_CORE.md](01_CORE.md), [12_ARCHIVE_PROTOCOL.md](12_ARCHIVE_PROTOCOL.md), [50_REVIEW_DIFF_FIRST.md](50_REVIEW_DIFF_FIRST.md), [60_TESTING_REGRESSION.md](60_TESTING_REGRESSION.md) | Changed files list, risk notes, decision to accept or request changes or split scope, test plan |
| Next MINOR planning and roadmap | Need goals for upcoming versions | [01_CORE.md](01_CORE.md), [30_PLANNING_ROADMAP.md](30_PLANNING_ROADMAP.md), [70_AUDITS.md](70_AUDITS.md) | MINOR goals, decomposition, updated roadmap and dependencies, audit recommendations |
| Long chat or context handoff | Session change or handoff required | [01_CORE.md](01_CORE.md), [90_LONG_CHAT_HANDOFF.md](90_LONG_CHAT_HANDOFF.md), [12_ARCHIVE_PROTOCOL.md](12_ARCHIVE_PROTOCOL.md), [TEMPLATES.md](TEMPLATES.md) | State summary, confirmed next steps, instructions for new chat and current archives |
| Archive packaging or transfer | Need to package and hand over safely | [01_CORE.md](01_CORE.md), [12_ARCHIVE_PROTOCOL.md](12_ARCHIVE_PROTOCOL.md), [PROFILES_OVERVIEW.md](PROFILES_OVERVIEW.md) | Archive with unique name and exclusions, safety guidance and restore notes |

Priority and conflict rules:
1) Security and data requirements override all other rules.
2) `01_CORE.md` is always mandatory.
3) Active profile (`PROFILES_OVERVIEW.md` and relevant `PROFILE_*.md`) applies on top of CORE.
4) Situation module (10..90, including `12_ARCHIVE_PROTOCOL.md`) defines the process for the context.
5) Templates (`TEMPLATES.md`) are used to format artifacts.

If information is missing, ask clarifying questions and record ASSUMPTIONS explicitly. If a required file is missing or unavailable, apply CORE and request the user to provide the missing module or clarify instructions. When working with archives, always reference `12_ARCHIVE_PROTOCOL.md` and follow its safety rules.
