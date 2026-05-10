# Cinematic Floating UI Aesthetic

The opinionated visual language of `d3-design`. Apply when the user asks for cinematic, premium dark, glassmorphism, floating, spatial, VisionOS-inspired, or Arc/Linear/Raycast-style interfaces.

All specific values below are **recommendations**, not mandates. The principle (offset darkness, layered surfaces, sparse meaningful accents, atmospheric lighting) matters more than the exact hex.

## Core Identity

This aesthetic combines:

- cinematic interface design
- glassmorphism
- spatial UI systems
- macOS-inspired layering
- luxury enterprise software aesthetics
- editorial minimalism
- futuristic AI platform interfaces
- floating operating-system panels

The UI should feel: **intelligent · atmospheric · expensive · responsive · physically layered · cinematic · futuristic · restrained**

Never: playful · colorful · cartoonish · aggressively animated · flat · noisy.

> "High-end software crafted like luxury hardware."

---

## Color System

### Recommended Surface Palette

```css
--bg-primary: #0a0a0b;
--bg-secondary: #101114;
--surface-primary: #15161a;
--surface-secondary: #1b1d22;
--surface-elevated: #202228;
```

Or any near-black palette with similar progressive offset (~`#0A`–`#22` range). Darkness should feel **soft, layered, atmospheric, cinematic** — never absolute.

### Recommended Text Palette

```css
--text-primary: rgba(255, 255, 255, 0.95);
--text-secondary: rgba(255, 255, 255, 0.72);
--text-muted: rgba(255, 255, 255, 0.45);
```

Light-on-dark with stepped opacity rather than separate hex values — this preserves atmospheric blending with surfaces underneath.

### Accent Philosophy

Accents must be **sparse, meaningful, intentional, functional**. Avoid rainbow palettes and competing accents.

Typical accent choices for this aesthetic — pick **one or two**, not all:

- electric blue
- neon orange
- soft purple
- signal green
- amber
- cyan

Or any single brand accent. The point is **one or two** accents max, used to guide attention. A single confident accent reads more premium than three competing ones.

---

## Surface Construction

### Surface Hierarchy

```
Background Scene
↓
Atmospheric Overlay
↓
Floating Window
↓
Panel
↓
Card
↓
Micro Component
```

### Standard Surface

```css
background: rgba(15, 15, 18, 0.72);
backdrop-filter: blur(24px);
border: 1px solid rgba(255, 255, 255, 0.06);
border-radius: 28px;
box-shadow: 0 20px 60px rgba(0, 0, 0, 0.45);
```

---

## Glassmorphism

### Core Glass Formula

```css
.glass {
  background: rgba(16, 16, 20, 0.68);
  backdrop-filter: blur(28px);
  border: 1px solid rgba(255, 255, 255, 0.06);
}
```

### Layered Glass — subtle depth gradient on top

```css
background: linear-gradient(
  180deg,
  rgba(255, 255, 255, 0.05),
  rgba(255, 255, 255, 0.01)
);
```

---

## Floating Window

```css
.floating-window {
  border-radius: 28px;
  overflow: hidden;
  background: rgba(10, 10, 12, 0.72);
  backdrop-filter: blur(32px);
  border: 1px solid rgba(255, 255, 255, 0.05);
  box-shadow: 0 20px 80px rgba(0, 0, 0, 0.55);
}
```

### Window Entrance

```
opacity: 0 → 1
scale: 0.96 → 1
translateY: 12px → 0
blur: 12px → 0
```

### Window Exit

```
fade out + slight shrink + blur increase
```

### Window Stacking

Use layered shadows, z-depth hierarchy, atmospheric separation.

---

## Sidebar

The sidebar isn't navigation. It's a **control dock** — an OS rail, spatial anchor, persistent command surface. It should feel grounded, atmospheric, tactile, elevated, softly illuminated.

### Width Strategy

```
72px   → icon rail
220px  → compact sidebar
280px  → standard dashboard sidebar
320px  → enterprise systems
```

### Surface

```css
background: rgba(15, 15, 18, 0.82);
backdrop-filter: blur(28px);
border-right: 1px solid rgba(255, 255, 255, 0.04);
```

### Nav Item

```css
.nav-item {
  height: 44px;
  border-radius: 14px;
  padding-inline: 14px;
  display: flex;
  align-items: center;
  gap: 12px;
}
```

### Nav States

```css
/* Idle */
color: rgba(255, 255, 255, 0.62);

/* Hover */
background: rgba(255, 255, 255, 0.04);
transform: translateX(2px);

/* Active */
background: rgba(255, 255, 255, 0.06);
border: 1px solid rgba(255, 255, 255, 0.08);
```

### Sidebar Entrance

```
opacity: 0 → 1
translateX: -12px → 0
blur: 12px → 0
```

---

## Card

```css
.card {
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid rgba(255, 255, 255, 0.05);
  border-radius: 24px;
  padding: 24px;
}
```

---

## Lighting

### Ambient Lighting

```css
background: radial-gradient(
  circle at top left,
  rgba(255, 255, 255, 0.06),
  transparent 40%
);
```

### Glow Recipe — subtle ambient

```css
box-shadow: 0 0 40px rgba(255, 255, 255, 0.06);
```

### Accent Glow — use sparingly

```css
box-shadow: 0 0 30px var(--accent);
```

Glow should **guide focus, enhance depth, improve atmosphere, create premium feel** — never overpower the UI or create neon overload.

---

## Shadow System

### Premium Shadow

```css
box-shadow: 0 10px 40px rgba(0, 0, 0, 0.45);
```

Avoid harsh black shadows. Premium shadows are wide, soft, and moderately opaque.

---

## Blur System

```
8px   → overlays
16px  → cards
24px  → panels
32px  → windows
40px  → cinematic glass
```

Avoid stacking too many blur layers — performance suffers.

---

## Borders & Dividers

```css
border: 1px solid rgba(255, 255, 255, 0.06);
```

Borders in this aesthetic are nearly invisible — they exist to separate planes, not to draw attention.

---

## Gradients

Gradients should feel **atmospheric, subtle, cinematic, soft**. Never rainbow-like, loud, or oversaturated.

### Premium Gradient

```css
background:
  radial-gradient(circle at top left, rgba(255, 255, 255, 0.08), transparent 35%),
  linear-gradient(180deg, rgba(255, 255, 255, 0.03), rgba(255, 255, 255, 0.01));
```

---

## Background Atmosphere

Backgrounds should never feel empty. Layer:

1. Dark gradient base
2. Radial ambient glow
3. Noise texture overlay
4. Subtle vignette
5. Slow animated blur drift

Background motion: extremely slow, subconscious, atmospheric.

### Noise Opacity

```
1%–4%
```

Subtle noise prevents flatness, sterile gradients, and lifeless surfaces.

---

## AI Interface Behavior

### AI Panel Feel

Predictive, intelligent, alive, responsive, spatial.

### AI Output

- stream smoothly
- reveal in chunks
- glow subtly
- maintain rhythm

### AI Cursor

```css
.ai-cursor {
  width: 2px;
  background: rgba(255, 255, 255, 0.92);
  box-shadow: 0 0 12px rgba(255, 255, 255, 0.55);
}
```

Pulse softly. Glow subtly. Never harsh blink.

### AI Streaming Pattern

```
Token batch appears
Tiny delay
Next batch
Cursor pulse
```

Avoid harsh character-by-character typing. Token bursts feel intelligent.

### AI Message Styling

- **User messages** — cleaner, more compact, lower emphasis
- **AI messages** — larger spacing, softer lighting, subtle glow, progressive reveal

---

## Cursor Reactive Systems

Panels subtly react to cursor movement:

- gradient shifts
- micro tilt
- reflection simulation
- glow movement

```css
transform: rotateX(...) rotateY(...) translateY(...);
```

Cursor reactivity is the signature interaction of this aesthetic. Use it on hero surfaces, primary cards, and feature showcases.

---

## Parallax

```
Background → slowest
Container  → medium
Cards      → faster
Glow       → fastest
```

Multi-layer parallax creates cinematic depth, spatial realism, and a floating feel.

---

## Charts & Data Viz

Charts should glow softly, avoid noise, use restrained color, integrate into dark surfaces.

- **Bars** — grow upward with spring physics
- **Lines** — path draws progressively
- **Counters** — animated numeric interpolation

---

## Hero Section (Aesthetic-Specific)

- oversized typography (`84px+` hero)
- atmospheric motion in background
- floating product/dashboard showcase
- cinematic spacing
- staggered text reveal
- floating card drift
- glow movement
- subtle zoom
- blur transitions

---

## Floating Drift (Ambient Motion)

Panels should drift subtly. Example:

```
translateY oscillation: 0px → 4px → 0px
duration: 4s–12s
```

Movement should be nearly invisible — atmospheric, soft, subconscious.

---

## Design Tokens (Recommended)

### Radius

```css
--radius-sm: 12px;
--radius-md: 20px;
--radius-lg: 28px;
--radius-xl: 36px;
```

### Blur

```css
--blur-sm: 8px;
--blur-md: 16px;
--blur-lg: 24px;
--blur-xl: 32px;
```

### Shadow

```css
--shadow-soft: 0 10px 40px rgba(0, 0, 0, 0.35);
--shadow-deep: 0 20px 80px rgba(0, 0, 0, 0.55);
```

### Surface Opacity

```css
--opacity-soft: 0.04;
--opacity-medium: 0.08;
--opacity-strong: 0.14;
```

---

## Aesthetic Formula

```
Dark minimal foundation
+ Floating glass surfaces
+ Layered spatial depth
+ Cinematic motion
+ Editorial typography
+ Ambient lighting
+ Sparse accent colors
+ Intelligent animation
+ Cursor-reactive interaction
+ Atmospheric composition
+ Premium microinteractions
= Cinematic Floating UI
```

> "A living cinematic operating environment crafted with the precision of luxury hardware and the intelligence of futuristic software."
