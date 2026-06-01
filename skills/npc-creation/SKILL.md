---
name: npc-creation
description: Use when adding a new NPC (Non-Player Character) to a Draw Steel campaign — standalone (the Director wants a detailed NPC file) or mid-flow when campaign-creation, arc-creation, or session-creation surface a new NPC worth a file. Captures voice, behavior, allegiances, persuasion-fit, hooks, and location attachment. Writes per-NPC files to npcs/<slug>.md and updates npcs/index.md.
---

# NPC creation

## When to use / when not to use

Use this skill when a new NPC needs a file in the campaign's `npcs/` folder. Two invocation paths:

- **Standalone** — the Director wants to add an NPC outside any other prep flow. *"Add the warlord Saxton."*
- **Mid-flow** — invoked from `campaign-creation`, `arc-creation`, or `session-creation` when those skills name a new NPC. The parent skill calls `npc-creation`, the file gets written, the parent skill drops the link back into its prep.

Do not use this skill to revise an existing NPC (use revision mode on the NPC file directly), to design a scene the NPC appears in (use the matching encounter skill), or to capture session-specific details about an NPC (those go into the session prep's per-NPC notes, not the NPC file).

**If the NPC is being used, assume they're worth the full file.** This skill runs one interview, not a branched short/long pair. Truly incidental NPCs (a tavern keeper met once, a named guard at a gate, a peasant the heroes interview about a rumor) belong as a one-line entry in the session prep's NPC list, *not* as their own file. The `session-creation` skill captures those inline; if the Director invokes `npc-creation` for one, that's a signal to either commit to the full file or push the entry back to session prep.

## Craft principles

NPCs are people, not stat lines. Five-field shape from the rulebook's *Creating NPCs* guidance: name+role, distinguishing feature, voice cue, one distinct behavior, one flaw. Plus a kernel of motivation — why would they help, or what stops them.

**One distinct behavior, one flaw.** Multiple flaws make NPCs *unlikable*, not authentic. The rulebook is direct: *"If all the people the characters come across are villainous, apathetic, or selfish, the players won't feel very motivated to get their heroics on."* Authentic NPCs need texture, not catalogues of shortcomings.

**Voice cues travel.** A one-line voice cue ("clipped military beats", "talks like a pirate, drops the H's", "high-pitched, voice cracks when angry") is what the Director needs at the table. A paragraph of literary description doesn't reach the chair fast enough.

**Persuasion-fit over stats.** What this NPC *responds to* and what *bounces off* matters more than their numbers. A coward is easy to intimidate; a battle-hardened soldier is impossible to awe. A bribe works for a corrupt noble; a wealthy queen has no interest in coin. Capture both lists. (Cross-references the same craft principle in `social-encounter`.)

**Allegiances, not biographies.** Major NPCs need to know whose side they're on — a faction tag, an enemy tag, who they owe — so they stay coherent across appearances. Full backstories are a trap; let them accrete through play in the file's `## Notes` section.

**Hooks they're attached to.** Each NPC names which PC's hooks (from `campaign.md`'s `## PC Hooks` section) or which arc's threads they're tangled in. This is what `arc-creation` and `session-creation` consult when picking who to bring back. An NPC attached to no thread is a sign the entry should probably be a one-line note in session prep instead of a file.

**Locations are durable anchors.** NPCs name where they're based, work, or are typically found. This is the spatial anchor `session-creation` consults to answer "if the heroes go to X, who do they find?" — distinct from "first appearance" (which is temporal). An NPC may be attached to multiple locations (a traveling bard, a faction lieutenant who patrols several sites). If the named location doesn't yet exist, this skill invokes `location-creation` mid-flow to create it.

**Files are for NPCs that earn them.** Every NPC file is overhead — a row in `npcs/index.md`, a path to maintain, a name to keep consistent across appearances. NPCs the heroes will only meet once belong as a one-line entry in session prep's `### NPCs likely to appear`, not as their own file. When in doubt, push back: *"this might land better as a session-prep line — do you want a full file?"*

### User additions

*Space for the user to add their own craft notes as the skill gets used. Leave the existing principles above intact; extend them here.*

## Reference consumption

When an NPC's background invokes a Draw Steel ancestry, culture or career, consult `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/ancestries.md`, `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/cultures.md` and `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/careers.md` for descriptive flavor. Surface relevant entries inline as suggestions for voice/behavior/allegiance.

When an NPC is anchored to a region or affiliated with a faction in the published setting, consult `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/regions.md` and `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/factions.md`.

Skills work gracefully when reference files are missing or stubbed — note "no <category> reference on file — proceeding with generic suggestions" and continue. Never block on missing references.

When the interview reaches the location-attachment question, scan `~/draw-steel-campaigns/<campaign-slug>/locations/index.md` for existing locations. Surface matches as link candidates. If the user names a location not in the index, invoke `location-creation` mid-flow.

When scanning `npcs/index.md` for collision checks or `locations/index.md` for link candidates, locate columns by **header-name match**, not by position — column orderings are documented in `${CLAUDE_PLUGIN_ROOT}/references/skill-contracts.md`.

## Inter-skill contracts

This skill participates in the inter-skill wire format documented at `${CLAUDE_PLUGIN_ROOT}/references/skill-contracts.md`:

- **Mid-flow return.** When invoked mid-flow from `campaign-creation`, `arc-creation`, `session-creation`, or `location-creation`, return exactly one markdown link string of the form `[<NPC Name>](<relative-path>)`, where the relative path is correct for the parent skill's output location per the contracts file's Relative-link depths table. Standalone invocations return the absolute file path plus a one-line confirmation instead.
- **Headers consumed.** This skill reads `## Factions` from `campaign.md` (Allegiances suggestions) and the index files cited above; the canonical header strings for those live in the contracts file.

If the contracts file ever disagrees with text in this skill, the contracts file wins.

## Interview template

**One question per turn. Wait for the user's answer before advancing. Never batch questions into one reply.**

Every question accepts a *"you decide"* / *"skip"* / *"leave blank"* deferral. On *"you decide"*, generate a plausible answer anchored in the craft principles, prior answers, and the loaded references; surface inline as *"Going with: …"* and record. On *"skip"*, record the field as empty.

### Interview (11 questions)

1. **Name + role** — short title (used as filename slug) plus one-phrase role. *"Saxton Vail — the warlord usurping Greysmark."*
2. **Distinguishing feature** — one short line, sight or scent. *"Burn scar across his right hand."*
3. **Voice cue** — one line, how they sound. *"Clipped military beats, never raises his voice."*
4. **One distinct behavior** — a thing they do that makes them recognizable in scene. *"Taps signet ring when thinking."*
5. **One flaw** — a single weakness, vulnerability, or unattractive trait. *"Vain about his lineage; can be drawn out by genealogical flattery."* One flaw is the cap.
6. **Kernel of motivation** — what they want, framed as the *why*. What would make them help the heroes? What would stop them?
7. **Persuasion-fit** — two short lists. *Responds to:* (intimidation, well-placed bribe, appeals to honor, displays of competence, shared grief, etc.). *Bounces off:* (approaches that won't work — incorruptible to bribes, immune to bluster, doesn't care about lineage).
8. **Allegiances** — factions, enemies, who they owe. Pull from `campaign.md`'s `## Factions` and the setting factions reference loaded above (`${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/factions.md`).
9. **Hooks/threads attached to** — which PC Hook from `campaign.md`'s `## PC Hooks` section, or which arc's threads. *"Sorin's complication — Saxton is the patron Sorin offers her services to."*
10. **Location(s) attached to** — where this NPC is based, works, or is typically found. Scan `locations/index.md` for matches; if the named location doesn't exist, invoke `location-creation` mid-flow to create it. An NPC may name multiple locations.
11. **First appearance** — session/encounter where introduced, or *"not yet"* if pre-prep.

## Output template

See `${CLAUDE_PLUGIN_ROOT}/skills/npc-creation/references/output-template.md`.

The agent ships the file to `~/draw-steel-campaigns/<campaign-slug>/npcs/<slug>.md` and appends a row to `npcs/index.md`.

## Anti-patterns

- **Files for NPCs the heroes will meet once** — incidental NPCs belong as a one-line entry in session prep's `### NPCs likely to appear`, not as their own file. If you can't fill in allegiances, hooks, or a location attachment for an NPC, that's a signal they don't need a file.
- **Multiple flaws** — one is the cap. Multiple flaws turn authentic NPCs into authentically unlikable ones fast.
- **Biographies in lieu of allegiances** — backstory accretes through play. Allegiances are what the Director needs at-prep.
- **NPCs without location attachment** — an NPC who isn't anchored anywhere is hard to bring back. The skill enforces this field; *"none"* / *"travels widely"* is acceptable, but the field can't be skipped.
- **Listing NPCs in location files** — the inverse direction is one-way (NPC → location). Don't try to populate `locations/<slug>.md` with anchored NPCs; the location file omits that. Reverse lookup is by grepping `npcs/` for the location's slug.
- **Inventing facts about existing NPCs** — if revising an NPC the campaign already has, use revision mode on the existing file. Don't re-create.
