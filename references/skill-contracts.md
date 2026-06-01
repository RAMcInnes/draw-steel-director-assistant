# Skill Contracts

> Plumbing reference for the Draw Steel director-assistant. The agent and its skills communicate through a small set of stable contracts — section header strings, mid-flow return values, relative-link depths, and index column orderings. Skills MUST cite this file when consuming a header string or producing a return value rather than restating the literal. A rename here is a single edit; restating literals across files invites drift.
>
> This file is plumbing, not Draw Steel canon. Editing it changes how skills talk to each other; editing `references/draw-steel/*` changes the descriptive content skills suggest from. The two trees are independent.

## Section header contracts

Producers write these headers verbatim into their output files; consumers read them by name. If a header here changes, every consumer in the right column needs updating in the same edit. Skills cite this table by reference; they do not restate the literal strings in their own SKILL.md content beyond the level needed for craft principles to read naturally.

| Producer | Header (exact string) | File | Consumers |
|---|---|---|---|
| `campaign-creation` | `## PC Hooks` | `campaign.md` | `arc-creation` (prep — `### PC Threads` source), `session-creation` (prep — Spotlight defaulting) |
| `campaign-creation` | `## Key NPCs` | `campaign.md` | `arc-creation` (prep), `session-creation` (prep), encounter skills (continuity) |
| `campaign-creation` | `## Notable Locations` | `campaign.md` | `session-creation` (prep), encounter skills (continuity) |
| `campaign-creation` | `## Factions` | `campaign.md` | `arc-creation` (prep), `session-creation` (prep), encounter skills, `npc-creation` (Allegiances), `location-creation` (Faction control) |
| `arc-creation` (prep) | `## Prep` | arc file | `arc-creation` (log — synthesis source), agent ship behavior |
| `arc-creation` (prep) | `### PC Threads` | arc file | `session-creation` (prep — Spotlight rotation source) |
| `arc-creation` (prep) | `### Key NPCs` | arc file | `session-creation` (prep) |
| `arc-creation` (log) | `## Outcome` | arc file | `arc-creation` (prep, when planning a follow-on arc) |
| `session-creation` (prep) | `## Prep` | session file | encounter skills (session-aware loading), `session-creation` (log — replaces stub `## Play log`) |
| `session-creation` (prep) | `### Spotlight` | session file | `session-creation` (log — pairs with `### Spotlight realized`) |
| `session-creation` (log) | `## Play log` | session file | `arc-creation` (log — synthesis), `session-creation` (prep — prior-session reads) |
| `session-creation` (log) | `### Spotlight realized` | session file | `session-creation` (prep — rotation), `arc-creation` (log — `### PC Threads realized` synthesis) |

## Mid-flow return string format

When a creation skill (`npc-creation`, `location-creation`, plus any future `*-creation` skill) is invoked **mid-flow** from another skill, it returns a single markdown link string of exactly this shape:

```
[<Display Name>](<relative-path-to-the-newly-created-file>)
```

Rules:
- Exactly one line. No surrounding prose, no JSON envelope, no leading/trailing whitespace beyond the line itself.
- The relative path is calculated for the **parent skill's output location** (see Relative-link depths below). The creation skill computes this from the parent's path, which the agent passes when invoking.
- The display name is the entity's canonical name as captured at intake (question 1 of the creation skill's interview).

Standalone invocations of the same creation skill return a **different** shape — absolute file path plus a one-line confirmation — because there's no parent artifact to embed into. The agent's orchestration flow distinguishes the two cases.

**Validation.** The agent (per Task 2's orchestration flow step) validates a mid-flow return matches `[Name](path)` shape before embedding it into the parent artifact. If validation fails, the agent surfaces the raw return verbatim in the parent's draft so the user sees the breakage rather than a silently-malformed file.

## Relative-link depths

Files at different depths under the campaign folder need different relative prefixes when linking to siblings or aunts. The agent and any skill emitting cross-file links MUST use these prefixes; creation skills' return strings follow the same rules.

| File at | Depth | Link to `npcs/<slug>.md` | Link to `locations/<slug>.md` | Link to `arcs/<slug>.md` | Link to `sessions/<dir>/session.md` |
|---|---|---|---|---|---|
| `campaign.md` | 0 | `npcs/<slug>.md` | `locations/<slug>.md` | `arcs/<slug>.md` | `sessions/<dir>/session.md` |
| `npcs/<slug>.md` | 1 | (self-folder; rarely needed) | `../locations/<slug>.md` | `../arcs/<slug>.md` | `../sessions/<dir>/session.md` |
| `locations/<slug>.md` | 1 | `../npcs/<slug>.md` | (self-folder) | `../arcs/<slug>.md` | `../sessions/<dir>/session.md` |
| `arcs/<slug>.md` | 1 | `../npcs/<slug>.md` | `../locations/<slug>.md` | (self-folder) | `../sessions/<dir>/session.md` |
| `sessions/<dir>/session.md` | 2 | `../../npcs/<slug>.md` | `../../locations/<slug>.md` | `../../arcs/<slug>.md` | (self) |
| `sessions/<dir>/encounters/<slug>.md` | 3 | `../../../npcs/<slug>.md` | `../../../locations/<slug>.md` | `../../../arcs/<slug>.md` | `../session.md` |
| `drafts/encounters/<slug>.md` | 2 | `../../npcs/<slug>.md` | `../../locations/<slug>.md` | `../../arcs/<slug>.md` | `../../sessions/<dir>/session.md` |

## Index column orderings

The agent is the sole writer of all four index files. **Skills consuming an index MUST locate columns by header-name match** (read the header row, find the column index by string match, then read that column from data rows). Direct positional access is forbidden — it makes column reordering a silent breakage.

Current header rows (the agent's ship behavior writes these verbatim):

- `arcs/index.md`: `| Arc | Premise | Sessions | Status |`
- `sessions/index.md`: `| Date | Arc | Session | Status |`
- `npcs/index.md`: `| NPC | Role | Status | First seen |`
- `locations/index.md`: `| Location | Type | Status | First visited |`

Adding a new column to any of these is non-breaking as long as existing column header names are preserved. Renaming an existing column header is a coordinated change here plus every consuming skill — search this file for the header string to find them.
