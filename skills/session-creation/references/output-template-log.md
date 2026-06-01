# Session Play log output template (log mode)

The session-creation skill (log mode) replaces the stub `## Play log` section in an existing session file with the following structure:

```markdown
## Play log

**Date played:** YYYY-MM-DD

### Recap
<one paragraph: what happened>

### Spotlight realized
- **<PC Name>:** <what actually advanced for this PC's hooks — or "spotlight missed; carry forward">
- **<PC Name>:** <same>

*(One row per PC in the prep `### Spotlight`. Drives next session's rotation choices and feeds `arc-creation` (log mode)'s `### PC Threads realized` synthesis at arc end.)*

### Threads
- **Opened:** <thread> — <one line>
- **Closed:** <thread> — <one line>
- **Transformed:** <thread> — <one line>

### NPCs encountered
- <name> — <state at session end (alive, escaped, allied, etc.)>
- …

### Party state changes
- **Level / XP:** <if any>
- **Conditions / resources:** <if any>
- **Allies / enemies gained:** <if any>
- **Significant items:** <if any>

### Untouched prep
*(Optional — what was in the Prep section but didn't come up. Candidate material for next session.)*
- …
```

The Status field in `sessions/index.md` updates to `played` on ship.
