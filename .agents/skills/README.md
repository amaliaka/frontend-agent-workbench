# Skills Index

This directory is the skill catalog.

Keep the skill folders in a flat namespace:

- `.agents/skills/<skill-name>/SKILL.md`
- put reference files, scripts, and assets inside the same skill folder
- avoid adding category subfolders above skills unless you also update the discovery mechanism

Use this file to find the right skill quickly. Use [`../PLAYBOOK.md`](../PLAYBOOK.md) for the recommended end-to-end workflow.

## Start Here

If you are not sure what to use:

1. Start with `using-superpowers`.
2. If you are creating or changing behavior, use `brainstorming` before implementation.
3. If you have an approved design or clear requirements, use `writing-plans`.
4. If you are fixing broken behavior, use `systematic-debugging`.
5. Before claiming success, use `verification-before-completion`.

## Quick Routing

- New frontend project from scratch: `frontend-project-orchestrator`
- New feature or behavior change: `brainstorming` -> `writing-plans` -> implementation skills
- Bugfix or flaky test: `systematic-debugging` -> `test-driven-development`
- New frontend app or boilerplate: `frontend-project-orchestrator` -> `frontend-scaffolder`
- Nuxt UI work: `nuxt-ui`
- shadcn work: `shadcn`
- Accessibility or quality review: `audit`
- Final refinements: `polish`
- Need a skill you do not have: `find-skills`

## Skill Groups

### Foundations And Process

- `using-superpowers`: mandatory startup skill for checking and invoking relevant skills first.
- `frontend-project-orchestrator`: preferred entry point for new frontend projects that need the right sequence of discovery, scaffolding, stack-specific work, planning, and verification.
- `brainstorming`: use before creative work, feature design, component design, or behavior changes.
- `writing-plans`: turn approved requirements into an implementation plan.
- `executing-plans`: execute a written plan in-session with checkpoints.
- `subagent-driven-development`: execute written plans with task-by-task delegation.
- `dispatching-parallel-agents`: split independent workstreams that can safely run in parallel.
- `using-git-worktrees`: isolate larger feature work in a separate worktree.
- `verification-before-completion`: verify with real commands before saying work is done.
- `finishing-a-development-branch`: choose how to wrap up after implementation and verification.

### Frontend Design And UX

- `frontend-design`: build distinctive, production-grade interfaces with strong design quality.
- `arrange`: improve layout, spacing, composition, and visual hierarchy.
- `typeset`: improve typography, readability, and text hierarchy.
- `colorize`: add more intentional and expressive color.
- `animate`: add purposeful motion and micro-interactions.
- `delight`: add personality and moments of joy.
- `bolder`: increase visual impact when a design feels too safe.
- `quieter`: reduce visual intensity when a design feels too loud.
- `distill`: simplify and remove unnecessary complexity.
- `polish`: final detail pass for alignment, consistency, and finish.
- `adapt`: make layouts work across breakpoints and devices.
- `normalize`: realign UI to an existing design system.
- `extract`: turn repeated patterns into reusable components and tokens.
- `clarify`: improve labels, instructions, and UX copy.
- `onboard`: improve onboarding flows, empty states, and first-run experience.
- `critique`: review a design from a UX perspective and identify weaknesses.
- `teach-impeccable`: establish persistent design context once for the project.

### Production Readiness And Quality

- `harden`: handle error states, i18n, overflow, and edge cases.
- `optimize`: improve UI performance, loading, animation smoothness, and bundle weight.
- `audit`: run a structured quality review across accessibility, performance, theming, and responsiveness.
- `test-driven-development`: implement features and bugfixes test-first.
- `systematic-debugging`: investigate failures methodically before proposing fixes.
- `requesting-code-review`: ask for review before merge or handoff.
- `receiving-code-review`: validate and interpret review feedback before applying it.

### Framework And Tooling Skills

- `frontend-scaffolder`: scaffold a new frontend project or boilerplate.
- `shadcn`: work with shadcn/ui components, registry items, and customization.
- `nuxt-ui`: build with `@nuxt/ui` v4 and use its docs and patterns effectively.
- `agent-browser`: automate browser actions, testing, screenshots, and page interaction.

### Meta Skills

- `find-skills`: discover installable skills for missing capabilities.
- `skill-creator`: create, improve, benchmark, and package skills.

## Common Flows

### New Feature

`using-superpowers` -> `brainstorming` -> `writing-plans` -> one of `frontend-design` / `nuxt-ui` / `shadcn` -> `test-driven-development` -> `requesting-code-review` -> `verification-before-completion`

### Bugfix

`using-superpowers` -> `systematic-debugging` -> `test-driven-development` -> implementation skill if needed -> `verification-before-completion`

### UI Refinement

Start with `frontend-design`, then layer in the most relevant refinements:

- structure: `arrange`, `distill`, `normalize`
- expression: `typeset`, `colorize`, `bolder`, `quieter`
- interaction: `animate`, `delight`
- shipping: `adapt`, `harden`, `optimize`, `polish`

### New Project

`using-superpowers` -> `frontend-project-orchestrator` -> chosen route such as `brainstorming` and/or `frontend-scaffolder` -> framework-specific skill -> `writing-plans` for substantial follow-up work

## Notes

- Prefer the smallest set of skills that fully covers the task.
- Use process skills first. Use implementation skills second.
- When multiple visual refinement skills apply, pick the one that matches the main problem instead of stacking all of them by default.
- If a request is broad, break it into phases rather than trying to trigger everything at once.
