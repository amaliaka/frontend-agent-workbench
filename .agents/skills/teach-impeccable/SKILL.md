---
name: teach-impeccable
description: One-time setup that gathers design context for your project and saves it to your AI config file. Run once to establish persistent design guidelines.
user-invocable: true
argument-hint: "[optional project or product context]"
---

Gather design context for this project, then persist it for all future sessions.

## Step 1: Explore the Codebase

Before asking questions, thoroughly scan the project to discover what you can:

- `README` and docs
  - project purpose, target audience, any stated goals
- `package.json` and config files
  - tech stack, dependencies, existing design libraries
- existing components
  - current design patterns, spacing, typography in use
- brand assets
  - logos, favicons, color values already defined
- design tokens and CSS variables
  - existing color palettes, font stacks, spacing scales
- any style guides or brand documentation

Note what you've learned and what remains unclear.

## Step 2: Ask UX-Focused Questions

STOP and ask the user concise questions to clarify only what you could not infer from the codebase exploration.

Focus on:

### Users And Purpose

- Who uses this?
- What's their context when using it?
- What job are they trying to get done?
- What emotions should the interface evoke? For example: confidence, delight, calm, urgency.

### Brand And Personality

- How would you describe the brand personality in 3 words?
- Any reference sites or apps that capture the right feel?
- What specifically about them?
- What should this explicitly NOT look like?
- Any anti-references?

### Aesthetic Preferences

- Any strong preferences for visual direction? For example: minimal, bold, elegant, playful, technical, organic.
- Light mode, dark mode, or both?
- Any colors that must be used or avoided?

### Accessibility And Inclusion

- Specific accessibility requirements? For example: WCAG level or known user needs.
- Considerations for reduced motion, color blindness, or other accommodations?

Skip questions where the answer is already clear from the codebase exploration.

## Step 3: Write Design Context

Synthesize your findings and the user's answers into a `## Design Context` section using this structure:

```md
## Design Context

### Users
[Who they are, their context, the job to be done]

### Brand Personality
[Voice, tone, 3-word personality, emotional goals]

### Aesthetic Direction
[Visual tone, references, anti-references, theme]

### Design Principles
[3-5 principles derived from the conversation that should guide all design decisions]
```

Write this section to `CLAUDE.md` in the project root. If the file exists, append or update the `Design Context` section.

Confirm completion and summarize the key design principles that will now guide all future work.
