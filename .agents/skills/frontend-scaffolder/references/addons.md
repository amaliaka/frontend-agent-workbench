# Add-ons Reference

Detailed setup instructions for common frontend add-ons.
Always install add-ons AFTER the base framework is scaffolded.

---

## Tailwind CSS v4

Tailwind v4 is a complete overhaul — no more `tailwind.config.js`, no content globs, no `@tailwind` directives, no `postcss.config.js` required for most setups. Just install, add a plugin, and import.

### With Vite-based projects (React+Vite, Vue, SvelteKit, vanilla Vite)

```bash
pnpm add -D tailwindcss @tailwindcss/vite
```

Update `vite.config.ts`:
```ts
import { defineConfig } from 'vite'
import react from '@vitejs/plugin-react' // or vue(), svelte(), etc.
import tailwindcss from '@tailwindcss/vite'

export default defineConfig({
  plugins: [
    react(),
    tailwindcss(),
  ],
})
```

Add to your main CSS file (e.g. `src/index.css` or `src/app.css`):
```css
@import "tailwindcss";
```

That's it — no config file, no content paths, no autoprefixer needed.

### With Next.js

Next.js uses PostCSS under the hood, so use `@tailwindcss/postcss` instead of the Vite plugin.

```bash
pnpm add -D tailwindcss @tailwindcss/postcss
```

Create `postcss.config.mjs` in the project root:
```js
export default {
  plugins: {
    '@tailwindcss/postcss': {},
  },
}
```

Add to `app/globals.css` (replace the existing `@tailwind` directives if present):
```css
@import "tailwindcss";
```

**Note:** `create-next-app --tailwind` still scaffolds v3-style config. After scaffolding, delete `tailwind.config.ts`, `postcss.config.mjs` (the old one), and replace with the v4 setup above.

### With Nuxt 4

Use the `@tailwindcss/vite` Vite plugin (not the old `@nuxtjs/tailwindcss` module — that's v3 only).

```bash
pnpm add -D tailwindcss @tailwindcss/vite
```

Update `nuxt.config.ts`:
```ts
import tailwindcss from '@tailwindcss/vite'

export default defineNuxtConfig({
  compatibilityDate: '2025-07-15',
  vite: {
    plugins: [tailwindcss()],
  },
  css: ['~/assets/css/main.css'],
})
```

Create `app/assets/css/main.css`:
```css
@import "tailwindcss";
```

### With SvelteKit

```bash
pnpm add -D tailwindcss @tailwindcss/vite
```

Update `vite.config.ts`:
```ts
import { defineConfig } from 'vite'
import { sveltekit } from '@sveltejs/kit/vite'
import tailwindcss from '@tailwindcss/vite'

export default defineConfig({
  plugins: [sveltekit(), tailwindcss()],
})
```

Add to `src/app.css` (or create it):
```css
@import "tailwindcss";
```

Make sure `src/routes/+layout.svelte` imports the CSS:
```svelte
<script>
  import '../app.css'
</script>
<slot />
```

### Customization (v4 style)

In v4, customization lives in your CSS file — no `tailwind.config.js` needed:

```css
@import "tailwindcss";

@theme {
  --color-brand: oklch(0.6 0.2 250);
  --font-sans: 'Inter', sans-serif;
  --radius-lg: 0.75rem;
}
```

---

## shadcn/ui

**Requires:** React (or Next.js), Tailwind CSS already configured, TypeScript.
shadcn/ui v2+ supports Tailwind v4.

### With Next.js (App Router)
```bash
pnpm dlx shadcn@latest init -d
```

### With React + Vite
```bash
pnpm dlx shadcn@latest init -d
```

**Note for Vite projects:** shadcn requires path aliases. Add to `vite.config.ts`:
```ts
import path from 'path'
// ...
resolve: {
  alias: { '@': path.resolve(__dirname, './src') },
},
```
And install:
```bash
pnpm add -D @types/node
```

**Adding components:**
```bash
pnpm dlx shadcn@latest add button card input dialog dropdown-menu
```

---

## ESLint

### For Vite-based React projects (not already included)
```bash
pnpm add -D eslint @eslint/js typescript-eslint eslint-plugin-react-hooks eslint-plugin-react-refresh globals
```

Create `eslint.config.js`:
```js
import js from '@eslint/js'
import globals from 'globals'
import reactHooks from 'eslint-plugin-react-hooks'
import reactRefresh from 'eslint-plugin-react-refresh'
import tseslint from 'typescript-eslint'

export default tseslint.config(
  { ignores: ['dist'] },
  {
    extends: [js.configs.recommended, ...tseslint.configs.recommended],
    files: ['**/*.{ts,tsx}'],
    languageOptions: { globals: globals.browser },
    plugins: { 'react-hooks': reactHooks, 'react-refresh': reactRefresh },
    rules: {
      ...reactHooks.configs.recommended.rules,
      'react-refresh/only-export-components': ['warn', { allowConstantExport: true }],
    },
  }
)
```

Add to `package.json` scripts:
```json
"lint": "eslint ."
```

---

## Prettier

```bash
pnpm add -D prettier eslint-config-prettier
```

Create `.prettierrc`:
```json
{
  "semi": false,
  "singleQuote": true,
  "tabWidth": 2,
  "trailingComma": "es5",
  "printWidth": 100
}
```

Add to `package.json` scripts:
```json
"format": "prettier --write ."
```

---

## Vitest (Unit Testing)

### For Vite-based projects
```bash
pnpm add -D vitest @vitest/ui @testing-library/react @testing-library/jest-dom jsdom
```

Update `vite.config.ts`:
```ts
/// <reference types="vitest" />
export default defineConfig({
  // ...existing config
  test: {
    globals: true,
    environment: 'jsdom',
    setupFiles: './src/test/setup.ts',
  },
})
```

Create `src/test/setup.ts`:
```ts
import '@testing-library/jest-dom'
```

Add to `package.json` scripts:
```json
"test": "vitest",
"test:ui": "vitest --ui",
"coverage": "vitest run --coverage"
```

---

## Playwright (E2E Testing)

```bash
pnpm dlx playwright install --with-deps
pnpm add -D @playwright/test
```

---

## Husky + lint-staged (Git Hooks)

```bash
pnpm add -D husky lint-staged
pnpm dlx husky init
```

Add to `package.json`:
```json
"lint-staged": {
  "*.{ts,tsx,js,jsx}": ["eslint --fix", "prettier --write"],
  "*.{json,md,css}": "prettier --write"
}
```

Update `.husky/pre-commit`:
```sh
pnpm lint-staged
```

---

## Zustand (State Management for React)

```bash
pnpm add zustand
```

Example store (`src/store/useCountStore.ts`):
```ts
import { create } from 'zustand'

interface CountState {
  count: number
  increment: () => void
}

export const useCountStore = create<CountState>((set) => ({
  count: 0,
  increment: () => set((state) => ({ count: state.count + 1 })),
}))
```

---

## TanStack Query

```bash
pnpm add @tanstack/react-query
```

Wrap app in `QueryClientProvider` in `main.tsx`:
```tsx
import { QueryClient, QueryClientProvider } from '@tanstack/react-query'
const queryClient = new QueryClient()

ReactDOM.createRoot(document.getElementById('root')!).render(
  <QueryClientProvider client={queryClient}>
    <App />
  </QueryClientProvider>
)
```

---

## Storybook

```bash
pnpm dlx storybook@latest init --no-dev
```

Add to scripts:
```json
"storybook": "storybook dev -p 6006",
"build-storybook": "storybook build"
```
