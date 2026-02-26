## Cursor Cloud specific instructions

### Project overview
This is a **Backstage Developer Portal** (monorepo) located at `daniel-portal/`. See `daniel-portal/README.md` for quick-start commands.

### Services
| Service | Port | Notes |
|---|---|---|
| Frontend (React SPA) | 3000 | Webpack dev server |
| Backend (Express API) | 7007 | All backend plugins (catalog, scaffolder, auth, search, techdocs, proxy) |

Both start together via `yarn dev` from `daniel-portal/`.

### Key caveats
- **Node version**: Requires Node 18 or 20 (`engines` field in `package.json`). Node 22+ is not supported. Use `nvm use 20` before running commands.
- **Database**: Dev mode uses in-memory SQLite (`better-sqlite3`). No external database needed.
- **GitHub OAuth**: The original `App.tsx` was hardcoded to require GitHub OAuth sign-in. The `SignInPage` component override has been removed to allow unauthenticated access for local development. To re-enable GitHub auth, add back the `SignInPage` component in `createApp()` and configure an OAuth app in `app-config.local.yaml` (see `README.md` steps 5-7).
- **Pre-existing lint error**: `packages/app/src/App.tsx` has a lint error (`import/newline-after-import`). This is in the existing code.
- **Lint command**: `yarn lint:all` lints all packages. The default `yarn lint` uses `--since origin/master` which may not work on branches without that ref.

### Standard commands (from `daniel-portal/`)
- `yarn dev` — start frontend + backend
- `yarn test --watchAll=false` — run all tests
- `yarn lint:all` — lint all packages
- `yarn tsc` — TypeScript type checking
- `yarn build:all` — build all packages
