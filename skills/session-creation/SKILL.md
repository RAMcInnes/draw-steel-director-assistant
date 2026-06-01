---
name: session-creation
description: Use when prepping a single Draw Steel session before play, or capturing the play log after a session has run. Prep mode plans the session (opening, beats, encounters lined up, decision points, NPCs likely to appear); log mode appends what happened. Reads campaign + current arc + recent session logs for continuity.
---

# Session creation

## When to use / when not to use

Use this skill for single-session work — either prepping the next sitting or recording what happened in the one that just played. Sessions sit one level below arcs and one level above encounters.

Do not use this skill to plan a multi-session arc (use `arc-creation`) or to design a single scene/encounter within a session (use the matching encounter skill). A session is a play sitting; an encounter is one scene inside it.

**Mode selection.** Branch on user intent at the opening of the interview:
- "design session N" / "prep next session" / "plan tomorrow's game" → **prep mode**
- "log what happened in session N" / "write up tonight's session" / "record session 4" → **log mode**

## Craft principles

A session has a shape. It opens with a hook the players engage with, escalates through 2–4 beats, and resolves with either a payoff or a cliffhanger that pulls the table back next time. A session that's "the party arrives at the city and does whatever" is shapeless; one that's "the party arrives, follows the lead to the underchapel, and discovers the body — but the cultist's escape sets up next session" has tension.

Sessions are not just encounter sequences. The flow between encounters — the travel, the conversations, the time-pass montages — is where most of the table's roleplay happens. Prep should call out the connective tissue, not just the scenes.

Decision points are where the session bends. Identify 1–3 moments where the party's choice meaningfully changes what comes next. The prep should anticipate the major branches without prescribing one.

Session prep is a forecast, not a script. Players will diverge. The prep is a tool for the Director to improvise from, not a railroad. If your prep needs to be followed exactly for the session to work, it's too tight.

Logs are continuity, not transcript. The log captures what happened with enough detail that next session's prep — and next arc's outcome synthesis — has source material. Player-facing recap is out of scope for this skill.

A session spotlights at most 1–2 PCs. The spotlight is a deliberate commitment to put pressure on those PCs' hooks during this sitting — a scene that puts their open question on the table, an NPC who knows about their complication, a decision only they can make. The 1–2 cap is what makes the moment land; spreading the spotlight thinner gives every PC a too-brief beat. **Read the parent arc's `### PC Threads` to see who's eligible** (the arc has already decided which PC threads it can pressure), then **read prior sessions' `### Spotlight realized`** to see who's been spotlighted recently and prefer PCs who haven't. If every eligible PC has had a recent spotlight, that's a signal the arc is approaching its emotional climax — make a deliberate choice instead of defaulting.

The rotation principle has rulebook backing. The *Complications and Adventures* sidebar in Chapter 15 is explicit: *"Rotate the hero whose complication is highlighted each time, so that every player gets a chance to be at the center of the story."* The 1–2-PC Spotlight cap is the operational shape of that rule at the session layer.

Sessions are made of scenes, and scenes happen at sites. The rulebook distinguishes **general locations** (a settlement or defined wilderness region — a city district, a desert, an entire world) from **specific sites** (where a scene actually plays out — a building, a clearing, a bridge, a city square). A session typically traverses one or two general locations and lands two to four specific sites. Prep should call out both layers: the *atmosphere* of the general locations the heroes pass through (mood, sensory hook, nonhostile creatures encountered), and the *purpose* of each specific site (why heroes come here, what scenes play out, which NPCs are found here, what they can discover).

NPCs are people, not stat lines. Each session NPC the heroes might meaningfully interact with deserves a quick five-field shape — name and role, a distinguishing feature, a voice cue, one distinct behavior, and one flaw — plus a kernel of motivation for why they'd help (or what would prevent them from helping). The rulebook is direct: *"If all the people the characters come across are villainous, apathetic, or selfish, the players won't feel very motivated to get their heroics on."* One distinct behavior per NPC; many flaws turn an authentic NPC into an authentically unlikable one fast.

### User additions

*Space for the user to add their own craft notes as the skill gets used. Leave the existing principles above intact; extend them here.*

## Reference consumption

Read `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/*.md` files relevant to the session's content:

- `factions.md` — sessions where faction politics or faction-driven NPCs are in play
- `regions.md` — sessions anchored in a specific region or settlement (the typical case)
- `timeline.md` — sessions touching historical events or revelations
- `cosmology.md` — sessions involving gods, planes, undeath, or other metaphysical content
- `overview.md` — sessions needing broad world orientation (e.g., the first session of a new campaign)

Skills work gracefully when reference files are missing or stubbed — note "no setting reference on file — proceeding with generic suggestions" and continue. Never block on missing references.

`${CLAUDE_PLUGIN_ROOT}/references/draw-steel/vocabulary.md` provides one-paragraph entries for Tests, Negotiation, etc. — pull from it when prep needs to call out which mechanical system a beat will use, without loading full mechanical files.

Always scan the parent arc file's `### PC Threads` (the menu of PCs this arc can pressure) and the **last 1–2 session logs' `### Spotlight realized`** (recently-spotlighted PCs) when picking this session's Spotlight. Both are already loaded by the standard context load — no extra reads needed. Spotlight rotation discipline lives here, not in `arc-creation`.

## Inter-skill contracts

This skill both **consumes** and **produces** headers documented at `${CLAUDE_PLUGIN_ROOT}/references/skill-contracts.md`:

- **Consumes** (prep mode): `## PC Hooks`, `## Key NPCs`, `## Notable Locations`, `## Factions` from `campaign.md`; `### PC Threads` and `### Key NPCs` from the parent arc file; `## Play log` and `### Spotlight realized` from prior session files. Canonical strings are in the contracts file.
- **Consumes** (log mode): the session file's own `## Prep` and `### Spotlight` (to mirror as `### Spotlight realized`).
- **Produces** (prep mode, written to `sessions/<date-slug>/session.md`): `## Prep`, `### Spotlight`. The output template in `references/output-template-prep.md` writes these verbatim.
- **Produces** (log mode, replacing the stub `## Play log`): `## Play log`, `### Spotlight realized`. Output template in `references/output-template-log.md`.

When mid-flow invocations of `npc-creation` and `location-creation` return link strings during prep-mode interview questions 4/5/8, validate per the contracts file's Mid-flow return rules before embedding.

If the contracts file ever disagrees with text in this skill, the contracts file wins.

## Interview template (prep mode)

**One question per turn. Wait for the user's answer before advancing. Never batch questions into one reply.**

Every question is accompanied by 2–3 suggestions anchored in the craft principles, prior answers, and the **loaded campaign context** (campaign.md, the current arc file, the last 1–2 session logs, threads from prior encounters).

Every question accepts a *"you decide"* / *"skip"* / *"leave blank"* deferral. On *"you decide"*, generate a plausible answer anchored in the craft principles, prior answers, and the loaded context; surface it inline as *"Going with: …"* and record it. On *"skip"* / *"leave blank"*, record the field as empty — the Director can fill it in later by editing the session file directly.

1. **Opening scene** — where does this session begin? What's the first thing the players see/hear/feel/decide? Cover *all* relevant senses, not just sight: smell, sound, the feel of the air. Write these details down up front so they're ready at the start of play.
2. **Spotlight** — 1–2 PCs whose hooks this session deliberately puts in focus. Source candidates from the parent arc's `### PC Threads` (the arc has already decided which PCs are eligible for pressure). Bias suggestions toward PCs who do *not* appear in the last 1–2 session logs' `### Spotlight realized` entries — rotation builds the "every PC gets a story" feel. For each chosen PC, note one line on *what* the spotlight looks like (a scene, a decision, an NPC who knows about their complication). *"You decide" picks the least-recently-spotlighted PC(s) from the arc's PC Threads and proposes a spotlight beat anchored in their PC Hooks entry.*
3. **Expected beats** — 1-3 narrative moments you anticipate. (These are *expectations*, not commitments — players will diverge.) At least one beat should be the Spotlight beat from step 2.
4. **General locations traversed** — which settlements, regions, or large landmarks does the session pass through? For each, scan `locations/index.md` (loaded during context load) and link to the existing file when one exists. For new general locations the heroes will meaningfully engage with, invoke `location-creation` mid-flow to get them on file. For passed-through regions that don't merit their own file, capture them as a one-line entry inline in this session's prep (no link, no file). Then capture **session-specific notes only** for each linked location: *tonight's mood* (the location's default mood may be "safe", but tonight it's "tense" because of the assassination), *tonight's nonhostile creatures* (color/passersby that will be in scene). The default mood + senses live in the location file; do not duplicate them in session prep.
5. **Specific sites** — where do scenes actually play out? Same link-out pattern: scan `locations/index.md` for matches, invoke `location-creation` for new sites that earn a file (recurring sites, sites that anchor multiple scenes, sites with their own NPCs). Sites the heroes will visit once and never return to — a forest clearing where a single ambush happens, a tavern visited once — stay as one-line entries inline in this session's prep, no file. Per site (file or inline), capture **only session-specific notes**: *why heroes come here tonight* (the site's general purpose lives in its file; the session notes the *tonight* angle — what they're seeking *this time*), *what scenes play out tonight*, *what NPCs are encountered tonight* (link from `npcs/` per the NPCs step), *what they can discover that advances tonight's story*. A session typically lands 1-3 specific sites.
6. **Encounters lined up** — which combat, exploration, or social encounters do you anticipate? Name them and pin each to a specific site from step 5; the encounter skills can be invoked separately to design them.
7. **Decision points** — 1–3 moments where the party's choice meaningfully bends what comes next. Sketch the branches.
8. **NPCs likely to appear** — who's in the session? Scan `npcs/index.md` (loaded during context load), the parent arc file's `### Key NPCs`, and `campaign.md`'s `## Key NPCs` for matches. For NPCs that already have a file, link to it and capture **only session-specific notes**: *what they want tonight*, *what they're doing when the heroes find them*, *which scene they appear in*. For brand new NPCs the session introduces who will recur or carry weight, invoke `npc-creation` mid-flow to get a file. For genuinely incidental NPCs (the bartender met once, the gate guard who lets them through), capture them as a one-line entry inline in this session's prep — no file, no link. The five-field NPC shape (feature, voice, behavior, flaw, motivation) lives in the NPC file when one exists; don't duplicate it in session prep.
9. **Connective tissue** — between encounters and sites, what is the table doing? Travel? Conversation? Downtime? Note the shape, not the dialogue.
10. **Cliffhanger or payoff target** — what do you want the session to end on? (The table may push past or stop short.)
11. **Session title** — *asked last.* With the opening, spotlight, sites, and cliffhanger now settled, propose 1–2 short, evocative session titles drawn from what's been captured and present them for the user to accept, tweak, or replace. Slugified by the agent for the folder name. *"You decide" → take your top suggestion. If the user named the session earlier in the interview, capture it then and simply confirm it here rather than re-proposing.*

## Interview template (log mode)

Log mode does not run a deep question-by-question interview. The user dictates what happened (typically as a brief summary or transcribed bullet list); the skill structures it into the log template. Light prompting:

1. **Recap** — one paragraph: what happened this session?
2. **Spotlight realized** — for each PC named in the session's prep `### Spotlight`: did the spotlight beat actually land? What advanced for that PC's hooks (or "spotlight missed; carry forward")? This drives `arc-creation` (log mode)'s `### PC Threads realized` synthesis at arc end and guides next session's rotation.
3. **Threads** — what threads opened, closed, or transformed?
4. **NPCs encountered** — who showed up, and what was their state at session end?
5. **Party state changes** — level-ups, conditions, gear, resources, allies/enemies gained.
6. **Untouched prep** *(optional)* — anything in the session's `## Prep` section that didn't get used? Worth noting for the next prep.

## Output templates

- Prep mode: see `${CLAUDE_PLUGIN_ROOT}/skills/session-creation/references/output-template-prep.md`. The agent writes this to `sessions/YYYY-MM-DD-<session-slug>/session.md`.
- Log mode: see `${CLAUDE_PLUGIN_ROOT}/skills/session-creation/references/output-template-log.md`. The agent appends to the existing session.md, replacing the stub `## Play log` placeholder.

## Anti-patterns

- **Prep as railroad** — if the session breaks when players diverge, the prep was too tight. Forecast, don't script.
- **Encounters without connective tissue** — sessions are not encounter trains. The flow between encounters is where most roleplay happens; the prep should anticipate it.
- **Logs as transcripts** — log mode captures continuity-grade summaries, not turn-by-turn play. If you want detailed transcripts, that's a separate artifact.
- **Logs that invent player choices** — log only what actually happened. If you don't know what happened, ask the user; don't fill in plausible-sounding details.
- **Skipping Untouched prep on the log** — same value as the arc-level version: untouched prep is candidate material for the next session or arc.
- **Spotlighting the same PCs session after session** — if Mira got spotlight in the last session, the next session should pick someone else from the arc's `### PC Threads` menu. Concentrating spotlight breaks the "every PC gets a story" feel; rotation discipline is what builds it. Read the last 1–2 session logs' `### Spotlight realized` entries before suggesting candidates.
- **Spotlighting more than 2 PCs in one session** — the cap is what makes each spotlighted moment land. Three-PC spotlights either thin each beat or run the session long. If the arc seems to demand three PCs in one sitting, that's usually a signal the arc's pacing wants two sessions, not one.
- **Capturing full NPC or location detail in session prep** — session-prep captures only the *tonight* angle for each entity. The five-field NPC shape and the four-field location shape live in `npcs/<slug>.md` and `locations/<slug>.md`. If an NPC or location doesn't have a file yet, invoke `npc-creation` or `location-creation` mid-interview rather than fleshing them out inline in `session.md`. This is what keeps `session.md` focused on *what's different this session* rather than re-stating durable entity facts.
