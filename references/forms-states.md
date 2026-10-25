# Forms, states, navigation, functional motion (read for modes 2–4, or any page with a form)

## E4. Forms
- Visible label for every input (never placeholder-only); required fields marked; persistent helper text for complex inputs; semantic types (`email`, `tel`, `number`) + `autocomplete`; inputs ≥ 44px tall; related fields grouped (`fieldset`/`legend`).
- Validate on blur, not on every keystroke; errors appear below the field, linked with `aria-describedby`, saying the cause and the fix; on failed submit show a focusable error summary at the top linking to each field.
- Submit: button disabled with a loading state → clear success (what happens next, reference number) or error with retry. Long or multi-step forms: progress indicator, back allowed, autosave drafts. Confirm destructive actions; offer undo where possible. Toasts `aria-live="polite"`, 3–5s, never steal focus.
- File/photo upload (e.g. repair requests): show previews, size limits and progress; check file type and size again on the server.
- **Abuse protection on every public form:** a hidden honeypot field, a minimum fill time (reject submits faster than ~3s) and a double-submit guard in the browser; on the server, validate type and length again, rate-limit per IP or email, drop repeats, and escape submitted text before showing it anywhere (never insert it as HTML). For a mainland-China audience use these instead of Google reCAPTCHA. Never put API keys, tokens or write-access endpoints in front-end code — use a server or serverless function, or the form service's own protection.
- **Privacy:** collect only the fields the task needs; a short note next to the submit button says what is collected, why, and who receives it (link the privacy policy when one exists); never send ID numbers, card numbers or health details through a simple form backend. When a site collects personal data, remind the user that local privacy rules may apply (e.g. PIPL in mainland China, CCPA in California, GDPR in the EU) without giving legal conclusions.

## E5. States
- Design every view's empty (helpful message + next action), loading (skeleton), success, error (cause + recovery), disabled (opacity 0.38–0.5 + attribute), read-only (distinct from disabled) and offline/timeout states.

## E6. Navigation
- Current location highlighted; placement consistent on every page; one primary action per screen in modes 3–4; back keeps scroll position, filters and inputs; every key view has a URL/hash (deep link); breadcrumbs at 3+ levels; systems use a sidebar at ≥ 1024px and a top or bottom bar on phone (bottom nav ≤ 5 items, icon + label); modals never used for primary navigation; don't mix tab, sidebar and bottom nav at the same level; move focus to main content after route changes.

## E8. Functional motion (modes 3–4)
- 1–2 animated elements per view, each expressing cause and effect (open, add, remove, confirm). Stagger lists 30–50ms; modals animate from their trigger; crossfade content swaps; forward = left/up, back = right/down; exits faster than enters; nothing decorative that delays the task.

