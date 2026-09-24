# Runboard Cloudflare

This repository hosts a personal [Runboard](https://github.com/Moe-Zbeeb/runboard) dashboard on Cloudflare Workers and D1.

Cloudflare automatically deploys every push to `main`. The dashboard and API share the Worker URL. Runboard clients authenticate writes with the `RUNBOARD_TOKEN` Worker secret; dashboard reads remain available from the browser URL.

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
