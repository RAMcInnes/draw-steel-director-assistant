# Campaign.md output template

The campaign-creation skill emits the following structure for the agent to write as `~/draw-steel-campaigns/<campaign-slug>/campaign.md`:

```markdown
# <Campaign name>

**Date created:** YYYY-MM-DD

## Premise
<one or two sentences — blank if skipped>

## Gameplay Breakdown
- **Combat:** <High / Medium / Low>
- **Exploration:** <High / Medium / Low>
- **Interpersonal:** <High / Medium / Low>
- **Intrigue:** <High / Medium / Low>
- *(custom categories as needed)*

## Player Buy-In
<one or two sentences naming the experience contract — blank if skipped>

## Player Option Restrictions
<any restrictions on character choices, or "None">

## House Rules
<any rule modifications, or "None">

## Campaign Style
<Long Arc / Adventure of the Week / Looming Threat / Multiple Fronts / hybrid description>

## Party (Level: #)
- <PC Name> — <Class>, <Ancestry>, <Culture>, <Career> — <one-line description>
- …

## PC Hooks

### <PC Name>
- **Hooks:** <build-derived, 1–3 short bullets — blank if skipped>
- **Complication:** <name + what it costs — blank if skipped>
- **Stance on complication:** <keep benefit / lose drawback / be rid of it entirely / accept as-is — blank if skipped>
- **Open question:** <the personal question this PC is investigating — blank if skipped>
- **Downtime projects:** <0–N short bullets, each "name — one-phrase intent"; "None" if not pursuing any; blank if skipped>

## Echelon Outline
**Span:** <e.g., "1st through 4th", "1st–3rd", "1st only">

- **<Start> Echelon:** <one or two sentences — dominant conflict / location / villain action — most specific entry>
- **<Start+1> Echelon:** <one or two sentences — vaguer>
- … *(one row per echelon in the span; entries get vaguer the further out — drop rows for echelons outside the span)*

*(Players' actions reshape later echelons; vagueness is the point. `arc-creation` consults this menu when sequencing arcs.)*

## Key NPCs
- [<NPC Name>](npcs/<slug>.md) — <one-phrase role>
- …

*(Headline-link list. Per-NPC depth lives in `npcs/<slug>.md`; descriptions are not duplicated here. The agent populates this list at ship time from the names captured in intake step 10.)*

## Factions
- <Faction> — <short description>
- …

*(Inline descriptions — no per-faction files.)*

## Notable Locations
- [<Location Name>](locations/<slug>.md) — <type>
- …

*(Headline-link list. Per-location depth lives in `locations/<slug>.md`; descriptions are not duplicated here. The agent populates this list at ship time from the names captured in intake step 12.)*

## Themes & Open Questions
- <theme/question>
- …
```

Empty sections are kept (with no list items) so the user can fill them in later by editing. The Key NPCs and Notable Locations sections may be empty on initial ship if the user deferred those questions; the npcs/ and locations/ folders still get created with empty indexes.
