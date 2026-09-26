# Runboard Cloudflare

This repository hosts a personal [Runboard](https://github.com/Moe-Zbeeb/runboard) dashboard on Cloudflare Workers and D1.

Cloudflare automatically deploys every push to `main`. The dashboard and API share the Worker URL. Every API and dashboard request requires the `RUNBOARD_TOKEN` Worker secret. Open the dashboard once as `/?token=...` to store it in an `HttpOnly` cookie.

## Local development

```bash
npm install
cp .dev.vars.example .dev.vars
npm run dev
```

The D1 binding and production database ID are configured in `wrangler.jsonc`. Keep `.dev.vars` private.

## Deploy

```bash
npm install
npm run deploy
```

The Cloudflare build integration runs the same deploy command automatically.

## Dashboard source

The Worker, migrations, and dashboard assets match [Runboard commit 4cd3fe3](https://github.com/Moe-Zbeeb/runboard/commit/4cd3fe3982832c626bbfbf73da733c601205e898). This update restyles the dashboard, bundles the Recursive typeface, and adds a per-run heartbeat trace of recent metric writes; it does not change the Worker API, authentication, or D1 data.
