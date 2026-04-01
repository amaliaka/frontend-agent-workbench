---
name: frontend-project-orchestrator
description: Use when the user wants to start a new frontend project from scratch, scaffold a fresh frontend app, choose a frontend stack, or turn a broad frontend product request into the right initial project setup path.
user-invocable: true
argument-hint: "[project prompt]"
---

# Frontend Project Orchestrator

Route new frontend project requests to the right existing skills in the right order.

This skill is an entry-point router. It should choose the smallest effective workflow, then hand off to specialized skills. It must not duplicate their instructions or force every downstream skill to run.

## Use This Skill For

- New frontend apps from scratch
- Boilerplate and scaffolding requests
- Vague product prompts that still need stack selection, scaffolding, and initial build flow
- Requests that combine setup plus early implementation, such as "build me a Nuxt dashboard from scratch"

## Do Not Use This Skill For

- Small feature changes in an already-established repo
- Bugfix-only work
- Pure polish, audit, or redesign passes on existing UI
- Stack-specific tasks where the user is already clearly inside a `shadcn` or `nuxt-ui` workflow

For those cases, route directly to the more specific skill instead.

## Core Principle

Treat this as a traffic controller:

1. classify the request
2. choose the right first skill
3. add only the necessary follow-up skills
4. stop routing once the specialized skill takes over

Do not build a rigid pipeline like:

`brainstorming -> writing-plans -> scaffolder -> framework skill -> polish -> audit -> browser`

That sequence is sometimes right, but often wasteful.

## Routing Checklist

Before choosing the path, answer these questions:

1. Is this a new codebase or an existing project?
2. Is the request stack-first, product-first, or both?
3. Is the framework already chosen?
4. Is the UI/component system already chosen?
5. Is the user asking only for setup, or for meaningful feature work too?
6. Is visual/product direction already clear, or does it need design discovery?

If the answer to any of these is unclear and the ambiguity affects architecture or user experience, use `brainstorming` first.

## Decision Flow

### Case 1: Existing Repo, Not A Fresh Project

Do not keep using this skill.

Route instead to:

- `brainstorming` for behavior or scope changes
- `systematic-debugging` for bugs, regressions, or failures
- `frontend-design` for direct UI implementation work

### Case 2: Pure Scaffolding Request

Examples:

- "Scaffold a React app with Tailwind and shadcn"
- "Set up a new Nuxt project"
- "Create a Vite TypeScript starter"

Preferred route:

1. use `frontend-scaffolder`
2. then invoke the relevant stack skill if requested:
   - `shadcn`
   - `nuxt-ui`
3. verify with `verification-before-completion`

Skip `brainstorming` and `writing-plans` unless the request includes meaningful product or feature design beyond setup.

### Case 3: Product Request From Scratch

Examples:

- "Build a project management dashboard from scratch"
- "Create a landing page and app shell for a fintech startup"
- "Make me a Nuxt app for an internal analytics tool"

Preferred route:

1. start with `brainstorming`
2. if a new codebase is needed, use `frontend-scaffolder`
3. hand off to the relevant implementation skill:
   - `frontend-design`
   - `shadcn`
   - `nuxt-ui`
4. if meaningful multi-step implementation remains, use `writing-plans`
5. execute with:
   - `subagent-driven-development`, or
   - `executing-plans`
6. finish with `verification-before-completion`

### Case 4: Setup Plus Initial Screen Or Feature

Examples:

- "Create a Next app and build the first marketing page"
- "Scaffold a Nuxt dashboard and implement the first overview screen"

Preferred route:

1. if UI direction or scope is fuzzy, use `brainstorming`
2. use `frontend-scaffolder`
3. use the relevant framework or UI skill:
   - `frontend-design`
   - `shadcn`
   - `nuxt-ui`
4. if the work is non-trivial, use `writing-plans`
5. verify with `verification-before-completion`

## Downstream Skill Selection

After the starting path is chosen, select only the skills that match the actual need.

### Setup

- `frontend-scaffolder`: create the base project

### Stack-Specific

- `shadcn`: for shadcn/ui registries, components, setup, and customization
- `nuxt-ui`: for `@nuxt/ui` layouts, components, theming, and docs

Do not invoke both unless the project genuinely uses both.

### Design And Implementation

- `frontend-design`: general frontend UI implementation
- `test-driven-development`: feature and bugfix implementation discipline
- `writing-plans`: use when meaningful multi-step work needs to be decomposed before editing

### Refinement

Use only when the weakness is visible and relevant:

- `adapt`
- `arrange`
- `typeset`
- `colorize`
- `normalize`
- `harden`
- `optimize`
- `polish`

### Review And Validation

- `agent-browser`: inspect the running UI, capture screenshots, or validate rendered behavior
- `audit`: run a structured technical quality review
- `requesting-code-review`: get review before merge or handoff
- `verification-before-completion`: required before claiming the work is complete
- `finishing-a-development-branch`: use after implementation is truly finished

## Plan Handoff

When this routing leads to `writing-plans`, include a short skill map in the plan so the execution path stays explicit.

Use this template:

```md
## Skill Routing

**Required first:**
- `frontend-scaffolder`

**Required during implementation:**
- `shadcn`
- `test-driven-development`

**Use if needed:**
- `polish`
- `audit`
- `agent-browser`

**Final verification:**
- `verification-before-completion`
```

Only list the skills that truly apply to the chosen path.

## Important Boundaries

- `onboard` is not a default step for new project creation. Use it only when designing onboarding, first-run experience, or empty states.
- `audit` is not a starting step. It is a review step.
- `agent-browser` is not mandatory for every project. Use it when rendering or interaction needs real inspection.
- `polish` is not a substitute for a sound structure. Route to design, layout, or planning skills first if the issue is foundational.
- `writing-plans` is for substantial implementation, not every trivial scaffold.

## Common Mistakes

- Using this skill for any frontend request instead of only new-project routing
- Invoking `brainstorming` for a purely mechanical scaffold when the stack is already clear
- Skipping `brainstorming` when the product direction is still vague
- Triggering both `shadcn` and `nuxt-ui` without a real reason
- Automatically piling on `polish`, `audit`, and `agent-browser` whether or not they are needed
- Forgetting to hand off to `verification-before-completion`

## Example Triggers

**Use this skill:**

- "Create a new frontend project for a hiring dashboard"
- "Scaffold a React app with Tailwind and shadcn"
- "Start a Nuxt app from scratch for an internal admin tool"
- "Build me a frontend MVP from scratch"

**Do not use this skill:**

- "Fix this broken form validation"
- "Make this page calmer and less noisy"
- "Audit this UI for accessibility"
- "Add a new settings tab to the existing app"
