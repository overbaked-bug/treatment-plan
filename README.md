# AesthetiPlan

AI-powered treatment plan generator for medical aesthetics consultations.

## What it does

- **Record** a live consultation via microphone (or paste a transcript)
- **AI analyses** the transcript and matches relevant treatments from your catalog
- **Generates** a personalised treatment plan with: consultation summary, concern areas, and for each treatment: name, price, why recommended, pain level, and downtime
- **Dashboard** tracks all plans generated in the session

## Files

| File | Purpose |
|------|---------|
| `index.html` | Main app — the only file users interact with |
| `catalog.json` | Treatment catalog — read by the AI to generate plans. Edit this to add/remove treatments. |

## Hosting on GitHub Pages

1. Push both files to a GitHub repository
2. Go to **Settings → Pages**
3. Set source to **main branch / root**
4. Your app will be live at `https://yourusername.github.io/your-repo-name`

> The Anthropic API key is handled by the Claude.ai artifact runtime. If you deploy this outside Claude.ai, you will need to add your own API key to the fetch call in `index.html`.

## Updating the treatment catalog

Edit `catalog.json` to add, remove, or update treatments. Each entry should follow this structure:

```json
{
  "name": "Treatment name",
  "price": "From £ X,XXX",
  "painLevel": "Low (2–3/10)",
  "downtime": "Description of downtime",
  "description": "What the treatment does, who it's for, expected results."
}
```

After editing, the updated catalog will be picked up automatically by the AI on the next plan generation.

## Browser support

Live recording requires Chrome or Edge (Web Speech API). Firefox users can paste transcripts manually.
