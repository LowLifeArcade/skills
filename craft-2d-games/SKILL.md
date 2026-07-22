---
name: craft-2d-games
description: Build, debug, and refine maintainable 2D games with clear coordinate systems, tunable gameplay, editor/runtime parity, strong pixel-art presentation, and visual verification. Use for 2D or pixel-art game work involving players, enemies, NPCs, animation, sprite sheets, hitboxes, colliders, combat, dialogue, cameras, stages, level editors, tuning screens, HUDs, save data, or gameplay architecture—especially in C, C++, SDL, raylib, Godot, or custom engines.
---

# Craft 2D Games

Make the game feel good to play and easy to continue building. Treat clear authoring models, useful developer tools, and visual verification as part of the feature.

Read `references/workbench-patterns.md` before changing entity transforms, animation, collision, tuning, persistence, or editor behavior.

## Start from the actual game

1. Read repository instructions and locate the build, test, asset, and capture workflows.
2. Trace the requested behavior end to end: authored data, load path, runtime state, update logic, draw path, editor controls, persistence, and tests.
3. Identify the current source of truth before editing. Call out split authority, hidden offsets, duplicated tables, and editor-only behavior.
4. Inspect relevant assets visually. Do not infer sprite content, frame boundaries, transparency, or animation quality from filenames alone.
5. Preserve unrelated changes and existing working content.

When asked only to explain or diagnose, stop after establishing the cause and model. Implement only when the request includes a change.

## Model behavior explicitly

- Give every entity one documented world origin.
- Express sprites, movement colliders, hurtboxes, attack boxes, effects, nameplates, and interaction zones as local data relative to that origin.
- Distinguish authored data, runtime state, and derived values. Avoid multiple writable representations of the same fact.
- Use the same conversion and draw helpers in tools and gameplay so previews match runtime.
- Name coordinate spaces and offsets by role. Replace unexplained `x/y`, `ox/oy`, or magic constants when their meaning is ambiguous.
- Centralize tuning and persistence catalogs. Adding one tunable field should not require synchronized edits in distant registries.

## Implement a complete slice

Carry the change through every affected surface:

1. Data model and defaults
2. Load, migration, and save behavior
3. Runtime update and rendering
4. Editor or tuning controls
5. On-screen labels and feedback
6. Tests and visual checks
7. Architecture or control documentation when the mental model changes

Do not leave a feature working for only one archetype, one direction, one animation, or one stage unless that limitation is intentional and visible.

## Build humane tools

- Prefer isolated workbench scenes for animation, collision, and actor tuning; keep world position editing in the stage context.
- Show origins, ground contact, collider roles, selected layers, current mode, units, and persisted values directly in the tool.
- Use outlines or halos so guides remain visible on light and dark artwork.
- Make global-versus-frame and archetype-versus-instance editing explicit.
- Provide save, reset, cycling, and coarse/fine adjustment controls where appropriate.
- Prevent selection and edits from leaking across inactive layers or unrelated entities.

## Protect the game feel

- Preserve the established art direction, scale, silhouette, palette, and character identity unless redesign is requested.
- Evaluate animation as motion: contact, weight, anticipation, follow-through, cadence, baseline stability, and directional behavior.
- Keep collision geometry stable when visual offsets or sprite scale change unless the user explicitly wants gameplay geometry changed.
- Favor readable feedback: short damage flashes, clear state transitions, legible HUD framing, and animation timing that matches movement speed.
- Keep decorative interfaces informative. Theme must not obscure values, controls, or game state.

## Verify proportionally

Run the strongest checks the repository supports:

- compile and static analysis
- focused unit tests, then the broader relevant suite
- save/load or migration round trips for authored data
- deterministic gameplay or state tests
- screenshots, frame strips, or video captures for visual changes
- both facing directions and every affected archetype
- baseline, center drift, crop bounds, alpha leakage, foot sliding, and collider alignment for animation work
- editor-versus-runtime comparison for tooling changes

If no capture workflow exists and the change is visual, add the smallest reusable one that fits the project rather than relying on compilation alone.

## Hand off clearly

Lead with what now works. Explain the source of truth and control model in plain language, list the important files or controls, and report the exact checks run. Mention any remaining limitation without burying it.
