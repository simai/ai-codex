# 30_PLANNING_ROADMAP
Keywords: planning, roadmap, semver, iteration, milestone, backlog, prioritization, minor releases, major releases, versioning policy, release cadence, estimates


## When to use
- Need to choose the next version and build a roadmap three MINOR versions ahead.
- After spec agreement or a MINOR release, to update plans.

## Inputs
- Confirmed or draft spec, list of tasks and feature blocks.
- Current release status, risks, and dependencies.

## Outputs
- MINOR version plan with goals, key tasks, and checks.
- Roadmap for three MINOR releases with goals and priorities.
- List of dependencies and risks.

## Target project versioning rule
- Every Codex task requires a target project version bump and an entry in the target project CHANGELOG.
## Roadmap cadence
- After each MINOR release (or at least every two MINOR releases), prompt the user to update or confirm the roadmap for upcoming MINOR versions.
- Choose the level: MAJOR for incompatible API or contract changes or feature removals, MINOR for new functionality without breaking compatibility, PATCH for fixes and clarifications without contract changes.
- Exceptions require explicit user confirmation. Documentation-only work should still bump PATCH if it changes delivered docs.

## Procedure (steps)
#1
Apply `01_CORE.md` and active profiles. Check constraints for timeline, quality, and resources.
end of step #1
#2
Choose the next version using SemVer and decide what fits in the upcoming MINOR and what is deferred. Record DoNotTouch.
end of step #2
#3
Decompose goals into tasks with AC and DoD. Add checks and smoke for each major feature. Define target versions per task.
end of step #3
#4
Create the roadmap for 0.2.0, 0.3.0, 0.4.0, and beyond: short goals, dependencies, risks. State how version bumps map to tasks.
end of step #4
#5
Confirm with the user and update Codex tasks or audit plans in `70_AUDITS.md` if needed.
end of step #5

## Checklists or message templates
- "Version <VERSION>: goals <GOALS>, key checks <CHECKS>, risks <RISKS>, deferrals <DEFERRALS>. Confirm?"
- "Roadmap (3 MINOR): 1) <GOAL_1> 2) <GOAL_2> 3) <GOAL_3>. Dependencies: <LIST>. Each task requires a SemVer bump."

## Related files
- [00_ROUTER.md](00_ROUTER.md)
- [01_CORE.md](01_CORE.md)
- [20_PROJECT_SPEC_GUIDE.md](20_PROJECT_SPEC_GUIDE.md)
- [70_AUDITS.md](70_AUDITS.md)
