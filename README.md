# Koda Skills Marketplace

This repository is the official marketplace for [Koda](https://github.com/antojunimaia-ui/Koda) agent skills.

Skills are Markdown files that inject specialized instructions into Koda's context on demand. Users install them directly from the Koda desktop app (Settings → Skills).

---

## Repository Structure

```
koda-skills/
  index.json              ← master index of all published skills (required)
  skills/
    <skill-name>/
      skill.md            ← the skill content (required)
  README.md
```

---

## How to Add a New Skill

### 1. Create the skill folder

Create a folder inside `skills/` using the skill's name in **kebab-case**:

```
skills/my-skill-name/
```

### 2. Create `skill.md`

This is the file Koda downloads and injects into the agent's context. It must start with a YAML front-matter block.

**Template:**

```markdown
---
name: my-skill-name
version: 1.0.0
description: One sentence describing what this skill does.
triggers: [keyword1, keyword2, keyword3]
---

Your skill instructions go here. Write in second person, addressing the agent directly.

Explain the rules, patterns, and standards the agent should follow when this skill is active.
Use Markdown freely — headers, code blocks, bullet lists all work.
```

**Front-matter fields:**

| Field | Required | Description |
|---|---|---|
| `name` | yes | Must match the folder name and the entry in `index.json`. Kebab-case. |
| `version` | yes | Semantic version. Must match the `version` in `index.json`. Start at `1.0.0`. |
| `description` | yes | Short description shown in the marketplace UI. One sentence. |
| `triggers` | yes | Array of keywords. When the user's message contains any of these words, Koda may auto-load the skill. |

### 3. Register in `index.json`

Add an entry to the root `index.json` array:

```json
{
  "name": "my-skill-name",
  "description": "One sentence describing what this skill does.",
  "author": "your-github-username",
  "version": "1.0.0",
  "tags": ["tag1", "tag2"],
  "triggers": ["keyword1", "keyword2", "keyword3"]
}
```

**Fields:**

| Field | Required | Description |
|---|---|---|
| `name` | yes | Must match the folder name and the `name` in `skill.md`. |
| `description` | yes | Shown in the marketplace browse tab. |
| `author` | yes | Your GitHub username. |
| `version` | yes | Semantic version. Start at `1.0.0`. |
| `tags` | yes | Used for search filtering in the UI. Can overlap with triggers. |
| `triggers` | yes | Same array as in `skill.md` front-matter. Keep them in sync. |

---

## Updating a Skill

1. Edit `skills/<skill-name>/skill.md` with your changes.
2. Bump the `version` field in `index.json` (e.g. `1.0.0` → `1.1.0`).

---

## Writing Good Skills

- **Address the agent directly.** Write "You are in X mode. Apply these rules..." not "The agent should...".
- **Be specific.** Vague instructions produce vague behavior. Concrete rules produce consistent results.
- **Scope it tightly.** A skill about React should only contain React rules, not general TypeScript advice.
- **Use examples.** Code blocks with good/bad examples are more effective than abstract descriptions.
- **Keep it focused.** One skill, one domain. If it covers too much, split it.

---

## Example

A complete, minimal skill:

**`skills/tailwind-expert/skill.md`**

```markdown
---
name: tailwind-expert
version: 1.0.0
description: Tailwind CSS v4 utility-first patterns and best practices.
triggers: [tailwind, css, styling, className]
---

You are operating in **Tailwind Expert** mode.

- Use utility classes directly in JSX. Never write custom CSS unless Tailwind cannot achieve the result.
- Prefer responsive prefixes (`sm:`, `md:`, `lg:`) over media query hacks.
- Use `@apply` in CSS files only for repeated patterns shared across many components.
- Avoid arbitrary values (`w-[347px]`) when a standard scale value is close enough.
- Group classes by category: layout → spacing → typography → color → effects.
```

**Entry in `index.json`:**

```json
{
  "name": "tailwind-expert",
  "description": "Tailwind CSS v4 utility-first patterns and best practices.",
  "author": "antojunimaia-ui",
  "version": "1.0.0",
  "tags": ["tailwind", "css", "frontend"],
  "triggers": ["tailwind", "css", "styling", "className"]
}
```
