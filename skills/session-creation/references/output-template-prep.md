# Session file output template (prep mode)

The session-creation skill (prep mode) emits the following structure for the agent to write as `~/draw-steel-campaigns/<campaign-slug>/sessions/YYYY-MM-DD-<session-slug>/session.md`:

```markdown
# <Session title>

**Arc:** [<arc title>](../../arcs/YYYY-MM-DD-<arc-slug>.md)
**Date prepped:** YYYY-MM-DD
**Status:** planned

## Prep

### Opening scene
<where does the session begin? cover sight + smell + sound + feel — written down up front>

### Spotlight
- **<PC Name>:** <one line on the spotlight beat — a scene, decision, or NPC moment that pressures this PC's hooks>
- **<PC Name>:** <same — only if a second PC is spotlighted; cap is 1–2 PCs>

*(Sourced from the parent arc's `### PC Threads`. Bias toward PCs not in the last 1–2 sessions' `### Spotlight realized`.)*

### Expected beats
1. <beat 1>
2. <beat 2>
…

### General locations traversed
- **[<Location Name>](../../locations/<slug>.md):**
  - **Tonight's mood:** <how this location feels *tonight*, possibly differing from the file's default — e.g., "tense; under occupation after the assassination">
  - **Tonight's nonhostile creatures:** <session-specific passersby, animals, color>
- …

*(Headline-link list. The location's default mood, senses, and faction control live in `locations/<slug>.md` — do not duplicate. New general locations are created via `location-creation` mid-interview before their link is dropped here.)*

### Specific sites
- **[<Site Name>](../../locations/<slug>.md):**
  - **Why heroes come here tonight:** <session-specific angle on the site's purpose>
  - **Scenes that play out tonight:** …
  - **NPCs encountered tonight:** [<NPC Name>](../../npcs/<slug>.md), [<NPC Name>](../../npcs/<slug>.md), …
  - **Discoverable tonight:** <session-specific information / items / outcomes>
- …

*(Headline-link list. The site's general purpose and physical features live in `locations/<slug>.md`; the prep captures only what's different / specific *this* session. New sites are created via `location-creation` mid-interview.)*

### Encounters lined up
- [ ] <encounter title> — <type: combat/exploration/social> — <site from above> — <one-sentence hook>
- [ ] …

*(Encounter files land in `./encounters/` as they're designed; check off here once attached.)*

### Decision points
1. <moment> — <branches A / B / …>
2. …

### NPCs likely to appear
- **[<NPC Name>](../../npcs/<slug>.md)** — <session-specific note: what they want tonight, what they're doing when heroes find them, which scene they appear in>
- …

*(Headline-link list. The five-field NPC shape (feature, voice, behavior, flaw, motivation) lives in `npcs/<slug>.md`; the prep captures only the *tonight* angle — what changes for this NPC in this session. New NPCs the session introduces are created via `npc-creation` mid-interview when they merit a file; genuinely incidental NPCs stay as a one-line inline entry here, no file, no link.)*

### Connective tissue
<travel, conversation, downtime — between-encounter flow>

### Cliffhanger or payoff target
<what the session aims to end on>

## Play log

*This section is populated by `session-creation` (log mode) after the session is played.*
```

The Play log section is left as a stub placeholder so log mode has a clear target to replace.
