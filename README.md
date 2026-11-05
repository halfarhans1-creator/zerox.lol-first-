# glitch-lol

## A) Netlify from GitHub (recommended - everything works)
1. Push this folder to a GitHub repo (keep `netlify/`, `package.json`, `netlify.toml` in the repo root).
2. Netlify -> Add new site -> Import from Git -> pick the repo. No build command, publish directory `.`
3. Add the environment variables (Site settings -> Environment variables): `DISCORD_CLIENT_ID`, `DISCORD_CLIENT_SECRET`, `DISCORD_GUILD_ID`, `DISCORD_STAFF_ROLE_IDS`, `DISCORD_BOT_TOKEN`, optional `ADMIN_TOKEN`, `IP_SALT`.
4. Every `git push` redeploys. (Drag & drop of a zip does not install `@netlify/blobs`; Git deploys do.)

## B) Frontend on GitHub Pages
GitHub Pages cannot run functions, so keep the Netlify site (A) as backend and edit `config.js`:
`api: "https://YOUR-SITE.netlify.app"`, `base: "/"` (or `"/repo-name/"` for a project site).
Then Settings -> Pages -> Source: GitHub Actions. Optional env var on Netlify: `ALLOWED_ORIGINS=https://USER.github.io`.
Discord login: set `DISCORD_REDIRECT_URI` to the Netlify function URL, and add it in the Discord Developer Portal.
