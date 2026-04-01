# Monorepo Reference

Use this when the user wants a monorepo setup — multiple apps/packages managed together.

---

## Turborepo (Most Popular Choice)

Best for: teams with multiple apps sharing packages (design system, utilities, etc.)

```bash
pnpm dlx create-turbo@latest <project-name>
cd <project-name>
pnpm install
```

**With specific package manager:**
```bash
pnpm dlx create-turbo@latest <project-name> --package-manager pnpm
```

**Structure you get:**
```
my-turbo/
├── apps/
│   ├── web/          ← Next.js app
│   └── docs/         ← Another Next.js app
├── packages/
│   ├── ui/           ← Shared component library
│   ├── eslint-config/
│   └── typescript-config/
├── turbo.json
└── package.json
```

**Running across all apps:**
```bash
pnpm dev      # start all apps
pnpm build    # build all apps
pnpm lint     # lint all packages
```

---

## Nx

Best for: large teams, Angular projects, or when you need more advanced task scheduling

```bash
npx create-nx-workspace@latest <project-name> \
  --preset=react-monorepo \
  --appName=my-app \
  --bundler=vite \
  --no-interactive
```

**Preset options:** `react-monorepo`, `vue-monorepo`, `angular-monorepo`, `next`, `nuxt`, `node-standalone`

---

## pnpm Workspaces (Lightweight)

Best for: simpler setups without a build orchestrator

```bash
mkdir <project-name> && cd <project-name>
pnpm --version || npm install -g pnpm
pnpm init
```

Create `pnpm-workspace.yaml`:
```yaml
packages:
  - 'apps/*'
  - 'packages/*'
```

Then scaffold apps individually inside `apps/`:
```bash
mkdir -p apps packages
cd apps
npm create vite@latest web -- --template react-ts
```
