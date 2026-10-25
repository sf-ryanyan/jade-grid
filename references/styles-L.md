# Style group L — High-end refined (read only when the chosen style is L1–L5)

## L — High-end refined

### L1. Editorial Luxury — real estate, lifestyle, agency, hospitality
- Palette: warm cream `#FDFBF7`, steps `#F7F2EA`/`#EFE8DC`, espresso ink `#2A211C`, muted sage, one warm accent (rust, brass, warm brown).
- Type: high-contrast serif headings (`Instrument Serif`, `Fraunces`, `Playfair Display`, `Cormorant Garamond` + `Noto Serif SC`); body `Plus Jakarta Sans` + `Noto Sans SC`; hero `clamp(64px,9vw,136px)`.
- Texture: fixed film grain ~0.03. Components: High-end kit. Motion: calm-medium, heavy fade-up with slight blur.

### L2. Ethereal Glass — AI, SaaS, tech launches
- Palette: OLED black `#050505`, radial mesh orbs (a colour-wheel pair, low opacity), white ink, white/10 hairlines.
- Type: wide geometric grotesk (`Clash Display` from Fontshare, `Geist`); body `Geist`/`Plus Jakarta Sans` + `Noto Sans SC`.
- Vantablack cards with heavy `backdrop-blur-2xl` and white/10 hairlines (blur only on fixed/sticky or a few panels); High-end kit. Motion: medium-high, glow and scale-in.

### L3. Soft Structuralism — health, consumer, portfolio
- Silver-grey or pure white ground, charcoal ink, one soft accent; massive bold grotesk (`Geist`, `Satoshi`/`Cabinet Grotesk` from Fontshare, `Outfit`) + `Noto Sans SC` bold; airy cards with very soft diffused shadows; High-end kit; springy motion.

### L4. Editorial Grid / Magazine — courses, long reads, reports, culture, agencies
- Paper white or warm off-white, black ink, ONE spot colour. Multi-column magazine grid, oversized serif headlines (`Fraunces`, `Playfair Display`, `Newsreader` + `Noto Serif SC`), body `Source Serif 4` or `Newsreader`, drop caps, pull quotes, captions, thin column rules allowed. Motion low: lines rising, image reveals.

### L5. Liquid Glass (light, Apple-like) — app product pages, premium consumer tech
- Light translucent layers over soft colourful backgrounds, specular highlights on edges, very large radii (24–40px), layered depth. Type `Geist`/`Manrope` + `Noto Sans SC`. Keep text on solid-enough fills for 4.5:1. Motion: smooth springs, morphing pills.

### High-end kit (L1–L3, optional for L5)
- **Double-bezel:** outer shell (fill black/5 or white/5, hairline ring ~5%, padding 6–8px, radius ~2rem) + inner core (own background, `inset 0 1px 1px rgba(255,255,255,.15–.7)` highlight, radius `calc(2rem - padding)`).
- **Island buttons:** full pills; trailing arrow in its own circle flush right; hover moves it `translate(3px,-1px) scale(1.05)`; active `scale(.98)`.
- **Eyebrow pill** before major headings (13px for Chinese, only with real info).
- **Fluid island nav:** floating glass pill detached from the top, centred, `w-max`; hamburger morphs into an X; full-screen blurred overlay with staggered links (100/150/200ms).
- **Layouts:** Asymmetrical Bento (`span 8 / row-span 2` beside stacked `span 4`), Z-Axis Cascade (slight overlaps, -2°/3°), Editorial Split (massive type left, scrolling image pills or staggered cards right).
- Sections `py-24`–`py-40`. Banned here: plain 1px grey borders, harsh dark shadows.

