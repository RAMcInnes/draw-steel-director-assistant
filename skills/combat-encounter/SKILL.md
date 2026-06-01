---
name: combat-encounter
description: Use when designing a combat encounter for a Draw Steel campaign. Provides narrative-first combat encounter-design principles, an ordered interview, and an output template. References stat blocks in book from the Draw Steel enemy reference; synthesizes Role/Tactics/Flavor only for entries missing from the reference.
---

# Combat encounter

## When to use / when not to use

Use this skill when the primary mode of resolution is expected to be violence — the GM is pre-shaping a scene that will most likely be fought, or a scene that is likely to break into a fight and the GM wants the combat pre-built. Use it even when the scene begins as a parley, if combat is the GM's planned payoff.

Do not use this skill when the scene is primarily about conversation (reach for `social-encounter` — it handles the combat-outbreak branch as a reaction) or primarily about navigation and discovery (reach for `exploration-encounter` — a fight that happens along the way is a complication inside that frame, not the frame itself).

## Craft principles

A combat encounter is not a list of stat blocks. It is a scene that happens to resolve through violence, and like every scene it needs a reason to exist, stakes the GM and players both care about, and a shape that isn't just "trade hit points until one side falls." Reach for the mechanics last, in service of the scene — not first, in place of it.

**Combat holds narrative weight.** Draw Steel is not a game of attrition, where many small trivial encounters weaken the heroes' resources to make a final epic clash more of a struggle. A quick combat with two bumbling guards at a gate that resolves in less than a round should not award Victory and should be rare. These can be fun roleplay moments, but most encounters when combat takes place should have high stakes for the heroes and the story. If an encounter doesn't carry narrative meaning, it shouldn't be a fight — handle it as brief roleplay or narration instead. The skill is allowed to push back during the interview when the user describes a low-stakes encounter: *"this might land better as a one-line description in session prep — no stat blocks, no map. Do you want to design it as a full combat encounter, or treat it as connective tissue?"*

Never make victory the only interesting outcome. Encounters that feel flat are encounters where the only axis is whether the PCs win. Add a second axis: a hostage to get out, a timer before something worse arrives, a secret escaping in the confusion, a moral cost to how the fight is prosecuted. When there is a second axis, "we won" becomes a partial answer rather than the whole one.

Treat terrain as a third participant in the fight. A featureless 30×30 room is a failure of imagination. Every combat worth running happens on ground that has opinions — elevation, cover, footing, hazards, moving parts, civilians in the crossfire — and those opinions should change as the fight progresses. The best terrain doesn't just decorate the space; it pressures decisions.

Enemies want something. Enemies who are merely trying to kill the PCs are the least interesting kind. Give every roster a motivation — they're guarding, delivering, fleeing, testing, feeding, bargaining, collecting. When enemies have goals, tactics emerge naturally, and the PCs get to exploit those goals to shape the fight rather than just grind HP.

Design for three resolution paths: victory, failure, and a third option. The third is almost always where the best play happens — flee, parley, partial capture, pyrrhic win, strategic retreat, "you beat them but the thing they were protecting is already out the back door." If the only way the table can resolve the scene is to fight to the last HP on one side, the encounter has flattened and play will flatten with it.

Plan one thing that can change mid-fight. Reinforcements arriving, an environmental shift (tide rising, fire spreading, bridge collapsing), a hidden participant revealing themselves, the target of the conflict escaping, an ally arriving, a player character's personal demon showing up. Give it a specific trigger condition — a round number, an HP threshold, a PC action — so it can actually fire. This is what keeps long fights from grinding.

Build the roster around role differentiation, not raw numbers. Five brutes is a worse encounter than two brutes, an artillery, and a skirmisher. A mixed roster forces real tactical choices about targeting, positioning, and action economy; a homogeneous roster collapses into "hit the nearest thing." When the user is vague about enemy composition, lean on the taxonomy file to mix roles rather than defaulting to a single type.

Mechanical content belongs in system books, not in encounter-design work. Hit points, damage dice, ACs, save DCs, conditions, recharge mechanics — these come from a source the GM already trusts, or they're marked for the GM to supply at the table. Synthesizing a stat block that looks right but hasn't been balanced is actively worse than writing nothing, because the GM is now holding a number they can't verify against anything.

### User additions

*Space for the user to add their own craft notes as the skill gets used. Leave the existing principles above intact; extend them here.*

## Inter-skill contracts

This skill participates in the inter-skill wire format documented at `${CLAUDE_PLUGIN_ROOT}/references/skill-contracts.md`:

- **Headers consumed.** When invoked from a `session-creation` flow, this skill reads the parent session's `## Prep` section and any linked NPC files (for allegiances and persuasion-fit) and location files (for atmosphere) named in the session's NPC and site lists. The canonical strings for those headers and the relative-link depth conventions for resolving the links live in the contracts file.
- **Headers produced.** Encounter files don't produce headers other skills consume; the file is a leaf artifact in the workflow tree. (Stat-block trailers and bundle-folder paths are agent-owned, not consumed by sibling skills.)

If the contracts file ever disagrees with text in this skill, the contracts file wins.

## Interview template

**One question per turn. Wait for the user's answer before advancing. Never batch questions into one reply.**

Every question is accompanied by 2–3 concrete suggestions anchored in these craft principles, the prior answers, and the **loaded campaign context** (NPCs, factions, locations, themes, and prior encounters from `campaign.md` and `encounters/`, per the director-assistant agent's context load). Generate them alongside the question so the user can pick one, tweak it, or supply something different — suggestions sharpen the ask from an open prompt into a menu without overriding the user's own answer. For questions backed by a catalog (encounter objectives, dynamic terrain, the enemy taxonomy), draw suggestions from that catalog; for everything else, synthesize them from the craft principles, prior answers, and campaign context.

**Let campaign context thread through the whole interview, not just the tie-in.** Antagonist motivations (Q4) can reference faction goals from `campaign.md`; stakes (Q6) can pull from Themes & Open Questions; terrain (Q7) can draw on Notable Locations when the scene sits in one; scene framing (Q1) can place recurring NPCs who'd plausibly be present; party state (Q2) can surface consequences from recent encounters. The tie-in question asked by the agent after the interview is for *explicit* connections the user wants named — it does not replace context-driven suggestions throughout.

**When invoked from a `session-creation` flow** (the user's request mentions a specific session, or the agent has the session in working context), additionally read the parent session's `## Prep` section. Use it to align the encounter's stakes, NPCs, and tone with the session's broader plan — e.g., if the session prep names a confrontation as the cliffhanger, frame the encounter to deliver that moment. Do not duplicate session-prep content into the encounter; reference and extend it. **Also load any linked NPC files** (`npcs/<slug>.md`) named in the session's NPC list and any linked location file (`locations/<slug>.md`) for the site this combat takes place at — pulling allegiances, persuasion-fit, and atmosphere directly from the canonical files keeps the encounter consistent with prior appearances.

Any question may be answered with *"you decide"* (or equivalent deferral). In that case, pick the suggestion that best fits the craft principles, prior answers, and loaded campaign context; surface the chosen suggestion inline so the user sees what was picked, and record it in the transcript so it remains revisable.

1. Where and when does this happen? Describe the scene as the party arrives.

**Stakes check.** Before going further: what makes this combat *matter*? *"What changes for the heroes — or the story — depending on how this fight goes?"* If the answer is "not much," surface the option to demote the encounter to a one-line description in session prep instead of designing it as a full encounter.

2. Where is the party *right now* — heroic-resource state, open personal threads, recent bruises that should color this fight? This is the stuff that lives *outside* `campaign.md`: what's been spent, whose storyline just landed a blow, who's nursing which grudge. Answer *"nothing special"* if none apply; the encounter will run on its own terms. On *"you decide"*, scan recent encounters in `encounters/` and the Themes & Open Questions in `campaign.md`, surface any consequence that could reasonably shape this fight, or fall through to "nothing to weave in today" if there's genuinely no hook.
3. What type(s) of enemy will the party face? (e.g., humanoid, undead, fiend, fey, beast — multiple types are fine if the encounter has a mixed group.) Answers here narrow the reference lookup.
4. Who are the antagonists, and what do they *want*? Name the specific enemy types you have in mind (e.g., hobgoblin captain, dire wolves, cult acolytes) — the skill will look them up in the enemy reference and embed their stat blocks.
5. What is the encounter's **objective** — the specific thing the heroes must accomplish? Pick from the catalog at `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/references/encounter-objectives.md` (Diminish Numbers, Defeat a Specific Foe, Get the Thing, Destroy the Thing, Save Another, Escort, Hold Them Off, Assault the Defenses, Stop the Action, Complete the Action) or describe a custom objective. Combined / Alternative / Changing Objective structures are also available — see the same file.
6. What's at stake beyond winning the fight? Why does this matter to the PCs or the world?
7. What is the terrain doing — how does the environment act as a third participant? If the user defers or is vague, suggest one or two features from the dynamic-terrain catalog at `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/references/dynamic-terrain.md` (which indexes environmental hazards, fieldworks, mechanisms, and siege engines), chosen to fit the scene, antagonists, and objective already on record.
8. What's one complication or escalation that could trigger mid-fight?
9. What do victory, failure, and a third option (flee, parley, pyrrhic win, partial victory/defeat) each look like?

*The tie-in question is asked by the agent after this interview, not here.*

## Enemy reference

User-maintained Draw Steel stat-block library at `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/references/enemies/` — one markdown file per creature category. The category index lives in `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/references/taxonomy.md` under `# Enemy categories` and maps user-named enemies ("goblins", "goblin cursespitter") to category files.

Key rules:
- **Never invent a stat block.** If an enemy isn't in the reference, flag it as *"[not in reference — GM to supply]"* and synthesize only Role / Tactics / Flavor.
- **Surface vague picks inline.** When the user names a category vaguely ("goblins"), pick a mix of variants and show what was chosen: *"Going with: 1 goblin cursespitter (leader) + 4 goblin warrior minions."*

**Optional setting flavor.** When the encounter takes place in a region or involves a faction from the campaign's published setting, additionally read `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/regions.md` and `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/factions.md` for descriptive flavor — use sparingly, to color the scene without inventing canon. Skills work gracefully when these references are missing or stubbed.

**Detailed lookup flow:** See `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/references/enemy-lookup.md`.
**Entry template:** See `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/references/enemy-entry-template.md`.

## Enemy taxonomy

When vague on enemy details (Q3, Q4), consult `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/references/taxonomy.md` to pick from Enemy Keywords, Organizations, Roles, and Categories rather than inventing — the skill maps vague answers to plausible combinations and surfaces its interpretation inline.

## Encounter strength

Formula for calculating party Encounter Strength (ES) at `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/references/encounter-strength.md`. The descriptive overview of what ES is lives in `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/vocabulary.md` under `## Encounter Strength (ES)`.

**Skill uses the ES formula in two spots:**
- *Sizing the roster (Q4):* once antagonists are named, compute the party's ES from PC count and levels (loaded at agent context-load time) and use it as the budget for picking the number and tier of enemies. The math is bookkeeping; don't surface it inline unless the user asks.
- *Output emission:* the Encounter Strength figure is emitted into the encounter output template alongside Difficulty Category, as GM reference.

If PC count and levels aren't in context, ask once before drafting; the answer carries forward to subsequent encounters in the same session.

## Encounter objectives

Catalog of combat objectives at `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/references/encounter-objectives.md` — 10 core objectives (Diminish Numbers, Defeat a Specific Foe, Get the Thing, Destroy the Thing, Save Another, Escort, Hold Them Off, Assault the Defenses, Stop the Action, Complete the Action) plus Combined / Alternative / Changing Objective structures. Each entry in the catalog includes Monster Roles and Organization, Map Advice, Difficulty Modifier, Success Condition, Victories, and Failure Condition.

Sourced from *Draw Steel: Monster Basics*. Each entry's Stamina and Victory numbers are emitted into the encounter output as GM reference.

**Skill uses the objective catalog in three spots:**
- *Interview Q5:* the user picks an objective from the catalog (by name) or describes a custom one. The skill records whichever they chose.
- *"You decide" fallback:* if the user defers on Q5, pick the catalog entry that best fits the antagonists, stakes, and terrain already on record — prefer non-"Diminish Numbers" objectives when the scene supports them (a second axis almost always sharpens the encounter).
- *Shaping Escalation, Terrain, and Outcomes:* once an objective is locked in, consult the catalog's Map Advice and Monster Roles sections when answering Q7 (terrain) and Q8 (escalation), and mirror the catalog's Success / Failure Conditions into Q9's Outcomes where they fit.

When combining objectives (e.g., assault the defenses *then* hold them off), name the combined shape explicitly in the output and list both component objectives.

## Dynamic terrain

Catalog of terrain objects at `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/references/dynamic-terrain.md`, which indexes four companion files:

- `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/dynamic-terrain/environmental-hazards.md` — natural terrain (brambles, corrosive pool, frozen pond, lava, quicksand, toxic plants, angry beehive).
- `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/dynamic-terrain/fieldworks.md` — temporary military fortifications and placed traps (archer's stakes, bear trap, flammable oil, hidey-hole, pavise shield, snare trap, spike trap).
- `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/dynamic-terrain/mechanisms.md` — built contraptions with trigger/effect pairs (column of blades, dart trap, pillar, portcullis, pressure plate, pulley, ram, switch).
- `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/dynamic-terrain/siege-engines.md` — crew-operated heavy weapons and fortifications (arrow launcher, boiling oil cauldron, catapult, exploding mill wheel, field ballista, iron dragon, watchtower).

Each entry uses the Tags / Source / Flavor / Tactics shorthand — full stat blocks live in the book. The catalog is user-maintained and user-extensible; the skill doesn't generate or update it when new entries are added.

**Skill uses the dynamic-terrain catalog in three spots:**
- *Interview Q7:* if the user describes a specific feature, record it and move on. If they defer or are vague, read `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/references/dynamic-terrain.md` and pick one or two features that fit the scene, antagonists, and objective already on record — surface the picks inline (*"Adding: a portcullis on the lane between the altar and the doors, plus a pressure plate 3 squares in front of it"*).
- *"You decide" fallback:* when the user defers entirely on terrain, default to one primary feature (the thing that pressures decisions) plus at most one secondary feature (flavor/complication). Don't clutter the map.
- *Shaping Escalation and Outcomes:* terrain picked here can drive Q8's complication (*the mill wheel starts rolling*, *the oil catches fire*, *the portcullis drops on round 3*) and Q9's third option (*sabotage the catapult instead of killing the crew*, *pull the switch to split the arena and flee*). Reach for the catalog's Tactics lines when writing those.

## Output template

See `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/references/encounter-output-template.md` for the full encounter output markdown template. The template includes sections for Scene, Objective, Antagonists, Enemy roster (with Encounter Strength and Difficulty Category), Stakes, Terrain, Escalation, Outcomes, and Ties to existing material.

## Anti-patterns

- **"Win-only" stakes** — if losing just means "roll new characters," the encounter has no second axis. Raise the non-death consequences.
- **Featureless terrain** — if the map has no features that change the fight, add at least one. A flat empty room is a failure state.
- **Single-track outcomes** — always provide a third option alongside victory and failure. Pyrrhic win, partial victory/defeat.
- **Inventing stat blocks** — if an enemy isn't in `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/references/enemies/`, do not synthesize mechanical numbers.
- **Enemy rosters without Role differentiation** — five brutes is a worse encounter than two brutes, an artillery, and a skirmisher. Lean on the taxonomy for role variety.
- **Ignoring the taxonomy** — when disambiguating vague user answers or filling "you decide," consult `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/references/taxonomy.md` first. Do not improvise keywords, organizations, roles, or categories that aren't in the taxonomy.
- **Defaulting every fight to "Diminish Numbers"** — if the scene plausibly supports Escort, Hold Them Off, Save Another, Stop the Action, or any other objective from `${CLAUDE_PLUGIN_ROOT}/skills/combat-encounter/references/encounter-objectives.md`, use that instead. "Defeat them all" is the least interesting objective available; reach for it last, not first.
- **Objective without a success condition** — naming the objective (e.g., "Stop the Action") is not enough. State the specific trigger the heroes must hit — what action, in how many rounds, against which target. The catalog entry for each objective tells you what to pin down.
- **Attrition-based encounter sequences** — do not design multiple small encounters *as a sequence* intended to drain the heroes' resources and weaken them for a later "real" fight. Each encounter the GM runs should hold narrative weight on its own. If an encounter doesn't carry stakes meaningful to the story or the heroes, don't make it a combat — handle it as brief roleplay or narration instead.

  **Diagnostic:** Before designing any encounter, ask: *What is this scene about?* If the answer is "resource management" or "wearing down the party," the scene doesn't belong in this skill's frame.

  **Rationalizations to reject:**

  | Excuse | Reality |
  |--------|---------|
  | "These 4 small fights each have narrative hooks" | Stacked consequences across encounters still function as attrition. Check if rest *between* them breaks the story — if not, it's attrition dressed as story. |
  | "The timer is a real stake, not pressure" | Test it: if heroes ignore the timer and face the consequences, do those consequences tell an interesting story, or just force faster ability spending? Real stakes invite choice; manufactured pressure eliminates it. |
  | "Reinforcements make the fight feel bigger" | Reinforcements that only add numbers (not narrative consequence) are hidden attrition. Real reinforcements change the story — they're tied to an enemy's goal, a deadline, or a reveal. |
  | "Flee and Negotiate are available as third options" | A third option isn't real if it costs the same resources as fighting. Each path must create a *different narrative consequence* (enemy escapes as nemesis vs. dies vs. becomes ally), not just a different resource cost. |
  | "The narrative calls for immediate continuation" | If a night of downtime would break the story, the sequence was designed for back-to-back pressure, not story inevitability. |
  | "This trivial fight is just a warm-up" | Trivial fights over in a round shouldn't award Victory. Handle them as brief roleplay or narration — not combat encounters.

  **The path-viability test:** Remove one resolution path entirely and ask *"does the encounter still make sense?"* If yes, that path wasn't genuinely appealing — it was just an efficiency option dressed as a choice.
