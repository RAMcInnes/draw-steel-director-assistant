# Arc file output template (prep mode)

The arc-creation skill (prep mode) emits the following structure for the agent to write as `~/draw-steel-campaigns/<campaign-slug>/arcs/YYYY-MM-DD-<arc-slug>.md`:

```markdown
# <Arc title>

**Date created:** YYYY-MM-DD
**Status:** planned

## Prep

### Premise
<one or two sentences>

### Antagonist
- **Identity:** <name; what they are — human, factional, environmental, temporal>
- **Motivation:** <vendetta / birthright / protection-by-conquest / save-the-world-via-dark-power / mayhem / etc.>
- **What they've done:** <sins/history the heroes can uncover — corpses, burned villages, betrayals already executed>
- **What they plan to do:** <the next, worse thing — this is what the arc opposes>
- **Hard line:** <line they will not / cannot cross — or "none">

### Inciting incident
<the moment that reveals the arc's goal to the heroes, or sets them on the path to discovering it>

### Beats
1. <beat 1>
2. <beat 2>
3. <beat 3>
…

### Stakes
<for the party, the antagonist, third parties — and how this differs from prior arcs>

### PC Threads
- **<PC Name>:**
  - **Room to breathe:** <one line on how this arc's premise/antagonist/beats give this PC's hooks room>
  - **Complication echelon move:** <how this PC's complication advances across the arc — omit if dormant this arc>
- **<PC Name>:**
  - **Room to breathe:** …
  - **Complication echelon move:** …
- …

*(List every PC whose hooks this arc plausibly pressures — no cap. PCs not listed are explicitly "not this arc." `session-creation` draws from this menu when picking each session's 1–2-PC Spotlight.)*

### Key NPCs
- [<NPC Name>](../npcs/<slug>.md) — <role in this arc; what changes for them>
- …

*(Headline-link list. Per-NPC depth lives in `npcs/<slug>.md`. New NPCs the arc introduces are created mid-interview via `npc-creation`; existing NPCs are linked from `npcs/index.md`. The arc-specific note here is just *"what this arc does to them"*, not a full NPC description.)*

### Resolution target
- **Planned shape:** <what the planned ending looks like — aspirational>
- **Alternate paths:** <1–2 alternate routes the heroes could take to the same goal, or a partial-victory shape if the goal isn't fully achievable>

### Estimated session count
<n sessions>

## Outcome

*This section is populated by `arc-creation` (log mode) after the arc concludes.*
```

The Outcome section is left as a stub placeholder so log mode has a clear target to replace.
