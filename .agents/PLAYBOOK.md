# Agent Playbook

This file is the workflow guide for this skill set.

Use [`skills/README.md`](./skills/README.md) when you need to find a specific skill quickly. Use this file when you want to know the best flow from idea to implementation to verification.

## Default Flow

For most frontend work, follow this sequence:

1. `using-superpowers`
2. choose the correct entry skill
3. plan if needed
4. implementation skill
5. refinement skills
6. review and verification
7. branch completion

In short:

`idea -> design -> plan -> build -> refine -> review -> verify -> finish`

## Phase 1: Intake

Start by deciding what kind of request you are handling.

- New feature, component, page, or behavior change: go to design first.
- Bug, regression, flaky behavior, or failing tests: go to debugging first.
- New app or boilerplate request: start with `frontend-project-orchestrator`.
- Review, polish, or accessibility pass: go straight to quality and refinement.

For new app requests, default to scaffolding-first unless feature/product design is explicitly the primary goal.

Primary skills:

- `using-superpowers`
- `frontend-project-orchestrator`
- `brainstorming`
- `systematic-debugging`
- `frontend-scaffolder`

## Phase 2: Design

Use this phase when the request changes behavior, structure, UI, or scope.

For net-new frontend projects, prefer `frontend-project-orchestrator` first. It decides whether this phase should begin with `brainstorming`, `frontend-scaffolder`, or both.

For setup-only scaffolding requests, skip design discovery and route directly to `frontend-scaffolder`.

Recommended flow:

1. `brainstorming`
2. present options and get approval
3. write the design/spec if the task is non-trivial
4. `writing-plans`

Use this phase to answer:

- what are we building?
- what is in scope?
- what is the recommended approach?
- which files or systems are likely to change?

## Phase 3: Planning

Once the direction is approved, create the implementation path.

Use `writing-plans` once per approved scope. Re-run only if requirements or scope materially change.

Recommended flow:

1. `writing-plans`
2. choose execution mode:
   - `subagent-driven-development` for task-by-task delegation
   - `executing-plans` for in-session execution
3. use `using-git-worktrees` if the work needs isolation

Good plans should define:

- the target files or areas of the codebase
- the testing strategy
- the order of work
- verification steps

For workflows that depend on multiple downstream skills, include a short `Skill Routing` section in the plan so the execution path stays explicit.

## Phase 4: Build Or Generate

Pick the most specific implementation skill for the job.

### UI Build Paths

- New frontend projects from scratch: `frontend-project-orchestrator`
- General frontend implementation: `frontend-design`
- Nuxt UI projects: `nuxt-ui`
- shadcn/ui projects: `shadcn`
- New project setup: `frontend-scaffolder`

### Engineering Discipline

- New feature or bugfix: `test-driven-development`
- Unexpected failure or regression: `systematic-debugging`
- Parallel independent work: `dispatching-parallel-agents`

Rule of thumb:

- process skills decide how to work
- implementation skills decide what patterns and tooling to use

## Phase 5: Refine

After the main implementation works, improve the experience intentionally instead of randomly piling on tweaks.

### Structure And Clarity

- `arrange`
- `distill`
- `normalize`
- `extract`
- `clarify`
- `onboard`

### Visual Expression

- `typeset`
- `colorize`
- `bolder`
- `quieter`
- `delight`
- `animate`
- `overdrive`

### Shipping Readiness

- `adapt`
- `harden`
- `optimize`
- `polish`

Use only the skills that match the actual weakness you see.

## Phase 6: Review

Before wrapping up, run the right review path.

- Need design feedback: `critique`
- Need technical quality review: `audit`
- Need code review before merge: `requesting-code-review`
- Need to handle incoming review comments: `receiving-code-review`

A helpful mental model:

- `critique` asks whether the experience is good
- `audit` asks whether the implementation is sound
- code review skills ask whether the change is ready to merge

## Phase 7: Verify And Finish

Do not stop at "looks good."

Recommended flow:

1. `verification-before-completion`
2. `finishing-a-development-branch`

Use these to confirm:

- the implementation actually works
- tests and checks were run
- the branch is ready for the next handoff step

## Common Playbooks

### 1. New Feature

1. `using-superpowers`
2. `brainstorming`
3. `writing-plans`
4. `test-driven-development`
5. implementation skill: `frontend-design` / `nuxt-ui` / `shadcn`
6. refinement skills as needed
7. `requesting-code-review`
8. `verification-before-completion`
9. `finishing-a-development-branch`

### 2. Bugfix

1. `using-superpowers`
2. `systematic-debugging`
3. `test-driven-development`
4. targeted implementation skill if needed
5. `verification-before-completion`
6. `requesting-code-review` for non-trivial fixes

### 3. New Frontend Project

1. `using-superpowers`
2. `frontend-project-orchestrator`
3. follow the chosen route:
   - `frontend-scaffolder` for setup-only scaffolding (including inside non-empty repos, target `apps/<project-name>` by default)
   - `brainstorming` if the product or UI direction is still fuzzy
   - combine both only when setup plus product design is requested
4. framework-specific skill: `nuxt-ui` or `shadcn` if relevant
5. `writing-plans` for the first substantial feature set
6. `verification-before-completion`

### 4. UI Polish Pass

1. `using-superpowers`
2. `frontend-design` or `critique`
3. apply the most relevant refinement skills
4. `adapt`
5. `harden`
6. `polish`
7. `audit` if accessibility or performance matters
8. `verification-before-completion`

### 5. Skill Maintenance

1. `using-superpowers`
2. `skill-creator`
3. `find-skills` if you need outside capabilities

## Minimal Decision Guide

If you only remember one thing, use this:

- changing behavior: `brainstorming`
- fixing failures: `systematic-debugging`
- starting a project from scratch: `frontend-project-orchestrator`
- planning work: `writing-plans`
- building UI: `frontend-design`
- scaffolding only: `frontend-scaffolder`
- framework-specific work: `nuxt-ui` or `shadcn`
- final checks: `verification-before-completion`

## Maintenance Rules For This Repo

- Keep skill folders flat under `.agents/skills/`.
- Keep this playbook procedural.
- Keep `skills/README.md` index-oriented.
- Add new skills to both docs only where they improve discoverability.
- When a new skill overlaps with an existing one, document the difference in trigger conditions instead of duplicating workflow text.
