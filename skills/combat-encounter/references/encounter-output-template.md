---
name: encounter-output-template
description: Template for the final drafted combat encounter output document
type: reference
---

# Encounter Output Template

Use this template when drafting the final combat encounter document after completing the interview questions.

```markdown
# <Encounter title>

**Type:** combat
**System:** Draw Steel
**Date drafted:** YYYY-MM-DD

## Scene
Where, when, and the sensory hook the moment the party arrives.

## Objective
Named objective from `references/encounter-objectives.md` (or custom), with the specific success condition the heroes must meet. For combined or alternative objectives, list each component and whether all-required or any-required.

## Stakes
What's on the line beyond winning the fight — for the PCs, the world, or both.

## Antagonists
Who they are and what they *want* collectively. Goals, motivations, and the dramatic role they play in the scene. Narrative only — per-enemy detail lives in the next section.

## Enemy roster
One entry per distinct enemy type named in question 3, each in the form:

**<Enemy name>** —  
**EV:** …  
**Role:** …  
**Flavor:** …  
**Tactics:** …  

In a new line below that line:
- *If the enemy exists in `references/enemies/`:* embed the page number to the reference's stat block.
- *If the enemy is missing from the reference:* write *"[not in reference — GM to supply]"*. Role/Flavor/Tactics are still synthesized so the GM has something to work with at the table.

**Stat block image.** When the variant's slug appears in the skill's stat-block manifest (`${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/assets/enemies/statblocks/manifest.json`), embed the image directly below the entry using a relative path that will resolve against the encounter's bundle folder:

```markdown
![<Enemy name>](<encounter-slug>/<variant-slug>.png)
```

Where `<encounter-slug>` matches the encounter filename (e.g. `2026-05-05-goblin-ambush`) and `<variant-slug>` matches the manifest key. The ship step copies the image into this folder; the relative path resolves wherever the encounter MD is rendered (VS Code preview, Pandoc, static site generators). For variants without a manifest entry, omit the image embed.

**Encounter Strength (ES):** At the bottom of the enemy roster section, calculate and display the total Encounter Strength by summing all individual monster EVs. Format: **Total ES: [sum]** (e.g., if the roster contains one monster with EV 16 and two with EV 8 each, total ES is 32).

**Party ES (agent-computed).** Read the `## Party (…)` heading from `campaign.md`, extract the integer level from inside the parenthetical (accept any of `Level: N`, `Level N`, `level N`, `lvl N`, or just a bare number — read semantically, not by strict regex), count the hero entries listed under it, then compute per-hero ES and Party ES using the formula in `references/encounter-strength.md`. (Reference check: 4 heroes at level 3 → Party ES = 40.) Emit the computed value inline as **Party ES: [value]** immediately after Total ES. The Difficulty Category breakpoints below reference "one hero's ES" — that's the same per-hero value from the formula. If `campaign.md` is missing a level number or the hero count is unclear, emit *"[Party ES not derivable from campaign.md — GM to supply]"* and skip the Difficulty Category.

**Difficulty Category (agent-computed).** Compare Encounter ES to Party ES and emit the matching category inline as **Difficulty: [category]**. Do not make the GM do this math at the table.

- **Trivial:** Encounter ES < (Party ES − one hero's ES)
- **Easy:** Encounter ES < Party ES
- **Standard:** Party ES ≤ Encounter ES < (Party ES + one hero's ES)
- **Hard:** (Party ES + one hero's ES) ≤ Encounter ES ≤ (Party ES + 3 heroes' ES)
- **Extreme:** Encounter ES > (Party ES + 3 heroes' ES)

## Terrain
Environmental features acting as a third participant. How the space pushes the fight.

**Dynamic terrain options** (always include 1–2, even if the GM ultimately cuts them):
Pick 1–2 entries from the dynamic-terrain catalog at `references/dynamic-terrain.md` that fit the scene, antagonists, and objective. For each, write one line in the form:

- **<Object name>** *(optional)* — one-sentence tactical purpose (what lane it shapes, what it punishes, or how it pressures decisions). *See `references/dynamic-terrain/<catalog-file>.md`.*

Mark each as *(optional)* so the GM can drop them without disrupting the core encounter; the suggestions are scaffolding, not mandates.

## Escalation
One complication or twist that can trigger mid-fight, and the condition that triggers it.

## Outcomes
- **Victory:** …
- **Failure:** …
- **Third option** (pyrrhic win, partial victory/defeat): …

## Ties to existing material
*Included only if the tie-in question surfaced connections. Omit the section otherwise.*

<!-- statblocks: variant-slug-1, variant-slug-2, variant-slug-3 -->
```

## Statblocks trailer

The encounter draft MUST end with an HTML-comment trailer listing every variant slug used in the encounter, comma-separated, on a single line:

```
<!-- statblocks: bugbear-roughneck, bugbear-sneak, goblin-runner -->
```

This is a machine-readable contract between the skill and the encounter-designer agent's ship step. The ship step parses this line, looks each slug up in the stat-block manifest, and copies the corresponding image files into the encounter's bundle folder adjacent to the MD file. Never re-parse the encounter prose for monster names — the trailer is authoritative.

Emit slugs that actually exist in `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/assets/enemies/statblocks/manifest.json`. For variants whose slugs aren't in the manifest, omit them from the trailer. If no variants have images available, emit an empty trailer: `<!-- statblocks: -->`.
