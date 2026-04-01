# Agent Workspace

This repo stores the agent workflow and skill set under `.agents`.

Use the two docs below depending on what you need:

- [`.agents/PLAYBOOK.md`](./.agents/PLAYBOOK.md): workflow-first guide for choosing the right flow from idea to implementation to verification
- [`.agents/skills/README.md`](./.agents/skills/README.md): index-first catalog for finding the right skill quickly

## Start Here

- If you want the recommended process, open [`.agents/PLAYBOOK.md`](./.agents/PLAYBOOK.md).
- If you already know the task and need the right skill, open [`.agents/skills/README.md`](./.agents/skills/README.md).
- If the request is for a brand-new frontend app, start with `frontend-project-orchestrator`.
- If the request is a bug or regression, start with `systematic-debugging`.
- If the request changes behavior or scope, start with `brainstorming`.

## Directory Structure

- `.agents/PLAYBOOK.md`: end-to-end workflow guidance
- `.agents/skills/`: skill library and supporting files
- `.agents/skills/README.md`: skill catalog and quick routing
- `.claude/skills/`: symlinks that mirror selected skills for Claude
- `skills-lock.json`: source and hash metadata for installed skills

## Recommended Entry Points

- New frontend project: `frontend-project-orchestrator`
- Feature or behavior change: `brainstorming`
- Bugfix or flaky behavior: `systematic-debugging`
- Stack-specific implementation:
  - `shadcn`
  - `nuxt-ui`
- Final verification: `verification-before-completion`

## Notes

- Keep skill folders flat under `.agents/skills/<skill-name>/`.
- Prefer the smallest set of skills that fully covers the task.
- Use process skills first, implementation skills second.
