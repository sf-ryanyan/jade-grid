# BUILD FLOOR — universal rules for building and layout changes (every project, every mode)

Part A and Part E rules that apply whenever code is written or layout is touched. Read per the route in SKILL.md.

## A2. Responsive: desktop, tablet, phone
- Breakpoints: desktop ≥ 1024px, tablet 768–1023px, phone < 768px (check 375/390 too). Design each, don't just shrink.
- Tablet: grids go to 2 columns; nav collapses to a menu button when links stop fitting.
- Phone: asymmetric layouts fall back to `width:100%`, ~16px side padding, single column; remove rotations and overlaps; core content first, secondary content folded.
- `min-height:100dvh`, never `100vh`/`h-screen`. Viewport meta `width=device-width, initial-scale=1`; never disable zoom.
- No sideways page scroll (`overflow-x:clip` on the page wrapper if animations go off-screen); tables wrap (`th{white-space:normal}`) on phone; long URLs/IDs use `overflow-wrap:anywhere`.

## A4. Fonts and Chinese typography
- **Free, properly licensed fonts only** — never paid fonts or fonts with an unclear licence. Each style lists options; check the licence before bundling or self-hosting any font.
- Universal ban as the main Latin face: **Inter, Roboto, Arial, Open Sans, Helvetica**.
- Chinese pairing: serif styles → `Noto Serif SC` (思源宋体); sans styles → `Noto Sans SC` (思源黑体; 900 for heavy display). Optional OFL display faces when the style fits: `LXGW WenKai` (霞鹜文楷 — warm, literary; N, M4, L4) and `Smiley Sans` (得意黑 — bold slanted display; B, T). Never ship commercial Chinese typefaces as webfonts unless the user holds a web licence.
- Fallback stack after the webfont — sans: `"PingFang SC", "Hiragino Sans GB", "Microsoft YaHei", "Noto Sans CJK SC", "Source Han Sans SC", sans-serif`; serif: `"Songti SC", "Noto Serif CJK SC", "Source Han Serif SC", SimSun, serif`. List the Latin face first so Latin glyphs use it and Chinese falls through to the CJK face.
- Sizes and rhythm: nothing readable below 13px; body 16–18px (16px minimum on phone); Chinese line-height 1.7–2.0, Latin 1.5–1.75; Chinese lines ~25–40 characters on desktop, Latin 60–75; CJK letter-spacing 0–0.05em for body, ≤ 0.2em only for short display labels; uppercase and wide-tracking rules apply to Latin only.
- Markup: `<html lang="zh-CN">` (`zh-Hant` / `zh-TW` / `zh-HK` for Traditional); on bilingual pages set `lang` on each language block so browsers pick the right glyphs and line breaking.
- Chinese–Latin mixing (中英混排): a space between Chinese and Latin letters or numbers (`text-autospace` where supported, manual spaces as fallback); full-width punctuation in Chinese text （，。：；！？“”）and half-width in Latin text; `line-break:strict` + `word-break:normal` so closing punctuation never starts a line; no `text-align:justify` on short lines or narrow phones; `text-spacing-trim` only as progressive enhancement.
- Emphasis: Chinese has no true italic — never fake-italicise Chinese; emphasise with weight, colour, underline or `text-emphasis` dots (editorial styles).
- Chinese display headlines: line-height 1.15–1.3, weight 700–900; don't split short words across lines (`word-break:keep-all` on short headings, or `<wbr>` at chosen points); ≤ 2 lines on desktop, ≤ 3 on phone — widen the container, then shrink the size.
- Chinese font loading (CJK font files are several MB): Google Fonts already serves Chinese in small `unicode-range` slices; when self-hosting, subset to the characters used (e.g. fonttools `pyftsubset`) or slice by unicode-range; if weight matters, use the webfont for headings and let long body text use the system stack. `font-display:swap`; preload only the critical Latin font, never a whole CJK file.
- **Audience in mainland China:** Google Fonts, Google Maps, YouTube, reCAPTCHA and some public CDNs can be slow or unreachable. Self-host fonts and scripts (or rely on the system font stack), inline small libraries, replace embeds with a static image + link, and use form protection that needs no Google service (E4). Overseas or international audience: standard CDNs are fine.
- Locale formats on Chinese pages: dates `2026年10月24日` or `2026-10-24`; 万 / 亿 for large numbers when the audience expects it; currency symbol for the market (¥, HK$, NT$, US$); phone fields accept the local format.
- Tabular figures (`font-variant-numeric:tabular-nums`) for prices, data columns and timers.

## A5. Technology and icons — decided per project
- Simple sites, demos, GitHub Pages: one self-contained `index.html` (inline CSS + JS, no build step); Tailwind values here translate to plain CSS.
- Existing stack (React, Next.js, Vue, Tailwind, GSAP, Framer Motion, Flutter, SwiftUI): stay in it; never migrate frameworks.
- Scroll effects: CSS `position:sticky` + `IntersectionObserver` + CSS scroll timelines first; GSAP ScrollTrigger only when needed.
- Icons: one set and one stroke weight per product. Modes 1–2: Phosphor (Light/Regular/Bold to match the style), Remix Line, Radix or inline SVG; default Lucide/FontAwesome/Material dropped in as-is are banned. Modes 3–4: any well-made standard set (Phosphor, Heroicons, Lucide, Radix) is fine if consistent. Never emoji as icons.
- State the technology choice in one line.

## A6. Motion safety and performance (all modes)
- Animate only `transform` and `opacity`; no layout shift from animation; `will-change` sparingly; `backdrop-filter` only on fixed/sticky layers; grain/noise only on a fixed `pointer-events:none` layer; z-index only for real layers.
- Reveals via `IntersectionObserver` (or `whileInView`), never raw scroll listeners. Hidden start states only when JS runs (class `js` on `<html>`); everything readable with JS off; reveal anything already scrolled past.
- `prefers-reduced-motion: reduce`: every element at its end state; no travel, scrubbing, pinning, auto-rotation or marquees.
- Animations never block input and can be interrupted; elements never linger below opacity 0.2.
- Every clickable thing gives feedback within 100ms: hover (behind `@media (hover:hover)`), `:active` scale 0.95–0.98, visible focus ring 2–4px; `cursor:pointer`; `touch-action:manipulation`.
- Easing: custom curves (e.g. `cubic-bezier(0.32,0.72,0,1)`, `cubic-bezier(0.16,1,0.3,1)`) or springs; never instant state changes; `linear` only for constant-rate progress or rotation; exits ~60–70% of the enter duration.

## A7. Images
- Never invent photos, hotlink images or present stock as real work. Use the user's own images when provided; otherwise leave slots for images the user generates or supplies.
- Leave every open slot **empty but laid out**: fixed aspect ratio (prevents layout shift), a calm tinted fill from the palette, and `<img src="img/<name>.png" alt="..." width height loading="lazy" onerror="this.remove()">` (no lazy on the hero image) so the user's file appears once added. Suggest WebP export.
- At delivery list every file name, aspect ratio and an **English AI image prompt** (English works best in most image tools): subject, composition, calm space for text, light, palette and treatment matching the style, ending with "no text, no logos". Image tools render Chinese text badly — headings and labels live in HTML, never inside images.

## A9. Known fixes from testing (always apply)
- Fixed/floating nav: `[id]{scroll-margin-top:100px}`; sticky UI never hides the focused element.
- Accordions: `details:not([open])>.content{display:none}`.
- Tables wrap on phone; floating buttons don't cover content on phone.

# Core standards (all modes)

## E1. Accessibility
- Contrast per A3; visible focus 2–4px with 3:1 contrast, never hidden by sticky UI; logical tab order = visual order; skip-to-content link; one `h1`, no skipped heading levels; alt text for meaningful images, decorative ones `alt=""`; icon-only buttons have an accessible name; carousels and moving content pausable; modals and multi-step flows have a clear way out (close, Esc, back).

## E2. Performance
- Images: WebP/AVIF, `srcset` where useful, width/height or aspect-ratio, lazy below the fold; reserve space for async content (CLS < 0.1); defer third-party scripts; debounce/throttle scroll, resize and input handlers; skeletons instead of long spinners for waits over ~1s.

## E3. Touch
- Targets ≥ 44×44px (≥ 24px for dense desktop UI), ≥ 8px apart; tap/click for primary actions, never hover-only; no horizontal swipe on main content; keep key controls away from notches and the home-indicator area; no precision taps on tiny icons.

## E9. Design-system file (MASTER)
- For multi-page or system projects, write the tokens, type scale, components and rules once: `design-system/<project>/MASTER.md` (or a commented token block at the top of a single-file site). Page-specific overrides go in `design-system/<project>/pages/<page>.md`.
- Before building any page: read MASTER, then the page override if it exists. Never rewrite MASTER without the user's OK.
