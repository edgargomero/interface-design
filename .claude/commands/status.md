---
name: kntor-design-atomic:status
description: Show current design system state including direction, tokens, and atomic hierarchy.
---

# kntor-design-atomic status

Show current design system state.

## What to Show

**If `.kntor-design-atomic/system.md` exists:**

Display:
```
Design System: [Project Name]

Direction: [Precision & Density / Warmth / etc]
Foundation: [Cool slate / Warm stone / etc]
Depth: [Borders-only / Subtle shadows / Layered]

Tokens:
- Spacing base: 4px
- Radius scale: 4px, 6px, 8px
- Colors: [count] defined

Atoms: [count]
- Button (36px h, 6px radius, 4 variants)
- Input (40px h, 6px radius)
- Badge, Label, Divider, ...

Molecules: [count]
- FormField (Label + Input + Error)
- NavItem (Icon + Text + Badge)
- StatDisplay (Value + Label + Trend)
- ...

Organisms: [count]
- Sidebar (Logo + NavItem[] + UserChip)
- DataTable (Header + Rows + Pagination)
- ...

Templates: [count]
- DashboardTemplate (Sidebar + Header + ContentGrid)
- SettingsTemplate (Sidebar + FormSection[])
- ...

Last updated: [from git or file mtime]
```

**If no system.md:**

```
No design system found.

Options:
1. Build UI → system will be established automatically (atoms → molecules → organisms → templates)
2. Run /kntor-design-atomic:extract → pull patterns from existing code, classified by atomic level
```

## Implementation

1. Read `.kntor-design-atomic/system.md`
2. Parse direction, tokens, atoms, molecules, organisms, templates
3. Format and display with composition chain visible
4. If no system, suggest next steps
