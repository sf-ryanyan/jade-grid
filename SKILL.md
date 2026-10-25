---
name: jade-grid
description: "Use when the user asks to build, redesign or polish a website, landing page, form or service page, dashboard or app screen (做网站、网页设计、官网、落地页、改版、美化页面) — high-end design that balances creativity and usability, optimised for Chinese-language pages and Chinese-speaking users, on desktop, tablet and phone."
---

# Jade Grid

Jade Grid © 2026 Ryan Yan, MIT License. Built on taste-skill and taste-skill-classics (Leonxlnx, MIT) and ui-ux-pro-max (Next Level Builder, MIT); colour rules adapted from color-expert by David Aerne (meodai, CC BY 4.0). Full credits in NOTICE.md.

**Objective:** agency-level digital experiences — haptic depth, cinematic rhythm, careful micro-interactions, fluid motion — AND real usability. Creativity and standards are balanced by page type: know the industry's standard answer first, then decide whether to follow it or break it. Chinese text is treated as a first-class design material, not an afterthought.

Structure: **0** route → **A** universal floor (core) → **B** mode + design brief → **C** style index → **E** standards map → **F** execution and checklist. The build floor (A2, A4–A7, A9, E1–E3, E9), style details, the creative toolbox and mode-specific standards live in `references/` and are read when the route says so.

---

# 0. ROUTE FIRST — decide the phase, then read only what it needs

Quality is never traded for tokens: everything a phase needs is read in full. What is skipped is only what that phase cannot use.

| Phase | How to recognise it | Read (in addition to this file) |
|---|---|---|
| **Discuss / brief** | idea, scope, questions — the brief is not agreed yet | `references/creative.md` when a page is mode 1–2 (hero types, strategies and effects feed the brief). Style files: only the 1–2 groups being considered, after shortlisting from the index (C). |
| **Build** | the user approved the brief, or explicitly asked to build now | `references/build-floor.md` (always) + the chosen style's group file (always) + every file the mode table (E0) marks for the modes in this project. |
| **Revise** | changes to a page already built in this conversation or project | Nothing new if the files are already in this conversation. If not: the page's MASTER / token block + `build-floor.md` + the style group file whenever the change touches layout, type, motion, images or adds a section. |
| **Quick fix** | small change: text, colour, copy, one component, a bug | Text, copy or colour only: no reference files. Anything touching layout, spacing, type, motion, images or responsiveness: `build-floor.md`. Always read the page's tokens / MASTER and edit a copy (A1). |

- When unsure which phase applies, pick the one that reads more.
- Never re-read a reference file already read in this conversation.
- A section added during a revise or quick fix gets the full rules for its mode (read the needed reference files).

---

# PART A — UNIVERSAL FLOOR (every project, every mode)

## A1. Workflow
1. **Brief first, build after.** For a new page or site: analyze, ask only what is missing, confirm purpose, audience, pages and scope, and present the design brief (Part B). Build once the user agrees. If the user asks to skip the brief or build immediately, put the brief as 3–5 short lines at the top of the reply and build.
2. Never overwrite an existing page; deliver new versions as new files.
   - **New version = copy, then targeted edits:** copy the current file to the next version name (e.g. `index-v2.html`), then change only what the request touches with exact edits. Regenerate a whole file only for a full redesign or when the change touches most of the page.
   - Write the code to files; never paste full page code into the chat.
3. If a browser or screenshot tool is available, check at 1440px, 768px and 390px, fix what looks wrong, then deliver.
   - Do this check once per delivery, after the build is complete — not after every step. After a fix, re-check only the widths the fix affects.
   - Quick fixes: screenshot only when the change can affect layout; text or colour-only changes need none.
4. Speak the user's language: if the user writes in Chinese, the brief, questions and delivery notes are in Chinese. Keep chat output short: the brief as short lines, and at delivery the one-line summary + image prompt list (F1). No recap of steps.

> A2 Responsive, A4 Fonts and Chinese typography, A5 Technology and icons, A6 Motion safety, A7 Images and A9 Known fixes are in `references/build-floor.md` — read it per the route (always when building).

## A3. Colour — the colour wheel (色轮) picks the hues; lightness, chroma and proportion make it high-end
The colour wheel decides **which** hues; lightness, chroma and area decide whether the page looks premium or cheap. Hue alone is a weak predictor of mood — a muted palette reads calm in almost any hue. Work in five steps and state the result in one line (e.g. "analogous sage + brass, muted character, 60-30-10, OKLCH").

1. **Hue:** start from the chosen style's palette (Part C; modes 3–4 may start from the industry palette) and pick a named scheme: **complementary**, **analogous** or **triadic**. Measure hue angles in OKLCH, not HSL (HSL spacing is uneven — greens are squeezed, reds stretched). Compute a complement from the actual colour (OKLCH hue + 180°), never from its name ("red ↔ green" is not reliable).
2. **Character:** choose one character for the palette — pale, muted, deep, vivid or dark — by setting lightness (L) and chroma (C), not by changing hue. Calm/premium = low-to-moderate chroma; energetic/playful = high chroma.
3. **High-end formula (default for modes 1–2):** a large neutral field (tinted with the brand hue, chroma ≲ 0.03 — never dead grey) + a main colour at low-to-moderate chroma + **one** accent that is the only vivid colour on the page. Too many saturated colours competing reads as discount, not luxury. Exceptions are style rules that say otherwise (B2, B4, B5, N3).
4. **Proportion 60-30-10:** ~60% dominant (usually ground/neutral), ~30% secondary (surfaces, main colour), ~10% accent (CTAs, key highlights). The accent works because it is rare.
5. **Build in OKLCH:** convert the style's hex values to `oklch()` tokens. Surface steps change L only (same H, near-zero C); hover/active derive from the base instead of new hex — `oklch(from var(--accent) calc(l - 0.06) c h)` or `color-mix(in oklab, var(--accent) 88%, var(--ink))`; gradients `linear-gradient(in oklch, …)` (RGB/HSL gradients go grey in the middle). If a colour looks dull or shifted, the chroma is outside the screen's range: lower C, keep L and H.

- Semantic tokens on `:root` (never raw hex or oklch values inside components): ground, 2–3 surface steps, ink, ink-2, ink-3, accent (+soft), secondary (+soft), plus success / warning / error / info when the page has states. Components use tokens only, so a palette change is one edit.
- Contrast ≥ 4.5:1 for text, ≥ 3:1 for large display and UI states. Body text never pure `#000`. Never convey meaning by colour alone (add icon or text).
- **Grayscale test:** view the palette (or a screenshot) in black and white — hierarchy, CTAs and text must still separate clearly. Same lightness across colours = illegible, whatever the hues. This checks lightness only; contrast still has to pass.
- Chinese colour meaning is context, not a rule: red can read as celebration, prosperity or warning, and in finance red/green meanings differ by market — check what the audience expects before using red or green for up/down or good/bad.

## A8. Content honesty (AI tells to avoid)
- No emojis in code, markup or copy. No placeholder names (John Doe, 张三, Acme, Lorem ipsum, 示例公司).
- No cliché copy. English: Elevate, Seamless, Unleash, Next-Gen, Game-changer, Delve. Chinese: 赋能、一站式、全方位、打造、引领、极致、颠覆、生态闭环、重新定义. Say what the thing does, in plain words.
- No empty meta-labels ("SECTION 01", "ABOUT US", "QUESTION 05"); small labels only with real information.
- No invented testimonials, reviews, client logos or statistics. Sample data in demos must be realistic and add up.
- Buttons always readable: dark fill → light text, light fill → dark text.

---

# PART B — MODE + DESIGN BRIEF (decide before building)

## B1. Pick the mode of each page
| Mode | Typical pages | Creative : Standard | Rule of thumb |
|---|---|---|---|
| **1 Showcase** | brand home, portfolio, demo/template homepage, photography, course intro | 8 : 2 | Style library + toolbox lead; standards are the safety net (E1–E3). |
| **2 Conversion** | landing page, product or listing page, sign-up page, quote page, pricing | 6 : 4 | Designed look, but structure follows a proven landing strategy (D1), one primary CTA, trust before the ask, forms per E4. |
| **3 Task** | service request, booking, application, checkout, login, contact forms | 3 : 7 | Standards lead: clear steps, E4–E6, minimal motion (E8). Visual style = the site's tokens and type only. |
| **4 System** | dashboards, admin, CRM, ordering systems, apps | 2 : 8 | E-layer leads (navigation, data, states, charts); style from the Minimal, System or Tech groups. |

- A multi-page project can mix modes (home = 1, offer page = 2, request form = 3) but **shares one design system** (E9) so it reads as one product.

## B2. How the mode resolves the usual conflicts
| Topic | Modes 1–2 | Modes 3–4 |
|---|---|---|
| Style choice | Not a repeat of the user's previous site; innovation first | Stable and consistent; the convention first |
| Colour | Style palette + colour-wheel hues + high-end formula (A3); industry palette only as reference | Industry-appropriate palette + colour-wheel tuning; low chroma except semantic colours; strict semantic colours |
| Motion amount | 2–3 signature effects allowed | 1–2 animated elements per view, each with meaning |
| Icons | Curated light/line set | Any consistent standard set |
| Glass / blur | May be decorative (nav, hero panels) | Only behind modals/sheets to show dismissal |
| CTAs | One primary + one quieter secondary | One primary action per screen |
| Layout | Asymmetry, overlaps, bold composition | Predictable grids, consistent placement |

## B3. The design brief (5–10 short lines in the user's language; show it, adjust, then build exactly to it)
1. **Mode** of each page (B1).
2. **Language and audience:** page language(s) (Chinese only / English only / bilingual with a switch) and where visitors are (mainland China / overseas Chinese / international). This decides fonts, CDN, embeds and form protection (A4, E4).
3. **Industry standard answer:** what this category usually looks like (palette, layout, patterns) — and whether we follow it or break it, per mode.
4. **Style:** one from Part C (+ layout archetype / sub-mode). Not the same as the user's previous site unless they ask; if unsure what they used last, ask.
5. **Three dials (1–10):** Variance (calm → experimental), Motion (hover only → scroll scenes), Density (airy → dense). Typical: luxury 6/5/3, minimalist 4/3/5, brutalist 8/4/7, task page 3/2/4, dashboard 4/3/8.
6. **Colour scheme (A3):** colour-wheel scheme (complementary/analogous/triadic) + character (pale/muted/deep/vivid/dark) + 60-30-10 roles (which colour is 60, 30, 10), as OKLCH tokens.
7. **Page structure / landing strategy** (D1) and **hero type** (D2).
8. **2–3 signature effects** (D3–D4) for modes 1–2; motion level for modes 3–4.
9. **The idea + one live thing** (D5) for modes 1–2 (optional in 3–4).
10. **Standards and technology:** E-layer items to apply, whether a MASTER design-system file is needed, and single HTML or the project's stack.

---

# PART C — STYLE INDEX (pick ONE per project; its own rules win inside that style)

Shortlist from this index, then read the group file in `references/` for full palette, type, components, motion and bans. Never build a style from this index alone.

| ID | Style | Best for | Look in one line | File |
|---|---|---|---|---|
| L1 | Editorial Luxury | real estate, lifestyle, agency, hospitality | warm cream, high-contrast serif, film grain, calm fade-up | styles-L.md |
| L2 | Ethereal Glass | AI, SaaS, tech launches | OLED black, mesh orbs, glass cards, wide grotesk | styles-L.md |
| L3 | Soft Structuralism | health, consumer, portfolio | silver/white, massive bold grotesk, soft shadows, springy | styles-L.md |
| L4 | Editorial Grid / Magazine | courses, long reads, reports, culture, agencies | magazine grid, oversized serif, one spot colour | styles-L.md |
| L5 | Liquid Glass (light) | app product pages, premium consumer tech | translucent layers, specular edges, big radii | styles-L.md |
| M1 | Minimalist Editorial | system demos, SaaS, tools, B2B | warm monochrome, flat bento, pastel tags, near-invisible motion | styles-M.md |
| M2 | Swiss Modernism 2.0 | professional services, architecture, consultancies, B2B | strict 12-col grid, black + one primary colour | styles-M.md |
| M3 | Exaggerated Minimalism | luxury products, architecture, photographers, single offer | one giant word per screen, extreme whitespace | styles-M.md |
| M4 | E-Ink / Paper | courses, documentation, fiction, newsletters | paper grey, serif body, reading-first | styles-M.md |
| B1 | Swiss Industrial Print | fitness, trades and construction, manifestos | paper + carbon + hazard red, macro type, 90° corners | styles-B.md |
| B2 | Neubrutalism | young brands, startups, events, games, creators | bright flat colours, thick borders, hard shadows | styles-B.md |
| B3 | Kinetic Typography | events, music, campaigns, launches | type is the image, scroll-driven words | styles-B.md |
| B4 | Bauhaus | education, art, culture, kids' learning | primary colours, geometric shapes as layout | styles-B.md |
| B5 | Memphis | parties, kids, playful creative brands | pastel + bold, squiggles, confetti shapes | styles-B.md |
| T1 | Tactical Terminal | data, analytics, AI agents, tech dashboards (+ Sci-Fi HUD) | CRT dark, mono type, dense readouts | styles-T.md |
| T2 | Aurora / Gradient Mesh | AI and creative SaaS, apps, fintech | slow colour mesh, clean sans | styles-T.md |
| T3 | AI-Native UI | AI tools, agents, AI training, assistants | prompt box as hero, streaming text | styles-T.md |
| N1 | Organic / Nature Distilled | wellness, clinics, tea, food and drink, sustainability | earthy palette, botanical lines, warm serif | styles-N.md |
| N2 | Vintage Analog / Retro Film | photography, cafes, travel, storytelling | faded colour, grain, polaroid frames | styles-N.md |
| N3 | Claymorphism | games, kids, cute apps, playful tools | soft 3D clay, pastels, bouncy | styles-N.md |
| S1 | Data Dashboard | admin, CRM, ordering, analytics | sidebar, KPI row, dense tables | styles-S.md |
| S2 | Enterprise SaaS / Portal | customer portals, service centres, B2B tools | Fluent/Polaris-like, task-first | styles-S.md |

The High-end kit (double-bezel, island buttons, island nav, bento/cascade/split layouts) is in `styles-L.md`.

---

# PART E — STANDARDS LAYER (adapted from ui-ux-pro-max; enable by mode)

## E0. What each mode enables, and where it lives
| Item | Mode 1 | Mode 2 | Mode 3 | Mode 4 | Where |
|---|---|---|---|---|---|
| E1 Accessibility, E2 Performance, E3 Touch | yes | yes | yes | yes | references/build-floor.md |
| E4 Forms (incl. abuse protection and privacy) | if any form | yes | yes | yes | references/forms-states.md |
| E5 States | basic | partial | yes | yes | references/forms-states.md |
| E6 Navigation | basic | basic | yes | yes | references/forms-states.md |
| E7 Charts and data | — | if any | if any | yes | references/charts-data.md |
| E8 Functional motion | — | — | yes | yes | references/forms-states.md |
| E9 Design-system file | multi-page | multi-page | yes | yes | references/build-floor.md |
| E10 App and dark mode | when needed | when needed | when needed | when needed | references/app-dark.md |
| D Creative toolbox | yes | yes | optional (D5) | — | references/creative.md |

---

# PART F — EXECUTION AND CHECKLIST

## F1. Execution protocol
1. **Brief:** Part B agreed with the user (or the user asked to build directly — brief shown in 3–5 lines).
2. **Load:** `build-floor.md` + the style group file + the reference files E0 marks for this project's modes (skip any already read in this conversation).
3. **System first:** tokens, type scale (Latin and Chinese), spacing for the chosen style (and MASTER file if E9 applies).
4. **Architect:** hero/top of page as chosen, then each section or screen with its own composition (modes 1–2) or consistent patterns (modes 3–4).
5. **Live thing** (modes 1–2) or **core task flow** (modes 3–4) built and working, including all states.
6. **Choreograph:** motion at the agreed level; feedback on every control.
7. **Responsive pass** at desktop, tablet and phone; screenshot check if possible (once, per A1).
8. **Output:** clean code + image prompt list + a one-line summary (mode, style, dials, effects, idea), in the user's language.

## F2. Checklist — all modes
- [ ] Brief agreed (or user asked to build directly); original file untouched
- [ ] Mode set per page; one style applied consistently with its own bans
- [ ] Palette = style/industry palette + named colour-wheel scheme + one character + 60-30-10; OKLCH semantic tokens; one vivid accent (unless the style says otherwise); contrast OK; grayscale test passed; meaning never by colour alone
- [ ] Free, properly licensed fonts; universal font ban; Chinese pairing and sizes (≥ 13px, body ≥ 16px on phone)
- [ ] Chinese pages: `lang` set, CJK font stack with system fallbacks, Chinese–Latin spacing, no punctuation at line start, Chinese font loading plan; mainland-China audience: no blocking external CDN, fonts, maps or captcha (A4)
- [ ] Headlines ≤ 2 lines desktop / 3 phone; buttons readable
- [ ] Works at 1440 / 768 / 390px; no sideways scroll; touch targets OK
- [ ] A6 motion safety; A9 fixes; E1–E3 applied
- [ ] Public forms: abuse protection, server-side checks, privacy note (E4)
- [ ] No emojis, placeholder names, clichés, empty meta-labels or invented proof
- [ ] Image slots empty but laid out (or filled with the user's own images); English AI prompt list delivered

## F3. Extra checks by mode
- **Modes 1–2:** style differs from the user's previous site; 2–3 signature effects; neighbouring sections differ; idea sentence + one live thing working; one primary + one quiet CTA; reads as a top-agency build, not a template with nice fonts.
- **Mode 2:** landing strategy clear; trust shown before the ask; form per E4.
- **Mode 3:** task completable in the fewest steps; E4–E6 and E8 applied; success state tells what happens next.
- **Mode 4:** E5–E9 applied; navigation consistent; data realistic; charts readable; MASTER file followed.
