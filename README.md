# Surpass IQ Community Skills

A community library of Claude Code Skills for [Surpass IQ](https://surpass.com) — browse, download, and contribute skills that configure Surpass IQ to perform specific tasks exceptionally well.

**Live site:** `https://<your-org>.github.io/surpass-iq-community/` *(update after deploying to GitHub Pages)*

---

## What's in this repo?

| Path | Description |
|---|---|
| `index.html` | Skill browser — search, filter, and view skills |
| `submit.html` | Submission page — links to the Google Form |
| `assets/css/styles.css` | Surpass-branded styles |
| `skills/_index.json` | **Skill registry** — the single source of truth read by the site |
| `skills/<id>/SKILL.md` | The skill content (rendered in the browser via marked.js) |
| `skills/<id>/meta.json` | Per-skill metadata |
| `CONTRIBUTING.md` | How to format and submit a skill |

## Adding a New Skill

No code changes are needed — only data changes:

1. Create `skills/<skill-id>/SKILL.md` and `skills/<skill-id>/meta.json`
2. Append the skill's metadata object to `skills/_index.json`
3. Commit to `main` — GitHub Pages republishes automatically in ~1 minute

See [CONTRIBUTING.md](CONTRIBUTING.md) for full formatting guidance.

## Tech Stack

Static HTML/CSS/Vanilla JS — no build step, no npm, no backend.

- **Hosting:** GitHub Pages
- **Markdown rendering:** [marked.js](https://marked.js.org/) via CDN
- **Fonts:** Source Sans Pro via Google Fonts
- **Submission flow:** Google Form → Surpass review → manual merge to repo
