---
name: figma-best-practices
description: Apply Figma's official editorial and structural best practices (file/page organization, component naming, variants, branching, auto-layout, variables/tokens, dev handoff) when building or editing Figma files. Trigger automatically alongside `figma-use`, `figma-generate-design`, and `figma-generate-library` whenever the user is about to create, edit, restructure, or hand off a Figma file, component, library, or design system — even if they don't explicitly mention "best practices." Especially trigger when the user mentions creating frames, components, variants, libraries, tokens, variables, pages, auto-layout, or preparing files for dev handoff. This skill complements (does not replace) the operational `figma:*` skills — they cover HOW to call the MCP, this one covers HOW TO STRUCTURE the work well.
version: 1.0.0
---

# figma-best-practices

Editorial and structural guidance for Figma work, distilled from figma.com/best-practices and Figma's official help docs. Use alongside the operational `figma:*` skills:

- `figma-use` — how to call the MCP (mechanics)
- `figma-generate-design` — how to assemble a screen from code/spec (workflow)
- `figma-generate-library` — how to build a design system (workflow)
- **this skill** — how to structure the work so the result is maintainable, scalable, and dev-ready (editorial)

When in doubt, prefer Figma's official conventions over personal preference — they're what most engineering teams and other designers expect.

## How to apply this skill

This skill should run quietly in the background. When the user is creating or modifying Figma content, check the sections below relevant to what they're doing and apply the guidance. Don't lecture — just produce work that already follows the conventions. If a user explicitly violates a convention, mention it once with a brief reason, then defer to their call.

---

## 1. File, project, and page organization

**Pages: one purpose per page.** Common structure for a product/feature file:

- `📋 Cover` — title, owner, status, last updated, link to ticket/doc
- `🗂 Resources` — research, references, links to related files
- `🚧 WIP / Exploration` — work in progress, sketches, alternative directions
- `✅ Ready for Review` — designs awaiting feedback
- `🚀 Final / Handoff` — locked designs going to dev
- `📦 Components` — local components used only in this file
- `🗑 Archive` — older versions kept for reference

Emojis at the start of page names make scanning faster and create a visual sort order. Pick a convention and stick with it across files.

**Files should have a single clear owner.** Multiple owners = no owner. Put the owner's name on the cover page.

**Don't dump everything in one file.** Split when:
- A single file has more than ~10 pages of active work
- Multiple features are being designed in parallel
- Different audiences need different access (e.g., research separate from production designs)

**Project naming.** Use a consistent pattern across the team — e.g., `[Squad] Project Name` or `[Product Area] Feature` — so projects sort predictably in the sidebar.

---

## 2. Components and variants

### When to use a variant vs. a separate component

**Use variants when** properties map cleanly to frontend props: state (default/hover/disabled), size (sm/md/lg), type (primary/secondary), boolean toggles (icon on/off).

**Use separate components (or nested instances) when:**
- The number of permutations would explode (e.g., every icon × every size × every color = unmanageable)
- The variations are conceptually different things (a card and a list item shouldn't be variants of one component)
- Color/theme variation — handle with variables/modes, not variants

**Rule of thumb:** if you can describe it as a React/Vue prop, it's probably a variant. If you'd build it as a different component in code, build it as a different component in Figma.

### Variant property naming

- Use **clear, semantic property names**: `state`, `size`, `type`, `hasIcon` — not `option1`, `variant2`
- Values use the same casing your engineers use (usually camelCase or kebab-case)
- For booleans, use `true/false` or `on/off` consistently
- Forward slashes in layer names auto-convert to property values: `Button/Primary/Large` becomes three properties

### Component documentation

Always add a **description** to component sets and individual variants — these show up in the inspect panel and are the closest thing to inline docs for engineers. Include: what the component is for, when to use it, when not to use it, link to the corresponding code component if Code Connect isn't wired up.

### Organization

- One component family per page (`Buttons`, `Inputs`, `Cards`) when the library is large
- Combine pages with only one component set into logical groupings (`Form elements`, `Navigation`)
- Order variants left-to-right / top-to-bottom in the order a developer would think about them (default first, then state progression)

---

## 3. Auto-layout

**Default to auto-layout.** Almost everything in a UI should be inside auto-layout — buttons, cards, lists, page layouts. Fixed-position absolute layouts are the exception, not the rule.

### Resizing modes

Get these right and the design behaves like the real product:
- **Hug contents** — frame shrinks to fit content (use for buttons, badges, chips)
- **Fill container** — child fills available parent space (use for inputs in a form, columns in a row)
- **Fixed** — locked dimension (use sparingly, usually for icons or fixed-width sidebars)

### Nesting

Stack horizontal auto-layout inside vertical auto-layout (or vice versa) to build multi-direction responsive layouts. Each level keeps its own padding and gap. This is how you get a real responsive layout, not a static mockup.

### Common patterns

- **Cards:** vertical auto-layout, hug height, fill width (or fixed width if grid item)
- **Form fields:** vertical stack (label / input / helper text), all fill-width
- **Button rows:** horizontal auto-layout, gap matching design system spacing token
- **Icon + text:** horizontal auto-layout, gap = small spacing token, icon hugs, text hugs or fills

### Pitfalls

- Avoid fixed-size text boxes — they break the moment copy changes or gets translated
- Don't ignore auto-layout to "just nudge it" — fix the layout properly or it'll break for the next person
- Components should have auto-layout applied to the main; instances inherit it

---

## 4. Variables and tokens

Variables are how design tokens live in Figma. Always prefer variables over hardcoded values.

### Collection structure

Typical setup for a design system:
- **Primitives** — raw values: `color/blue/500`, `space/4`, `radius/sm`. These are not used directly in designs.
- **Semantic / aliases** — meaningful tokens that reference primitives: `color/surface/default`, `color/text/primary`, `space/component/inline-md`. These ARE used in designs.
- **Component-level** (optional) — component-specific tokens that alias semantic ones, e.g., `button/background/primary`.

Designs should bind to semantic tokens, not primitives. That's what lets you theme or rebrand without touching every layer.

### Naming

- Use forward slashes for hierarchy: `color/text/primary`, `space/4`
- Lowercase, kebab-case for multi-word names
- Be specific about purpose: `color/border/subtle` beats `color/gray-200`
- Match your engineering team's token naming if they have one — alignment beats elegance

### Modes

Use modes for **contexts that swap together**: light/dark, brand A / brand B, density compact/comfortable. Don't use modes for component variants (that's what variants are for).

When defining a token, set a value for every mode. Missing values silently fall back and cause bugs.

### Aliasing

Always alias semantic tokens to primitives (or to other semantic tokens) rather than re-typing raw values. This is what lets a single primitive change propagate everywhere.

### Variables vs. styles

- **Variables** — single values (color, number, string, boolean). Support modes and aliasing. Prefer for tokens.
- **Styles** — compound properties (effects, complex fills, typography combinations). Use for things variables can't express yet.

For new design systems, lead with variables and use styles only where necessary.

---

## 5. Branching

**Branch when:**
- Proposing changes to a published library
- Sharing in-progress feature work for review without polluting main
- Running design experiments or A/B explorations
- Freezing a version for dev handoff while continuing iteration on main

**Don't branch when:**
- It's a ground-up redesign (start a new file instead)
- It's a tiny solo edit on main
- You're exploring multiple concurrent concepts (use pages on the main file)

### Naming

Use a prefix scheme aligned with the dev team's git conventions. Examples:
- `PWM-946: Store locator desktop layout`
- `🔥 Fix payment info spacing`
- `[proposal] New input states`

### Workflow

- Fill in the branch description like a PR description — what changed, why, what to review
- Tag stakeholders in comments for iterative feedback
- Archive or delete merged/abandoned branches; stale branches confuse everyone
- Libraries can only be published from main, not from branches — plan accordingly

---

## 6. Developer handoff

The goal of handoff isn't a beautiful file — it's a file engineers can build from without 20 follow-up questions.

### Before handoff, check:

- **Styles and variables are named the way engineers will name them in code.** Discuss naming with at least one engineer upfront.
- **Every interactive element has all its states designed** (default, hover, focus, active, disabled, loading, error, empty).
- **Edge cases are shown**: long text, zero state, error state, very long lists, missing data.
- **Responsive behavior is documented** — at least show the breakpoints you're targeting (mobile / tablet / desktop) with explicit frames.
- **Components are actual components** (not detached). Engineers should see "this is the Button component" in inspect.
- **Auto-layout is applied properly** so spacing values are real, not vibes.
- **Annotations call out anything non-obvious**: animations, transitions, accessibility requirements, business rules.
- **Comments are resolved or deleted** — old open comments create noise.

### File structure for handoff

- A dedicated `🚀 Final / Handoff` page with only the production-ready frames
- Frames named the way the feature/screen is named in code or in the ticket (`StoreLocator/Desktop/Default`)
- A single shareable URL for the project — the "source of truth"
- Link the Jira ticket on the cover page (and vice versa)

### Exports

- Mark layers that should be exported (icons, illustrations) with export settings configured
- Prefer SVG for icons and simple illustrations, PNG for raster, at the densities engineers need (1x, 2x, 3x for mobile)

---

## 7. Quick reference — do this / don't do that

**Do:**
- Auto-layout everything by default
- Bind colors and spacing to variables/tokens
- Add descriptions to components and variants
- Use semantic token names (`color/text/primary`), not raw values (`#1A1A1A`)
- One purpose per page, clear page naming
- Match engineering's naming conventions

**Don't:**
- Detach instances unless absolutely necessary (and document why)
- Create variants for every color or icon (use nested instances + variables)
- Leave fixed-size text boxes in production designs
- Ship a file with unresolved comments or open WIP mixed with final
- Branch for tiny solo edits
- Use modes for what should be variants (or vice versa)

---

## Sources

- figma.com/best-practices (creating-and-organizing-variants, branching-in-figma, tips-on-developer-handoff)
- help.figma.com (auto-layout, variables)
- General Figma community consensus where official docs are silent (file organization patterns, token hierarchy)

If a recommendation here ever conflicts with what the user's team explicitly does, the team's convention wins — alignment with engineering and other designers on the team is more valuable than abstract correctness.
