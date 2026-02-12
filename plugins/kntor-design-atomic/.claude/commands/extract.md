---
name: kntor-design-atomic:extract
description: Extract design patterns from existing code to create a system.md file organized by atomic levels.
---

# kntor-design-atomic extract

Extract design patterns from existing code to create an atomic design system.

## Usage

```
/extract          # Extract from common UI paths
/extract <path>   # Extract from specific directory
```

## What to Extract

**Scan UI files (tsx, jsx, vue, svelte) for:**

1. **Tokens — Repeated values across components**
   ```
   Spacing: 4px (12x), 8px (23x), 12px (18x), 16px (31x), 24px (8x)
   → Suggests: Base 4px, Scale: 4, 8, 12, 16, 24

   Colors: #1e293b (18x), #64748b (12x), #3b82f6 (8x)
   → Suggests: foreground: slate-900, secondary: slate-500, accent: blue-500

   Radii: 6px (28x), 8px (5x)
   → Suggests: Radius scale: 6px, 8px

   Depth: box-shadow (2x), border (34x)
   → Suggests: Borders-only
   ```

2. **Atoms — Repeated base elements**
   ```
   Buttons found: 8 instances
   - Height: 36px (7/8), 40px (1/8)
   - Padding: 12px 16px (6/8), 16px (2/8)
   - Variants: 3 visual treatments detected
   → Suggests Atom: Button — 36px h, 12px 16px pad, 3 variants

   Inputs found: 5 instances
   - Height: 40px (5/5)
   - Border: 1px solid (4/5), none (1/5)
   → Suggests Atom: Input — 40px h, 1px border
   ```

3. **Molecules — Repeated atom groupings**
   ```
   Label + Input patterns: 5 instances
   → Suggests Molecule: FormField (Label + Input)

   Icon + Text + Badge patterns: 4 instances
   → Suggests Molecule: NavItem (Icon + Text + Badge)

   Number + Label patterns: 6 instances
   → Suggests Molecule: StatDisplay (Value + Label)
   ```

4. **Organisms — Repeated section patterns**
   ```
   Sidebar-like structures: 2 instances
   - Contains: Logo, NavItem[], UserChip
   → Suggests Organism: Sidebar

   Table structures: 3 instances
   - Contains: Header row, data rows, pagination
   → Suggests Organism: DataTable
   ```

5. **Templates — Page-level layout patterns**
   ```
   Sidebar + Header + Content layout: 3 pages
   → Suggests Template: DashboardTemplate
   ```

**Then prompt:**
```
Extracted patterns (organized by atomic level):

Tokens:
  Spacing base: 4px → Scale: 4, 8, 12, 16, 24, 32
  Depth: Borders-only (34 borders, 2 shadows)
  Colors: 5 primitives detected
  Radius: 6px, 8px

Atoms:
  Button: 36px h, 12px 16px pad, 6px radius, 3 variants
  Input: 40px h, 1px border, 6px radius
  Badge: 2px 6px pad, 4px radius
  Label: 13px, 500 weight

Molecules:
  FormField: Label + Input (5 instances)
  NavItem: Icon + Text + Badge (4 instances)
  StatDisplay: Value + Label (6 instances)

Organisms:
  Sidebar: Logo + NavItem[] + UserChip (2 instances)
  DataTable: Header + Rows + Pagination (3 instances)

Templates:
  DashboardTemplate: Sidebar + Header + Content (3 pages)

Create .kntor-design-atomic/system.md with these? (y/n/customize)
```

## Implementation

1. Glob for UI files
2. Parse for repeated values → extract tokens
3. Identify repeated base elements → classify as atoms
4. Find repeated atom groupings → classify as molecules
5. Find repeated section patterns → classify as organisms
6. Find repeated page layouts → classify as templates
7. Present organized by atomic level
8. Offer to create system.md
9. Let user customize before saving
