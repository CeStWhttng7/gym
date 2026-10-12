# Base44 Setup Notes

## Project
React Router 7 + Cloudflare Workers app using Vite 7 and TailwindCSS 4.
No database, no external services, no secrets required.

## Running in the sandbox
- `docker compose -f docker-compose.base44.yml up -d --build`
- The dev server (`react-router dev`) runs on port 5173 inside the container, mapped to host port 3000.
- `npm ci` runs on container startup before the dev server starts.
- File-watch polling is enabled via `vite.config.ts` when `BASE44_PREVIEW_MODE === "1"` (bind mounts need it).
- Vite host allowlisting is handled by `__VITE_ADDITIONAL_SERVER_ALLOWED_HOSTS` (platform-set env var passed through compose).

## Verifying
- `curl http://localhost:3000/` should return the rendered HTML of the welcome page.
- The page title is "New React Router App".
