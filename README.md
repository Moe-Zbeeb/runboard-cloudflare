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

The Worker, migrations, and dashboard assets match [Runboard v0.3.0, commit 061d6f0](https://github.com/Moe-Zbeeb/runboard/commit/061d6f0). This update makes Worker deduplication atomic when a timed-out request and its retry arrive together, accepts rows without client session fields, keeps queries under D1's 100-parameter limit for batches from many sessions, and escapes run status in the dashboard. The API, authentication, and D1 schema are unchanged.
