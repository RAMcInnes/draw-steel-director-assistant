# Location file output template

The location-creation skill emits the following structure for the agent to write as `~/draw-steel-campaigns/<campaign-slug>/locations/<slug>.md`:

```markdown
# <Location Name>

**Type:** <city / district / building / wilderness / dungeon / specific site / etc.>
**Scope:** <general location | specific site>
**Status:** <one-line current state — e.g., "tense; under occupation" / "seal broken" / "neutral">
**First visited:** <session link, or "not yet">

## Atmosphere
- **Mood:** <one-word handle>
- **Senses on arrival:** <sight / sound / smell / feel — at least three of four>

## Purpose at the table
- **Why heroes come here:** <…>
- **What they can discover:** <information / NPCs / items / outcomes>

## Faction control
- **Held by:** <…>
- **Contested by:** <…>

## Hooks / threads
- <which arc or PC Hook this location is tangled in — one bullet per attachment>
- …

## Notable features
- <feature 1>
- <feature 2>
- <feature 3>

## Connected locations
- [<location>](<slug>.md) — <how they connect>
- …

## Notes
*(Director-edited free-text — accretes through play. To find which NPCs are anchored here, grep `npcs/` for this file's slug.)*
```

Empty fields are kept (with the field heading and a blank value). Skipped sections collapse cleanly when rendered.
