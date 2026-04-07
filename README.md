# Agent Workspace

This repository is a practical workflow template for building frontend apps with AI tools.
It helps you choose the right skill quickly and move from idea to shipped UI with less back-and-forth.

## Quick Start

- New app: use [`frontend-project-orchestrator`](./.agents/skills/frontend-project-orchestrator/SKILL.md)
- New feature or behavior change: use [`brainstorming`](./.agents/skills/brainstorming/SKILL.md)
- Bug or regression: use [`systematic-debugging`](./.agents/skills/systematic-debugging/SKILL.md)

## Core Skills Used Here

- Superpowers (SDLC foundation) from https://github.com/obra/superpowers
- Impeccable (UI/UX foundation) from https://github.com/pbakaus/impeccable
- Shadcn UI (component implementation) from https://github.com/shadcn/ui

## Prerequisites

- Recommended runtime: OpenCode CLI
- Model support: works with paid and free models (for example, Big Pickle)
- Git installed and configured (`git --version`)
- Node.js LTS installed (`node --version`)
- Package manager available (prefer `pnpm`; `npm` also works)
- Optional for browser-based UI QA: install `agent-browser` with `pnpm add -g agent-browser`, then run `agent-browser install`

> [!INFO]
> For brand-new projects, the workflow scaffolds the app under `apps/<project-name>` by default.
> You do not need to manually create the `apps/` directory first.

## Golden Path (New Frontend App)

`using-superpowers` -> `frontend-project-orchestrator` -> `frontend-scaffolder` -> stack skill (`shadcn` or `nuxt-ui`) -> `verification-before-completion`

## Entry Point Guide

- App setup and project bootstrap: [`frontend-project-orchestrator`](./.agents/skills/frontend-project-orchestrator/SKILL.md)
- Product direction, UX, and behavior scope: [`brainstorming`](./.agents/skills/brainstorming/SKILL.md)
- Root-cause bug investigation: [`systematic-debugging`](./.agents/skills/systematic-debugging/SKILL.md)
- General frontend implementation: [`frontend-design`](./.agents/skills/frontend-design/SKILL.md)
- Stack-specific implementation: [`shadcn`](./.agents/skills/shadcn/SKILL.md) or [`nuxt-ui`](./.agents/skills/nuxt-ui/SKILL.md)
- UI refinement and visual quality: [`arrange`](./.agents/skills/arrange/SKILL.md), [`typeset`](./.agents/skills/typeset/SKILL.md), [`colorize`](./.agents/skills/colorize/SKILL.md), [`polish`](./.agents/skills/polish/SKILL.md)
- UX and technical quality checks: [`critique`](./.agents/skills/critique/SKILL.md), [`audit`](./.agents/skills/audit/SKILL.md), [`harden`](./.agents/skills/harden/SKILL.md), [`optimize`](./.agents/skills/optimize/SKILL.md)
- Final code verification before completion: [`verification-before-completion`](./.agents/skills/verification-before-completion/SKILL.md)
- Browser flow validation and screenshot QA: [`agent-browser`](./.agents/skills/agent-browser/SKILL.md)

## Prompt Starters

- New app: "Create a new frontend app for [product] with [stack], [key pages], and [design mood]."
- Feature: "Add [feature] to [existing app], including UI states, validation, and edge cases."
- Bugfix: "Investigate and fix [bug], include root cause and verification steps."
- UI pass: "Polish this screen for hierarchy, typography, responsive behavior, and accessibility."

## What Good Output Looks Like

- Working app scaffolded and runnable
- Clear folder structure and consistent UI patterns
- Mobile and desktop layouts both usable
- Verification evidence for code quality (lint/types/tests/build)
- UI quality pass completed (visual polish + UX critique)

## Quick Verify Checklist

- Install deps: `pnpm install`
- Start dev server: `pnpm dev`
- Lint: `pnpm lint`
- Type check: `pnpm typecheck`
- Tests: `pnpm test`
- Build: `pnpm build`

## Common Recovery Routes

- Output feels generic: run `frontend-design` then `bolder` or `typeset`
- Layout breaks on mobile: run `adapt`
- UI is inconsistent: run `normalize`
- Slow or janky interactions: run `optimize`
- Unclear labels or messages: run `clarify`

## Example Flows

- Marketing site: `frontend-project-orchestrator` -> `frontend-design` -> `colorize` -> `polish`
- SaaS dashboard: `frontend-project-orchestrator` -> `shadcn` -> `arrange` -> `audit`
- Existing app refresh: `brainstorming` -> `frontend-design` -> `typeset` -> `critique` -> `verification-before-completion`

## Reference

- [`.agents/PLAYBOOK.md`](./.agents/PLAYBOOK.md): end-to-end workflow
- [`.agents/skills/README.md`](./.agents/skills/README.md): full skill catalog
- [`.agents/skills/`](./.agents/skills/): skill definitions
