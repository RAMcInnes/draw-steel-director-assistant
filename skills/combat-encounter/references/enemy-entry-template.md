---
name: enemy-entry-template
description: Template for creating monster stat block entries in enemy reference files
type: reference
---

# Enemy Category and Entry Template

## File Structure

Each enemy reference file (e.g., `references/enemies/goblins.md`) contains a category-level section followed by individual variant entries.

## Category-Level Section (Top of File)

```markdown
# <Category name>

*Source: <Book title>, pp. XX–YY. Reference only — stat blocks live in the book.*

<2–3 paragraphs describing who these creatures are, their culture, motivations, and role in the world.>

- **Key Feature 1.** Explain how this shapes encounters or tactics.
- **Key Feature 2.** Relevant cultural or mechanical trait.
- **Languages.** <Most common languages for this category.>

## Shared traits (or "Shared mechanics")

- **Trait Name.** How it works and tactical implications.
- <repeat for each universal trait in this category>

## <Category> Malice features

<Describe any encounter-wide Malice abilities usable by any member of this category. Optional if there are none.>

---
```

## Individual Variant Entry Template

For each variant inside the category file, use this format:

```markdown
## <Variant name>

**Role:** <one of: brute, artillery, skirmisher, controller, leader, minion — see `taxonomy.md` for the authoritative list>
**Tags:** <level, rarity (elite/solo), EV cost, category/type, optional special trait>
**Source:** <book + page, or "homebrew">

**Flavor:** One or two sentences on appearance and presence — what the party sees and feels when this variant enters play.

**Tactics:** Target priority, positioning, signature moves, how they react under pressure, and interaction with category features.
```

## Metadata Fields

**Source**, **Tags**, and **Role** are GM-library metadata only — used for organizing, searching, and calculating encounter strength. They never appear in the drafted encounter output.

