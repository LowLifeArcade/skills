# 2D game workbench patterns

Use these patterns selectively. Adapt names and structures to the engine rather than forcing a framework onto the repository.

## Entity transform hierarchy

Use one world-space origin per actor:

```text
actor world origin
├── movement collider: local rectangle
├── hurtbox: local rectangle
├── attack hitbox: local rectangle or shape
├── interaction zone: local shape
├── sprite: frame crop + local visual offset + visual scale
└── effects and labels: local anchors
```

Good invariants:

- Moving the actor moves every child representation.
- Nudging artwork does not silently move gameplay boxes.
- Resizing artwork pivots around the documented actor origin.
- Flipping direction applies one consistent transform to every directional child.
- World placement belongs to the stage instance; reusable visual and combat tuning belongs to the archetype.

Separate adjustments by scope:

- **Frame**: crop, per-frame visual offset, optional per-frame scale, duration
- **Clip**: playback mode, loop, event timing
- **Archetype**: global visual offset, base scale, default boxes, movement and combat tuning
- **Instance**: world position, patrol bounds, stage-specific overrides, state

Avoid adding unexplained draw-time constants after authored offsets. If compatibility requires one, name it, document its coordinate space, and migrate toward the canonical model.

## Authored, runtime, and derived data

Keep three concepts distinct:

- **Authored data**: stable values the developer edits and saves
- **Runtime state**: transient values such as velocity, current frame, cooldown, or health
- **Derived values**: world rectangles, mirrored offsets, current crop, and presentation coordinates computed from the first two

Write authored values through one API. Make editors mutate the same structures that serialization reads and gameplay consumes. Do not maintain a legacy tuning table beside stage assets or a preview-only copy beside runtime data.

For large tuning sets, use one declarative catalog to drive lookup, serialization, defaults, inspection, and validation. Test that every persisted key maps exactly once and that old files migrate safely.

## Animation quality model

For a walk cycle, look for readable phases rather than merely different frames:

1. Contact
2. Recoil or down pose
3. Passing pose
4. High point
5. Opposite contact
6. Opposite recoil
7. Opposite passing
8. Opposite high point

Adapt the count to the style, but keep opposite contacts unmistakable. Check:

- planted foot displacement relative to character speed
- baseline drift and center drift
- silhouette changes between adjacent frames
- stable head and torso motion appropriate to the character
- consistent crop padding and no accidental clipping
- transparency or chroma-key leakage
- left/right rendering, including asymmetric props
- attack anticipation, active frames, recovery, and hitbox timing

Frame duration and world movement must agree. A beautiful cycle still slides if cadence does not match velocity.

## Isolated tuning workbench

Use a dedicated scene for reusable actor properties:

- neutral graph or low-contrast background
- labeled ground/contact line aligned to the movement collider
- origin cross with high-contrast halo
- distinct colors and labels for movement collider, hurtbox, hitbox, and interaction zone
- animation state, frame index, timing, scale, and offset values
- actor and animation cycling
- pause, step, slow motion, reset, save, and coarse/fine edit modes
- explicit indicator for frame, clip, archetype, or instance scope

Keep stage placement and patrol/world bounds in the stage editor, where environmental context is meaningful. Share rendering and geometry helpers between both tools.

## Stage and layer editing

- Select only objects on the active layer unless an explicit all-layer mode is enabled.
- Give stable IDs to placed instances; do not use array position as long-term identity.
- Apply deletion, cycling, and reordering to the canonical stage collection.
- Draw inactive layers with clear visual de-emphasis when useful, but never let them intercept active-layer input.
- Make the selected object, layer, and edit scope visible before a destructive action.

## Combat and feedback

- Keep movement collision, damage reception, and attack reach as separate shapes with separate roles.
- Drive active hit frames from animation events or an explicit timing table.
- Prevent repeated damage from one swing unless intended.
- Use brief flashes, hit stop, knockback, sound, particles, or camera response proportionally; preserve input responsiveness.
- Represent health mechanically and visually from the same value. Test threshold colors and zero/death transitions.

## Verification matrix

Choose rows and columns relevant to the change:

| Dimension | Examples |
|---|---|
| Actor | player, enemy archetypes, NPCs |
| State | idle, walk, attack, hurt, death, interaction |
| Direction | left, right, up, down |
| Context | isolated workbench, stage editor, live gameplay |
| Persistence | defaults, saved values, legacy migration |
| Presentation | normal scale, resized, nudged, bright/dark sprite |

Cover each meaningful intersection without exploding into redundant tests. For visual changes, save representative captures and compare them deliberately rather than treating screenshot generation as proof by itself.
