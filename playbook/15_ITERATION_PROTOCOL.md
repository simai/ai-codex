# 15_ITERATION_PROTOCOL
Keywords: iteration protocol, analysis-first, gating, two-phase flow, definition of ready, review gate, codex task gate

Goal: enforce a reliable loop so Codex execution is always bounded by a spec/contract and a review gate.

## Non-negotiables
- One response = one phase. Do NOT mix these in the same reply:
  - Spec / discovery (questions + assumptions + draft spec)
  - Archive / diff review (findings + decision)
  - A Codex task (single code block)
- A Codex task may be produced ONLY when:
  - the user explicitly asks for a Codex task in that message, AND
  - the Definition of Ready (DoR) is satisfied.
- When an archive is received, ALWAYS run `50_REVIEW_DIFF_FIRST.md` first and provide a decision:
  - Accept / Request changes / Split scope
  - Then propose next steps (but do not emit a Codex task in that reply).

## Definition of Ready (DoR) for a Codex task
A task is "ready" only if all are true:
- Active profile is selected (or an explicit ASSUMPTION is recorded with rationale).
- Scope and out-of-scope are written down.
- Acceptance Criteria exist and are testable.
- Checks or tests exist (at minimum: smoke steps; ideally regression items).
- DoNotTouch and constraints are explicit.
- Target version is selected (SemVer) and CHANGELOG update requirement is stated.
- For archive-based work: the most recent review decision is "Accept" OR the task is explicitly a fix-only iteration addressing review findings.

## Phase outputs
Phase A — Discovery / Spec:
- Output: clarifying questions, explicit ASSUMPTIONS, draft spec (or delta spec), risks, and a proposed next step (planning or review).
- No Codex task.

Phase B — Codex Task:
- Output: one (1) Codex task code block following `40_CODEX_TASKING.md`.
- No review content.

Phase C — Review (Diff-first):
- Output: changed files summary, requirement-to-change mapping, compliance gates, risks, test status, and decision.
- No Codex task.

Phase D — Roadmap / Next MINOR:
- Output: next 1–3 iterations, audit recommendations, regression updates.
- No Codex task unless the user explicitly asks AND DoR is satisfied.

## Related files
- [00_ROUTER.md](00_ROUTER.md)
- [01_CORE.md](01_CORE.md)
- [20_PROJECT_SPEC_GUIDE.md](20_PROJECT_SPEC_GUIDE.md)
- [40_CODEX_TASKING.md](40_CODEX_TASKING.md)
- [50_REVIEW_DIFF_FIRST.md](50_REVIEW_DIFF_FIRST.md)
