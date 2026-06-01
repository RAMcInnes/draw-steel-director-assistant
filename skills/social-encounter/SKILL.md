---
name: social-encounter
description: Use when designing a social encounter for a Draw Steel campaign — negotiation, interrogation, courtly maneuvering, or any scene where the primary mode is people talking. Provides narrative-first social-design principles (NPC wants/fears/hard lines, leverage, non-binary outcomes), an ordered interview, and an output template. Embeds the Draw Steel Negotiation ruleset.
---

# Social encounter

## When to use / when not to use

Use this skill when the primary mode of resolution is people talking — the scene resolves through conversation, leverage, and choice, and most of the interesting play is verbal. Use it even when violence could break out, so long as the fight is a reaction that the NPCs might trigger, not the planned payoff.

Do not use this skill when the scene is prelude to a planned fight (use `combat-encounter`; the talking is setup) or when the scene is primarily about discovering information from a space rather than a person (use `exploration-encounter`; talking to witnesses is a beat inside that frame). If the key thing is who the PCs are talking to and what they can get, this is the right skill.

## Craft principles

Every key NPC needs three things: what they want, what they fear, and a hard line they will not cross. Wants drive their opening posture; fears are leverage the PCs can exploit; the hard line is what keeps the scene from collapsing into "give them whatever they ask for." An NPC with no hard line is an NPC who says yes to enough leverage, and the scene has no shape.

Design for non-binary outcomes. At minimum: success, compromise, failure. Compromise is where most of the interesting play lives — the PCs get what they wanted but at a cost, or they get less than they wanted but it's enough. If the only two outcomes are "they said yes" and "they said no," you've built a flowchart, not a scene.

Leverage is currency. Information, favors, reputation, material wealth, threats, coercion, shared history, third-party pressure — these are what PCs spend to move an NPC, and what NPCs threaten with in return. Name the leverage on both sides before the scene starts so you know what the conversation can actually move.

Approaches shape reactions. Given 2-3 plausible angles the PCs might take — hard-line demand, charming appeal, factual argument, bribery, threat — the NPC reacts differently to each. Not a flowchart (if-X-then-Y), but shaded: the NPC's disposition, their read on the PC, and what they just heard all bend the reaction. Sketch two or three approaches so you're not improvising all the NPC responses at the table.

Stakes cut both ways. The PCs want something from the NPC; the NPC also has something on the line. A negotiation where only one side is exposed isn't a negotiation — it's an ask. Surface the NPC's stakes explicitly: if the PCs fail here, what does the NPC lose? If they succeed, what does the NPC keep?

Third parties change the scene. Most "private" conversations have someone else watching or listening — a patron, a rival, a faction, a public. Their presence shapes what the NPC can say out loud, what the PCs can afford to be seen doing, and what the real subtext is. When a scene feels flat, check whether there's an offstage audience that should be shaping it.

Negotiations — structured social conflict with mechanical backing — are a craft pattern in their own right. Draw Steel has formal rules for them: disposition tracks, Interest and Patience, Arguments, Motivations, Pitfalls. This skill embeds that ruleset into the output for any encounter the user frames as a real negotiation.

### User additions

*Space for the user to add their own craft notes as the skill gets used. Leave the existing principles above intact; extend them here.*

## Interview template

**One question per turn. Wait for the user's answer before advancing. Never batch questions into one reply.**

Every question is accompanied by 2–3 concrete suggestions anchored in these craft principles and the prior answers. Generate them alongside the question so the user can pick one, tweak it, or supply something different — suggestions sharpen the ask from an open prompt into a menu without overriding the user's own answer.

**When invoked from a `session-creation` flow** (the user's request mentions a specific session, or the agent has the session in working context), additionally read the parent session's `## Prep` section. Use it to align the NPC's wants/fears/leverage with the session's broader plan — e.g., if the session prep flags this as the moment a recurring antagonist is unmasked, scale the NPC's hard line accordingly. **Also load the linked NPC file** (`npcs/<slug>.md`) for the NPC at the center of this scene — this is critical for social encounters because allegiances, persuasion-fit, voice, behavior, and prior-appearance state all live in that file. Without loading it, the encounter risks contradicting the NPC's prior appearances. Also load the linked location file (`locations/<slug>.md`) if the site is named.

Any question may be answered with *"you decide"* (or equivalent deferral). In that case, pick the suggestion that best fits the craft principles and prior answers; surface the chosen suggestion inline so the user sees what was picked, and record it in the transcript so it remains revisable.

**Mode pre-question (asked first, every time).** *"Is this an Interaction or a full Negotiation?"*
- **Interaction** — lighter NPC conversation; necessary info offered freely; optional info via persuasion or a Test. No Interest/Patience scaffold. Use for "the heroes need to talk to the watch captain" and similar information-gathering scenes.
- **Negotiation** — adventure-changing conversation. Full Negotiation ruleset (Interest, Patience, Motivations, Pitfalls, Impression). Use when the conversation's outcome materially shapes the arc.

Branch the rest of the interview on the answer. The Interaction branch uses a leaner template (NPC profile + necessary info + optional info + persuasion-fit); the Negotiation branch uses the existing fuller template extended below.

1. Who is the key NPC? What do they want (motivations)? / What are they driven by (motivations)? What do they fear (pitfalls)? / What is their hard line (pitfall)?
   *Motivation and pitfall suggestions should be drawn from the campaign system's Negotiation ruleset when one exists. For Draw Steel, the 12 are: benevolence, discovery, freedom, greed, higher authority, justice, legacy, peace, power, protection, revelry, vengeance — each can be either a motivation or a pitfall depending on the NPC. See [negotiation-motivations-and-pitfalls.md](${CLAUDE_PLUGIN_ROOT}/skills/social-encounter/references/negotiation-motivations-and-pitfalls.md) for descriptions and example arguments.*

   **Persuasion-fit.** What does this NPC respond to, and what bounces off? Two short lists:
   - **Responds to:** <intimidation / a well-placed bribe / appeals to honor / displays of competence / shared grief / etc.>
   - **Bounces off:** <approaches the heroes might reasonably try that won't work — the NPC is incorruptible to bribes, immune to bluster, doesn't care about lineage, etc.>

   This drives test difficulty and offer-making during the conversation; it also signals to the heroes (through NPC reactions) what *will* work, so the players can adjust without grinding.

   **Archetype shape (suggestion only — Negotiation mode).** When asking what kind of NPC this is, surface the rulebook's twelve sample archetypes by name as a shape menu:

   > Bandit Chief, Knight, Guildmaster, Warlord, Burgomaster, Virtuoso, High Priest, Duke, Dragon, Monarch, Lich, Deity.

   Each is a *shape* the user can adapt: the Bandit Chief shape works for any local big shot (an arrogant tavern darts champion, a corrupt watch sergeant); the Virtuoso shape works for any local celebrity (a master crafter, a famous gladiator); etc. If the user picks an archetype, point them at the full archetype entry in the rulebook for the mechanical scaffolding (Impression Score, canonical motivations and pitfalls). If the user wants a fresh NPC, skip the archetype list and proceed.

2. What do the PCs want from this encounter?
3. What's at stake — for the PCs, for the NPC, for any third parties?
4. What leverage or currency is in play? (Information, threats, favors, reputation, money.)
5. What are 2–3 approaches the PCs might plausibly take, and how does the NPC react to each?

**Upfront-ness (Negotiation mode).** How clearly does the NPC tell the heroes what they want? *Default: straightforward.* A coy / unreadable NPC is a puzzle the heroes have to crack — interesting at high tables but harder to roleplay and easier to derail. The skill will warn against unreadable NPCs unless the user explicitly wants the puzzle shape.

**Negotiation style (Negotiation mode).** How does this NPC negotiate? *Anchor the answer in the NPC's voice / behavior / flaw* (already captured at the session or campaign layer): bluster, smiling rejection, verbose speeches, terse "yes / no," constant deflection through a third party, etc. Style and persona must agree — a flowery virtuoso who suddenly negotiates in clipped military beats reads as inconsistent.

**Pre-negotiation recon hooks (optional — Negotiation mode).** Are there leads the heroes can pursue *before* the conversation to learn the NPC's motivations and pitfalls? A downtime project of research, a montage test of rumor-gathering, a favor-trade with someone close to the NPC. List 1–2 if it fits the arc; this connects the social encounter into the parent session's prep and gives the players a way to feel prepared. Per the rulebook: *"It's always a good idea to let the heroes do a little recon before jumping into a negotiation."*

6. **(Negotiation mode.)** What do success, compromise, and failure each look like? (Not binary.) For Interaction mode, skip this — the Interaction output template's `## Out` field captures how the conversation typically ends.

**Outcome shelf (required — Negotiation mode).** Before the conversation runs, sketch all four levels:

- **Best case** — heroes get what they want and then some. List 1–2 *bonuses* the NPC might throw in (a favor, an item, a piece of information, an introduction).
- **Middle ground** — the NPC offers what's asked but wants a favor in exchange. List 1–2 *asks* the NPC could plausibly make of the heroes.
- **Worst case** — heroes offend the NPC into hostility. Sketch what the NPC might do to retaliate. (The rulebook's reassurance: "revenge is a dish best served cold — and maybe a few sessions from now — so you've got time to plan." A seed is enough.)
- **Always** — at least one **alternate path forward if the negotiation fails entirely.** A different NPC the heroes could approach instead, a theft, a workaround, a way to push forward without the NPC's help. The adventure cannot dead-end on a failed negotiation.

The Always row is non-negotiable. If the user can't sketch one, the encounter is mis-shaped — either the negotiation isn't actually adventure-critical (downgrade to an Interaction), or the adventure's structure needs revision before this scene gets prepped.

*The tie-in question is asked by the agent after this interview, not here.*

## Negotiation reference

User-maintained Draw Steel ruleset library at `${CLAUDE_PLUGIN_ROOT}/skills/social-encounter/references/negotiation-*.md`, organized as one file per topic. The full set:

- [`negotiation-overview.md`](${CLAUDE_PLUGIN_ROOT}/skills/social-encounter/references/negotiation-overview.md) — what a negotiation is, when to use it, threat-of-violence boundary
- [`negotiation-stats.md`](${CLAUDE_PLUGIN_ROOT}/skills/social-encounter/references/negotiation-stats.md) — Interest, Patience, Motivations, Pitfalls, starting-attitude table
- [`negotiation-motivations-and-pitfalls.md`](${CLAUDE_PLUGIN_ROOT}/skills/social-encounter/references/negotiation-motivations-and-pitfalls.md) — the 12 motivation/pitfall entries with example arguments
- [`negotiation-opening.md`](${CLAUDE_PLUGIN_ROOT}/skills/social-encounter/references/negotiation-opening.md) — opening, stop-combat-to-negotiate, uncovering motivations
- [`negotiation-arguments.md`](${CLAUDE_PLUGIN_ROOT}/skills/social-encounter/references/negotiation-arguments.md) — argument resolution, lying, Renown and Impression
- [`negotiation-response-and-offer.md`](${CLAUDE_PLUGIN_ROOT}/skills/social-encounter/references/negotiation-response-and-offer.md) — NPC response by Interest tier 0–5, when to keep going or stop

**Lookup:** at drafting time, the skill reads the relevant files and applies the rules to populate the `## Negotiation structure` section of the output template below. The skill never invents new mechanical content; it only applies what's in the references.

**Optional setting flavor.** When the social encounter involves a faction or region from the campaign's published setting, additionally read `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/factions.md` and `${CLAUDE_PLUGIN_ROOT}/references/draw-steel/setting/regions.md` for descriptive flavor — use sparingly, to anchor the NPC's allegiances and stakes in canon without inventing new lore. Skills work gracefully when these references are missing or stubbed.

## Inter-skill contracts

This skill participates in the inter-skill wire format documented at `${CLAUDE_PLUGIN_ROOT}/references/skill-contracts.md`:

- **Headers consumed.** When invoked from a `session-creation` flow, this skill reads the parent session's `## Prep` section and — critically — the linked NPC file for the NPC at the center of the scene, where allegiances, persuasion-fit, voice, behavior, and prior-appearance state live. Without loading that file, the social encounter risks contradicting the NPC's prior appearances. Linked location files are read when the site is named. The canonical header strings and relative-link depth conventions live in the contracts file.
- **Headers produced.** Encounter files don't produce headers other skills consume; the file is a leaf artifact in the workflow tree.

If the contracts file ever disagrees with text in this skill, the contracts file wins.

## Output template

See `${CLAUDE_PLUGIN_ROOT}/skills/social-encounter/references/encounter-output-template.md` for the full encounter output markdown template. The template includes sections for Key NPC(s), PC goals, Stakes, Leverage & currency, Negotiation structure (conditional, with Opening / Stats / Motivations / Pitfalls / Offers by Interest tier subsections), and Ties to existing material.

## Anti-patterns

- **Binary success/fail** — always offer a compromise outcome alongside success and failure. Two-option scenes are flowcharts, not roleplay.
- **NPCs with no hard line** — if the NPC will say yes to anything with enough leverage, the scene has no shape. Every key NPC needs a line they won't cross, even at cost.
- **Flowchart reactions** — "if they offer X, NPC does Y" flattens roleplay. Shade reactions: the NPC's disposition, their read on the PC, and what they just heard all matter.
- **Ignoring the Negotiation ruleset** — if the scene is a real negotiation, the `## Negotiation structure` section MUST be populated from the `${CLAUDE_PLUGIN_ROOT}/skills/social-encounter/references/negotiation-*.md` files.
- **Inventing mechanical content** — never synthesize Interest/Patience thresholds, Argument mechanics, disposition scales, or any other rules-layer material. This prohibition extends to the underlying Tests-layer rules the Negotiation references depend on (power-roll math, tier thresholds, test difficulty bands, edge/bane stacking, characteristics, skill-group membership, Renown values): if those aren't supplied by a reference, leave the gap visible rather than filling it from training-data guesses. Mechanical content comes from a reference or the section is omitted.
- **Single-NPC scenes with no third party** — even a private conversation usually has stakes for someone not in the room. Surface them; they change the subtext.
