# AGENTS.md

## Cursor Cloud specific instructions

This is a workshop monorepo with multiple independent frontend-only React + Vite apps. There are no backends, databases, or external APIs.

### Relevant services

| App | Path | Port | Dev command |
|-----|------|------|-------------|
| LinkedOut (teams 1-5) | `linkedout/team_N/` | 3001-3005 | `npm run dev` |
| Workshop Slides | `slides-react/` | 5175 | `npm run dev` |

Each team app under `linkedout/` is an identical copy (React 18 + Vite 5). The `slides-react/` app uses React 19 + Vite 7.

### Lint / Build / Dev

- **Lint:** Only `slides-react` has ESLint configured — run `npm run lint` from `slides-react/`.
- **Build:** `npm run build` in any app directory.
- **Dev:** `npm run dev` in any app directory. Use `-- --port NNNN --host 0.0.0.0` for custom ports.

### Gotchas

- LinkedOut teams 3-5 have no lockfile; `npm install` generates one on first run.
- The `linkedout/` apps use Vite 5 CJS Node API which prints a deprecation warning — this is cosmetic and harmless.
- `.cursor/hooks.json` defines a pre-commit hook (`require-member.sh`) that blocks commits to `linkedout/` unless a team member file exists. Cloud agents working in `linkedout/` should be aware of this gate.
- The `teams/` directory contains only markdown PRDs and cheatsheets — no runnable code.
