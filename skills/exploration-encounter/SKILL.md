---
name: exploration-encounter
description: Use when designing an exploration encounter for a Draw Steel campaign. Provides narrative-first exploration-design principles (sensory hook, layered reveals, time pressure, fail-forward), an ordered interview, and an output template. Always loads the Draw Steel Tests and Skills rulesets, and conditionally loads the Hiding & Sneaking, Group Tests, and Montages subsystems when the encounter's content calls for them.
---

# Exploration encounter

## When to use / when not to use

Use this skill when the primary mode of resolution is discovery, investigation, navigation, or traversal — the party is finding things out, moving through a space, or making their way past obstacles. Use it even when combat is likely along the way, as long as the combat is a complication inside the exploration frame rather than the frame itself.

Do not use this skill when combat is the expected primary event (reach for `combat-encounter`) or when a specific NPC interaction is the main thing that has to happen (reach for `social-encounter`). A key NPC conversation inside an exploration is a beat, not the point; if it *is* the point, the whole encounter is social.

## Craft principles

Every exploration encounter starts with a sensory hook. The first moment the party arrives, they should see, hear, smell, or feel something specific enough that it anchors the scene. "You arrive at the old lighthouse" is not a hook; "Wet kelp is stacked against the door of the lighthouse, and the light up top turns the wrong way — counterclockwise — against the storm" is. Pick details that hint at what's wrong before the party has had a chance to investigate.

Conversely, every detail you describe invites investigation. If you mention the tapestries, players will spend five minutes on the tapestries. Stick to details that lead somewhere — a clue, a hazard, a trace of recent activity, or a hook into a point of interest. Stalactites and wind noise are filler; cut them or accept the time cost.

Layer the reveals. A good exploration has at least three depths: what's visible on arrival, what a meaningful look finds, and what sustained pressure eventually pays off. Flat encounters put everything on the surface; frustrating encounters hide everything at the deepest layer. The middle layer is where most of the play happens.

Make lingering cost something. Exploration without time pressure flattens into sightseeing. The pressure doesn't have to be a timer on a bomb — it can be a rival closing in, a worsening condition (tide rising, fog thickening, a wound not healing), a patrol rotation, a ritual approaching completion. Something should push the party forward while the space pulls them to investigate.

Populate the space with at least three points of interest. Fewer than three and the space reads as empty or railroaded. Each point should offer a different mode of engagement — something to discover (a clue), something to interact with (a device, a person, a hazard), and something to be threatened by (a creature, a trap, a moral dilemma). Mix modes on purpose.

**Fail-forward is the unifying principle.** Across exploration scenes, hazards, and montage tests, the rulebook is consistent: failure is allowed, but failure cannot grind the story to a halt. Concretely:
- **In exploration**, every piece of *necessary* information (the kind without which the adventure can't continue) must have at least one path that does not require a Test. Tests can still be the *best* way to obtain it; if the Test fails or isn't made, there must be another way — likely harder, with consequences. The bare minimum the party needs to advance the story should be findable without a roll — they enter the king's chambers and they see the body, the knife, and the crest on its hilt. Tests gate richer information: the poison residue on the chalice, the apprentice's pattern of movements, the alchemist who sold the killing dose. *Bonus* information and rewards can be Test-gated freely; missing them costs time, advantage, or flavor, not the adventure. Designing this way means a failed test slows the party but never stalls the story, and it frees the GM to call tests honestly without quietly handing out auto-successes when the plot demands it.
- **In hazards outside combat**, effects should be lasting and story-shaped (lose a Recovery, gain a curse with narrative weight) rather than short-term combat-style penalties. But a hazard whose effects make the whole rest of the campaign about un-cursing the PC has gone too far — unless the table explicitly wants that.
- **In montage tests**, all three outcomes (total success / partial success / total failure) must be sketched up front, and total failure must leave options for continuing the adventure. *"They lose track of the lackeys, but they know they can raid the mage's tower for the same information"* is fail-forward; *"they fail, end of investigation"* is not.

When a key check fails in an exploration scene, the scene should advance — at a cost. The party still learns something, but it's partial; they still reach the next room, but they've triggered something; they still find the clue, but someone else has found it first. Dead-ends (where a failed roll just means "nothing happens, try again") kill exploration pacing.

The skill enforces fail-forward as a hard requirement, not a suggestion. If the user prep-writes an exploration / hazard / montage where failure dead-ends the story, the skill names the gap and asks for a fallback before the artifact ships.

The space is a character. Give it a pattern — what the locals believe about it, what the land does at different times of day, what eats what here, who used to live here. When the space has internal coherence, investigation has texture; when it doesn't, exploration collapses into "just roll for it."

Draw Steel layers formal rulesets over these craft principles. Tests and Skills are foundational mechanics, and subsystems exist for Hiding & Sneaking, Group Tests, and Montages. This skill always embeds the foundational rules into the output, and embeds each subsystem's rules whenever the encounter's content calls for them.

## Interview template

**One question per turn. Wait for the user's answer before advancing. Never batch questions into one reply.**

Every question is accompanied by 2–3 concrete suggestions anchored in these craft principles, the prior answers, and the **loaded campaign context** (NPCs, factions, locations, themes, and prior encounters from `campaign.md` and `encounters/`, per the director-assistant agent's context load). Generate them alongside the question so the user can pick one, tweak it, or supply something different — suggestions sharpen the ask from an open prompt into a menu without overriding the user's own answer.

**Let campaign context thread through the whole interview, not just the tie-in.** Location and sensory hook (Q1) can place the scene inside a Notable Location from `campaign.md` and seed its hook with details already established there; the core draw (Q2) can hook into a Theme & Open Question the campaign has been seeding, or pull on an NPC/faction goal that would plausibly lure the party; time pressure (Q3) can reference a rival faction closing in or a consequence still playing out from a recent entry in `encounters/`; points of interest (Q4) can surface recurring NPCs who'd plausibly be present, or features already documented for the location; necessary/bonus information (Q5) should tie the required recoverable items directly to current campaign stakes; layered reveals (Q6) — especially the deepest layer — can pay off a long-running Open Question; fail-forward (Q7) can cash out as a campaign-level complication (a faction learns something, a recurring NPC is compromised, a theme escalates) rather than an in-scene cost alone. The tie-in question asked by the agent after the interview is for *explicit* connections the user wants named — it does not replace context-driven suggestions throughout.

**When invoked from a `session-creation` flow** (the user's request mentions a specific session, or the agent has the session in working context), additionally read the parent session's `## Prep` section. Use it to align the exploration's pressure, points of interest, and reveal layers with the session's broader plan — e.g., if the session prep flags a specific cliffhanger, position the exploration's deepest reveal to land just before that moment. **Also load the linked location file** (`locations/<slug>.md`) for the site the exploration takes place at — pulling the location's mood, sensory hooks, and notable features directly from the canonical file keeps the exploration consistent with what's been established. Load any linked NPC files for NPCs anchored at the location (per the session's NPC list).

Any question may be answered with *"you decide"* (or equivalent deferral). In that case, pick the suggestion that best fits the craft principles, prior answers, and loaded campaign context; surface the chosen suggestion inline so the user sees what was picked, and record it in the transcript so it remains revisable.

1. What's the location, and what's the sensory hook the moment the party arrives? What biome is the party in?

   **Opening sensory hook (all senses).** What do the heroes notice when they arrive — sight, smell, sound, feel? Cover at least three of the four. Write these down up front so they're ready at the start of play; improvising the opening hook on the fly tends to produce only sight. Stick to environment pieces *worthy of the characters' notice* — the things that pay off later. Skip the stalactites and the slugs unless they matter.

   On *"you decide"*, prefer placing the scene in a Notable Location from `campaign.md` if one fits; otherwise pick a biome consistent with where the party currently is per recent entries in `encounters/`.
2. What's the core question or mystery drawing them in — what do they hope to find? On *"you decide"*, scan the Themes & Open Questions in `campaign.md` and surface whichever thread this scene can plausibly advance.
3. What's the time pressure or cost of lingering? (Why can't they take forever?) On *"you decide"*, reach for a rival faction or antagonist from `campaign.md` whose goals create natural pressure here, or a consequence still unresolved from a recent encounter.
4. Name 3+ things in this space the party can discover, interact with, or be threatened by. On *"you decide"*, include at least one item that connects to existing campaign material (a recurring NPC who'd plausibly be here, a faction-coded object, a feature the location is already known for).
5. What information or objects must the heroes recover here for the adventure to continue, and what's optional?

   **Necessary information / objects** — what must heroes recover here for the adventure to continue? For each, name at least one **Test-free path** to obtain it (a body in plain view, a knife with an obvious crest, a witness who'll talk freely). Tests may still be the best path; the Test-free fallback is required.

   **Bonus information / rewards** — what *additional* information or rewards can heroes earn if they explore fully and successfully? These can be freely Test-gated. Missing them costs time or advantage, not the adventure.

   For each item in either list, capture **where it is** and **how it can be found** (which action by the heroes — a player declaration like "I search the desk," a Test, a conversation). Don't enumerate every possible approach; capture at least one and adjudicate other paths at the table.

6. What's revealed at progressive depths — surface, deeper investigation, deepest? Aim the deepest layer at an Open Question the campaign has been building toward when one fits — this is where exploration payoffs compound across sessions.
7. What does a fail-forward look like if a key test goes badly? Consider whether the "cost" can ripple outward into the campaign (a faction learns, an NPC reacts, a theme escalates) rather than being purely local to the scene.
8. *(Conditional — ask only if Q4 or earlier answers mention a trap, hazard, or environmental threat.)* How does the hazard work?

   **Hazard classification.** If the encounter includes a hazard, classify it:
   - **Activated Perpetual** — triggered by the heroes (tripwire, pressure plate, noise) and remains active until dealt with. Pendulum scythe across a bridge.
   - **Activated One-Time** — triggered, single instance of danger. May leave lasting consequences (cave-in damages then traps the party).
   - **Obstruction** — static; heroes must find a way over or around. Acid pool, chasm, river of lava.

   **What does this hazard stand in the way of?** A pool of lava the heroes can simply walk around isn't a hazard — it's scenery. A real hazard blocks something they want or forces a costly choice. Name what it blocks.

   **Effect quality (out of combat).** If the hazard fires outside a combat encounter, its effects should be lasting and story-shaped: *"loses a Recovery,"* *"gains a curse imposing a bane on Presence tests until cleansed,"* *"is teleported into a nearby body of water."* Combat-style short-term effects (stunned for a turn) don't carry weight outside combat.

9. *(Conditional — ask only if the encounter is a montage or the user has indicated a multi-scene push.)* What are the three possible montage outcomes?

   **Montage outcomes (required).** Sketch all three before the test runs:
   - **Total success** — the heroes accomplish what they set out to do.
   - **Partial success** — they accomplish their goal at a cost, create a new problem for themselves, or don't quite reach their full goal.
   - **Total failure** — they fail to do what they set out to do, **but the adventure does not grind to a halt.** Name the alternate path forward: *"they lose track of the fleeing lackeys, but they know they can raid the mage's tower to find the same information."*

   If you can't write a fail-forward total-failure path, this probably shouldn't be a montage test — the encounter is gating the adventure's progress, which calls for a Test-free fallback (per the necessary-information rule above) rather than a montage.

   **Optional twist.** Is there a quick combat / negotiation / trap you'd like to insert partway through? Often lands well at the end of the first montage round; the test pauses, the twist resolves, the test resumes.

*The tie-in question is asked by the agent after this interview, not here.*

## Mechanical references

User-maintained Draw Steel ruleset library at `${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/`, one file per ruleset.

**Foundational files — always loaded:**
- `${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/tests.md` — Test resolution: when a Test is called for, the power-roll procedure, difficulty tiers, the full Test Difficulty Outcomes matrix, all six outcome shapes (including reward / consequence variants), opposed power rolls, reactive tests, and fail-forward guidance.
- `${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/skills.md` — The full skills list (five groups: crafting, exploration, interpersonal, intrigue, lore) with per-skill uses, the +2 / edge / characteristic-flex rules for applying skills to tests, and the **Assist a Test** mechanic (note: Assist lives in the skills file because it requires an applicable skill, not in the tests file).

These ground the mechanical framing for every exploration encounter. They inform which skills the encounter will exercise and how tests resolve, and are treated as prerequisite context for the subsystem files below.

**Subsystem files — loaded conditionally based on encounter content:**
- `${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/hide-and-sneak.md` — Hiding requirements (cover / concealment / not-observed), in-combat vs. out-of-combat resolution, the benefits of being hidden, the Search maneuver with its 10-square envelope, sneaking at half speed, and how "surprise" emerges from stealth + NPCs-Roll-for-Deceptive-Tasks. Load when the encounter involves hiding, sneaking, surprise, or detection.
- `${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/grouptest.md` — **One moment, same task, every participant rolls once.** Half-or-more threshold for pass/fail, collective reward / consequence pass, the no-assist-between-participants rule. Load when the whole party simultaneously attempts the *same* task (all climbing the same wall, all sneaking past the same ogre).
- `${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/montages.md` — **Multi-scene push, different tasks, 2-round vignette loop.** Success / failure limits by difficulty (table), the can't-reuse-skill-per-hero rule, the three outcome tiers (total success / partial success / total failure) and their Victory rewards, and guidance for mapping narrative beats onto test slots. Load when the encounter is a journey, extended investigation, or time-pressured push where *different* heroes tackle *different* obstacles across time.

**Lookup:** at drafting time, the skill:
1. Always reads the foundational files (`${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/tests.md`, `${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/skills.md`).
2. Inspects the interview answers to decide which subsystem files to load:
   - Stealth signals (hiding, sneaking, surprise, detection, avoiding observers) → `${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/hide-and-sneak.md`
   - **Same-task** collaboration signals (whole party attempts one unified task in a single moment; crowd/mob challenge resolved as one beat) → `${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/grouptest.md`
   - **Multi-task** montage signals (multi-scene journey, compressed time, escalating stakes, different heroes covering different obstacles, explicit "montage" framing) → `${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/montages.md`

   *Same-task vs. multi-task is the key distinction — a party climbing one tower together is a group test; a party crossing a desert over days, with one hero scouting, one navigating, one foraging, is a montage. Load both only if the encounter genuinely contains both (e.g., a montage that includes a single group-test moment inside one round).*
3. Embeds the relevant rules into the matching output section(s) below.

The reference files cross-link to each other using `[[name]]` wiki-links (e.g., montage notes link to the tests file for the fail-forward rule). When embedding one ruleset's mechanics, resolve cross-linked concepts by reading the linked file rather than paraphrasing from memory.

The skill never invents new mechanical content; it only applies what's in the references.

**Optional setting flavor.** When the exploration takes place in a region or involves a faction from the campaign's published setting, additionally read `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/regions.md` and `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/factions.md` for descriptive flavor — use sparingly, to color the scene without inventing canon. Skills work gracefully when these references are missing or stubbed.

## Inter-skill contracts

This skill participates in the inter-skill wire format documented at `${CLAUDE_PLUGIN_ROOT}/references/skill-contracts.md`:

- **Headers consumed.** When invoked from a `session-creation` flow, this skill reads the parent session's `## Prep` section, the linked location file (mood, sensory hooks, notable features) for the site the exploration takes place at, and any linked NPC files for NPCs anchored at that location. The canonical header strings and the relative-link depth conventions for resolving the links live in the contracts file.
- **Headers produced.** Encounter files don't produce headers other skills consume; the file is a leaf artifact in the workflow tree.

If the contracts file ever disagrees with text in this skill, the contracts file wins.

## Output template

See `${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/encounter-output-template.md` for the full encounter output markdown template. The template includes sections for Location & first impression, Draw, Pressure, Points of interest, Layered reveals, Fail-forward, Test structure (conditional), Stealth structure (conditional), Group test structure (conditional), Montage structure (conditional), and Ties to existing material.

## Anti-patterns

- **Featureless spaces** — if the map has no points of interest, add at least three. A space with nothing to investigate is not exploration; it's travel narration.
- **True dead-ends on failed checks** — always fail-forward with a cost. A failed roll that stalls the scene kills pacing.
- **Single-path reveals** — layered reveals should support multiple approaches to reaching them. One-way secrets reward guessing the designer's mind, not play.
- **No cost to lingering** — if time doesn't pressure the party, the exploration flattens into sightseeing. Always give lingering a price.
- **Ignoring applicable rulesets** — `${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/tests.md` and `${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/skills.md` are always loaded; the corresponding output section MUST be populated. For `${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/hide-and-sneak.md`, `${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/grouptest.md`, and `${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/montages.md`, if the encounter's content matches the trigger, the corresponding output section MUST be populated. Missing a relevant ruleset is a bug.
- **Inventing mechanical content** — never synthesize test difficulties, skill rules, stealth procedures, group-test thresholds, or montage resolution rules. These come from the reference files verbatim or the section is omitted entirely.
