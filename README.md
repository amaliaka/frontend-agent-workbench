# Agent Workspace

This repo stores the agent workflow and skill set under `.agents`.

Use the two docs below depending on what you need:

- [`.agents/PLAYBOOK.md`](./.agents/PLAYBOOK.md): workflow-first guide for choosing the right flow from idea to implementation to verification
- [`.agents/skills/README.md`](./.agents/skills/README.md): index-first catalog for finding the right skill quickly

## Start Here

- If you want the recommended process, open [`.agents/PLAYBOOK.md`](./.agents/PLAYBOOK.md).
- If you already know the task and need the right skill, open [`.agents/skills/README.md`](./.agents/skills/README.md).
- If the request is for a brand-new frontend app, start with `frontend-project-orchestrator`.
- For new app prompts, scaffolding is treated as the default first step (the user does not need to explicitly write "scaffold").
- If scaffolding inside an existing/non-empty repo, route to `frontend-scaffolder` and target a subdirectory (default `apps/<project-name>`).
- If the request is a bug or regression, start with `systematic-debugging`.
- If the request changes behavior or scope, start with `brainstorming`.

## Directory Structure

- `.agents/PLAYBOOK.md`: end-to-end workflow guidance
- `.agents/skills/`: skill library and supporting files
- `.agents/skills/README.md`: skill catalog and quick routing
- `.claude/skills/`: symlinks that mirror selected skills for Claude

## Recommended Entry Points

- New frontend project: `frontend-project-orchestrator`
- Existing repo + new starter scaffold: `frontend-scaffolder` in `apps/<project-name>`
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
