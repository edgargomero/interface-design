# Craft in Action

This shows how the subtle layering principle and atomic hierarchy translate to real decisions. Learn the thinking, not the code. Your values will differ — the approach won't.

---

## The Subtle Layering Mindset

Before looking at any example, internalize this: **you should barely notice the system working.**

When you look at Vercel's dashboard, you don't think "nice borders." You just understand the structure. When you look at Supabase, you don't think "good surface elevation." You just know what's above what. The craft is invisible — that's how you know it's working.

---

## Example: Dashboard with Sidebar and Dropdown

### The Surface Decisions

**Why so subtle?** Each elevation jump should be only a few percentage points of lightness. You can barely see the difference in isolation. But when surfaces stack, the hierarchy emerges. This is the Vercel/Supabase way — whisper-quiet shifts that you feel rather than see.

**What NOT to do:** Don't make dramatic jumps between elevations. That's jarring. Don't use different hues for different levels. Keep the same hue, shift only lightness.

### The Border Decisions

**Why rgba, not solid colors?** Low opacity borders blend with their background. A low-opacity white border on a dark surface is barely there — it defines the edge without demanding attention. Solid hex borders look harsh in comparison.

**The test:** Look at your interface from arm's length. If borders are the first thing you notice, reduce opacity. If you can't find where regions end, increase slightly.

### The Sidebar Decision

**Why same background as canvas, not different?**

Many dashboards make the sidebar a different color. This fragments the visual space — now you have "sidebar world" and "content world."

Better: Same background, subtle border separation. The sidebar is part of the app, not a separate region. Vercel does this. Supabase does this. The border is enough.

### The Dropdown Decision

**Why surface-200, not surface-100?**

The dropdown floats above the card it emerged from. If both were surface-100, the dropdown would blend into the card — you'd lose the sense of layering. Surface-200 is just light enough to feel "above" without being dramatically different.

**Why border-overlay instead of border-default?**

Overlays (dropdowns, popovers) often need slightly more definition because they're floating in space. A touch more border opacity helps them feel contained without being harsh.

---

## Example: Form Controls

### Input Background Decision

**Why darker, not lighter?**

Inputs are "inset" — they receive content, they don't project it. A slightly darker background signals "type here" without needing heavy borders. This is the alternative-background principle.

### Focus State Decision

**Why subtle focus states?**

Focus needs to be visible, but you don't need a glowing ring or dramatic color. A noticeable increase in border opacity is enough for a clear state change. Subtle-but-noticeable — the same principle as surfaces.

---

## Example: Atomic Composition in Practice

### How a Dashboard Page Decomposes

A well-structured dashboard page traces cleanly through every atomic level:

```
Page: TeamDashboard
  └─ Template: DashboardTemplate
       ├─ Organism: Sidebar
       │    ├─ Atom: Logo
       │    ├─ Molecule: NavItem × 6
       │    │    ├─ Atom: Icon
       │    │    ├─ Atom: Text
       │    │    └─ Atom: Badge (optional)
       │    ├─ Atom: Divider
       │    └─ Molecule: UserChip
       │         ├─ Atom: Avatar
       │         └─ Atom: Text (name)
       ├─ Organism: PageHeader
       │    ├─ Molecule: Breadcrumbs
       │    ├─ Atom: Heading
       │    └─ Atom: Button × 2
       └─ Organism: MetricsGrid
            └─ Molecule: StatCard × 4
                 ├─ Atom: Icon (in circle)
                 ├─ Atom: Text (value)
                 ├─ Atom: Text (label)
                 └─ Atom: Badge (trend)
```

**What this gives you:**

- Change the Button atom once → every button in every organism updates
- Swap NavItem molecule's Badge atom for a different indicator → all nav items change
- Replace DashboardTemplate with a different layout → all organisms still work
- Test the Sidebar organism in isolation → it renders completely on its own

### The Anti-Pattern

What most first drafts look like — a monolith:

```
Page: TeamDashboard
  ├─ <div class="sidebar">  ← inline styles, not an organism
  │    ├─ <nav> with inline link styles  ← not using NavItem molecule
  │    └─ <div> with hardcoded avatar  ← not using Avatar atom
  ├─ <div class="header"> with inline padding  ← not using PageHeader organism
  └─ <div class="grid">
       └─ <div class="card"> × 4 with hardcoded hex colors  ← token leak
```

Same visual result. Completely different structural quality. The monolith works today. The atomic version works forever.

---

## Adapt to Context

Your product might need:
- Warmer hues (slight yellow/orange tint)
- Cooler hues (blue-gray base)
- Different lightness progression
- Light mode (principles invert — higher elevation = shadow, not lightness)

**The principle is constant:** barely different, still distinguishable. Build bottom-up, compose strictly. The values adapt to context.

---

## The Craft Check

Apply the squint test and the atomic test to your work:

1. Blur your eyes or step back
2. Can you still perceive hierarchy?
3. Is anything jumping out at you?
4. Can you tell where regions begin and end?
5. Can you trace any element from page → template → organism → molecule → atom → token?

If hierarchy is visible, nothing is harsh, and the composition chain is clean — the system is working.
