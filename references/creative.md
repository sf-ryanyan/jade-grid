# PART D — CREATIVE TOOLBOX (read for modes 1–2 when briefing and building)

## D1. Page structure and landing strategies
- Default flow (AIDA): Nav → **Attention** (hero) → **Interest** (features / proof / bento) → **Desire** (scroll scene, media, the live thing) → **Action** (big high-contrast CTA + a designed footer).
- Landing strategies to choose from: **Hero-Centric**, **Conversion-Optimized** (one goal, objections answered, CTA repeated), **Trust & Authority** (credentials, process, guarantees — real only), **Storytelling** (chapters), **Interactive Demo** (product in action), **Feature-Rich Showcase**, **Minimal & Direct**, **Social Proof** (only with real quotes).
- Each section a distinct chapter with large vertical padding; **neighbouring sections never share a layout**; carry the idea into every section, footer included.

## D2. Hero types (rotate across sites)
- **Cinematic Center:** centred wide H1, primary + quiet secondary CTA, full-bleed image with a dark radial wash.
- **Asymmetric Split**, **Artistic Asymmetry** (floating image overlapping from bottom right), **Editorial Manifesto** (poster type only), **Inline-Image Headline** (small image inside the headline), **Sentence Split by a Frame** (headline split around one media frame or reel), **Text Mask** (type as a window onto an image/video), **Scroll-Pinned / Curtain Hero**, **Prompt Hero** (T3: the input is the hero), **3D Product Preview** (rotatable product).
- Hero bans: random floating stamps/badges, pill tags under the hero, raw stat rows inside the hero.

## D3. Section and component arsenal
- **Gapless bento:** `grid-auto-flow:dense`; spans interlock with no empty cells; 3–5 intentional cards beat 8.
- **Statements on colour fields**, **figures inside a sentence**, **horizontal accordion**, **infinite marquee** (pausable), **index with preview**, **masonry / split-screen / sticky-stack sections**, **morphing modal**, **spotlight border card**, **parallax tilt card** (subtle), **testimonial carousel** (real quotes only, pausable), **drop-cap picture**, **question at both edges** (closing CTA), **before/after slider**, **comparison table**, **timeline / process steps**, **map section**.

## D4. Scroll effects (2–3 per site, matched to the Motion dial)
- Pinned story, sticky card stack, scrubbed text reveal (0.1 → 1 opacity), image scale & fade (`scale(.8)` → 1), zoom parallax (< 8% travel), short horizontal scroll section, scroll progress path, lines rising, hover physics (image `scale(1.05)` inside `overflow:hidden`, ~700ms). All obey A6.

## D5. The idea + one live thing
- Inventory 8–12 things only this subject has (name and meaning, place, numbers, rituals, materials, constraints, printed artefacts).
- One sentence: **"On this page, [something only this subject has] becomes [the device]."** Competitor test: if the nearest competitor fits too, find another.
- **One live thing** from real content: calculator, picker, before/after, live status, configurator (e.g. a barbell plate calculator on a strength-training site). Real data, thumb-friendly, no-JS fallback, never blocks reading, ONE thing.

