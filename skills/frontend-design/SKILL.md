---
name: frontend-design
version: v2.0
description: >
  Create distinctive, production-grade frontend interfaces with high design quality.
  Use this skill when the user asks to build web components, pages, artifacts, posters,
  or applications — including websites, landing pages, dashboards, React components,
  HTML/CSS layouts, or when styling and beautifying any web UI.
  Generates creative, polished code that avoids generic AI aesthetics.
tags: [react, html, css, ui, components, design, landing-page, dashboard]
category: Design
author: Marketplace
license: MIT
---

# Frontend Design Skill

This skill guides the creation of distinctive, production-grade frontend interfaces
that avoid generic "AI slop" aesthetics. It produces real, working code with exceptional
attention to visual detail and creative decision-making.

The user provides frontend requirements: a component, page, application, or interface
to build. They may include context about the purpose, audience, or technical constraints.

---

## 1. Design Thinking — Do This First

Before writing a single line of code, understand the context and commit to a **bold
aesthetic direction**:

| Question | What to resolve |
|---|---|
| **Purpose** | What problem does this UI solve? Who uses it daily? |
| **Tone** | Pick one extreme and own it — brutally minimal, maximalist, retro-futuristic, organic, luxury, playful, editorial, brutalist, art-deco, soft pastel, industrial… |
| **Constraints** | Framework (React / Vue / plain HTML), performance budget, accessibility requirements |
| **Differentiation** | What is the *one* thing a user will remember about this interface? |

> **CRITICAL:** Choose a clear conceptual direction and execute it with precision.
> Bold maximalism and refined minimalism both work — the key is **intentionality**, not intensity.

---

## 2. Implementation Standards

Produce working code (HTML/CSS/JS, React, Vue, etc.) that is:

- ✅ **Production-grade and fully functional** — no placeholder logic
- ✅ **Visually striking and memorable** — not forgettable
- ✅ **Cohesive** — one clear aesthetic point-of-view throughout
- ✅ **Meticulously refined** — spacing, alignment, and rhythm feel considered

---

## 3. Aesthetic Guidelines

### Typography
- Choose **beautiful, unexpected** fonts. Avoid Arial, Roboto, Inter, system-ui.
- Pair a **distinctive display font** (headings) with a **refined body font** (copy).
- Use font weight, tracking, and line-height as design tools, not defaults.

### Colour & Theme
- Commit to a **cohesive palette** driven by CSS variables.
- Use **dominant colours with sharp accents** — avoid timid, equally-weighted palettes.
- Dark themes, light themes, or duotone — vary per project; never default to the same.

### Motion & Interaction
- Prioritise **CSS-only animations** for HTML artifacts; use the Motion library for React.
- Focus on **high-impact moments**: a well-orchestrated page load with staggered reveals
  creates more delight than scattered micro-interactions.
- Hover states should **surprise** — not just opacity changes.

### Spatial Composition
- Prefer **unexpected layouts**: asymmetry, overlapping elements, diagonal flow, grid-breaking.
- Use **generous negative space** OR **controlled density** — never accidental clutter.

### Backgrounds & Visual Atmosphere
- Avoid flat solid backgrounds. Add **depth**: gradient meshes, noise textures, geometric
  patterns, layered transparencies, dramatic shadows, grain overlays.
- Every surface should feel *crafted*, not default.

---

## 4. Hard Rules

| ❌ Never do this | ✅ Do this instead |
|---|---|
| Use Inter, Roboto, Arial, or system fonts | Pick a characterful display + body font pairing |
| Purple gradient on white background | Commit to a specific, unusual colour story |
| Predictable card/list/navbar layout | Break the grid intentionally |
| Generic hover: `opacity: 0.8` | Design the hover as part of the experience |
| Repeat the same aesthetic across projects | Every output should feel unique to its context |

---

## 5. Output Format

- **Single file** unless the user explicitly requests separate CSS/JS files.
- HTML artifacts: everything in one `.html` file.
- React artifacts: one `.jsx` file with Tailwind utility classes (core only — no compiler needed).
- Always include a **brief comment header** describing the component and its aesthetic direction.

---

## 6. Example Trigger Phrases

Use this skill when the user says things like:

- *"Build me a landing page for…"*
- *"Create a dashboard that shows…"*
- *"Design a React component for…"*
- *"Make a beautiful UI for…"*
- *"Style this page / make it look better"*
- *"Generate an HTML artifact with…"*

---

## 7. Quality Checklist (self-review before output)

- [ ] Does the font pairing feel intentional and distinctive?
- [ ] Is there a clear visual hierarchy — headline → sub → body → action?
- [ ] Are interactive states (hover, focus, active) all designed?
- [ ] Does the layout have rhythm? Is whitespace deliberate?
- [ ] Would someone screenshot this and share it?
