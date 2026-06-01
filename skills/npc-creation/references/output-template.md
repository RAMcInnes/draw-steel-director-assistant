# NPC file output template

The npc-creation skill emits the following structure for the agent to write as `~/draw-steel-campaigns/<campaign-slug>/npcs/<slug>.md`:

```markdown
# <NPC Name>

**Role:** <one-phrase role>
**Status:** <alive / dead / missing / hostile / allied / unknown — default "alive">
**First seen:** <session link, or "not yet">
**Location(s):** [<location>](../locations/<slug>.md), [<location>](../locations/<slug>.md), …

## Profile
- **Distinguishing feature:** <one line, sight or scent>
- **Voice:** <one-line cue>
- **Behavior:** <one distinct behavior>
- **Flaw:** <one flaw>
- **Motivation:** <kernel — what they want; why they'd help the heroes, or what would stop them>

## Persuasion-fit
- **Responds to:** <approaches that work — short list>
- **Bounces off:** <approaches that won't work — short list>

## Allegiances
- **Factions:** <…>
- **Enemies:** <…>
- **Owes:** <… — debts, oaths, favors>

## Hooks / threads
- <which PC Hook or arc thread this NPC is tangled in — one bullet per attachment>
- …

## Notes
*(Director-edited free-text — accretes through play. Capture facts established at the table here so they don't drift across appearances.)*
```

Empty fields are kept (with the field heading and a blank value) so the user can fill them in later. Skipped sections collapse cleanly when rendered.
