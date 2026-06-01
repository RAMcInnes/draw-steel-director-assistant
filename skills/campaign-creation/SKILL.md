---
name: campaign-creation
description: Use when starting a new Draw Steel campaign — runs an intake interview to capture premise, party, key NPCs, factions, locations, and themes, then emits the campaign.md artifact for the director-assistant to ship. Consults the shared Draw Steel reference library to surface class/ancestry/culture/career/complication descriptions and propose setting-aware NPCs and themes informed by PC build choices.
---

# Campaign creation

## When to use / when not to use

Use this skill when the user is starting a fresh Draw Steel campaign — there's no `campaign.md` yet, or the user explicitly wants to create a new one alongside existing campaigns.

Do not use this skill to revise an existing campaign (use revision mode on `campaign.md` directly), to design a single arc/session/encounter (use the matching skill — `arc-creation`, `session-creation`, or one of the encounter skills), or to brainstorm campaign ideas without committing (this skill writes the artifact).

## Craft principles

A campaign isn't a setting summary; it's a contract between the Director and the players about what kind of story they're going to tell together. The intake captures the spine of that contract — premise, cast, world surface, and themes — at a level of detail that supports years of play without prescribing how every session will go.

Every PC choice creates story hooks. A Censor sworn to a god implies a faith and an order. A Revenant brings a death they came back from. A "Sage" career implies a teacher, a body of knowledge, and a question the PC was investigating. The intake should consult the reference library when it sees these choices and propose NPCs, factions, or themes that *answer* what the build is *asking*.

A PC's hooks are the campaign's seed bank. Capture each PC's build-derived hooks, their complication, and one open personal question — short, terse, written so a future arc can mine them. The question form matters: *"Will Mira choose vengeance or rebuilding?"* travels further than *"Mira wants revenge."* These hooks live in their own `## PC Hooks` section of `campaign.md` so `arc-creation` can scan them when planning spotlight rotation; they are not folded into Themes (which hold campaign-level questions, not per-PC ones).

Themes are questions, not answers. "Loyalty" is weak; "What is loyalty worth when it costs you the truth?" is strong. The Themes & Open Questions section should hold the questions the campaign is *investigating*, not the morals it's preaching.

Recurring NPCs and factions are the connective tissue that makes the campaign feel like one story. Capture the few that will reappear; leave the rest for sessions to invent. A campaign with too many named NPCs at intake collapses under the weight of its own cast list.

Notable locations are anchors, not maps. List the few places the party will revisit. Detailed worldbuilding lives in `setting.md` (per-campaign) or in the shared `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/` (the published canon).

Start small and keep things vague. The rulebook's *Building the Campaign* guidance is explicit: don't try to detail every settlement on every continent before play starts. Build a starting town or initial district, then work outward as the campaign needs it. For details outside the immediate starting area (the nearest settlement, the name of the country's monarch), capture a name plus one sentence — no more. Overpreparation is wasted work the moment players surprise you. The aim of intake is the minimum a Director needs to be comfortable starting; further detail accretes through arc and session prep.

Suggestions are remix-friendly. When the skill proposes NPCs, factions, themes, or hooks during the interview, frame them as starting points the Director can lift wholesale, modify, or replace — not finished canon. The rulebook's *Stealing is Encouraged* sidebar is the spirit: borrow shapes from media the Director already loves and reskin lightly. The skill should explicitly invite this when offering "you decide" defaults: *"Going with: …; happy to swap if you have a better source in mind."*

### User additions

*Space for the user to add their own craft notes as the skill gets used. Leave the existing principles above intact; extend them here.*

## Reference consumption

When the user names PC classes, ancestries, cultures, careers, or complications, consult the corresponding file under `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/` — specifically `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/classes.md`, `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/ancestries.md`, `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/cultures.md`, `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/careers.md`, and `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/complications.md`. Surface relevant flavor inline as suggestions for NPCs, factions, or themes that would resonate with the PC build.

When PC Hooks (step 7) reaches the downtime-projects subfield, consult `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/downtime-projects.md` to anchor suggestions or *"you decide"* defaults in canonical project types rather than generic fantasy filler.

Skills work gracefully when reference files are missing or stubbed — note "no <category> reference on file — proceeding with generic suggestions" and continue. Never block on missing references.

## Inter-skill contracts

This skill is the **canonical producer** of several headers in `campaign.md` that downstream skills read: `## PC Hooks`, `## Key NPCs`, `## Notable Locations`, `## Factions`. The exact header strings, their consumers, and the ship-time mid-flow invocations of `npc-creation` and `location-creation` are documented at `${CLAUDE_PLUGIN_ROOT}/references/skill-contracts.md`. The output template in this skill's `references/output-template.md` writes the header strings verbatim; renaming any of them is a coordinated change there plus the contracts file plus every consuming skill (the contracts file lists them).

When mid-flow invocations of `npc-creation` and `location-creation` return their link strings at ship time, the agent validates the return shape per the contracts file's Mid-flow return string format rules before embedding into `## Key NPCs` and `## Notable Locations`.

If the contracts file ever disagrees with text in this skill, the contracts file wins.

## Interview template

**One question per turn. Wait for the user's answer before advancing. Never batch questions into one reply.**

Every question accepts a *"you decide"* / *"skip"* / *"leave blank"* deferral. On *"you decide"*, generate a plausible answer anchored in the craft principles, prior answers, and (where applicable) the reference library; surface it inline as *"Going with: …"* and record it. On *"skip"* / *"leave blank"*, record the field as empty — the Director can fill it in later by editing `campaign.md` directly.

1. **Premise** — one or two sentences on the campaign's overall arc or goal. *"What's this campaign about, at a high level?"* The rulebook's *Opening Overview* lens: where does it take place, what major events have already occurred, what kinds of adventures will the heroes have? Don't spoil secrets — leave players wanting to know more.
2. **Gameplay Breakdown** — for each of the four rulebook categories (Combat, Exploration, Interpersonal, Intrigue), assign a frequency: **High** (multiple scenes per session), **Medium** (~one scene per session), or **Low** (less than once per session). The user may add custom categories (e.g., "Puzzles") if their pitch calls for it. This sets player expectations and shapes how `session-creation` later balances scene types.
3. **Player Buy-In** — one or two sentences telling the players what's expected of them to enjoy the game. *"In order to get the most out of this game, you'll need to enjoy diving into ancient ruins,"* or *"this game has horror themes — if you're not interested in playing heroes who have fears they need to face, this isn't the game for you."* Names the *experience contract*, not just the premise.
4. **Player Option Restrictions** — any restrictions on character choices implied by the campaign. *"All heroes must be memonek or time raiders,"* or *"no Aristocrat or Politician careers — this is a peasant rebellion."* Captured at intake so the agent can offer/disallow options when the Party question runs. *"None"* is a valid answer.
5. **House Rules** — any rule modifications the Director plans to use. *"Respite is 8 hours instead of overnight,"* *"crit only on natural 20,"* etc. Captured at intake so encounter skills can reference them later. *"None"* is a valid answer; users running RAW can skip.
6. **Party** — who the PCs are. For each: name, class, ancestry, culture, career, and one-line role/descriptor. What level is the party? When the user names a class/ancestry/culture/career, consult the reference library and surface 1–2 relevant story hooks alongside subsequent questions (e.g., "the Censor of the Storm-God suggests the Storm Cult could be active in the campaign — worth a faction?"). Honor any restrictions captured in step 4.
7. **PC Hooks** — for each PC named in step 6, capture five short items:  
(a) hooks their class/ancestry/culture/career imply (consult the reference library),  
(b) their complication and what it costs them,  
(c) **the player's stance on the complication**: do they want to keep the benefit but lose the drawback, or be rid of the entire complication? (per the rulebook's *Complications and Campaigns* discussion pattern — this answer shapes how the complication evolves across echelons),  
(d) one open personal question their build is asking, and  
(e) **current downtime projects, if any** — short personal projects the PC is pursuing between adventures (research, training, crafting, relationship-building, etc.). Capture name + one-phrase intent only. These give arcs and sessions opportunistic hooks to incorporate when the fiction allows; they evolve via revision mode as projects start, advance, or finish. Consult `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/downtime-projects.md` when proposing suggestions or filling *"you decide"* defaults. *"None"* is a valid answer for PCs not currently pursuing anything. Keep each item short and concrete — these are seeds for arc-level spotlights, not character essays. *"You decide" deferral generates plausible items per PC, anchored in the reference entries; surface inline as "Going with: …" per the standard pattern. "Skip" leaves the PC's entry empty; the Director can fill it in later.*
8. **Campaign Style** — pick one (or describe a hybrid): **Long Arc** (one villain/organization behind almost every threat); **Adventure of the Week** (entirely new threat each adventure); **Looming Threat** (mostly standalone adventures with a recurring villain orchestrating a few); **Multiple Fronts** (several villains advancing in parallel; heroes must prioritize). This shapes how `arc-creation` paces antagonists across arcs.
9a. **Echelon Span** — what echelon does the campaign start at, and what's the highest echelon it's expected to reach? Acceptable answers: a single echelon (*"1st only"*), a range (*"1st–3rd"*), or *"all four"*. Many Draw Steel campaigns are scoped to fewer than four echelons; don't presume the long arc. *"You decide"* defaults to a span anchored in the premise + style — a long-arc campaign with a 4th-echelon villain naturally spans 1st–4th; a tighter premise may scope to 1st–2nd.
9b. **Echelon Outline** — for each echelon in the span captured in 9a, one or two sentences naming the dominant conflict, location, or villain action. Vaguer the further out — players' actions reshape later echelons. *"You decide"* generates a plausible outline anchored in the premise + style + party. This becomes the menu `arc-creation` consults when sequencing arcs.
10. **Key NPCs** — recurring figures the party is likely to encounter more than once, allies and antagonists alike. Suggestions can pull from the reference library when PC builds imply specific NPC types (e.g., a Censor's god, a Sage's teacher) and from the PC Hooks captured in step 8. **Capture each named NPC's name + one-phrase role only here** — the agent will invoke `npc-creation` for each at ship time, which runs that skill's full interview to flesh out voice, behavior, allegiances, location attachment, etc. Do not duplicate `npc-creation`'s full interview here.
11. **Factions** — recurring organizations or groups the party will cross paths with. Same suggestion rule. (Factions stay as inline-description bullets in `campaign.md`'s `## Factions` section — no per-faction files; this is intentional scope.)
12. **Notable Locations** — cities, towns, regions, or landmarks the party will revisit. Pull from `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/regions.md` if the Director uses the published setting. Per the *Start Small* principle: detail the starting area; for further-out locations, name + one sentence is enough. **Capture each named location's name + type (city/region/building/etc.) only here** — the agent will invoke `location-creation` for each at ship time, which runs that skill's full interview to flesh out mood, senses, purpose, faction control, etc. Do not duplicate `location-creation`'s full interview here.
13. **Themes & Open Questions** — the big questions the campaign is working toward, framed at the campaign level (not per-PC; per-PC questions belong in step 7). Pull from PC complications and class flavor when relevant.
14. **Campaign name** — *asked last, not first.* Now that premise, party, factions, and themes are on the table, propose 1–2 evocative campaign titles drawn from what's been captured (premise, recurring antagonists/factions, themes) and present them for the user to accept, tweak, or replace. The chosen title becomes the folder name (slugified by the agent: lowercase, hyphenated, ASCII only). *"You decide" → take your top suggestion. If the user volunteered a name earlier in the interview, capture it then and simply confirm it here rather than re-proposing.*

## Output template

See `${CLAUDE_PLUGIN_ROOT}/skills/campaign-creation/references/output-template.md` for the campaign.md output structure.

## Anti-patterns

- **Skipping the reference consultation step** — if a PC's class/ancestry/culture/career has a reference entry, surface relevant flavor as suggestions. Don't reduce intake to generic fantasy defaults when system-specific content is on file.
- **Folding PC Hooks into Themes** — PC Hooks are per-character; Themes are campaign-level. Mira's "revenge or rebuilding?" is a hook; "what does loyalty cost?" is a theme. Keeping them separate lets `arc-creation` scan PC Hooks for spotlight rotation without sifting through campaign-wide material.
- **Over-populating the cast at intake** — capture only NPCs and factions that *will recur*. One-shot characters belong in session prep, not campaign intake.
- **Themes as answers rather than questions** — "honor matters" is a statement; "what does honor cost?" is a theme. Reach for the question form.
- **Inventing setting content** — if the Director is using the published Draw Steel setting, pull from `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/`. If they're using a custom setting, prompt them to author `setting.md` separately rather than fabricating canon.
- **Detailing the Echelon Outline beyond the first echelon in span** — the rulebook is explicit: the further out, the vaguer. A four-paragraph plan for the highest echelon is wasted work because players' choices in earlier echelons will rewrite it. One sentence per echelon, decreasing in specificity, is the target. Echelons outside the span captured in step 9a get no entry at all — don't speculate beyond the planned scope.
- **Treating the Gameplay Breakdown as a contract** — it's an expectation-setter, not a quota. If a session or arc skews differently because the heroes did something unexpected, that's normal. The Breakdown shapes pacing suggestions in `session-creation`; it doesn't lock anyone in.
- **Duplicating npc-creation / location-creation interviews here** — Key NPCs (step 10) and Notable Locations (step 12) capture **only name + role / type** at intake. The full per-entity interview runs at ship time when the agent invokes `npc-creation` and `location-creation` for each named entity. Asking for voice cues, distinguishing features, mood, senses, etc. inside campaign-creation's interview duplicates work and diverges the source of truth.
