---
name: kntor-design-atomic:audit
description: Check existing code against your design system for spacing, depth, color, pattern, and atomic composition violations.
---

# kntor-design-atomic audit

Check existing code against your design system.

## Usage

```
/audit <path>     # Audit specific file/directory
/audit            # Audit common UI paths
```

## What to Check

**If `.kntor-design-atomic/system.md` exists:**

1. **Spacing violations**
   - Find spacing values not on defined grid
   - Example: 17px when base is 4px

2. **Depth violations**
   - Borders-only system → flag shadows
   - Subtle system → flag layered shadows
   - Allow ring shadows (0 0 0 1px)

3. **Color violations**
   - If palette defined → flag colors not in palette
   - Allow semantic grays

4. **Pattern drift**
   - Find buttons not matching Button atom spec
   - Find cards not matching Card molecule/organism spec

5. **Atomic composition violations**
   - **Token leak:** Hardcoded values (hex colors, pixel values) instead of token references
   - **Atom skip:** An organism styling button-like elements inline instead of using the Button atom
   - **God molecule:** A molecule with 5+ child elements or multiple distinct responsibilities (should be an organism)
   - **Fat atom:** An atom that arranges other atoms internally (should be a molecule)
   - **Phantom template:** Page-level layout logic mixed into data/state logic (extract the template)
   - **Level confusion:** Components classified at wrong atomic level

**Report format:**
```
Audit Results: src/components/

Token Violations:
  Button.tsx:12 - Height 38px (atom spec: 36px)
  Card.tsx:8 - Shadow used (system: borders-only)
  Input.tsx:20 - Spacing 14px (grid: 4px, nearest: 12px or 16px)

Atomic Violations:
  UserCard.tsx - God molecule: contains avatar, name, email, role, 3 actions, edit form (split into organism)
  Dashboard.tsx:45 - Token leak: hardcoded #3b82f6 (use --accent token)
  Header.tsx - Atom skip: inline button styles at line 23, 47 (use Button atom)

Suggestions:
  - Update Button height to match atom spec
  - Replace shadow with border
  - Split UserCard into organism with UserChip molecule + action atoms
  - Extract Dashboard inline color to token
  - Refactor Header to compose Button atoms
```

**If no system.md:**

```
No design system to audit against.

Create a system first:
1. Build UI → establish system automatically
2. Run /kntor-design-atomic:extract → create system from existing code
```

## Implementation

1. Check for system.md
2. Parse system rules (tokens, atoms, molecules, organisms, templates)
3. Read target files (tsx, jsx, css, scss)
4. Compare against token rules
5. Compare against atomic level specs
6. Check composition hierarchy (are molecules made of atoms? organisms of molecules?)
7. Report violations with suggestions organized by category
