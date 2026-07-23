`LOW LIFE ARCADE / FIELD MANUAL 01`

# Agent Skills

Portable instruction sets for making distinctive creative work and better 2D games.

[![skills.sh](https://skills.sh/b/LowLifeArcade/skills)](https://skills.sh/LowLifeArcade/skills)

**STATUS:** 2 modules · compatible with agents supported by the skills CLI

## 01 / Quick install

```sh
npx skills add LowLifeArcade/skills
```

Choose a module and any compatible agent when prompted. To install one directly:

```sh
npx skills add LowLifeArcade/skills --skill 90s-japan
npx skills add LowLifeArcade/skills --skill craft-2d-games
```

## 02 / Select a module

### Module 01 — [90s Japan](./90s-japan/SKILL.md)

Give websites, images, slides, writing, branding, and other creative work a coherent 1990s Japan direction without sacrificing purpose or usability.

**Useful for:** Heisei-era art direction, retro Tokyo interfaces, analog-tech texture, editorial layouts, packaging, and period-aware creative concepts.

> Try: “Use `$90s-japan` to reinterpret this landing page as a mid-1990s Japanese consumer-electronics campaign.”

### Module 02 — [Craft 2D Games](./craft-2d-games/SKILL.md)

Build, debug, and refine maintainable 2D games with explicit coordinate systems, tunable gameplay, editor/runtime parity, and visual verification.

**Useful for:** player and enemy behavior, sprites and animation, hitboxes, combat, dialogue, cameras, level tools, tuning screens, HUDs, save data, and gameplay architecture.

> Try: “Use `$craft-2d-games` to tune this character’s run animation and verify its collider alignment in both directions.”

## 03 / Operating notes

- **Invoke:** Name a skill directly—such as `$90s-japan`—or make a request that matches its description.
- **Update:** Run `npx skills update` to refresh installed skills.
- **Compatibility:** See the skills CLI’s current [supported agents](https://skills.sh/docs/cli#supported-agents).
- **Inspect:** Skills are instructions your agent will follow. Read the linked `SKILL.md` and reference files before installing code you do not trust.

---

`COPY. INSTALL. MAKE SOMETHING WITH A POINT OF VIEW.`
