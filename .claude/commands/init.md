---
name: kntor-design-atomic:init
description: Build UI with craft and consistency. For interface design (dashboards, apps, tools) — not marketing sites.
---

## Required Reading — Do This First

Before writing any code, read this file completely:

1. `../skills/kntor-design-atomic/SKILL.md` — the foundation, principles, atomic design law, craft knowledge, and checks

Do not skip this. The craft knowledge and atomic hierarchy are in this file.

---

**Scope:** Dashboards, apps, tools, admin panels. Not landing pages or marketing sites.

## Intent First — Answer Before Building

Before touching code, answer these out loud:

**Who is this human?** Not "users." Where are they? What's on their mind? A teacher at 7am with coffee is not a developer debugging at midnight.

**What must they accomplish?** Not "use the dashboard." The verb. Grade submissions. Find the broken deployment. Approve the payment.

**What should this feel like?** In words that mean something. "Clean" means nothing. Warm like a notebook? Cold like a terminal? Dense like a trading floor?

If you cannot answer these with specifics, stop and ask the user. Do not guess. Do not default.

## Before Writing Each Component

State the atomic level, composition, AND the technical approach:

```
Level: [atom | molecule | organism | template | page]
Composes: [what lower-level pieces this uses]
Intent: [who, what they need to do, how it should feel]
Palette: [foundation + accent — and WHY these colors fit the product's world]
Depth: [borders / subtle shadows / layered — and WHY]
Surfaces: [your elevation scale — and WHY this temperature]
Typography: [your typeface choice — and WHY it fits the intent]
Spacing: [your base unit]
```

Every choice must be explainable. If your answer is "it's common" or "it works" — you haven't chosen. You've defaulted.

**The test:** If another AI given a similar prompt would produce the same output, you have failed. The interface must emerge from THIS user, THIS problem, THIS intent.

## Build Order — Always Bottom-Up

When building a new interface:

1. **Define tokens** — spacing, colors, typography, shadows, radii
2. **Build atoms** — buttons, inputs, labels, badges, avatars, dividers (consuming tokens only)
3. **Compose molecules** — form fields, search bars, stat displays, nav items (from atoms)
4. **Assemble organisms** — sidebars, data tables, form sections, headers (from molecules + atoms)
5. **Define templates** — page layouts that place organisms (structure, not content)
6. **Instantiate pages** — fill templates with real data

Never start from the page and work backward. That creates monolith components.

## Communication

Be invisible. Don't announce modes or narrate process.

**Never say:** "I'm in ESTABLISH MODE", "Let me check system.md...", "Building atoms first..."

**Instead:** Jump into work. State suggestions with reasoning. The atomic structure should be evident in the code, not narrated.

## Suggest + Ask

Lead with your exploration and recommendation, then confirm:
```
"Domain: [concepts from this product's world]
Color world: [colors that exist in this domain]
Signature: [one element unique to this product]

Direction: [approach that connects to the above]

Atomic inventory:
  Atoms: [list the atoms needed]
  Molecules: [list the molecules needed]
  Organisms: [list the organisms needed]
  Template: [the page template]"

[AskUserQuestion: "Does that direction feel right?"]
```

## Flow

1. Read the required files above (always — even if system.md exists)
2. Check if `.kntor-design-atomic/system.md` exists
3. **If exists**: Apply established patterns — atoms, molecules, organisms, templates are already classified
4. **If not**: Assess context, suggest direction + atomic inventory, get confirmation, build bottom-up

The skill files contain the craft principles and atomic hierarchy. system.md contains project-specific decisions. You need both.

## After Every Task

Offer to save when you finish building UI:

"Want me to save these patterns to `.kntor-design-atomic/system.md`?"

Save patterns classified by atomic level — atoms with measurements and states, molecules with composition notes, organisms with their molecule/atom references, templates with organism placement.

Always offer — new patterns should be captured whether system.md exists or not.
