# Agent Workspace

This repository is organized around one question: **what skill should I start with?**
It is grounded in two core skills: **Superpowers** for SDLC workflow discipline and **Impeccable** for UI/UX quality direction.

## Core Skills Used Here

- Superpowers (SDLC foundation) from https://github.com/obra/superpowers
- Impeccable (UI/UX foundation) from https://github.com/pbakaus/impeccable
- Shadcn UI (component implementation) from https://github.com/shadcn/ui

## Prerequisites

- Recommended runtime: OpenCode CLI
- Model support: works with both paid and free models (for example, Big Pickle)
- Git installed and configured (`git --version`)
- Node.js LTS installed (`node --version`)
- Package manager available (`pnpm` or `npm`)
- Optional for browser-based UI QA: install `agent-browser` (`pnpm add -g agent-browser`) and run `agent-browser install`

## Entry Point Guide

- Building a new frontend app: [`frontend-project-orchestrator`](./.agents/skills/frontend-project-orchestrator/SKILL.md)
- Changing product behavior, UX, or scope: [`brainstorming`](./.agents/skills/brainstorming/SKILL.md)
- Fixing a bug, regression, or flaky behavior: [`systematic-debugging`](./.agents/skills/systematic-debugging/SKILL.md)
- Designing or refining UI/UX: [`frontend-design`](./.agents/skills/frontend-design/SKILL.md)
- Improving layout and hierarchy: [`arrange`](./.agents/skills/arrange/SKILL.md)
- Improving typography and readability: [`typeset`](./.agents/skills/typeset/SKILL.md)
- Improving color and visual expression: [`colorize`](./.agents/skills/colorize/SKILL.md)
- Implementing UI in a known stack: [`shadcn`](./.agents/skills/shadcn/SKILL.md) or [`nuxt-ui`](./.agents/skills/nuxt-ui/SKILL.md)
- Verifying code quality before completion: [`verification-before-completion`](./.agents/skills/verification-before-completion/SKILL.md) (tests, lint, types, build)
- Verifying UI/UX quality before completion: [`polish`](./.agents/skills/polish/SKILL.md) + [`critique`](./.agents/skills/critique/SKILL.md) (optionally [`audit`](./.agents/skills/audit/SKILL.md), [`harden`](./.agents/skills/harden/SKILL.md), and [`optimize`](./.agents/skills/optimize/SKILL.md))
- Browser-based validation and flow checks: [`agent-browser`](./.agents/skills/agent-browser/SKILL.md) (optional for interactive UI QA)

> [!INFO]
> For brand-new projects, the workflow scaffolds the app under `apps/<project-name>` by default.
> You do not need to manually create the `apps/` directory first.

## How To Use This Repo

- Start with the best entry point above.
- Follow the full workflow in [`.agents/PLAYBOOK.md`](./.agents/PLAYBOOK.md).
- Browse all available skills in [`.agents/skills/README.md`](./.agents/skills/README.md).

## Reference

- `.agents/PLAYBOOK.md`: end-to-end workflow
- `.agents/skills/README.md`: skill catalog
- `.agents/skills/`: skill definitions
