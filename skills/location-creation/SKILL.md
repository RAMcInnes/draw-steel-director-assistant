---
name: location-creation
description: Use when adding a new location to a Draw Steel campaign — standalone (the Director wants a detailed location file) or mid-flow when campaign-creation, arc-creation, session-creation, or npc-creation surface a new location worth a file. Captures mood, sensory hooks, purpose at the table, faction control, hooks, notable features, and connected locations. Writes per-location files to locations/<slug>.md and updates locations/index.md.
---

# Location creation

## When to use / when not to use

Use this skill when a new location needs a file in the campaign's `locations/` folder. Two invocation paths:

- **Standalone** — the Director wants to add a location outside any other prep flow. *"Add the city of Greysmark."*
- **Mid-flow** — invoked from `campaign-creation`, `arc-creation`, `session-creation`, or `npc-creation` when those skills name a new location. The parent skill calls `location-creation`, the file gets written, the parent skill drops the link back into its prep.

Do not use this skill to revise an existing location (use revision mode on the location file directly), to design a scene that takes place at the location (use the matching encounter skill), or to capture session-specific details about how the location appears tonight (those go into the session prep's per-site notes, not the location file).

**If the location is being used, assume it's worth the full file.** This skill runs one interview, not a branched short/long pair. Truly incidental sites (a forest clearing where a single ambush happens, a tavern visited once) belong as a one-line entry in session prep's `### Specific sites`, *not* as their own file. The `session-creation` skill captures those inline; if the Director invokes `location-creation` for one, that's a signal to either commit to the full file or push the entry back to session prep.

## Craft principles

**Locations have a purpose at the table.** Every location with a file should answer: *why do heroes come here, what do they discover, what do they leave with?* A location without a reason to visit it is set dressing and belongs in prose (in session prep), not a file. The interview enforces this — if a Director can't fill in the *purpose* and *discovery* fields, that's a signal the entry should be a session-prep line, not a file.

**General locations vs specific sites.** A *general location* is a settlement, region, or large landmark — a city, a desert, a forest, an entire kingdom. A *specific site* is where a scene plays out — a building, a clearing, a bridge, a city square. Both can have files; they differ in what's worth capturing. General locations focus on mood and inhabitants; specific sites focus on scene shape and what heroes can do there. (Already a craft principle in `session-creation`; carries over.)

**Sensory hooks across all senses.** What does this place look, sound, smell, feel like on arrival? At least three of the four. The opening sense-line is what the Director needs ready when the heroes step through the door. Improvising sensory hooks on the fly produces only sight; writing them down up front gives every sense its turn.

**Mood is a one-word handle.** Tense, safe, dire, eerie, festive, oppressive, vibrant — pick one. The mood is what the Director plays toward; nuance accretes through scenes. A multi-paragraph mood description is a sign the file is over-detailing.

**Hooks the location is attached to.** Like NPCs, locations name which threads or arcs they're tangled in. A location that doesn't connect to any current thread is probably set dressing. The hook attachment is what `arc-creation` and `session-creation` consult when picking where to send the heroes.

**Inhabitants come from query, not duplication.** Major locations name which factions hold or contest the place. Specific NPCs anchored here are *not* listed in the location file — they're discovered by grepping `npcs/` for the location's slug. This avoids the sync-drift problem (when an NPC moves, only one file needs updating).

**Don't pre-detail what play hasn't pressed on.** A market square gets one line about *what the heroes notice first* until a scene actually plays there. The rulebook's *Start Small / Keep Things Vague* principle from chapter 15 applies at the location layer too — overpreparation is wasted work the moment players surprise you.

### User additions

*Space for the user to add their own craft notes as the skill gets used. Leave the existing principles above intact; extend them here.*

## Reference consumption

When the location is part of the published Draw Steel setting, consult `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/regions.md` for descriptive flavor. When a faction holds or contests the location, consult `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/factions.md`.

Skills work gracefully when reference files are missing or stubbed — note "no setting reference on file — proceeding with generic suggestions" and continue. Never block on missing references.

When the interview reaches the connected-locations question, scan `~/draw-steel-campaigns/<campaign-slug>/locations/index.md` for existing locations to link to. Surface matches as link candidates.

When scanning `locations/index.md`, locate columns by **header-name match**, not by position — column orderings are documented in `${CLAUDE_PLUGIN_ROOT}/references/skill-contracts.md`.

## Inter-skill contracts

This skill participates in the inter-skill wire format documented at `${CLAUDE_PLUGIN_ROOT}/references/skill-contracts.md`:

- **Mid-flow return.** When invoked mid-flow from `campaign-creation`, `arc-creation`, `session-creation`, or `npc-creation`, return exactly one markdown link string of the form `[<Location Name>](<relative-path>)`, where the relative path is correct for the parent skill's output location per the contracts file's Relative-link depths table. Standalone invocations return the absolute file path plus a one-line confirmation instead.
- **Headers consumed.** This skill reads `## Factions` from `campaign.md` (Faction control suggestions) and the index files cited above; the canonical header strings for those live in the contracts file.

If the contracts file ever disagrees with text in this skill, the contracts file wins.

## Interview template

**One question per turn. Wait for the user's answer before advancing. Never batch questions into one reply.**

Every question accepts a *"you decide"* / *"skip"* / *"leave blank"* deferral. On *"you decide"*, generate a plausible answer anchored in the craft principles, prior answers, and the loaded references; surface inline as *"Going with: …"* and record. On *"skip"*, record the field as empty.

### Interview (10 questions)

1. **Name + type** — short title (used as filename slug) plus type. *"Greysmark — city."* / *"The Undercroft — dungeon."* / *"Crow Bridge — specific site."*
2. **General location or specific site?** — informs which questions land hardest. (A city is general; a building inside the city is specific.)
3. **Mood** — one-word handle. *"Tense."* / *"Eerie."* / *"Festive."*
4. **Senses on arrival** — sight / sound / smell / feel; at least three of the four. *"Sight: low gray buildings under a perpetual overcast. Sound: bells from the keep, off the hour. Smell: rain on stone, woodsmoke. Feel: damp wind off the cliffs."*
5. **Why heroes come here** — the location's purpose at the table. *"To petition Saxton's court for safe passage."* / *"To investigate the seal that broke."*
6. **What they can discover** — information, NPCs, items the location yields. Pull from grep of `npcs/` for the location's slug as suggestions for "NPCs found here."
7. **Faction control or contest** — which factions hold or compete for the place. Pull from `campaign.md`'s `## Factions` and the setting factions reference loaded above (`${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/factions.md`).
8. **Hooks/threads attached to** — which arcs, which PC Hooks. *"Sorin's complication — Saxton's seat is where Linn was last seen."*
9. **Notable features / hazards** — 1–3 distinguishing physical or environmental elements. *"The Eyrie tower; the sealed undercroft beneath; the perpetual fog off the Greymere."*
10. **Connected locations** — neighboring sites a Director might pivot to (gives `session-creation` a routing menu). Scan `locations/index.md` for existing locations to link. *"Crow Bridge (south); the Undercroft (beneath the keep)."*

## Output template

See `${CLAUDE_PLUGIN_ROOT}/skills/location-creation/references/output-template.md`.

The agent ships the file to `~/draw-steel-campaigns/<campaign-slug>/locations/<slug>.md` and appends a row to `locations/index.md`.

## Anti-patterns

- **Files for sites the heroes will visit once** — incidental sites belong as a one-line entry in session prep's `### Specific sites`, not as their own file. If you can't fill in *purpose* and *what they can discover*, that's a signal the entry should be a session-prep line.
- **Listing NPCs in the location file** — violates the one-direction rule. NPCs name their location; locations don't list NPCs. Use grep for the reverse query.
- **Pre-detailing locations the heroes haven't pressed on** — a market square gets one line until a scene actually plays there. *Start Small / Keep Things Vague* applies.
- **Multi-paragraph mood descriptions** — mood is a one-word handle. Multi-paragraph means the file is over-detailing.
- **Inventing setting canon** — if the location is part of the published setting, pull from `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/regions.md`. If the campaign uses a custom setting, the user authors lore separately rather than the skill fabricating it.
