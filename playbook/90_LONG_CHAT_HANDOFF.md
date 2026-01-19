# 90_LONG_CHAT_HANDOFF
Keywords: long chat, handoff, export chat, project summary, context snapshot, resume work, archive workflow, next iterations, state summary, requirements recap


## When to use
- Long dialogue, session change, or handoff to a new chat.
- User requests an export or state summary.

## Inputs
- Current context, decisions, open questions, active tasks.
- Confirmed ASSUMPTIONS and DoNotTouch.
- Current archive name or snapshot (see `12_ARCHIVE_PROTOCOL.md`).

## Outputs
- Project state summary using `TEMPLATES.md`.
- Current Issue Log snapshot: OPEN items, FIXED_PENDING_VERIFY items, and DEFERRED items with reasons.
- Near-term next steps and dependencies.
- Instructions for chat export and restart in a new session.
- Decision log with tradeoffs and declined options.

## Procedure (steps)
#1
Apply `01_CORE.md` and active profiles. Gather key facts: goals, done, in progress, blockers, risks, and checks. Confirm the current archive.
end of step #1
#2
Produce a state summary using the template: context, decision log (tradeoffs and declined options), open questions, next steps, links to spec, roadmap, tests, recorded ASSUMPTIONS, Issue Log snapshot, archive name with timestamp.
end of step #2
#3
Offer chat export to MD or PDF via a browser extension such as ChatGPT Exporter or equivalent. Provide the summary and archive name.
end of step #3
#4
When a new chat starts, first read the summary and confirm the archive per `12_ARCHIVE_PROTOCOL.md`, then propose 1 to 3 next steps and restart with `10_ONBOARDING.md`.
end of step #4

## Checklists or message templates
- "State summary ready: context <CONTEXT>, decisions and tradeoffs <DECISIONS>, open questions <QUESTIONS>, next steps <NEXT_STEPS>, risks <RISKS>, checks <CHECKS>, archive <ARCHIVE_NAME>. Any corrections?"
- "Chat export: saving to MD or PDF via an extension, attaching the summary and archive name. In a new chat we start by reading the summary and confirming the archive."

## Related files
- [00_ROUTER.md](00_ROUTER.md)
- [01_CORE.md](01_CORE.md)
- [80_DOCS.md](80_DOCS.md)
- [10_ONBOARDING.md](10_ONBOARDING.md)
- [12_ARCHIVE_PROTOCOL.md](12_ARCHIVE_PROTOCOL.md)
- [TEMPLATES.md](TEMPLATES.md)
