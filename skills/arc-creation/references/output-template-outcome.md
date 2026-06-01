# Arc Outcome output template (log mode)

The arc-creation skill (log mode) replaces the stub `## Outcome` section in an existing arc file with the following structure:

```markdown
## Outcome

**Date concluded:** YYYY-MM-DD

### What happened
<chronological narrative summary, drawn from session logs in this arc — typically 1–3 paragraphs>

### Outcomes vs. plans
| Prepped beat / NPC / thread | Status | Notes |
|---|---|---|
| <prep item 1> | hit / transformed / skipped | <how it played, or why it didn't> |
| <prep item 2> | … | … |
…

### Untouched prep
- <prep element that never came up — bullet form>
- …

*(These are candidate material for future arcs.)*

### PC Threads realized
- **<PC Name>:** <what actually advanced for this PC across the arc's sessions, drawn from each session log's `### Spotlight realized` — or "thread carried forward; candidate for next arc" if never spotlighted>
- **<PC Name>:** <same>
- …

*(One row per PC listed in the arc's `### PC Threads`. PCs whose threads carried forward are flagged for the next arc's planning.)*

### Final state
- **Party:** <level, key allies/enemies gained, significant resources/items, ongoing conditions>
- **Antagonist:** <actual fate — defeated, escaped, transformed, set aside>
- **Key NPCs:** <named NPCs and their fates>
- **Threads dangling:** <open threads heading into the next arc>
```

The synthesis populates each subsection from session logs; the user reviews and revises before commit.
