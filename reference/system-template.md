# Design System

## Direction

**Personality:** [Precision & Density | Warmth & Approachability | Sophistication & Trust | Boldness & Clarity | Utility & Function | Data & Analysis]

**Foundation:** [warm | cool | neutral | tinted]

**Depth:** [borders-only | subtle-shadows | layered-shadows]

## Tokens

### Spacing
Base: [4px | 8px]
Scale: [4, 8, 12, 16, 24, 32, 64]

### Colors
```
--foreground: [slate-900]
--secondary: [slate-600]
--muted: [slate-400]
--faint: [slate-200]
--accent: [blue-600]
```

### Radius
Scale: [4px, 6px, 8px] (sharp) | [8px, 12px, 16px] (soft)

### Typography
Font: [system | Inter | Geist]
Scale: 12, 13, 14 (base), 16, 18, 24, 32
Weights: 400, 500, 600

## Atoms

### Button
- Height: 36px
- Padding: 12px 16px
- Radius: 6px
- Font: 14px, 500 weight
- States: default, hover, active, focus, disabled
- Variants: primary (accent bg), secondary (border), ghost (no border)

### Input
- Height: 40px
- Padding: 8px 12px
- Radius: 6px
- Border: 1px solid (faint)
- States: default, hover, focus, error, disabled
- Background: slightly darker than surface (inset)

### Badge
- Padding: 2px 8px
- Radius: 4px
- Font: 12px, 500 weight
- Variants: neutral, success, warning, error

### Avatar
- Sizes: 24px (xs), 32px (sm), 40px (md)
- Radius: 50%
- Fallback: initials on accent bg

### Label
- Font: 13px, 500 weight
- Color: secondary

### Divider
- Height: 1px
- Color: faint border

## Molecules

### FormField
- Composes: Label + Input + ErrorMessage
- Gap: 6px between label and input
- Error: 4px below input, destructive color, 13px

### SearchBar
- Composes: Input (with icon) + Button
- Input: flex-1, icon-left
- Button: ghost variant, right-aligned

### StatDisplay
- Composes: Label + Value + TrendBadge
- Value: 24px, 600 weight, tabular-nums
- Label: 13px, muted
- Trend: badge below value

### NavItem
- Composes: Icon + Text + Badge (optional)
- Padding: 8px 12px
- States: default, hover, active (accent bg at low opacity)
- Active indicator: left border or background shift

## Organisms

### Sidebar
- Composes: Logo + NavItem[] + Divider + UserChip
- Width: [280px]
- Background: same as canvas
- Border-right: 1px solid (faint)
- Padding: 16px 12px

### DataTable
- Composes: TableHeader + TableRow[] + Pagination
- Header: 13px, 500 weight, muted, sticky
- Rows: 14px, border-bottom faint
- Cell padding: 8px 12px

### FormSection
- Composes: Heading + FormField[] + Button
- Gap: 24px between fields
- Button: aligned right or full-width

### PageHeader
- Composes: Breadcrumbs + Title + Actions (Button[])
- Title: 18px, 600 weight
- Actions: gap 8px between buttons

## Templates

### DashboardTemplate
- Composes: Sidebar + PageHeader + ContentGrid
- Sidebar: fixed left
- Content: flex-1, max-width optional
- Grid: responsive columns for stat cards and tables

### SettingsTemplate
- Composes: Sidebar + PageHeader + FormSection[]
- Content: max-width 640px, centered
- Sections: stacked with 32px gap

### DetailTemplate
- Composes: Sidebar + PageHeader + TabbedContent
- Tabs: border-bottom navigation
- Content: adapts per tab

## Decisions

| Decision | Rationale | Date |
|----------|-----------|------|
| Borders-only depth | Dashboard tool, users want density. Shadows add visual weight without information value. | YYYY-MM-DD |
| 4px spacing base | Tight enough for data tables, divisible by common UI sizes | YYYY-MM-DD |
