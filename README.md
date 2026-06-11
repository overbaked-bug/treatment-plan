# AesthetiPlan

**AI-powered treatment plan generator for medical aesthetics consultations.**

🔗 **[Live demo → overbaked-bug.github.io/treatment-plan](https://overbaked-bug.github.io/treatment-plan/)**

---

## Overview

AesthetiPlan turns a consultation recording into a fully structured treatment plan in seconds. A practitioner records or transcribes a patient consultation, and the AI analyses the discussion to produce a personalised plan — pulling from a private treatment catalog to recommend relevant procedures with clinical rationale, pricing, pain level, and downtime.

Built as a practical tool for the medical aesthetics industry, where consultations are time-intensive and treatment plan documentation is often done manually after the appointment.

## Features

- 🎙️ **Live voice recording** — record directly in the browser using the Web Speech API; transcript appears in real time
- 🤖 **AI plan generation** — Claude analyses the transcript and matches treatments from the catalog, generating personalised "why I recommend this" rationale for each
- 💷 **Treatment catalog** — a structured JSON catalog of treatments with name, price, pain level, and downtime; the AI reads from this silently to ensure recommendations stay on-menu
- 📋 **Structured output** — consultation summary, concern areas, and treatment cards each showing name, price, recommendation rationale, pain badge, and downtime badge
- 🖨️ **Print / PDF export** — one-click print layout for sharing with patients
- 📊 **Dashboard** — tracks plans generated and session history

## Tech stack

| Layer | Technology |
|-------|-----------|
| Frontend | Vanilla HTML, CSS, JavaScript — no framework, no build step |
| AI | Anthropic Claude API (`claude-sonnet-4-20250514`) |
| Voice transcription | Web Speech API (native browser) |
| Backend proxy | Vercel serverless function (Node.js) — secures the API key |
| Hosting | GitHub Pages |

## Architecture

```
Browser (GitHub Pages)
  → Vercel proxy (api/proxy.js)
    → Anthropic Claude API
```

The Vercel proxy exists to keep the Anthropic API key out of the frontend codebase. The frontend sends the prompt to the proxy; the proxy injects the key server-side and forwards to Anthropic. This means the GitHub repo can be fully public with no secrets exposed.

## Repository structure

```
treatment-plan/
├── index.html       # Full frontend application
├── catalog.json     # Treatment catalog (AI reads this to generate plans)
└── README.md
```

## Updating the treatment catalog

Edit `catalog.json` to add, remove, or update treatments:

```json
{
  "name": "Treatment name",
  "price": "From £XXX",
  "painLevel": "Low (2–3/10)",
  "downtime": "Description of downtime",
  "description": "What the treatment does, who it's for, expected results."
}
```

Changes are picked up automatically on the next plan generation — no redeployment needed.

## Browser support

Live recording requires **Chrome or Edge** (Web Speech API). Firefox and Safari users can paste a transcript manually using the text field provided.

---

*Built with Claude · Deployed on GitHub Pages + Vercel*
