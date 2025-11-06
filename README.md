# Algorim

A modern Vite + React + TypeScript starter focused on algorithm tracking, visualization, and developer tooling. Algorim provides UI components and integrations for tracking algorithm performance, visualizing execution flows, and delivering feedback on code solutions.

This README gives a concise guide to getting the project running locally, required environment variables, common commands, and how to contribute.

## Highlights

- Algorithm tracking and visualization UI
- Integrations with Supabase for storage/auth and Google Generative AI (Gemini) for code evaluation
- Built with Vite, React, TypeScript, Tailwind CSS and shadcn/ui primitives

## Tech stack

- Vite (dev server & build)
- React 18 + TypeScript
- Tailwind CSS
- Supabase (`@supabase/supabase-js`)
- Google Generative AI (`@google/generative-ai`) — used for code evaluation
- shadcn-based UI + Radix primitives

## Quickstart (Windows / PowerShell)

Prerequisites:
- Node.js 18+ (LTS recommended)
- npm (or pnpm/yarn if you prefer; commands below use npm)

1. Clone and enter the project folder

```powershell
git clone https://github.com/rnt07s/Algorim.git
cd Algorim
```

2. Install dependencies

```powershell
npm install
```

3. Create a local environment file with the values described below, then start the dev server:

```powershell
npm run dev
```

Vite will usually serve at http://localhost:5173 — open that in your browser.

## Environment variables

Create a `.env` (or `.env.local`) file in the project root. The project reads Vite env variables using the `VITE_` prefix. Example variables used by the integrations in this repo:

```env
# Supabase (used by src/integrations/supabase/client.ts)
VITE_SUPABASE_URL=https://your-project.supabase.co
VITE_SUPABASE_PUBLISHABLE_KEY=your-supabase-anon-key

# Google Generative AI (used by src/integrations/gemini/client.ts)
VITE_GEMINI_AI_API=your-google-generative-api-key

# Other optional envs
VITE_SOME_OTHER_KEY=value
```

Important: Do not commit `.env` to version control. Add any secrets to your deployment provider's environment configuration when deploying.

## Available scripts

From `package.json`:

- `npm run dev` — start Vite dev server
- `npm run build` — build for production
- `npm run build:dev` — build in development mode
- `npm run preview` — locally preview production build
- `npm run lint` — run ESLint

## Environment / file structure (high level)

- `src/` — app source
  - `components/` — reusable UI and shadcn primitives
  - `integrations/` — supabase and gemini clients
  - `pages/` — page-level routes (e.g., `Chat.tsx`, `InterviewPage.tsx`)
  - `context/` and `hooks/` — state management and utilities

## Testing & linting

The repository includes ESLint configuration. You can run:

```powershell
npm run lint
```

Add unit tests or e2e tests as needed. This starter does not include a test framework configured out of the box.

## Troubleshooting

- If `npm install` fails with network errors (ECONNRESET) on Windows:
  - Check your network / VPN / proxy and try again
  - Inspect npm proxy config:

```powershell
npm config get proxy
npm config get https-proxy
```

  - Try increasing npm fetch retries and timeout:

```powershell
npm install --fetch-retries=5 --fetch-retry-factor=10 --network-timeout=600000
```

- If you see permission errors while removing `node_modules`, close programs that might lock files (editors, terminals), then retry.

## Deploy

Build the app and deploy the `dist` output to any static hosting provider (Vercel, Netlify, Cloudflare Pages, etc.). Vite's `preview` command lets you verify the production build locally:

```powershell
npm run build
npm run preview
```

For server-side integrations (e.g., server functions that use secrets), configure environment variables in your host and avoid exposing keys to the browser.

## Contributing

Contributions are welcome. Suggested flow:

1. Fork the repository
2. Create a branch: `git checkout -b feature/awesome`
3. Make changes & commit: `git commit -m "feat: add ..."`
4. Push and open a PR

Guidelines:
- Keep changes small and focused
- Add or update docs for new features
- Follow existing code style (TypeScript + React patterns)

## License

MIT License. See the `LICENSE` file for details.

---

Happy hacking — go visualize some algorithms!
