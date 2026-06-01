# Dynamic Terrain

*Source: Draw Steel Monsters, p. 331. Overview of terrain object stat blocks — individual terrain objects live in the book.*

A **terrain object** is an element placed in an encounter that alters tactics on the battlefield and lets the Director better theme the scene. Range is wide: hazards that make tempting forced-movement targets, fieldworks and siege engines that grant locational advantage, and supernatural objects an entire encounter can be built around.

## Terrain object stat blocks

Terrain objects use a distinct stat block format from monsters. The fields are:

- **EV.** Each dynamic terrain object has an encounter-value cost, just like monsters. Some objects — especially environmental hazards — have a cost representing an *area* (e.g., a 10×10-square section). A hazard can always be smaller than its listed size.
- **Stamina.** Either a fixed amount, or an amount *per square* depending on the object's nature and size. Per-square Stamina means an object can be partially destroyed square by square.
- **Size.** Either a standard creature size (e.g., 1M) or a count of squares of terrain/material. If sized in squares, creatures can move through the object but may trigger its effects. Many square-sized objects are difficult terrain, noted in the Size entry.
- **Direction.** Some objects have a defined direction indicating how they are placed (e.g., archer's stakes have a front side).
- **Deactivate.** Most terrain objects can be deactivated under the right circumstances. **Sabotage** is the general skill for deactivating mechanisms and siege engines; traps may use other skills depending on setup (Alchemy for a pool of flammable oil, Nature for a spiked pit trap in a forest, Magic or Psionics for a supernatural object, etc.). Disabling supernatural objects requires a more intricate process detailed in each stat block. Once deactivated, the Director determines how (and how long) to reset it.
- **Activate.** Most objects activate when a creature enters their space or when interacted with in a specific way. Unless otherwise noted, there's no limit on how often an object activates.
  - Traps and objects set up by creatures may activate only for creatures/objects of a particular size — e.g., goblins and kobolds typically calibrate traps for size 1M and larger, letting smaller creatures pass safely.
  - Many *area* terrain objects activate when a creature enters their area **without shifting**. If such an object is difficult terrain, remember that creatures can't usually shift through difficult terrain without a trait or feature that allows it.
- **Effect.** Defines what happens when the object is triggered.
- **Upgrades.** Some objects can be upgraded for additional effects. If an object has a size in squares, upgrade cost is paid *per square* unless otherwise noted.

### Hidden terrain objects

Some terrain objects are inherently hidden, or can be hidden via an upgrade. Hidden objects can be found as part of the **Search for Hidden Creatures** maneuver (see *Draw Steel: Heroes*). When making an Intuition test to search for hidden creatures and objects, use:

- **≤11:** find all hidden terrain objects adjacent to you.
- **12–16:** find all hidden terrain objects within 5 squares.
- **17+:** find all hidden terrain objects within 10 squares.

### Allied Awareness

Some terrain objects have an **Allied Awareness** trait noting benefits and options available to creatures familiar with and trained on the object. If a creature is aware of a terrain object and has had sufficient time to study it, they gain the object's Allied Awareness benefits at the Director's determination.

## Catalog

Specific terrain objects live in companion files under `dynamic-terrain/`. Each file follows the same Tags / Source / Flavor / Tactics shorthand — full stat blocks live in the book.

- [Environmental Hazards](dynamic-terrain/environmental-hazards.md) — natural terrain that defenders cultivate or channel for advantage (brambles, corrosive pool, frozen pond, lava, quicksand, toxic plants, angry beehive). Best when the scene is outdoors or in a wild/natural interior; leans on forced-movement and turn-start triggers to punish careless positioning.
- [Fieldworks](dynamic-terrain/fieldworks.md) — temporary military fortifications and placed traps (archer's stakes, bear trap, flammable oil, hidey-hole, pavise shield, snare trap, spike trap). Best when the antagonists had time to prepare a defensive position — camps, ambush sites, dug-in skirmish lines.
- [Mechanisms](dynamic-terrain/mechanisms.md) — built contraptions that often chain a trigger to an effect (column of blades, dart trap, pillar, portcullis, pressure plate, pulley, ram, switch). Best in dungeons, tombs, villain lairs, and engineered spaces; excels at splitting the party, denying lanes, and rewarding perception/sabotage play.
- [Siege Engines](dynamic-terrain/siege-engines.md) — crew-operated heavy weapons and fortifications (arrow launcher, boiling oil cauldron, catapult, exploding mill wheel, field ballista, iron dragon, watchtower). Best at higher levels and in set-piece fights — castle assaults, battlefield encounters, boss arenas where the engine itself is a participant.

**When suggesting terrain**, pick from the catalog above in priority order:
1. Match the **scene** (indoor/outdoor, prepared/improvised, scale).
2. Match the **antagonists** — who built or placed this, and why? Disciplined humanoids field fieldworks and siege engines; monsters in a wild biome lean on environmental hazards; trapped lairs lean on mechanisms.
3. Match the **objective** — Hold Them Off wants fieldworks and mechanisms to shape lanes; Assault the Defenses wants siege engines on the defender side; Escort wants environmental hazards along the route; Stop/Complete the Action wants a mechanism the heroes can sabotage or race.
4. Pick **one or two** features, not five. Terrain that pressures decisions is better than a dense clutter that noises up the map.
