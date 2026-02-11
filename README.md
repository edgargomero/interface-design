# kntor-design-atomic

<p align="center">
  <strong>Craft &middot; Atomic Design &middot; Memory &middot; Consistency</strong>
</p>

<p align="center">
  Build interfaces with purist Atomic Design. Tokens &rarr; Atoms &rarr; Molecules &rarr; Organisms &rarr; Templates &rarr; Pages.
</p>

<p align="center">
  <em>For interface design &mdash; dashboards, apps, tools, admin panels. Not for marketing sites.</em>
</p>

---

## Acknowledgments

This project is a fork of [**interface-design**](https://github.com/Dammyjay93/interface-design) by [Damola Akinleye](https://github.com/Dammyjay93). The original project provides an excellent foundation for building interfaces with craft, memory, and consistency inside Claude Code.

**kntor-design-atomic** extends the original by adapting the entire system to work with **purist Atomic Design methodology** (Brad Frost). All principles, commands, templates, and examples have been restructured around the five atomic levels: Tokens, Atoms, Molecules, Organisms, Templates, and Pages.

Thank you Damola for the craft philosophy and the foundation that made this possible.

---

## What This Does

When you build UI with Claude, design decisions get made: spacing values, colors, depth strategy, surface elevation, component structure. Without structure, those decisions drift across sessions and components become monoliths.

**kntor-design-atomic helps you:**

1. **Craft** &mdash; Principle-based design that produces professional, polished interfaces
2. **Atomic Structure** &mdash; Every component classified by level: atom, molecule, organism, template, page
3. **Memory** &mdash; Save decisions to `.kntor-design-atomic/system.md`, load automatically
4. **Consistency** &mdash; Composition flows strictly through the atomic hierarchy

## Before & After

**Without atomic design:**
- Components grow into monoliths with mixed concerns
- Button styles duplicated across 12 files
- Page components contain layout, data, and styling all in one
- No reusability, no consistency

**With kntor-design-atomic:**
- Every component has a clear level (atom, molecule, organism, template, page)
- Button atom defined once, used everywhere
- Templates handle layout, organisms handle sections, molecules handle small groups
- Change an atom and every molecule, organism, and template that uses it updates

---

## Installation

### Manual

```bash
git clone https://github.com/kntor/kntor-design-atomic.git
cd kntor-design-atomic
cp -r .claude/* ~/.claude/
cp -r .claude-plugin/* ~/.claude-plugin/
```

Restart Claude Code.

---

## How It Works

### The Atomic Hierarchy

```
Tokens      Design variables (colors, spacing, typography, shadows)
   |
Atoms       Indivisible elements (Button, Input, Badge, Avatar, Label)
   |
Molecules   Small atom groups, 1 job (FormField, SearchBar, NavItem)
   |
Organisms   Self-contained sections (Sidebar, DataTable, PageHeader)
   |
Templates   Page skeletons (DashboardTemplate, SettingsTemplate)
   |
Pages       Concrete instances with real data (TeamDashboard)
```

### The Flow

**If system.md exists:**
```
1. Reads skill files and principles
2. Loads .kntor-design-atomic/system.md
3. Applies established atoms, molecules, organisms, templates
4. States level + composition before each component
5. Builds bottom-up
6. Offers to save new patterns
```

**If no system.md:**
```
1. Reads skill files and principles
2. Explores product domain
3. Suggests direction + atomic inventory
4. Gets confirmation
5. Builds bottom-up: tokens -> atoms -> molecules -> organisms -> templates -> pages
6. Offers to save system
```

### Example: First Session

```
You: "Build a user dashboard with metrics cards"

Claude:
Domain: operations monitoring, team productivity, delivery velocity
Color world: slate, steel, signal green, amber warning
Signature: velocity sparklines embedded in metric atoms

Direction: Precision & Density, borders-only, cool slate

Atomic inventory:
  Atoms: Button, Badge, Avatar, Label, Divider, Icon
  Molecules: StatDisplay, NavItem, UserChip, SearchBar
  Organisms: Sidebar, MetricsGrid, PageHeader
  Template: DashboardTemplate

Does that direction feel right?

[You: y]

[Builds tokens, then atoms, then molecules, then organisms, then template, then page]

Want me to save these patterns to .kntor-design-atomic/system.md?
```

---

## System File

After establishing direction, decisions live in `.kntor-design-atomic/system.md`:

```markdown
# Design System

## Direction
Personality: Precision & Density
Foundation: Cool (slate)
Depth: Borders-only

## Tokens
### Spacing
Base: 4px
Scale: 4, 8, 12, 16, 24, 32

### Colors
--foreground: slate-900
--accent: blue-600

## Atoms
### Button
- Height: 32px
- Padding: 8px 12px
- States: default, hover, active, focus, disabled
- Variants: primary, secondary, ghost

## Molecules
### NavItem
- Composes: Icon + Text + Badge
- Padding: 6px 12px

## Organisms
### Sidebar
- Composes: Logo + NavItem[] + Divider + UserChip
- Width: 240px

## Templates
### DashboardTemplate
- Composes: Sidebar + PageHeader + ContentGrid
```

---

## Commands

```bash
/kntor-design-atomic:init           # Start building with Atomic Design
/kntor-design-atomic:status         # Show current system (tokens, atoms, molecules, organisms, templates)
/kntor-design-atomic:audit <path>   # Check code against system + atomic composition violations
/kntor-design-atomic:extract        # Extract patterns from existing code, classified by atomic level
/kntor-design-atomic:critique       # Critique build for craft + atomic structure, rebuild what defaulted
```

---

## Design Directions

The skill infers direction from project context, but you can customize:

| Direction | Feel | Best For |
|-----------|------|----------|
| **Precision & Density** | Tight, technical, monochrome | Developer tools, admin dashboards |
| **Warmth & Approachability** | Generous spacing, soft shadows | Collaborative tools, consumer apps |
| **Sophistication & Trust** | Cool tones, layered depth | Finance, enterprise B2B |
| **Boldness & Clarity** | High contrast, dramatic space | Modern dashboards, data-heavy apps |
| **Utility & Function** | Muted, functional density | GitHub-style tools |
| **Data & Analysis** | Chart-optimized, numbers-first | Analytics, BI tools |

---

## Examples

For system file templates, see `reference/examples/`:
- **[system-precision.md](reference/examples/system-precision.md)** &mdash; Dashboard/admin with full atomic hierarchy
- **[system-warmth.md](reference/examples/system-warmth.md)** &mdash; Collaborative/consumer with full atomic hierarchy

---

## Philosophy

**Atomic Design is structural law.** Tokens flow into atoms, atoms compose into molecules, molecules assemble into organisms, organisms fill templates, templates become pages. No level is skipped. No component lives outside the hierarchy.

**Decisions compound.** A spacing token chosen once shapes every atom. An atom defined once appears in every molecule. Consistency isn't a goal &mdash; it's a structural consequence.

**Build bottom-up, always.** Never start from the page and work backward. That's how monolith components are born. Define tokens, build atoms, compose upward.

**Memory enables iteration.** When you can see what you decided and why, organized by atomic level, you can evolve intentionally instead of drifting accidentally.

---

## Based On

This project builds upon [interface-design](https://github.com/Dammyjay93/interface-design) by [Damola Akinleye](https://github.com/Dammyjay93), licensed under MIT. The original craft philosophy &mdash; intent-first design, subtle layering, the mandate, the checks &mdash; remains the foundation of this project. The Atomic Design adaptation adds structural methodology to that craft.

## License

MIT &mdash; See [LICENSE](LICENSE)
