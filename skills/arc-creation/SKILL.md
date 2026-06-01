---
name: arc-creation
description: Use when designing or wrapping up a multi-session arc within a Draw Steel campaign. Two modes — prep mode plans a new arc (beats, antagonist, stakes, expected resolution); log mode synthesizes an Outcome from session logs after the arc plays. Reads campaign + prior arcs' Outcome sections and consults the shared Draw Steel setting references when relevant.
---

# Arc creation

## When to use / when not to use

Use this skill when the user wants to plan or close out a multi-session storyline — typically 3–8 sessions of bounded narrative within a longer campaign. Prep mode runs at the start of an arc (or partway through, if revising); log mode runs after the arc concludes, synthesizing what happened across its sessions.

Do not use this skill for single-session planning (use `session-creation`) or for the campaign as a whole (use `campaign-creation`). If the user is unclear whether they want an arc or a session, ask: an arc spans multiple sessions; a session is one play sitting.

**Mode selection.** Branch on user intent at the opening of the interview:
- "plan act/arc N" / "design the next arc" / "start arc 2" → **prep mode**
- "wrap up arc N" / "log how arc N played out" / "arc N is over, capture what happened" / "synthesize the outcome of arc N" → **log mode**

## Craft principles

An arc is a chapter, not a campaign. It has a beginning, middle, and end. Its antagonist either dies, escapes (to seed the next arc), transforms, or is set aside. Its central question gets answered, deferred with new texture, or transmuted into a different question. If your arc's beats could fuel 30 sessions, you've described a campaign; trim.

Arcs co-evolve with the campaign. The first arc is set at campaign creation; subsequent arcs are set after the previous arc has played, because what *actually happened* at the table reshapes what should come next. Don't pre-plan arcs 2, 3, 4 at campaign-creation time — that's writing a novel, not running a TTRPG.

Every arc needs an antagonist (or antagonistic force). Generic "danger" without a face fizzles; a named antagonist with goals, leverage, and a credible path to those goals creates pressure that the players can grapple with directly. The antagonist may be human, factional, environmental, or temporal — but they must be specific.

A villain is defined by **what they've done and what they plan to do**, not what they are. The rulebook's *Villain Sins* principle: actions speak louder than words. Heroes should encounter the corpses, the burning villages, the survivors' accounts before they meet the villain. *What they've done* shows they're capable of evil — not just nominally evil. *What they plan to do* is worse than what they've done, and is what the heroes must stop. Both are required arc-prep fields; "the villain is bad" is not enough.

Most villains don't see themselves as evil. Heroes and villains often share motivations — ambition, revenge, protecting others, saving the world. The difference is that villains believe their goals justify sacrificing others. The arc's antagonist field should name the *motivation* (vendetta, birthright, protect-by-conquest, save-the-world-via-dark-power, raw mayhem) so the antagonist's choices stay coherent across sessions.

An arc's resolution must allow multiple paths to the goal. The rulebook's *Adventure Goal* principle: ideally the heroes can accomplish the goal in more than one way. *"Depose the tyrant"* is a goal — *"help the rightful heir,"* *"infiltrate and assassinate,"* *"raise a rebellion"* are paths. The arc's `### Resolution target` should sketch the planned shape **and** name 1–2 alternate paths the heroes could plausibly take. Sometimes the goal is to prevent total disaster (*"escape the city leading civilians to safety"*) rather than defeat the villain — heroes are still heroes for saving people even if the villain wins this round.

An arc names which PC threads it opens room for. Read `campaign.md`'s `## PC Hooks` and call out, per PC, whether this arc's premise/antagonist/beats give that PC's hooks room to breathe. There is no cap — an arc may legitimately touch all PCs' threads if the fiction supports it. The arc's `### PC Threads` field is the **menu** that `session-creation` draws from when picking the per-session Spotlight (which is capped at 1–2 PCs); spotlight rotation discipline lives at the session layer, not here.

Beats are the arc's skeleton. List 4–8 beats — narrative moments the arc moves through. They aren't sessions (one beat may span sessions or vice versa); they're the dramatic shape. Beats should escalate.

Stakes scale with the arc. Don't reuse the same stakes across arcs (rescue the kid → stop the cult → save the kingdom is an escalation; rescue → rescue → rescue is a stall). Each arc should put a different kind of pressure on the party.

Resolution targets are aspirational, not contractual. Plan a resolution shape (the antagonist falls, the city burns, the relic is destroyed, the truth is revealed), but expect the table to bend it. Log mode captures what actually happened; prep mode is just your best guess.

### User additions

*Space for the user to add their own craft notes as the skill gets used. Leave the existing principles above intact; extend them here.*

## Reference consumption

Read `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/*.md` files relevant to the arc's content:

- `factions.md` — faction-driven arcs
- `regions.md` — place-anchored arcs
- `timeline.md` — historical-touch arcs
- `cosmology.md` — arcs involving gods, planes, or the afterlife
- `overview.md` — broad world orientation (e.g., the first arc of a campaign)

Skills work gracefully when reference files are missing or stubbed — note "no setting reference on file — proceeding with generic suggestions" and continue. Never block on missing references.

For the foundational Tests / Skills / Negotiation systems mentioned during arc planning, consult `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/vocabulary.md` for descriptive entries; defer to the skill-local files (`${CLAUDE_PLUGIN_ROOT}/skills/exploration-encounter/references/tests.md`, `${CLAUDE_PLUGIN_ROOT}/skills/social-encounter/references/negotiation-*.md`) if mechanical detail is needed (rare at arc level).

Always scan `campaign.md`'s `## PC Hooks` section when planning an arc. Each PC's open question / complication / build-derived hooks / current downtime projects are the source material for the arc's `### PC Threads` field; the arc decides which of those hooks its premise and beats have room to pressure. Downtime projects are opportunistic rather than required pressure points — incorporate them when the arc's fiction allows (a research project's missing tome turns up in a beat; a training arc dovetails with the antagonist's schedule), but don't force them.

## Inter-skill contracts

This skill both **consumes** and **produces** headers documented at `${CLAUDE_PLUGIN_ROOT}/references/skill-contracts.md`:

- **Consumes** (prep mode): `## PC Hooks`, `## Key NPCs`, `## Notable Locations`, `## Factions` from `campaign.md`. The canonical strings are in the contracts file — if a header here ever disagrees with the contracts file, the contracts file wins.
- **Consumes** (log mode): `## Play log` and `### Spotlight realized` from each session file in the closing arc; both strings are documented in the contracts file.
- **Produces** (prep mode, written to `arcs/<date-slug>.md`): `## Prep`, `### PC Threads`, `### Key NPCs`. The output template in `references/output-template-prep.md` writes these verbatim.
- **Produces** (log mode, written to the same arc file by replacing the stub `## Outcome`): `## Outcome`, `### PC Threads realized`. Output template in `references/output-template-outcome.md`.

When mid-flow invocations of `npc-creation` return link strings during prep-mode interview question 7 (Key NPCs), validate per the contracts file's Mid-flow return rules before embedding into `### Key NPCs`.

If the contracts file ever disagrees with text in this skill, the contracts file wins.

## Interview template (prep mode)

**One question per turn. Wait for the user's answer before advancing. Never batch questions into one reply.**

Every question is accompanied by 2–3 suggestions anchored in the craft principles, prior answers, and the **loaded campaign context** (campaign.md, prior arcs' Outcome sections, the most recent session log).

Every question accepts a *"you decide"* / *"skip"* / *"leave blank"* deferral. On *"you decide"*, generate a plausible answer anchored in the craft principles, prior answers, and the loaded context; surface it inline as *"Going with: …"* and record it. On *"skip"* / *"leave blank"*, record the field as empty — the Director can fill it in later by editing the arc file directly.

1. **Premise** — one or two sentences. What is this arc about? What question does it ask?
2. **Antagonist** — who or what is opposing the party in this arc? Capture five subfields:
   - **Identity** — name, what they are (human, factional, environmental, temporal).
   - **Motivation** — what they want, framed as the *why* (vendetta, birthright, protection-by-conquest, save-the-world-via-dark-power, mayhem).
   - **What they've done** (sins/history) — evil already accomplished that heroes can uncover. Corpses, burned villages, survivor accounts, betrayals already executed. *"What's their first sin the heroes will encounter?"*
   - **What they plan to do** — the next, worse thing. This is what the arc opposes.
   - **Hard line** — the line they will not cross, or cannot. (Sometimes there is none — note that.)
3. **Inciting incident** — the moment that reveals the arc's goal to the heroes (or sets them on the path to discovering it). The fresh corpse in the street, the messenger arriving with the burning village's account, the artifact going missing. The first thing that happens when the arc begins.
4. **Beats** — 4–8 narrative moments the arc moves through, in rough order. (Not sessions; beats can span or compress.) Each should escalate.
5. **Stakes** — what is at stake for the party, the antagonist, and any third parties? How does this differ from prior arcs' stakes?
6. **PC Threads** — for each PC in `campaign.md`'s `## PC Hooks` section, capture two pieces:
   - **Room to breathe** — does this arc's premise/antagonist/beats give that PC's hooks room? One line on *how* if yes; *"not this arc"* if no.
   - **Complication echelon move** — for PCs whose complication is being pressured this arc, sketch how it advances *across* the arc. *"Sorin offers her services to Saxton for a chance to face Linn — Sorin attacks during the keep assault."* Pulls from the PC's complication stance captured at campaign intake. Omit for PCs whose complication is dormant this arc.
   
   There is no cap — list every PC the arc can plausibly pressure. This is the menu `session-creation` draws from for per-session Spotlight; do not pick winners here. *"You decide" populates the field by walking each PC's Hook entry against the arc's premise and proposing complication echelon moves anchored in their stance.*
7. **Key NPCs** — who develops, transforms, dies, or enters during this arc? (1–4 named NPCs is plenty.) For NPCs that already exist in `npcs/index.md` (loaded during context load), surface as link candidates and capture only the arc-specific change ("what does this arc do to them?"). For NPCs the arc *introduces*, invoke `npc-creation` mid-flow — the new file gets written, the link comes back, the arc's `### Key NPCs` field stores the link plus the arc-specific change. Do not capture full NPC details here; that's `npc-creation`'s job.
8. **Resolution target** — what does the planned ending of this arc look like? Acknowledge it's aspirational. **Required:** name 1–2 alternate paths the heroes could take to reach the same goal (or a partial-victory shape if the goal isn't fully achievable). *"Depose Saxton via the rightful heir, OR via assassination, OR via inciting Saxton's own troops to mutiny."* The arc's resolution shape is the destination; the alternate paths are the menu of routes the table can pick from.
9. **Estimated session count** — how many sessions do you expect this arc to take?
10. **Arc title** — *asked last.* With premise, antagonist, beats, and resolution now settled, propose 1–2 short, evocative arc titles drawn from what's been captured and present them for the user to accept, tweak, or replace. Slugified by the agent for the filename. *"You decide" → take your top suggestion. If the user named the arc earlier in the interview, capture it then and simply confirm it here rather than re-proposing.*

## Interview template (log mode)

Log mode does not run a question-by-question interview. Instead, it runs a **synthesis-then-review** pattern:

1. Confirm with the user which arc is being closed (resolve from `arcs/index.md` if ambiguous).
2. Load the arc file's `## Prep` section and **all session logs for sessions belonging to this arc** (resolved via the Sessions column in `arcs/index.md` or session-file backreferences to the arc).
3. **Synthesize a draft `## Outcome` section** with these subsections (see `${CLAUDE_PLUGIN_ROOT}/skills/arc-creation/references/output-template-outcome.md`):
   - **What happened** — narrative arc summary pulled from session logs, in chronological order
   - **Outcomes vs. plans** — for each prepped beat: did it hit, transform, or get skipped?
   - **Untouched prep** — explicit list of prepped beats, NPCs, threads that never came up (these are candidate material for future arcs)
   - **PC Threads realized** — for each PC listed in the arc's `### PC Threads`, what actually advanced for them across the arc's sessions? Synthesized from each session log's `### Spotlight realized` entries. PCs whose threads were named but never spotlighted get noted as "thread carried forward — candidate for next arc."
   - **Final state** — party state at arc end (level, allies/enemies gained, significant resources/items), antagonist's actual fate, key NPC fates, threads dangling into the next arc
4. Present the synthesized draft to the user, with an explicit invitation to revise any subsection.
5. Run the standard ship/revise loop until the user ships.

The log mode never invents events that aren't in the session logs. If a session log is sparse, the synthesis says so and asks the user to expand rather than inventing detail.

## Output templates

- Prep mode: see `${CLAUDE_PLUGIN_ROOT}/skills/arc-creation/references/output-template-prep.md`
- Log mode: see `${CLAUDE_PLUGIN_ROOT}/skills/arc-creation/references/output-template-outcome.md` (the agent appends the Outcome section to the existing arc file)

## Anti-patterns

- **Arcs without antagonists** — generic "danger" fizzles; every arc needs a specific opposing force, named.
- **Villains defined only by what they are, not what they do** — "an evil sorcerer" is a label; "the sorcerer who poisoned three rival merchants last year and now plans to dose the city's well with the same compound" is a villain. The What-they've-done / What-they-plan subfields are required.
- **Resolution targets without alternate paths** — heroes need more than one credible route to the goal. A single-path resolution turns the arc into a railroad.
- **Reused stakes across arcs** — escalate or vary; rescuing the same person three arcs in a row is a stall, not an escalation.
- **Pre-planning arcs 2+ at campaign creation** — arcs co-evolve with what happens at the table. The next arc's prep is informed by the previous arc's Outcome, which doesn't exist until that arc has played.
- **Synthesis inventing events not in the session logs** — log mode is content generation FROM existing session logs, not creative writing. If a log is sparse, ask the user to expand rather than fabricate.
- **Skipping Untouched prep** — this is the genuinely novel output of arc-log mode. Don't drop it; future arcs will mine it.
