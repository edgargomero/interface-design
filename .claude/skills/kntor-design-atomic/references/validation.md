# Memory Management

When and how to update `.kntor-design-atomic/system.md`.

## When to Add Patterns

Add to system.md when:
- Component used 2+ times
- Pattern is reusable across the project
- Has specific measurements worth remembering

Always classify by atomic level when saving.

## Pattern Format by Level

```markdown
## Atoms

### Button
- Height: 36px
- Padding: 12px 16px
- Radius: 6px
- Font: 14px, 500 weight
- States: default, hover, active, focus, disabled
- Variants: primary, secondary, ghost

### Input
- Height: 40px
- Padding: 8px 12px
- Radius: 6px
- Border: 1px solid (faint)
- States: default, hover, focus, error, disabled

## Molecules

### FormField
- Composes: Label + Input + ErrorText
- Gap: 6px between label and input
- Error: 4px below input, destructive color

### NavItem
- Composes: Icon + Text + Badge (optional)
- Padding: 8px 12px
- Active: accent bg at low opacity

## Organisms

### Sidebar
- Composes: Logo + NavItem[] + Divider + UserChip
- Width: 280px
- Border-right: 1px solid (faint)

## Templates

### DashboardTemplate
- Composes: Sidebar + PageHeader + ContentGrid
- Sidebar: fixed left
- Content: flex-1
```

## Don't Document

- One-off components
- Temporary experiments
- Variations better handled with props
- Pages (they are instances, not patterns)

## Pattern Reuse

Before creating a component, check system.md:
- Atom exists? Use it.
- Molecule exists? Use it.
- Need variation? Add a variant to the existing atom/molecule, don't create new.
- Building a new organism? Check that its constituent molecules and atoms already exist. If not, create them first.

Memory compounds: each pattern saved makes future work faster and more consistent. The atomic hierarchy amplifies this — a single atom improvement propagates through every molecule, organism, and template that uses it.

---

# Validation Checks

If system.md defines specific values, check consistency:

**Tokens** — All spacing values multiples of the defined base? All colors from the defined palette? All radii from the defined scale?

**Atoms** — Using documented atom specs? Button heights, input sizes, badge styles matching?

**Molecules** — Composed from documented atoms? Not reinventing atoms inline?

**Organisms** — Composed from documented molecules + atoms? Not creating molecule-level groupings inside organisms?

**Templates** — Using documented organisms? Not mixing layout logic with content logic?

**Composition chain** — Can you trace any visible element from page → template → organism → molecule → atom → token without gaps?
