# Design System - Warmth & Approachability

Example system for collaborative/consumer apps

## Direction

**Personality:** Warmth & Approachability
**Foundation:** Warm (stone)
**Depth:** Subtle shadows

## Tokens

### Spacing
Base: 4px
Scale: 8, 12, 16, 24, 32, 48 (generous)

### Colors
```
--foreground: stone-900
--secondary: stone-600
--muted: stone-400
--faint: stone-200
--accent: orange-500
--shadow: 0 1px 3px rgba(0, 0, 0, 0.08)
```

### Radius
Scale: 8px, 12px, 16px (soft, friendly)

### Typography
Font: Inter (approachable, readable)
Scale: 13, 14, 15, 16 (base), 18, 20, 24
Weights: 400, 500, 600

## Atoms

### Button
- Height: 40px (comfortable)
- Padding: 12px 20px
- Radius: 8px
- Font: 15px, 500 weight
- Shadow: subtle
- States: default, hover (lift + shadow), active (press), focus (ring), disabled (muted)
- Variants: primary (accent), secondary (border), ghost, destructive

### Input
- Height: 44px
- Padding: 12px 16px
- Radius: 8px
- Border: 1.5px solid (faint)
- Font: 15px
- States: default, hover, focus (accent border + shadow), error, disabled
- Background: white

### Badge
- Padding: 4px 10px
- Radius: 6px
- Font: 13px, 500 weight
- Variants: neutral, success, warning, error

### Avatar
- Sizes: 28px (sm), 36px (md), 48px (lg)
- Radius: 50%
- Border: 2px solid white (stacking)
- Fallback: initials on warm gradient

### Toggle
- Width: 44px, Height: 24px
- Radius: 12px (pill)
- Knob: 20px, white, shadow
- On: accent bg

### Label
- Font: 14px, 500 weight
- Color: foreground (not muted — warm means present)

### Divider
- Height: 1px
- Color: stone-200
- Margin: 24px 0

## Molecules

### FormField
- Composes: Label + Input + HelpText/ErrorText
- Gap: 8px between label and input
- Help: 13px, muted, 4px below input
- Error: destructive color, 13px

### UserChip
- Composes: Avatar (sm) + Name (14px) + Role (13px, muted)
- Layout: horizontal, gap 10px, center-aligned

### StatCard
- Composes: Icon (in circle bg) + Value + Label + TrendBadge
- Value: 24px, 600 weight
- Label: 14px, muted
- Icon: 20px in 36px circle, accent at 10% opacity

### NavItem
- Composes: Icon (20px) + Text (15px) + Badge (optional)
- Padding: 10px 16px
- Radius: 8px
- Active: accent bg at 8% opacity, accent text
- Hover: stone-100 bg

### SearchBar
- Composes: Input (icon-left, 20px icon) + Button (optional)
- Width: 320px default
- Placeholder: muted, friendly tone

## Organisms

### Sidebar
- Composes: Logo + NavItem[] + Divider + NavItem[] (footer) + UserChip
- Width: 280px
- Background: same as canvas
- Border-right: 1px solid (faint)
- Padding: 20px 16px

### CardGrid
- Composes: StatCard[]
- Grid: auto-fit, min 240px, gap 16px
- Cards: shadow, 20px padding, 12px radius

### FormSection
- Composes: Heading (18px, 600) + Description (14px, muted) + FormField[] + Button
- Gap: 20px between fields
- Max-width: 480px

### PageHeader
- Composes: Breadcrumbs + Title + Description + Button[] (actions)
- Title: 20px, 600 weight
- Description: 15px, muted, 4px below title
- Actions: gap 8px

## Templates

### DashboardTemplate
- Composes: Sidebar + PageHeader + CardGrid + ContentArea
- Sidebar: fixed left, 280px
- Content: padding 32px, max-width 1200px
- Gap: 32px between sections (generous, breathable)

### SettingsTemplate
- Composes: Sidebar + PageHeader + FormSection[]
- Content: max-width 560px, centered
- Sections: 48px gap (spacious)

### DetailTemplate
- Composes: Sidebar + PageHeader + TabbedContent
- Tabs: pill-style, 8px radius, gap 4px
- Content: 24px padding within tab panels

## Decisions

| Decision | Rationale | Date |
|----------|-----------|------|
| Subtle shadows | Gentle depth, approachable feel, objects feel touchable | 2026-01-15 |
| Generous spacing | Focused tasks, not cramming info, breathing room | 2026-01-15 |
| Warm foundation | Human, comfortable, inviting — users return by choice | 2026-01-15 |
| 280px sidebar | Generous — nav is a companion, not just a menu | 2026-01-15 |
