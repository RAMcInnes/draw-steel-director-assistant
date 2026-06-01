# Social encounter output template

The social-encounter skill writes finished encounters using this template. The Negotiation structure section (and its subsections) is included when the scene is a real negotiation, populated from the Draw Steel Negotiation references at `references/negotiation-*.md`; it's omitted for social scenes that aren't structured negotiations.

```markdown
# <Encounter title>

**Type:** social
**System:** Draw Steel
**Date drafted:** YYYY-MM-DD

## Key NPC(s)
For each: who they are, what they want, what they fear, and the hard line they will not cross.

## PC goals
What the party is trying to get out of this scene.

## Stakes
What's on the line for the PCs, the NPC, and any third parties watching.

## Leverage & currency
What each side can spend or threaten — information, favors, reputation, material wealth, coercion.

## Negotiation structure
*Included only when the scene is a real negotiation. Populate from the `references/negotiation-*.md` files. Omit for social scenes that aren't structured negotiations.*

### Opening
How PCs are most likely to open the negotiation given the leverage, approaches, and motivations established above. One or two sample opening arguments tailored to this NPC and scene — not generic.

### Stats
- **Attitude:** <hostile / suspicious / neutral / open / friendly / trusting>
- **Interest:** <starting value 1–4, from attitude>
- **Patience:** <starting value 1–5, from attitude; apply language bonuses if applicable>
- **Impression:** <NPC's level, or Director override>

### Motivations
The motivations this NPC actually has (typically 2), each with the personal context that makes the motivation true for *this* NPC and a sample argument a PC might use to invoke it.
- **<Motivation name>** — *why this NPC has it (one or two sentences of personal context).*
  - *Example argument:* "<a concrete line a PC might say to appeal to this motivation in this scene>"

### Pitfalls
The pitfalls this NPC reacts badly to (typically 1–2), each with the personal context and a sample misstep so the GM can recognize the trip-wire at the table.
- **<Pitfall name>** — *why this NPC reacts badly to it.*
  - *Example misstep:* "<a concrete line that would trip this pitfall>"

### Offers by Interest tier
What this specific NPC offers — or threatens — at each Interest level. Reference things this NPC actually controls; avoid generic phrasing. Every tier should be filled in so the GM has a concrete pivot ready when Interest moves at the table.
- **5 — *"Yes, and..."*** what they give, plus the sweetener.
- **4 — *"Yes."*** exactly what was asked.
- **3 — *"Yes, but..."*** what they give, plus what they ask in return.
- **2 — *"No, but..."*** the lesser offer they make in place of what was asked.
- **1 — *"No."*** refusal, plus what they might press the PCs about.
- **0 — *"No, and..."*** refusal, plus the harm the NPC seeks to do.

## Ties to existing material
*Included only if the tie-in question surfaced connections. Omit the section otherwise.*
```
