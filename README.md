# DESIGN.md — LYTDesign™ · LYTGrid™

> The shared design language for every LYTDesign product.
> Deep violet night, white type, one yellow highlighter. Calm software that respects attention.

Each product keeps its own `DESIGN.md` that **extends this file**. A product file may add components and override tokens. It may not break the rules in section 1.

**How to read this file.** Every value is tagged:

- `[MEASURED]` — a pixel color sampled from the live lytdesign.com. Use exactly.
- `[OBSERVED]` — read by eye from the live site (fonts, radii, sizes). Confirm against the site's CSS.
- `[LOCKED]` — a decision already made. Do not change or "improve" it.
- `[PROPOSED]` — a recommended value, contrast-checked.
- `[TO DEFINE]` — not decided. **Do not invent a value. Ask.**

---

## 1. Visual Theme & Atmosphere

**One sentence:** a quiet violet night with a single yellow highlighter.

- **Mood:** calm, dignified, unhurried. Nothing competes with the content.
- **Density:** low. One purpose per box. Generous space. `[LOCKED]`
- **Character:** deep violet background, white titles, soft grey-lavender body text, and **one** yellow used to highlight: headlines, icons, quote bars, and the main call to action.
- **Yellow is a highlighter, not a frame.** It does not draw card borders. Card borders are a faint white hairline. `[MEASURED]`
- **Studio principles:** `[LOCKED]`
  - **Simplified.** Start from what can be taken away.
  - **Human.** Design for a real person in a real moment, not for engagement metrics.
  - **Accessible.** A starting constraint, not a final pass.
  - **Private.** No ads, no tracking, no data resale. Revenue comes from features, never from user data.

### LYTGrid rules `[LOCKED]`

1. Every feature gets its own dedicated, visible box.
2. Nothing is nested more than **one layer** deep.
3. Important actions stay visible. No hidden menus, no tab mazes.
4. Learn the pattern once, understand it everywhere.
5. Clarity is never sacrificed for density.
6. Design for how much a person can hold in mind, not for how much fits on a screen.

**Never:** ads, tracking prompts, streaks, urgency, engagement bait, loud badges, playful bounce.

---

## 2. Color Palette & Roles

### Surfaces

| Token | Value | Role |
| --- | --- | --- |
| `--lyt-bg-top` | `#200D39` `[MEASURED]` | Top of the page gradient |
| `--lyt-bg-bottom` | `#160530` `[MEASURED]` | Bottom of the page gradient |
| `--lyt-nav` | `#14062A` `[MEASURED]` | Navigation bar background |
| `--lyt-card` | `#26123E` → `#1D0939` `[MEASURED]` | Box fill, subtle gradient left to right |
| `--lyt-border` | `rgba(255,255,255,0.09)` ≈ `#34234C` `[MEASURED]` | 1px hairline on boxes and section dividers |

Page background = vertical gradient `--lyt-bg-top` → `--lyt-bg-bottom`.

### Text

| Token | Hex | Contrast on card | Role |
| --- | --- | --- | --- |
| `--lyt-text` | `#FFFFFF` `[MEASURED]` | 17.0 : 1 | Titles, nav links, emphasis |
| `--lyt-text-muted` | `#968DA3` `[MEASURED]` | 5.4 : 1 | Body copy, descriptions |

### Yellow (the only accent)

| Token | Value | Role |
| --- | --- | --- |
| `--lyt-yellow` | `#FCD53F` `[MEASURED]` | Headlines, icons, quote bar, buttons. 11.9 : 1 on card |
| `--lyt-on-yellow` | `#130428` `[MEASURED]` | Text on yellow buttons. 13.7 : 1 |
| `--lyt-yellow-fill` | `rgba(252,213,63,0.125)` ≈ `#412B3E` `[MEASURED]` | Icon medallion fill |
| `--lyt-yellow-ring` | `rgba(252,213,63,0.35)` `[MEASURED, approx]` | Icon medallion ring. Decorative only |
| `--lyt-yellow-line` | `rgba(252,213,63,0.60)` ≈ `#A6873F` | Borders on **controls** (inputs). 5.0 : 1, so the control stays identifiable |

### Status `[PROPOSED]`

| Token | Hex | Role |
| --- | --- | --- |
| `--lyt-success` | `#2EC4A0` | Confirmation |
| `--lyt-danger` | `#FF8A8A` | Errors. Always paired with a text message |

### Rules

- **No hardcoded colors in code.** Always a token. `[LOCKED]`
- Yellow never appears as long body text. Use it for short highlights only.
- The card hairline is decorative. Anything interactive (buttons, inputs) must be identifiable without it.
- Never rely on color alone to carry meaning.
- Extra themes (defined per product) must keep these token names and keep every text pairing at 4.5 : 1 or better.

---

## 3. Typography Rules

| Role | Font | Notes |
| --- | --- | --- |
| Display / headlines | **Bebas Neue**, uppercase `[OBSERVED]` | White, with yellow for the emphasised words |
| Body / UI (web) | **Inter** `[OBSERVED]` | Titles 600, body 400 |
| Body / UI (Flutter apps) | Poppins `[LOCKED]` | The apps' existing theme font |

Web and Flutter apps currently use different body fonts. Whether to unify them is `[TO DEFINE]`.

### Scale `[PROPOSED]`

| Style | Font | Size | Line height |
| --- | --- | --- | --- |
| Display | Bebas Neue | 56 (40 on phones) | 1.05 |
| Headline | Bebas Neue | 40 (32 on phones) | 1.1 |
| Card title | Body font, 600 | 18 | 1.3 |
| Body | Body font, 400 | 16 | 1.7 |
| Label | Body font, 500 | 14 | 1.4 |
| Caption | Body font, 400 | 12 | 1.4 |

- The site's body copy is airy (line height about 1.7). Keep it.
- In the Flutter apps, sizes go through `scaledFontSize` and content width through `maxContentWidth`. `[LOCKED]`
- Body never below 16 on phones. Respect the system font-size setting.

---

## 4. Component Stylings

### LYTGrid Box (the core component)

- Fill `--lyt-card` gradient, 1px `--lyt-border`, radius about 16 `[OBSERVED]`.
- Padding about 22–24. One purpose per box.
- Content order: icon medallion, bold white title, muted description.
- No shadow. Hover: border brightens to `rgba(252,213,63,0.35)` `[PROPOSED]`.

### Icon medallion

- 52 px circle, fill `--lyt-yellow-fill`, 1px ring `--lyt-yellow-ring`, glyph in `--lyt-yellow`. `[OBSERVED]`
- One line-style icon per box. Decorative, so mark it hidden from screen readers.

### Quote block

- 3 px `--lyt-yellow` bar on the left, Bebas Neue uppercase white text, emphasised words in yellow. `[MEASURED bar]`

### Navigation bar

- Background `--lyt-nav`, hairline `--lyt-border` beneath, logo mark plus wordmark left, white links right.
- The single call to action ("Contact Us") is a yellow button. `[OBSERVED]`

### Buttons

| Type | Style |
| --- | --- |
| Primary | Fill `--lyt-yellow`, text `--lyt-on-yellow`, radius about 10, min height 46–48 |
| Secondary | 1.5px `--lyt-yellow` outline, yellow text, transparent fill `[PROPOSED]` |
| Text | Yellow text, no border, 48 px touch target `[PROPOSED]` |

Focus: 2px white ring, offset 2. Always visible.
Button sizes only ever grow as the layout grows. They never shrink at a larger tier. `[LOCKED]`

### List boxes `[LOCKED]`

For pages showing a repeating scrollable list of cards, boxes **auto-grow to fit their content**. Never force an item count. Single-layout pages (settings, about, contact) do not use this rule.

### Settings row `[PROPOSED]`

- Full-width Box, label left, control right, min height 56, one control per row.

### Inputs `[PROPOSED]`

- Fill `--lyt-bg-bottom`, 1px `--lyt-yellow-line` border, radius 12, min height 48.
- Focus: border `--lyt-yellow` plus the focus ring. Error: `--lyt-danger` border and a text message.

Product-specific components live in the product's own `DESIGN.md`.

---

## 5. Layout Principles

- **Spacing scale (px):** 4, 8, 12, 16, 24, 32, 48, 64 `[PROPOSED]`
- **Cards:** two columns beside the text on desktop, three across for feature grids, one column on phones `[OBSERVED]`
- **Whitespace:** more than feels necessary.
- **Voice in copy:** first person "I", never "we" or "us". `[LOCKED]`
- **Tone:** plain, warm, direct. No jargon, no hype, no guilt.

---

## 6. Depth & Elevation

Depth comes from **a slightly lighter fill and a hairline**, not shadows.

| Level | Treatment |
| --- | --- |
| 0 — canvas | Gradient background |
| 1 — nav | `--lyt-nav` + hairline beneath |
| 2 — box | `--lyt-card` + `--lyt-border` |
| 3 — hover | Border `rgba(252,213,63,0.35)` |
| Modal | Scrim `rgba(19,4,40,0.72)`, dialog at level 2 |

---

## 7. Do's and Don'ts

**Do**
- Use tokens for every color, size, and spacing value.
- Give every feature its own visible box.
- Keep one primary action per screen, in yellow.
- Test on a real device at narrow widths before calling anything done.
- Change one variable at a time, then compare against a saved baseline.

**Don't**
- Don't draw card borders in yellow. Borders are the white hairline.
- Don't use yellow for body paragraphs.
- Don't hide features in menus, drawers, or nested tabs.
- Don't add ads, trackers, streaks, badges, or urgency.
- Don't claim compliance (for example WCAG) that hasn't been independently audited.
- Don't add a dependency, database, or architecture without stopping to ask.
- Don't animate with bounce, shake, or spin.

**Motion:** 150–250 ms, ease-out, fades and gentle slides only. Honor "reduce motion". `[PROPOSED]`

---

## 8. Responsive Behavior

| Tier | Breakpoint `[LOCKED for Flutter apps]` |
| --- | --- |
| Mobile | up to 500 dp |
| Tablet | up to 840 dp |
| Tablet landscape | up to 1200 dp |
| Desktop | 1200 dp and above |

- Breakpoints use **logical width**, not physical pixels.
- Web breakpoints for lytdesign.com are `[TO DEFINE]` until read from the site's CSS.
- Touch targets: minimum 48 × 48.
- Layouts reflow by stacking or widening boxes, never by hiding features.

---

## 9. Agent Prompt Guide

### Quick reference

```
Page gradient:   #200D39 → #160530      Nav: #14062A
Box:             #26123E → #1D0939      Hairline: rgba(255,255,255,.09)
Text:            #FFFFFF                Muted: #968DA3
Yellow:          #FCD53F                Text on yellow: #130428
Medallion:       fill rgba(252,213,63,.125) · ring rgba(252,213,63,.35)
Display font:    Bebas Neue, uppercase  Body: Inter
Radius:          box 16 · button 10 · input 12
```

### Ready-to-use prompts

- *"Build this section with LYTGrid: one box per feature, an icon medallion, a bold white title and muted description. Hairline border, never yellow. Yellow only for headlines, icons and the one main button."*
- *"Write the headline in Bebas Neue uppercase, white, with the key words in yellow."*
- *"Read this file, then the product's own DESIGN.md. The product file wins for that product, except for section 1."*

### Before finishing any UI task, confirm

1. Tokens only; no hardcoded colors or sizes.
2. Every text pairing meets 4.5 : 1 (3 : 1 for large text).
3. Box borders are the white hairline, not yellow.
4. Works at 360 and 412 wide, and at larger text sizes.
5. Anything marked `[TO DEFINE]` was asked about, not guessed.
6. Nothing added that tracks, advertises to, or pressures the person using it.

---

*LYTDesign™ · Independent product studio · Norway*
