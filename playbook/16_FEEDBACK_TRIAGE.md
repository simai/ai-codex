# 16_FEEDBACK_TRIAGE
Keywords: feedback triage, bug report intake, ux issues, ui issues, visual issues, backlog, prioritization, severity, iteration gate, fix-first, retest checklist, clarification questions

Goal: prevent repeated re-testing of the same problems by forcing a single source of truth for user feedback and a fix-first loop.

## When to use
- The user reports test results, bugs, UX/UI problems, visual glitches, or inconsistencies.
- The user says “it still doesn’t work / same issue again”.
- Any time the assistant might lose track of earlier feedback.

## Inputs
- User message(s) describing issues, plus screenshots/logs when available.
- Current “Issue Log” snapshot from the assistant (if already started).
- Active profile (Bitrix, etc.) and the current iteration goal.

## Outputs
- Updated Issue Log (single source of truth) with:
  - Categories (functionality / UI / UX / visual / performance / security / l10n / docs / other)
  - Severity and priority
  - Status and verification state
  - Clarifying questions (only where needed)
- A prioritized fix plan (1–3 iterations) that resolves all user-reported issues before new functionality.
- A focused re-test checklist for the user that avoids re-checking unchanged areas.

## Non-negotiables
- Every user-reported issue must be captured in the Issue Log.
- Do NOT move to new features while the Issue Log has OPEN items, unless the user explicitly defers specific issues.
- If the user defers an issue, record it as DEFERRED with a reason and an explicit user confirmation.
- Never mark an issue “Verified” unless the user confirms it or there is explicit evidence (logs/screenshots) that it is fixed.

## Severity and priority rules
Use both a severity and a priority (they are related but not identical):

- Severity:
  - S0 Blocker: prevents use of core flow, data loss, security vulnerability, fatal errors.
  - S1 Major: breaks important flow, admin page unusable, incorrect results.
  - S2 Minor: partial malfunction, workaround exists.
  - S3 Cosmetic: visual/wording/layout only.
  - S4 Enhancement: improvement idea, not a defect.

- Priority:
  - P0: must be fixed now (all S0, security, data loss).
  - P1: fix in the next iteration (most S1).
  - P2: schedule soon (some S2).
  - P3: later (S3/S4).

Default ordering: P0 → P1 → P2 → P3.

## Procedure (steps)
#1
Apply `01_CORE.md`, the active profile, and `15_ITERATION_PROTOCOL.md`.
If the user message is test feedback, treat this as a triage phase (analysis). Do NOT emit a Codex task in the same reply.
end of step #1

#2
Parse the user feedback into atomic issues (split combined messages). For each issue, capture:
- short title
- category
- expected vs actual
- steps to reproduce (if unknown, ask)
- environment (Bitrix version, browser, role, etc.) only if relevant
end of step #2

#3
De-duplicate: merge identical issues, keep the earliest ID, and record duplicates as references.
end of step #3

#4
Assign severity + priority, then produce a fix plan:
- Iteration 1: all P0/P1
- Iteration 2: remaining P1/P2
- Iteration 3: P2/P3 or deferred
Do not include new features until the backlog is empty or the user explicitly defers items.
end of step #4

#5
Ask clarifying questions ONLY for issues that cannot be actioned safely. If the user does not know, propose 2–3 solution options:
- Option A: safest, minimal change
- Option B: best UX
- Option C: fastest
Recommend one default option with rationale.
end of step #5

#6
Provide a focused re-test checklist mapped to issue IDs. Avoid asking the user to re-test unrelated areas.
end of step #6

## Issue Log format (mandatory)
Maintain a compact Issue Log in every reply after triage starts. Keep it short but stable.

Mini-ritual rule (mandatory):
- The Issue Log snapshot MUST be the final section of the assistant reply (a "footer"), after plans and questions.
- Title: "Issue Log (last updated: <DATE>)".
- Keep it compact: prioritize OPEN, IN_PROGRESS, and FIXED_PENDING_VERIFY.
- Continue printing the snapshot on every assistant reply until all issues are VERIFIED or explicitly DEFERRED.

Required fields per item:
- ID (e.g., ISS-001)
- Category
- Severity / Priority
- Status: OPEN / IN_PROGRESS / FIXED_PENDING_VERIFY / VERIFIED / DEFERRED
- Summary

## Message templates
- “I captured your feedback into the Issue Log below. Please confirm: did I miss anything?”
- “To avoid you re-testing the same things, next iteration will fix issues: <IDs>. Please re-test only these steps: <CHECKLIST>.”
- “This issue is ambiguous. Question: <QUESTION>. If you’re not sure, choose: A) <A>, B) <B>, C) <C>. Recommended: <REC>.”

## Related files
- [00_ROUTER.md](00_ROUTER.md)
- [01_CORE.md](01_CORE.md)
- [15_ITERATION_PROTOCOL.md](15_ITERATION_PROTOCOL.md)
- [40_CODEX_TASKING.md](40_CODEX_TASKING.md)
- [60_TESTING_REGRESSION.md](60_TESTING_REGRESSION.md)
- [TEMPLATES.md](TEMPLATES.md)
