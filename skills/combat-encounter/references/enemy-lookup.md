---
name: enemy-lookup
description: Detailed flow for resolving user-named enemies to stat-block reference files
type: reference
---

# Enemy Lookup Flow

## Library structure

User-maintained Draw Steel stat-block library at `references/enemies/`, with **one markdown file per creature category**. A *category* groups related variants under a shared keyword, organization, and role (e.g., leader, minion, support).

Source PDFs (if retained) live in the parallel `assets/enemies/` folder. The skill never reads those directly — only the markdown files under `references/`.

## Category index

Resolution from "enemy the user named" to "which category file to read" happens via an index maintained in `references/taxonomy.md` (under `# Enemy categories`). Each index line carries the category name, a link to the category file, and a description:

```markdown
- [Goblin](enemies/goblin.md) — small humanoid minions who use hit-and-run tactics and curses; found in caves, ruins, and forests; often serve stronger masters but can be a threat in numbers.
- [Hobgoblin](enemies/hobgoblin.md) — larger humanoid elites who organize goblins into militias and warbands; disciplined and territorial.
```

The category index is user-maintained and user-extensible; the skill doesn't generate it or update it when new categories are added.

## Lookup flow

1. Read the `# Enemy categories` section of `references/taxonomy.md` to resolve each enemy named in Q2 and Q3 to a file. Category-level names ("goblins") and variant names ("goblin cursespitter") both resolve to the same category file.
2. Read the resolved category file(s) once. The file contains all variants for that category; scan `^## ` headings to find available variants.
3. **If the user named a specific variant** in Q3 (e.g., "goblin cursespitter"), include the exact page number to the reference's stat block.
4. **If the user named the category vaguely** in Q2 (e.g., "goblins"), pick a mix of variants that fits the encounter's objective, stakes, and role composition — typically a leader plus minions, or whatever the catalog's Monster Roles advice calls for. **Surface the choice inline** so the user sees what was picked (*"Going with: 1 goblin cursespitter (leader) + 4 goblin warrior minions"*).
5. **If no category in the index matches** the user's named enemy, flag the stat-block portion as *"[not in reference — GM to supply]"* and synthesize only the narrative metadata (Role / Tactics / Flavor). Never invent a stat block.
6. **Category-only deferrals** (user says "undead" without naming a category) — filter the index to categories matching that keyword and pick one (or more) that fit the encounter; surface the pick inline.

