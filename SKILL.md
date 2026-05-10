---
name: d3-design
description: Personal design philosophy and standards for UI, frontend, and component work. Provides universal principles (spatial depth, motion hierarchy, premium restraint, typography, performance, anti-patterns) that inform any interface, plus an opinionated cinematic floating-glass aesthetic available on-request when the user uses keywords like cinematic, glassmorphism, floating UI, spatial, AI control panel, premium SaaS, VisionOS-inspired, Arc/Linear/Raycast-style, or premium dark interfaces.
---

# d3-design

A two-layer design system. The **universal principles** below apply to every UI you build. The **cinematic floating-glass aesthetic** is opinionated and only applies when the user explicitly asks for that look.

## How to use this skill

**Always apply** the universal principles in this file to any UI, frontend, component, or design work. They are aesthetic-agnostic — they work in light themes, dark themes, brutalist, Material, anything.

**Load `cinematic-aesthetic.md`** when the user asks for any of:

- cinematic, premium, floating, glass, glassmorphism, spatial, atmospheric
- VisionOS / macOS-inspired / Arc / Linear / Raycast / Vercel-style
- AI control panel / dashboard / command palette aesthetic
- "premium dark interface" / "floating glass dashboard" / "luxury enterprise"

**Load `blueprints.md`** when building any of:

- landing page, marketing hero
- dashboard / analytics surface
- AI chat interface
- command palette / spotlight / floating omnibar
- when the user wants a specific UI composition recipe

If the user wants a different aesthetic (Material, brutalist, light editorial, etc.), apply the universal principles only — do not load the cinematic file.

---

## Universal Principles

### Foundation as Material

Never use pure values — no `#000` or `#FFF`. Foundations should feel atmospheric and offset, not absolute. Use a layered, slightly-shifted palette so surfaces feel like material rather than ink on paper.

In dark themes this means near-blacks. In light themes this means off-whites. The principle is the same: avoid the extreme, use offsets, layer your surfaces.

### Controlled Contrast

Three layers of contrast working together:

- low contrast between surfaces
- high contrast typography
- sparse accent highlights

This creates readability, focus, and premium restraint. Avoid uniform contrast — it flattens the interface.

### Spatial Layering

Everything floats. No flat interfaces. Every surface should:

- detach from its background
- cast depth
- react to light
- layer with intent

Use shadow, blur, opacity, and perspective in combination. A single technique alone (just shadow, just blur) reads as cheap.

### Motion Hierarchy

Not every element animates equally. Reserve emphasis for what matters.

- **Hero motion** — oversized, cinematic, sets the tone
- **Active interactions** — tactile, immediate, responsive
- **Focused components** — clear and confident
- **Ambient atmospherics** — nearly invisible, subconscious
- **Background drift** — extremely slow, atmospheric only

If everything moves with the same energy, nothing reads as important.

### Premium Restraint

Premium interfaces avoid excess. Use:

- fewer colors
- fewer accents
- cleaner spacing
- intentional motion
- meaningful highlights

Restraint is the single most reliable signal of quality. When in doubt, remove rather than add.

### Editorial Typography

Sophistication comes from typography choices:

- large, confident headlines
- restrained weight palette (often just 2–3 weights total)
- generous line-height and letter-spacing
- geometric structure
- clear hierarchy through size and weight, not color

Recommended type families: Inter, Geist, SF Pro, Neue Montreal, Satoshi, or any well-drawn neo-grotesque or geometric sans.

### Spacing System

Use a consistent scale. A typical scale that works:

```
4 · 8 · 12 · 16 · 20 · 24 · 32 · 48 · 64 · 96
```

Honor the rhythm. Avoid one-off values.

### Hero Typography Reference

```css
font-size: 84px;
line-height: 0.95;
font-weight: 300;
letter-spacing: -0.04em;
```

Adjust for brand, but keep the tight line-height and negative tracking — that's where the editorial feel comes from.

### Visual Hierarchy

Hierarchy is built from:

- scale
- spacing
- contrast
- lighting
- motion order
- blur depth
- elevation

Never rely on color alone. Important content should animate first, sit higher visually, and have the strongest depth.

---

## Motion System

### Timing Reference

| Interaction    | Duration    |
| -------------- | ----------- |
| Hover          | 120–220ms   |
| Buttons        | 140–200ms   |
| Cards          | 250–400ms   |
| Panels         | 400–700ms   |
| Modals         | 500–800ms   |
| Hero reveals   | 700–1400ms  |
| Ambient motion | 2s–10s      |

Fast motion: responsive, tactile, subtle. Slow motion: cinematic, atmospheric, immersive.

### Animation Curves

- **Ease Out Quart** — cards, panels, overlays, hover states. Polished and responsive.
- **Ease Out Expo** — hero entrances, cinematic reveals, onboarding. Dramatic and elegant.
- **Spring Physics** — floating windows, drag systems, cursor reactions. Physical and alive.

Spring example:

```js
{ type: "spring", stiffness: 140, damping: 22, mass: 0.8 }
```

### Common Motion Patterns

- **Floating reveal** — fade + blur + scale together
- **Staggered entrance** — container first, then children stagger
- **Blur interpolation** — animate `blur(12px) → blur(0px)` on entrance/exit/focus
- **Cinematic scroll** — parallax + opacity + scale combined
- **Spotlight hover** — cursor glow follows mouse
- **AI typing** — token bursts with glowing cursor pulse

### Interaction Choreography

Premium interfaces synchronize multiple properties at once. Example hover sequence — all simultaneous, not staggered:

- border brightens
- glow intensifies
- shadow deepens
- card lifts
- background lightens

Hover should *improve illumination, increase clarity, deepen depth* — never dramatically transform or aggressively animate.

---

## CSS & Performance

### Architecture Layers

```
Design Tokens
↓
Base Surfaces
↓
Layout Systems
↓
Components
↓
Motion Layer
↓
Effects Layer
```

Build bottom-up. Tokens before surfaces. Surfaces before layout. Effects last.

### Performance Rules

Animate only GPU-accelerated properties:

```css
transform
opacity
filter
```

Avoid animating layout properties:

```css
width / height
top / left / right / bottom
margin / padding
```

Avoid: layout thrash, excessive simultaneous blur layers, particle storms.

### Recommended Stack

- **Framework** — Next.js or any modern React/SSR-capable framework
- **Styling** — Tailwind CSS, CSS variables for tokens
- **Motion** — Framer Motion, Motion One, or GSAP
- **Smooth scroll** — Lenis, GSAP ScrollSmoother
- **Components** — Radix UI, shadcn/ui, React Aria
- **Charts** — Recharts, Visx, Tremor
- **Effects** — CSS `backdrop-filter`, `mask-image`, `mix-blend-mode`, SVG gradients, Canvas/WebGL for advanced

---

## Component Behavior

Components should feel **tactile, layered, responsive, weighted**.

- **Buttons** — soft corners, ambient shadows, slight compression on press, subtle gradients
- **Inputs** — surface materials, glowing focus states, animated placeholders
- **Dropdowns** — scale + blur transitions, staggered items, layered shadows
- **Cards** — float above background, react to hover with synchronized illumination

### State Systems

- **Active** — accent illumination, soft highlight, subtle elevation
- **Disabled** — `opacity: 0.4; filter: grayscale(0.2)`
- **Loading** — shimmer, pulse, gradient drift, skeleton screens — never spinners alone

---

## Anti-Patterns

Avoid:

- **Pure black or pure white surfaces** — feels cheap and clinical
- **Too much blur** — muddy interface
- **Too many accent colors** — destroys premium restraint
- **Harsh shadows** — feels low-quality
- **Over-animation** — breaks sophistication
- **Excessive bounce** — feels toy-like
- **Excessive transparency** — hurts readability
- **Flat composition** — removes spatial realism
- **Random motion** — every motion needs purpose
- **Uniform motion energy** — flattens hierarchy
- **Color-only hierarchy** — fails accessibility, lacks depth
- **Layout-property animation** — kills performance

---

## Checklists

### Visual

- offset foundation (no pure black/white)
- layered surfaces with separation
- restrained accent palette
- editorial typography with confident hierarchy
- ambient illumination (not flat lighting)

### Motion

- smooth, intentional easing
- spring physics where physical motion is appropriate
- blur interpolation on entrances/exits
- staggered reveals with clear order
- ambient drift for backgrounds
- cursor-reactive lighting where appropriate

### UX

- clear hierarchy
- spacious layout, generous negative space
- intelligent focus management
- smooth transitions between states
- responsive interactions with immediate feedback
- calm overall atmosphere

### Technical

- GPU-accelerated transforms only
- optimized blur usage (avoid stacking)
- maintained 60fps under load
- consistent design tokens
- reusable motion primitives
- structured component hierarchy

---

## Final Principle

The interface should not feel like a webpage, a template, or a standard dashboard. It should feel like a *living environment* — crafted with the precision of luxury hardware and the intelligence of futuristic software.
