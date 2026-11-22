# Manufacturer Engineering Suite

> A single-file interactive demo for tyre and rubber manufacturers.

**Live demo →** [View on GitHub Pages](https://oussamarevolotionary.github.io/manufacturer-engineering-suite/)

**v1 — superseded by the TC Cure Engine demo.** The chatbot runs in sandbox mode by default (canned answers, no network calls); add `?live=1` for the n8n backend.

---

## What's inside

| Section | What it does |
|---|---|
| **BOM Intelligence** | Tyre catalog · component BOM breakdown (rubber / textile / steel) · compound recipes (phr, cost, function) |
| **Cure Analytics** | 12-position thermocouple cure analysis · CEQ (Arrhenius) · %CEF · TaT · post-deflation cure · mold health |
| **AI Assistant** | Context-aware chatbot scoped to tyre engineering — formulations, curing, BOM questions |

## Setup

1. **Deploy** — rename `index.html` is already the entry point for GitHub Pages.
2. **Chatbot** — import `n8n-chatbot-workflow.json` into your n8n instance, add your API key, activate. See `N8N_SETUP.md` for full steps.
3. **Update webhook URL** — replace `N8N_WEBHOOK_URL` in `index.html` with your live webhook URL.

## Tech stack

Single self-contained HTML file. No framework, no build step. CDN only:
- [Chart.js 4.4.1](https://www.chartjs.org/) — all charts
- [Lucide Icons](https://lucide.dev/) — UI icons
- [Inter + JetBrains Mono](https://fonts.google.com/) — typography

---

*Built by Oussama Labs · June 2026*
