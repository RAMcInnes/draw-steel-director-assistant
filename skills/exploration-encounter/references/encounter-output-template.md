# Exploration encounter output template

The exploration-encounter skill writes finished encounters using this template. Sections marked *"Included when..."* are conditional on the encounter's content triggering the matching Draw Steel subsystem (Stealth / Group test / Montage); the Test structure section is always included.

```markdown
# <Encounter title>

**Type:** exploration
**System:** Draw Steel
**Date drafted:** YYYY-MM-DD

## Location & first impression
Where this happens and the sensory hook as the party arrives.

## Draw
The core question, mystery, or promise pulling the party in.

## Pressure
Why lingering costs something — time, resources, a rival, a worsening condition.

## Points of interest
Three or more concrete things to discover, interact with, or be threatened by.

## Layered reveals
- **Surface** (what's visible on arrival): …
- **Deeper** (reward for meaningful investigation): …
- **Deepest** (payoff for sustained pressure): …

## Fail-forward
If a key check fails, the scene advances at a cost rather than stalling. Describe the cost.

## Test structure
*Always included. For each Test the PCs will likely face: the characteristic the GM calls for (Might / Agility / Reason / Intuition / Presence — never a skill; players decide for themselves which of their skills to apply), the difficulty tier per `tests.md`, and a fail-forward sketch covering at minimum plain failure and failure-with-consequence (success-with-reward hooks are a bonus). Skip abstracting difficulty into vague phrases like "a tough check" — state the tier the ruleset names.*

## Stealth structure
*Included when the encounter involves hiding, sneaking, or surprise. Per `hide-and-sneak.md`: who is hiding from whom, what cover / concealment / observer conditions apply, detection range and the characteristic detectors test against, and what happens when stealth is broken (including which abilities bypass hidden). If a non-default characteristic substitution is permitted in this scene (e.g., Presence in place of Agility to hide in a flock), pre-commit to it here. Omit otherwise.*

## Group test structure
*Included when the encounter frames a single collaborative moment where every participant attempts the SAME task. Per `grouptest.md`: participants, the shared characteristic the GM calls for, difficulty tier, pass/fail threshold, and what the collective reward / consequence shapes are for this specific task. Omit otherwise. If participants tackle DIFFERENT sub-tasks, that's a Montage, not a group test.*

## Montage structure
*Included only when the encounter is a multi-scene push where different heroes tackle different obstacles. Per `montages.md`: difficulty (with the matching success/failure limits, adjusted for party size), an obstacle pool (at least 2–3× the success limit), which obstacles can recur vs. are one-shot, skill-group coverage so no hero is stranded (per the can't-reuse-skill rule), and one-sentence narratives for total success / partial success / total failure outcomes. Map which Points of interest above correspond to which montage-test slots. Omit otherwise.*

## Ties to existing material
*Included only if the tie-in question surfaced connections. Omit the section otherwise.*
```
