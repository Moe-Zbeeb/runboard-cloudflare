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

The Worker, migrations, and dashboard assets match [Runboard commit ddb36ac](https://github.com/Moe-Zbeeb/runboard/commit/ddb36ac44183cf1e5a0971ada0ab71c36216a455). This update skips metric rows already stored for a client session, returns several metric batches per request, and makes the dashboard poll less often. The Worker creates the new `run_sessions` D1 table automatically on its first request; existing data is unchanged.
