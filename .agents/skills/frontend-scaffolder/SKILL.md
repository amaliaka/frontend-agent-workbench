---
name: frontend-scaffolder
description: Scaffolds production-ready frontend boilerplate projects directly in the user's working environment. Use this skill whenever the user wants to start a new frontend project, set up a tech stack, initialize a codebase, or asks about boilerplate for React, Vue, Angular, Next.js, Nuxt, Svelte, SvelteKit, Vite, Astro, or any combination with Tailwind CSS, shadcn/ui, TypeScript, ESLint, Prettier, or other frontend tooling. Trigger this skill even if the user says things like "spin up a project", "scaffold me a", "start a new app with", "set up a boilerplate", "create a template", "init a project with", or just lists a tech stack and implies they want to get started. This skill handles both single-framework and multi-tool combo setups.
---

# Frontend Scaffolder Skill

This skill installs a fully working, opinionated frontend boilerplate tailored to the user's specified tech stack — batteries included, ready to `pnpm dev`.

## Workflow Overview

1. **Understand the stack** — clarify what the user wants if ambiguous
2. **Pick the right scaffold strategy** — choose the right base installer command
3. **Layer on add-ons** — install and configure extras (Tailwind, shadcn, ESLint, etc.)
4. **Verify and present** — confirm the project works, show the user what was built

---

## Step 1: Understand the Stack

If the user is vague (e.g., "set me up a React project"), ask one quick clarifying question before proceeding. Keep it short — don't bombard them.

Key things to nail down:
- **Framework** (React, Vue, Angular, Next.js, Nuxt, Svelte/SvelteKit, Astro, Vite vanilla)
- **Language** (TypeScript vs JavaScript — default to TypeScript unless they say otherwise)
- **Styling** (Tailwind CSS? Plain CSS? CSS Modules?)
- **UI components** (shadcn/ui? Radix? Headless UI?)
- **Extras** (ESLint, Prettier, testing, Storybook, Husky/lint-staged)

If the user already gave most of this info, skip the questions and confirm your interpretation before proceeding.

**Example interpretation:**
> User: "set up a Next.js project with Tailwind and shadcn"
> Confirm: "Cool — I'll scaffold a Next.js 14 app with TypeScript, Tailwind CSS, and shadcn/ui. Sound right?"

---

## Step 2: Scaffold the Base Project

Use the canonical scaffolding command for the chosen framework. **Always scaffold into a named directory** (use the project name the user gives, or default to `my-app`).

See `references/scaffold-commands.md` for the exact commands per framework and combination.

Key principles:
- Prefer the **official CLI** for each framework — don't DIY when a well-maintained tool exists
- Use `--yes` / `--defaults` flags where available to avoid interactive prompts blocking the script
- Always install **non-interactively** — use environment variables or flags to suppress interactive prompts (e.g., `create-next-app` flags, `FORCE_COLOR=0`, etc.)
- Capture and show relevant output so the user can see what was scaffolded

---

## Step 3: Layer on Add-ons

After the base is scaffolded, install any requested extras in the correct order (some tools require the base framework first).

See `references/addons.md` for detailed setup instructions per add-on.

**Order matters:**
1. Base framework first
2. Tailwind CSS (if requested and not included in base)
3. shadcn/ui (requires Tailwind to already be set up)
4. ESLint / Prettier config
5. Testing (Vitest, Jest, Playwright, Cypress)
6. Other extras (Husky, lint-staged, Storybook, etc.)

---

## Step 4: Verify and Present

After scaffolding, do a quick sanity check:

```bash
cd <project-name>
npm install  # if not already done
npm run build  # verify it compiles clean
```

Then tell the user:
- What was created and where
- How to start the dev server (`npm run dev` or equivalent)
- Any manual steps they might need (e.g., filling in `.env` vars, configuring a DB)
- A quick summary of the project structure

**Present the project directory** using the file tool so they can see the layout.

---

## Important Notes

- **Node.js is required** — if `node` or `npm` isn't available in the environment, tell the user and stop
- **Working directory** — scaffold into `/home/claude/` or wherever the user specifies; ask if unclear
- **Package manager preference** — default to `pnpm`; switch to `npm` or `yarn` only if the user explicitly requests it. Always check `pnpm` is available first (`pnpm --version`), and install it via `npm install -g pnpm` if missing.
- **Tailwind v4** — always use Tailwind v4 (`@tailwindcss/vite` for Vite-based projects, `@tailwindcss/postcss` for Next.js). No `tailwind.config.js`, no content globs, no `autoprefixer` — just `@import "tailwindcss"` in CSS. See `references/addons.md` for per-framework setup.
- **Don't overconfigure** — only install what the user asked for; don't add things "just because"
- **Monorepos** — if the user wants a monorepo (Turborepo, Nx), see `references/monorepo.md`
- **Non-interactive environments** — always use flags to prevent CLI tools from waiting for user input; the bash tool can't handle interactive prompts

---

## Framework Quick Reference

| Framework | Base Command | Notes |
|-----------|-------------|-------|
| Next.js | `create-next-app@latest` | App router default in Next.js 15 |
| React (Vite) | `npm create vite@latest` | Most common React SPA setup today |
| React (CRA) | ❌ Not recommended | CRA is deprecated; use Vite instead |
| Vue 3 | `npm create vue@latest` | Official Vue scaffolder (create-vue) |
| Nuxt 4 | `npx nuxi@latest init` | Nuxt 4 is current stable, Nuxt 3 EOL July 2026 |
| Angular | `npx @angular/cli@latest new` | Angular 19; standalone components default |
| SvelteKit | `npx sv create` | `create-svelte` deprecated; use `sv` CLI now |
| Astro | `npm create astro@latest` | Great for content/static sites |
| Vite (vanilla) | `npm create vite@latest` | Pick template with `--template` flag |
| Remix | `npx create-remix@latest` | React-based full-stack framework |

For the full command reference with flags, see `references/scaffold-commands.md`.
