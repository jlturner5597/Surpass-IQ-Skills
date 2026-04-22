# Contributing a Skill

Thank you for contributing to the Surpass IQ Community Skills library. This guide explains how to format and submit a skill.

---

## What is a Skill?

A Skill is a structured instruction set — typically a system prompt or workflow guide — that configures Surpass IQ to perform a specific task exceptionally well. Skills should be focused, tested, and useful to a broad audience.

---

## Submission Process

1. Go to the **[Submit a Skill](submit.html)** page and fill in the Google Form
2. The Surpass team will review your submission within 5 working days
3. If approved, a team member will format your skill into the correct file structure and merge it into the repository
4. The site updates automatically within ~1 minute of merging

You do not need a GitHub account or any coding knowledge to submit a skill.

---

## Skill File Format

Each skill lives in its own folder under `skills/` and consists of two files:

```
skills/
└── your-skill-id/
    ├── SKILL.md      ← The skill content
    └── meta.json     ← Metadata (title, description, category, etc.)
```

### `SKILL.md`

Write your skill in Markdown. A well-structured skill file includes:

| Section | Description |
|---|---|
| `# Title` | The skill name as an H1 heading |
| **Purpose** | One paragraph explaining what the skill does and when to use it |
| **How to Activate** | Brief instructions for loading the skill |
| **Skill Instructions** | The core instruction block (usually inside a fenced code block) |
| **Example Output** | A realistic example showing the skill in action |
| **Tips for Best Results** | 3–5 bullet points of practical guidance |

### `meta.json`

```json
{
  "id": "your-skill-id",
  "title": "Human-Readable Skill Title",
  "description": "One or two sentences shown on the skill card. Be specific about what the skill does.",
  "category": "Item Authoring",
  "tags": ["keyword1", "keyword2"],
  "author": "Your Name or Organisation",
  "version": "1.0",
  "date": "YYYY-MM-DD",
  "skill_file": "skills/your-skill-id/SKILL.md"
}
```

**Valid categories:** `Item Authoring`, `Tag Management`, `Bulk Workflows`, `Analysis`, `Other`

**Skill ID:** lowercase letters and hyphens only, e.g. `item-authoring`, `bulk-tagging-workflow`

---

## Quality Guidelines

- **One skill, one job** — focused skills are easier to use and maintain
- **Tested** — use the skill yourself before submitting and include a real example
- **Generalisable** — avoid hardcoding institution-specific content; parameterise where possible
- **Clear instructions** — another user should be able to activate and use the skill without asking you questions

---

## Updating an Existing Skill

If you'd like to update or improve an existing community skill, submit a new version via the Google Form and note which skill you're updating and what changed. The team will review and replace the existing file if the update is an improvement.
