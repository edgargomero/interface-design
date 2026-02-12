# Design System - Precision & Density

Example system for dashboard/admin interfaces

## Direction

**Personality:** Precision & Density
**Foundation:** Cool (slate)
**Depth:** Borders-only

## Tokens

### Spacing
Base: 4px
Scale: 4, 8, 12, 16, 24, 32

### Colors
```
--foreground: slate-900
--secondary: slate-600
--muted: slate-400
--faint: slate-200
--border: rgba(0, 0, 0, 0.08)
--accent: blue-600
```

### Radius
Scale: 4px, 6px, 8px (sharp, technical)

### Typography
Font: system-ui (fast, native)
Scale: 11, 12, 13, 14 (base), 16, 18
Weights: 400, 500, 600
Mono: SF Mono, Consolas (for data)

## Atoms

### Button
- Height: 32px (compact)
- Padding: 8px 12px
- Radius: 4px
- Font: 13px, 500 weight
- Border: 1px solid
- States: default, hover (bg shift), active (darker), focus (ring), disabled (muted)
- Variants: primary (accent), secondary (border), ghost, destructive

### Input
- Height: 32px (compact)
- Padding: 6px 10px
- Radius: 4px
- Border: 1px solid (faint)
- Font: 13px
- States: default, hover, focus (accent border), error, disabled
- Background: inset (darker than surface)

### Badge
- Padding: 2px 6px
- Radius: 3px
- Font: 11px, 500 weight, tabular-nums
- Variants: neutral (slate), info (blue), success (green), warning (amber), error (red)

### Checkbox
- Size: 16px
- Radius: 3px
- Border: 1px solid
- Checked: accent bg, white check

### Tag
- Padding: 2px 8px
- Radius: 4px
- Font: 12px, 500 weight
- Removable: X icon, 12px

### Label
- Font: 12px, 500 weight, uppercase optional
- Color: muted
- Letter-spacing: 0.5px when uppercase

### Divider
- Height: 1px
- Color: border token

## Molecules

### FormField
- Composes: Label + Input + ErrorText
- Gap: 4px between label and input
- Error: destructive color, 12px, 4px below input

### TableCell
- Composes: Text | Badge | Button (contextual)
- Padding: 8px 12px
- Font: 13px tabular-nums
- Border-bottom: 1px solid (faint)

### StatDisplay
- Composes: Label + Value + DeltaBadge
- Value: 20px, 600 weight, tabular-nums, mono
- Label: 12px, muted, uppercase
- Delta: badge variant based on positive/negative

### NavItem
- Composes: Icon (16px) + Text (13px) + Badge (optional)
- Padding: 6px 12px
- Radius: 4px
- Active: accent bg at 8% opacity, accent text

### SearchBar
- Composes: Input (icon-left, 16px icon) + kbd hint (optional)
- Width: 240px default
- Shortcut indicator: muted, right-aligned

## Organisms

### Sidebar
- Composes: Logo + NavItem[] + Divider + NavItem[] (footer)
- Width: 240px (narrow for density)
- Background: same as canvas
- Border-right: 1px solid (faint)
- Padding: 12px 8px

### DataTable
- Composes: TableHeader + TableCell[][] + Pagination
- Header: sticky, 12px uppercase muted, sort indicators
- Rows: alternating bg optional, hover state
- Pagination: right-aligned, compact buttons

### FilterBar
- Composes: SearchBar + Tag[] + Button (clear)
- Layout: horizontal, gap 8px, wrapping

### PageHeader
- Composes: Breadcrumbs + Title + Button[] (actions)
- Title: 16px, 600 weight
- Actions: gap 6px

## Templates

### DashboardTemplate
- Composes: Sidebar + PageHeader + StatDisplay[] (grid) + DataTable
- Sidebar: fixed left, 240px
- Stat grid: auto-fit, min 200px
- Table: full width below stats
- Gap: 16px between sections

### ListTemplate
- Composes: Sidebar + PageHeader + FilterBar + DataTable
- Filter: sticky below header
- Table: flex-1, scrollable

## Decisions

| Decision | Rationale | Date |
|----------|-----------|------|
| Borders-only | Information density matters more than lift | 2026-01-15 |
| Compact sizing (32px) | Power users, high information density | 2026-01-15 |
| System fonts | Performance, native feel | 2026-01-15 |
| 240px sidebar | Narrow — content is primary, nav is secondary | 2026-01-15 |
