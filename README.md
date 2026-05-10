# d3-design

A personal Claude Code agent skill encoding a two-layer design system: universal UI principles that inform every interface, plus an opinionated cinematic floating-glass aesthetic available on-request.

## What this is

`d3-design` is an [agent skill](https://docs.anthropic.com/en/docs/agent-skills) for Claude Code. When installed, Claude automatically pulls it into context for UI / frontend / component work and applies the embedded design philosophy to whatever it builds.

## The two-layer model

**Universal principles** — always applied, aesthetic-agnostic:

- Foundation as Material — never pure black or pure white
- Controlled contrast
- Spatial layering
- Motion hierarchy
- Premium restraint
- Editorial typography
- Performance-first animation

These work in any aesthetic — light, dark, brutalist, Material, anything.

**Cinematic floating-glass aesthetic** — on-request, opinionated:

- Near-black layered foundation
- Glassmorphism with `backdrop-filter` blur
- Floating window architecture
- Ambient lighting and subtle glow
- Cursor-reactive surfaces
- Spring physics motion
- Atmospheric backgrounds with noise

This layer activates only when the user asks for it — via keywords like *cinematic*, *premium*, *glass*, *spatial*, *VisionOS-inspired*, *Arc/Linear/Raycast-style*, *AI control panel*, *floating dashboard*, etc.

## What this isn't

- Not a UI component library or kit — it's a *philosophy* skill
- Not a replacement for your project's design system
- Not for every aesthetic — if you want playful, colorful, cartoonish, or maximalist UI, this skill will fight you
- Not framework-locked — recommendations exist (Next.js, Tailwind, Framer Motion, Radix), but the principles apply broadly

## Installation

Clone this repo and link it into your Claude Code skills directory:

```sh
git clone git@github.com:D3OXY/d3-design.git
ln -s "$(pwd)/d3-design" ~/.claude/skills/d3-design
```

Verify with `/skills` inside Claude Code — `d3-design` should appear in the list.

## Files

| File | Purpose | When loaded |
| --- | --- | --- |
| `SKILL.md` | Universal principles, motion system, anti-patterns, checklists | Whenever the skill activates (any UI / frontend work) |
| `cinematic-aesthetic.md` | The opinionated dark/glass aesthetic — color palette, glass formulas, lighting, blur values, AI cursor styling, design tokens | Loaded only when the user asks for the cinematic look |
| `blueprints.md` | Composition recipes — landing pages, dashboards, AI chat, command palettes, atmosphere recipes, real-world references | Loaded when building those specific surfaces |

## Aesthetic in one line

> "High-end software crafted like luxury hardware."

Inspirations: Apple VisionOS · Arc Browser · Linear · Raycast · Stripe · Vercel.

## Customization

The skill is designed to be forked. The universal principles are stable; the cinematic aesthetic is a strong recommendation, not a mandate. Adjust hex values, accent palettes, blur strengths, or motion timing to your brand — the underlying principles will still hold.

## License

MIT — see [LICENSE](LICENSE).

## Author

[D3OXY](https://github.com/D3OXY)
