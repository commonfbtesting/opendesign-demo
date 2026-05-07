# DESIGN.md — Cathay Pacific

Extracted from the reference layout (layout.png) and the production output built in this project. Use these tokens and posture rules for all future work on this project.

---

## Color tokens

```css
:root {
  --bg:          #f4f4f0;   /* warm off-white — page background, hero text panel, utility bar */
  --white:       #ffffff;   /* nav bar, booking panel, form fields */
  --fg:          #1a1a1a;   /* body text, headlines, active nav underlines */
  --muted:       #666666;   /* secondary text, placeholder text, icon strokes */
  --border:      #e0e0dc;   /* all hairline dividers — form rows, nav, card edges */
  --green-dark:  #1e3a2f;   /* primary CTA bg (Search button, Learn more, active booking tab) */
  --green-mid:   #2d5a45;   /* hover state for green-dark buttons */
  --teal:        #006564;   /* brand accent — links, eyebrows, pills, borders, Cathay for Business */
  --teal-light:  #e8f4f4;   /* pill hover fill, tinted backgrounds */
  --image-bg:    #c8dde8;   /* fallback behind hero images while loading */
}
```

**Accent budget:** `--teal` appears on links, eyebrow labels, offer pills, and the anniversary badge — never as a fill on large surfaces. `--green-dark` is reserved for primary action buttons and the active booking tab background only.

---

## Typography

```
--font: -apple-system, BlinkMacSystemFont, 'Helvetica Neue', Arial, sans-serif;
```

Single family throughout — system sans. No display / body split. This is intentional: airline utility aesthetic prioritises legibility and brand neutrality over editorial character.

### Type scale

| Role | Size | Weight | Notes |
|---|---|---|---|
| Utility bar | 12px | 500 | muted links; teal for primary link |
| Nav links | 14px | 400 | 60px tall tap target; teal on hover |
| Logo wordmark | 20px | 700 | letter-spacing: -0.3px |
| Hero eyebrow | 13px | 500 | teal; letter-spacing: 0.01em |
| Hero headline | clamp(28px, 3.5vw, 44px) | 700 | letter-spacing: -0.5px; line-height: 1.15 |
| Hero body | 14px | 400 | muted; line-height: 1.6; max-width: 320px |
| Booking tab | 14px | 500 | — |
| Subtab / form label | 11px | 500 | muted; letter-spacing: 0.01em; all-caps intent |
| Form value | 16px | 400 | fg; placeholder weight 300 |
| CTA button | 14–15px | 500 | white on green-dark |
| Offer pill | 12px | 400 | teal |
| Slider dot | 12px | 400 / 700 active | letter-spacing: 0.5px |

---

## Spacing & layout

- **Max content width:** 1200px, centred with `margin: 0 auto`
- **Page padding:** `0 24px` on the wrapper (not on the grid cells themselves)
- **Utility bar height:** 36px
- **Nav height:** 60px (sticky, z-index 100)
- **Hero split:** `38% 62%` (text / image), `min-height: 360px`
- **Hero text padding:** 48px (all sides), 40px bottom
- **Form field padding:** 14px 20px
- **Form action row padding:** 14px 20px
- **Booking tab padding:** 14px 20px
- **Subtab padding:** 14px 16px
- **Border weight:** 1px solid `--border` everywhere — no 2px, no shadows
- **Button border-radius:** 20px for secondary (Sign in); 0px (square) for primary CTAs (Search, Learn more)
- **Toggle dimensions:** 40×22px track, 18×18px thumb

---

## Posture rules

1. **No shadows.** Borders and whitespace separate sections. Zero box-shadow on any surface.
2. **No border-radius on primary CTAs.** Search button and Learn more are square-cornered. Only the Sign In pill and offer pills use radius.
3. **No gradient backgrounds.** The hero background is flat `--bg`. Images are photos, not illustrated gradients.
4. **One accent.** `--teal` is used for links, eyebrows, and pills. It is never used as a large fill. `--green-dark` is the action colour — keep them distinct and never mix on the same element.
5. **Hairline borders define structure.** Every section boundary, every form row, every tab divider is `1px solid --border`. Heavier borders signal active state via `--fg` (slider dot underline, subtab underline).
6. **Image bleeds to viewport edge on right side.** The hero image panel has no padding, no rounded corners — it runs flush to the right edge of the browser.
7. **Active booking tab = dark green fill** (#1e3a2f), white text. All other tabs are ghost on `--white` background.
8. **Form fields are tappable zones** — full padding, hover background `#fafaf8`, no visible input chrome (no border on individual inputs, border lives on the wrapping row).
9. **Transition timing:** `0.15s` for colour/background transitions; `0.6s ease` for image cross-fades; `0.2s` for toggles.

---

## Responsive breakpoints

| Breakpoint | Changes |
|---|---|
| ≤ 900px | Hero stacks (single column); hero image fixed 240px height; booking tabs go 2×2; form rows single column; multi-column forms collapse |
| ≤ 640px | Nav links hidden (mobile menu implied); utility bar stacks vertically; btab font 12px; remaining 2-col forms collapse to 1 col |

---

## Component inventory

- **Utility bar** — 36px, bg-colored, left teal link, right muted icon-links
- **Main nav** — white, sticky, logo + anniversary badge + nav links + sign-in pill
- **Hero** — 38/62 grid, bg-colored left panel (eyebrow + h1 + body + CTA), photo right panel
- **Slider controls** — right-aligned, numbered dots (01–04), pause/play icon
- **Booking section** — white, 4-col top tabs (green-dark active), subtabs with redeem toggle, form rows, offers bar, action row
- **Offer pills** — teal border, teal text, teal-light hover fill, border-radius 20px
- **Search button** — green-dark fill, white text, square corners, full-width feel on mobile

---

## What to avoid

- Rounded cards with a left coloured border accent
- Gradient hero backgrounds
- Emoji feature icons
- Inter / Roboto as the font (system stack is correct)
- Invented metrics without a source
- Shadow layers of any kind
- Using `--teal` as a button fill (it's an accent/text colour only)
