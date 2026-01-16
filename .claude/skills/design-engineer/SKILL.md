---
name: design-engineer
description: This skill should be used when building user interfaces, creating UI components, designing dashboards, or working on frontend visual design. It helps establish and maintain design systems with consistent direction, patterns, and quality standards.
---

# Design Engineer

Help establish and maintain design systems. Ensure consistency across sessions.

## If system.md exists

Use it. The decisions are made.

1. Read `.design-engineer/system.md`
2. Apply the established direction and patterns
3. Consult `references/principles.md` for quality floor
4. If new reusable patterns emerge, offer to add them to system.md

## If no system.md

Help establish one. Your goal: understand what this product needs to feel like, commit to a direction, confirm with user, build, offer to save.

1. **Assess context** — What has the user told you? What does the project look like? What's the conversation history?
2. **Form a hypothesis** — Based on context, what direction fits? Consult `references/directions.md` for the 6 personalities
3. **Propose with reasoning** — State your suggestion and why ("This feels like a dashboard for power users, suggesting Precision & Density with cool slate and borders-only depth")
4. **Get ONE confirmation** — "Does this direction fit? (y/n/customize)"
5. **Build** — Apply the direction. Consult `references/principles.md` for quality standards
6. **Offer to save** — "Save design system to .design-engineer/system.md? (y/n)"

Use the template at `reference/system-template.md` in the plugin root for the system.md format.

## Skip establishment when

User explicitly signals temporary work: "prototype", "quick test", "experiment", "don't save", "one-off"

In this case: apply quality standards from `references/principles.md`, build, don't offer to save.

## Scope

**You decide:**
- Personality (precise, warm, bold, sophisticated, utility, data)
- Color foundation (warm, cool, neutral, tinted)
- Depth strategy (borders-only, subtle shadows, layered)
- Layout density (tight, generous)

**You don't decide:**
- Tech stack (infer from project or user's stated preference)
- Features (user already told you what to build)
- Project structure (not your concern)

## Before finishing

Run self-validation per `references/validation.md`. Fix issues before showing work to user.

## Related Commands

- `/design-engineer:status` — Show current design system state
- `/design-engineer:audit` — Validate existing code against system
- `/design-engineer:extract` — Extract patterns from existing code

---

## Additional Resources

### Reference Files

- **`references/directions.md`** — The 6 design personalities, product type mapping, color foundations, layout approaches, and typography guidance
- **`references/principles.md`** — Core craft quality standards: 4px grid, depth strategies, typography hierarchy, animation, contrast, and dark mode considerations
- **`references/validation.md`** — Pre-delivery checklist, memory management rules, anti-patterns to avoid, and the quality standard

### Examples (in plugin root)

- **`reference/system-template.md`** — Template for creating system.md files
- **`reference/examples/system-precision.md`** — Example: Precision & Density direction
- **`reference/examples/system-warmth.md`** — Example: Warmth & Approachability direction
