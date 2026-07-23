# Skills Repository README Design

**Date:** 2026-07-22
**Status:** Approved

## Goal

Create a useful, memorable README for people installing and using the Low Life Arcade skills collection. The README should work for any agent supported by the `skills` CLI, explain the available skills quickly, and make installation easy.

## Direction

Use an install-first **Field Manual** concept inspired by retro Japanese hardware documentation. The tone should feel collectible and distinctive without compromising GitHub readability. Favor restrained monochrome styling, numbered modules, technical labels, and small arcade-flavored phrases over loud decorative effects.

The README will use GitHub-native Markdown rather than custom HTML or generated image assets. This keeps it accessible, fast, maintainable, and consistent in light and dark GitHub themes.

## Content Structure

1. **Identification header**
   - Low Life Arcade field-manual label
   - Clear `Agent Skills` title
   - One-sentence description of the collection
   - skills.sh badge linking to the repository listing

2. **Quick install**
   - Lead with `npx skills add LowLifeArcade/skills`
   - Explain that the interactive CLI lets users choose skills and compatible agents
   - Include a copyable command for installing one named skill

3. **Skill modules**
   - Present each skill as a numbered module
   - Include its purpose, useful situations, and a realistic example prompt
   - Link each module name to its local `SKILL.md`
   - Cover `90s-japan` and `craft-2d-games`

4. **Operating notes**
   - Explain that a skill activates when a request matches its description or when named directly
   - Include `npx skills update` for updates
   - State that the collection is intended for agents supported by the `skills` CLI
   - Encourage users to inspect skill contents before installation

5. **Closing mark**
   - End with a short on-brand line: `COPY. INSTALL. MAKE SOMETHING WITH A POINT OF VIEW.`

## Voice and Visual System

- Concise, confident, and practical
- Hardware-manual vocabulary used sparingly: `field manual`, `module`, `quick install`, `operating notes`
- No fake Japanese text, excessive emoji, ASCII art, animated badges, or wide comparison tables
- No claims of universal compatibility beyond the current `skills` CLI support
- Keep commands and examples easy to copy

## Source of Truth

Descriptions and prompts must reflect the checked-in `SKILL.md` and `agents/openai.yaml` files. Installation syntax and the badge format must follow the current official skills.sh documentation.

## Verification

- Confirm every relative repository link resolves
- Confirm skill names in commands match YAML frontmatter
- Confirm Markdown structure renders sensibly using a local Markdown parser when available
- Review the final diff for accidental inclusion of brainstorming artifacts
- Verify the working tree before publishing

## Out of Scope

- Contributor documentation
- Skill authoring instructions
- Generated hero artwork or screenshots
- Agent-specific installation walkthroughs
- Repository restructuring or changes to the skills themselves
