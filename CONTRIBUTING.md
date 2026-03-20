# Contributing to Vibe Coding Skills Guild

Thanks for wanting to contribute! This project thrives on community input.

Whether you discovered a handy Claude Code skill, want to polish an existing one, or can
help translate -- there's a place for you here. No deep technical background needed.

---

## Pick Your Track

### 1. Add a Skill

Found a Claude Code skill we're missing? Awesome. We catalog 1,282+ skills and counting,
so there's always room for more.

**Before you start:**
- Search the existing tables in `skills/` to make sure it isn't already listed.
- One skill per row. If a skill does multiple things, pick its primary purpose.

### 2. Improve Existing Skills

Better descriptions, clearer examples, or fixed typos -- all welcome. Small improvements
add up fast when 1,000+ people read the same table.

### 3. Translate

Help us reach more vibe coders worldwide. Translations live in `guide/` or alongside
the original file with a language suffix (e.g., `SKILLS_GUIDE_ES.md`).

If you're starting a new language, open an issue first so we can coordinate.

---

## PR Workflow

Keep it simple:

1. **Fork** this repo.
2. **Create a branch** with a descriptive name:
   ```
   git checkout -b add-skill-docker-compose
   ```
3. **Make your changes** and commit with a clear message:
   ```
   git commit -m "Add Docker Compose skill to automation table"
   ```
4. **Push** your branch and open a Pull Request against `main`.
5. Fill in what you changed and why. A sentence or two is fine.

We'll review and merge quickly -- no red tape.

---

## Skill Format Spec

Every skill goes in a Markdown table with three columns:

```markdown
| Skill | What it does | Level |
|-------|-------------|-------|
| `/docker-compose` | Generate docker-compose.yml from description | [AUTO] |
| `/explain-error` | Translate stack traces into plain English | [CORE] |
```

- **Skill** -- The slash command or skill name, in backticks or code format.
- **What it does** -- A short, plain-language description (see Style Guide below).
- **Level** -- One of the four classification tags.

---

## Level Classification

| Tag | Meaning | Example |
|-----|---------|---------|
| `[CORE]` | Essential -- most people need this | `/commit`, `/explain-error` |
| `[SPEC]` | Specialized -- for specific use cases | `/latex-to-pdf`, `/prisma-migrate` |
| `[SEC]` | Security-focused | `/audit-deps`, `/scan-secrets` |
| `[AUTO]` | Automation | `/ci-pipeline`, `/docker-compose` |

When in doubt, use `[SPEC]`. We can always re-classify during review.

---

## Style Guide

1. **Keep descriptions under 50 characters.** If you can't, the description is too complex.
2. **No jargon.** Write for someone who builds with AI but isn't a developer.
   - Bad: "Scaffold a CRUD REST API with JWT auth middleware"
   - Good: "Create a basic API with login support"
3. **Be specific.** Say what the skill *does*, not what it *is*.
   - Bad: "A tool for databases"
   - Good: "Create database tables from plain English"
4. **Start with a verb.** Generate, Create, Fix, Convert, Scan, etc.
5. **No periods at the end** of table descriptions.

---

## What Makes a Good Contribution

- Adds something genuinely useful for vibe coders
- Follows the table format and style guide
- Doesn't duplicate an existing skill
- Includes the right level tag

Don't overthink it. If you use a skill and it helps you, others probably want it too.

---

## Questions?

Not sure where a skill belongs? Confused about the format? Just curious?

[Open an issue](../../issues) -- we're happy to help.
