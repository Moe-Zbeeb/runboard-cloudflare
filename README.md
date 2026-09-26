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

The Worker, migrations, and dashboard assets match [Runboard commit d24722c](https://github.com/Moe-Zbeeb/runboard/commit/d24722cb27e98c07e14bf1a544073f071272f18c). This update restyles the dashboard, bundles the Recursive typeface, and adds a per-run heartbeat trace of recent metric writes; it does not change the Worker API, authentication, or D1 data.
