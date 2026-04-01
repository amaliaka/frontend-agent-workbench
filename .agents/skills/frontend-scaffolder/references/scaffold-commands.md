# Scaffold Commands Reference

This file contains the exact non-interactive commands to scaffold each supported framework.
**Default package manager is `pnpm`.** Use `npm` or `yarn` only if the user explicitly asks.

---

## Next.js

```bash
pnpm create next-app@latest <project-name> \
  --typescript \
  --eslint \
  --tailwind \
  --app \
  --src-dir \
  --import-alias "@/*" \
  --no-turbopack
```

**Without Tailwind:**
```bash
pnpm create next-app@latest <project-name> \
  --typescript \
  --eslint \
  --no-tailwind \
  --app \
  --src-dir \
  --import-alias "@/*"
```

**JavaScript variant:** Replace `--typescript` with `--no-typescript`

**Notes:**
- `--app` uses the App Router (default in Next.js 15, recommended)
- `--src-dir` puts code in `src/` which is cleaner for larger apps
- Tailwind is integrated by default when `--tailwind` is passed — no extra steps needed

---

## React + Vite

```bash
pnpm create vite@latest <project-name> --template react-ts
cd <project-name>
pnpm install
```

**JavaScript variant:**
```bash
pnpm create vite@latest <project-name> --template react
```

**Available Vite templates:** `vanilla`, `vanilla-ts`, `vue`, `vue-ts`, `react`, `react-ts`, `react-swc`, `react-swc-ts`, `preact`, `preact-ts`, `lit`, `lit-ts`, `svelte`, `svelte-ts`, `solid`, `solid-ts`, `qwik`, `qwik-ts`

---

## Vue 3 (via create-vue)

```bash
pnpm create vue@latest <project-name> -- \
  --ts \
  --router \
  --pinia \
  --eslint \
  --prettier
cd <project-name>
pnpm install
```

**Flags reference:**
- `--ts` — TypeScript
- `--router` — Vue Router
- `--pinia` — Pinia state management
- `--vitest` — Vitest testing
- `--cypress` — Cypress E2E
- `--eslint` — ESLint
- `--prettier` — Prettier

---

## Nuxt 4

Nuxt 4 is the current stable release (as of mid-2025). `nuxi@latest init` scaffolds Nuxt 4 by default.

```bash
pnpm dlx nuxi@latest init <project-name>
cd <project-name>
pnpm install
```

**With Tailwind module:**
```bash
pnpm dlx nuxi@latest init <project-name>
cd <project-name>
pnpm install
pnpm dlx nuxi@latest module add tailwindcss
```

**With Nuxt UI (Tailwind + headless component library):**
```bash
pnpm dlx nuxi@latest init <project-name> -t ui
cd <project-name>
pnpm install
```

**Notes:**
- Nuxt 4 is the current default — `nuxi@latest` will install it
- Nuxt is opinionated — routing, SSR, and state are all built-in
- Nuxt modules (`@nuxtjs/tailwindcss`, `@nuxt/ui`) are the preferred way to add integrations
- Nuxt 3 EOL is July 2026; always use Nuxt 4 for new projects

---

## SvelteKit

`create-svelte` is **deprecated** as of 2024. The new official CLI is `sv` (the Svelte CLI).

```bash
pnpm dlx sv create <project-name>
cd <project-name>
pnpm install
```

The `sv create` CLI is interactive by default. To make it non-interactive, use these flags:

```bash
pnpm dlx sv create <project-name> \
  --template minimal \
  --types ts \
  --no-add-ons
cd <project-name>
pnpm install
```

**Adding Tailwind via sv:**
```bash
cd <project-name>
pnpm dlx sv add tailwindcss
```

**Adding other add-ons via sv:**
```bash
pnpm dlx sv add eslint prettier vitest playwright drizzle
```

**Template options:** `minimal`, `demo`
**Types options:** `ts` (TypeScript), `jsdoc`, `none`

**Notes:**
- `sv` is the unified Svelte CLI — it also handles `sv add`, `sv migrate`, `sv check`
- Svelte 5 (with runes) is the current default in all new projects

---

## Angular

```bash
pnpm dlx @angular/cli@latest new <project-name> \
  --routing \
  --style=css \
  --skip-git \
  --no-interactive \
  --package-manager=pnpm
cd <project-name>
```

**With SCSS:**
Replace `--style=css` with `--style=scss`

**Notes:**
- Angular CLI is heavy — first-time install takes a while
- Standalone components are the modern default in Angular 19
- `--package-manager=pnpm` tells Angular CLI to use pnpm for the project

---

## Astro

```bash
pnpm create astro@latest <project-name> -- \
  --template minimal \
  --install \
  --no-git \
  --typescript strict
cd <project-name>
```

**Template options:** `minimal`, `blog`, `portfolio`, `starlight` (docs)

**Adding a UI framework to Astro:**
```bash
# React
pnpm dlx astro add react

# Vue
pnpm dlx astro add vue

# Svelte
pnpm dlx astro add svelte

# Tailwind
pnpm dlx astro add tailwind
```

---

## Vite (Vanilla)

```bash
pnpm create vite@latest <project-name> --template vanilla-ts
cd <project-name>
pnpm install
```

---

## Remix

```bash
pnpm dlx create-remix@latest <project-name> --no-install --no-git-init
cd <project-name>
pnpm install
```

---

## Expo (React Native)

```bash
pnpm dlx create-expo-app@latest <project-name> --template blank-typescript
cd <project-name>
```
