# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A static GitHub Pages site for browsing and submitting community Claude Code Skills for Surpass IQ. No build pipeline, no npm, no backend — pure HTML/CSS/Vanilla JS deployed directly from the `main` branch.

The full build plan is in `surpass-iq-skills-site-plan.md`.

## Development

No build step or local server is required. Open HTML files directly in a browser, or use any static file server:

```bash
# Quick local dev server (Python, no install needed)
python -m http.server 8080

# Or with Node (if available)
npx serve .
```

There are no tests, linters, or CI pipelines for the POC.

## Architecture

### Data Flow

Skills are driven by a single JSON registry (`skills/_index.json`). On page load, `index.html` fetches this file and renders skill cards dynamically. Search and category filtering happen client-side with no page reload.

When a user opens a skill detail view, the full `SKILL.md` is fetched on demand and rendered to HTML via `marked.js` (loaded from CDN).

### Key Files

| File | Purpose |
|---|---|
| `index.html` | Skill browser — card grid, search, category filter, detail modal |
| `submit.html` | Links to Google Form, explains review process |
| `assets/css/styles.css` | All Surpass-branded styles |
| `skills/_index.json` | **Single source of truth** — all skill metadata, read by JS on load |
| `skills/<id>/SKILL.md` | The actual skill content (rendered via marked.js) |
| `skills/<id>/meta.json` | Per-skill metadata (title, description, category, tags, author, version, date) |

### Adding a New Skill

No code changes needed — only data changes:
1. Create `skills/<skill-id>/SKILL.md` and `skills/<skill-id>/meta.json`
2. Append the skill's metadata object to `skills/_index.json`
3. Commit to `main` — GitHub Pages republishes automatically (~1 min)

### CDN Dependencies (no local install)

```html
<script src="https://cdn.jsdelivr.net/npm/marked/marked.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/fuse.js/dist/fuse.min.js"></script>
<link href="https://fonts.googleapis.com/css2?family=Source+Sans+Pro:wght@400;600&display=swap" rel="stylesheet">
```

## Branding

```css
:root {
  --surpass-dark-grey: #265063;   /* nav/hero background */
  --surpass-cyan: #2099D5;        /* links */
  --surpass-yellow: #F4CA11;      /* primary CTA button */
  --surpass-light-cyan: #BDE3F3;  /* category badges */
  --surpass-very-light-cyan: #EEF6FC; /* card hover background */
  --font-primary: 'Source Sans Pro', 'Helvetica Neue', Arial, sans-serif;
}
```

## `meta.json` Schema

```json
{
  "id": "item-authoring",
  "title": "Clinical Vignette Item Authoring",
  "description": "Short description shown on skill card.",
  "category": "Item Authoring",
  "tags": ["MCQ", "clinical", "healthcare"],
  "author": "Surpass Community",
  "version": "1.0",
  "date": "2025-04-01",
  "skill_file": "skills/item-authoring/SKILL.md"
}
```

Valid categories: `Item Authoring`, `Tag Management`, `Bulk Workflows`, `Analysis`, `Other`

## Deployment

Hosted on GitHub Pages from the `main` branch root. Every commit to `main` triggers an automatic republish — no manual deployment step. The live URL follows the pattern `https://<org>.github.io/surpass-iq-community/`.
