# Prince Kumar — Portfolio Design Notes

**File:** `index.html` (single file, no framework, no build step)
**Last updated:** 22 October 2026
**Assets in the folder:** `index.html`, `Prince_Kumar_Resume.pdf`, `designprince.md`

The design is editorial and paper-like: warm off-white, near-black ink, and a rust
accent. It deliberately avoids blue, gradients, glass effects, drop shadows, pill
buttons, emoji, and large rounded cards so it does not look like a generated template.

---

## 1. Colour

All colours are CSS variables declared on `:root`, with dark values on
`:root[data-theme="dark"]`.

### Light theme (default)

| Token | Hex | Used for |
|---|---|---|
| `--bg` | `#f3efe6` | Page background (warm paper) |
| `--surface` | `#ece6d8` | Reserved panel tone (currently unused) |
| `--ink` | `#1c1a17` | Headings, body text, borders on filled elements |
| `--muted` | `#615b50` | Secondary copy, labels, dates, captions |
| `--line` | `#d2c9b9` | Hairline rules and row borders |
| `--line-strong` | `#a89c88` | Dashed card border, heavier rules, link underlines |
| `--accent` | `#a3401a` | Rust accent: name dot, section numbers, hover, markers |
| `--grain` | `.032` | Paper-grain overlay opacity |

- Browser `theme-color`: `#f3efe6`
- Text selection: background `#a3401a`, text `#f3efe6`

### Dark theme (true black)

| Token | Hex | Used for |
|---|---|---|
| `--bg` | `#070706` | Page background (true black, not navy or grey-blue) |
| `--surface` | `#0e0e0c` | Reserved panel tone (currently unused) |
| `--ink` | `#e9e3d6` | Warm off-white text |
| `--muted` | `#a09a8d` | Secondary copy, labels, dates |
| `--line` | `#24211c` | Hairline rules |
| `--line-strong` | `#3b362d` | Dashed card border, heavier rules |
| `--accent` | `#e58355` | Soft rust accent for dark backgrounds |
| `--grain` | `.045` | Slightly stronger grain in dark mode |

- Browser `theme-color`: `#070706`
- Text selection: background `#e58355`, text `#070706`

### Contrast (WCAG ratios)

| Pair | Ratio |
|---|---|
| Light ink on background | 15.13:1 |
| Light muted on background | 5.86:1 |
| Light accent on background | 5.54:1 |
| Dark ink on background | 15.76:1 |
| Dark muted on background | 7.20:1 |
| Dark accent on background | 7.40:1 |

All body and secondary text pass AA. The accent is used for small text and
non-text marks; it also passes AA on both backgrounds.

### Accent rules

- Rust is the only accent. No second accent colour.
- Blue is never used, in either theme.
- Accent appears on: the full stop after "Prince Kumar", section numbers,
  bullet markers, the "Currently" rule, hover states, focus rings, selection.

### Paper grain

`body::before` is a fixed, full-viewport overlay containing a monochrome SVG
`feTurbulence` noise texture (`baseFrequency 0.85`, 2 octaves). It is
`pointer-events: none`, sits above content (`z-index: 100`), and uses
`opacity: .032` light / `.045` dark. Hidden when printing.

---

## 2. Typography

Three system font stacks — no web fonts, nothing to load.

| Role | Stack |
|---|---|
| Serif (display) | `"Iowan Old Style", "Palatino Linotype", Palatino, "Book Antiqua", Georgia, serif` |
| Sans (body) | `-apple-system, BlinkMacSystemFont, "Segoe UI", Roboto, Helvetica, Arial, sans-serif` |
| Mono (labels) | `ui-monospace, SFMono-Regular, Menlo, Consolas, "Liberation Mono", monospace` |

Headings use the serif at **weight 400**. Body copy uses the sans. Dates, labels,
navigation, buttons and metadata use the mono, usually uppercase with wide tracking.

### Type scale

Sizes are `rem` unless marked. 1rem = 16px in a default browser.

| Element | Font | Size | Weight | Line height | Letter spacing | Notes |
|---|---|---|---|---|---|---|
| Page body | Sans | `1rem` | 400 | `1.6` | normal | Base text |
| Hero name (`h1`) | Serif | `clamp(3.2rem, 9vw, 6.6rem)` | 400 | `0.9` | `-.035em` | Mobile: `clamp(2.8rem, 12vw, 4.4rem)` |
| Hero eyebrow | Mono | `.68rem` | 400 | inherited | `.15em` | Uppercase, muted |
| Hero intro (`.lede`) | Sans | `clamp(1.03rem, 1.6vw, 1.18rem)` | 400 | `1.65` | normal | Max `42ch`; mobile `1rem` |
| Hero links | Mono | `.69rem` | 400 | inherited | `.1em` | Uppercase |
| Section number | Mono | `.66rem` | 400 | inherited | `.08em` | Accent |
| Section heading (`h2`) | Serif | `clamp(1.65rem, 3vw, 2.1rem)` | 400 | `1.1` | `-.02em` | |
| Fact card label | Mono | `.64rem` | 400 | inherited | `.16em` | Uppercase, muted |
| Fact term (`dt`) | Mono | `.62rem` | 400 | inherited | `.08em` | Uppercase, muted |
| Fact value (`dd`) | Sans | `.88rem` | 400 | inherited | normal | Right aligned |
| Resume link | Mono | `.64rem` | 400 | `1` | `.1em` | Uppercase |
| About paragraphs | Sans | `1.01rem` | 400 | `1.7` | normal | First paragraph `1.13rem`, max `66ch` |
| "Currently" label | Mono | `.64rem` | 400 | inherited | `.12em` | Uppercase, accent |
| "Currently" text | Sans | `.93rem` | 400 | inherited | normal | Muted |
| Education date | Mono | `.68rem` | 400 | inherited | `.05em` | Muted; mobile `.64rem` |
| Education title (`h3`) | Serif | `1.12rem` | 400 | `1.35` | normal | Mobile `1.05rem` |
| Education school | Sans | `.89rem` | 400 | inherited | normal | Muted |
| Score tag (`.mark`) | Mono | `.68rem` | 400 | inherited | normal | 1px border, 2px radius |
| Project title | Serif | `1.35rem` | 400 | `1.25` | normal | Turns accent on hover |
| Project copy | Sans | `.95rem` | 400 | inherited | normal | Muted, max `60ch` |
| Project tech / link | Mono | `.65rem` / `.75rem` | 400 | inherited | `.1em` / `.06em` | |
| Skill label (`dt`) | Mono | `.62rem` | 400 | inherited | `.13em` | Uppercase, muted |
| Skill value (`dd`) | Serif | `1.06rem` | 400 | `1.45` | normal | |
| Email link | Serif | `clamp(1.25rem, 3.2vw, 2rem)` | 400 | `1.2` | `-.02em` | Wraps if needed |
| Contact list | Sans | `.9rem` | 400 | inherited | normal | |
| Contact label | Mono | `.61rem` | 400 | inherited | `.1em` | Uppercase, muted |
| Footer | Mono | `.62rem` | 400 | inherited | `.08em` | Uppercase, muted |
| Nav links | Mono | `.67rem` | 400 | inherited | `.13em` | Uppercase; mobile `.7rem` |
| Theme/menu buttons | Mono | `.65rem` | 400 | `1` | `.11em` | Uppercase |

No italic, no bold headings, no letter-spacing on body copy.

---

## 3. Layout and spacing

| Token / rule | Value |
|---|---|
| Content width | `min(100% - 3rem, 1080px)` |
| Page gutters | 24px each side (desktop); 16px below 560px |
| Header height | 66px desktop; 60px at ≤760px |
| Sticky header | `top: 0`, solid background, 1px bottom border |
| Hero padding | `clamp(3.5rem, 8vw, 6.5rem)` top, `clamp(3rem, 6vw, 5rem)` bottom |
| Hero padding, mobile | `2.75rem` top and bottom |
| Hero grid | `minmax(0, 1.6fr) minmax(250px, .75fr)`, gap `clamp(2rem, 5vw, 4.5rem)` |
| Fact card | Dashed 1px border, padding `1.4rem 1.45rem 1.2rem`; mobile `1.2rem 1.2rem 1rem` |
| Section padding | `clamp(2.7rem, 6vw, 4.2rem)` top and bottom |
| Section separators | 1px solid `--line` above every section |
| Section scroll offset | `scroll-margin-top: 76px`; 68px mobile |
| Section heading row | number + heading + flexible 1px rule, gap `1rem` |
| About copy width | Max `66ch` |
| Education row grid | `8.5rem minmax(0, 1fr) auto`, gap `1.5rem`, `1.2rem` vertical padding |
| Skills grid | Two equal columns; odd items have a right border |
| Contact grid | `minmax(0, 1.25fr) minmax(0, .75fr)`, gap `clamp(1.5rem, 5vw, 4rem)` |
| Footer | 1px top border, padding `1.5rem` top / `2.5rem` bottom |

### Breakpoints

| Width | Behaviour |
|---|---|
| `≤ 860px` | Hero becomes one column; fact card max `26rem`; contact becomes one column; header actions pushed right; nav can wrap (non-JS fallback) |
| `≤ 760px` | Mobile header: 60px tall, "Menu" button appears, nav becomes a dropdown panel; hero name `clamp(2.8rem, 12vw, 4.4rem)`; hero padding `2.75rem`; section offset 68px; buttons at least 40px tall |
| `≤ 560px` | 16px gutters; brand name hidden (monogram only); education date and score share one line and the title spans full width; skills stack to one column; project stacks; "Currently" note stacks |

### Mobile navigation

- Below 760px the nav is hidden only when JavaScript is available
  (`html.js .site-nav`). With JS off, the links remain visible and wrap.
- The "Menu" button toggles `.is-open` on `#site-nav`.
- Button label switches between "Menu" and "Close"; the hamburger icon becomes an X.
- `aria-expanded` and `aria-label` are updated.
- The panel closes when a link is tapped, when Escape is pressed (focus returns to
  the button), or when the viewport grows past 760px.
- Panel background is solid `--bg` with a `--line-strong` bottom border; no shadow.

---

## 4. Components

### Header

- Sticky, solid background, bottom hairline.
- Left: a filled square monogram "PK" (mono, `.64rem`, ink background, background-coloured
  text) followed by the name in serif `1.05rem`.
- Centre/right: five mono nav links (About, Education, Projects, Skills, Contact).
- Right: theme toggle; on mobile also the Menu button.
- Hover: text goes to ink, bottom border goes accent.
- Mobile hides the text name, keeping only the monogram.

### Theme toggle

- 1px `--line-strong` border, 2px radius, transparent background.
- Moon icon + "Dark" in light mode; sun icon + "Light" in dark mode.
- Saves choice to `localStorage` under `pk-theme`.
- First visit follows `prefers-color-scheme`.
- Applied before first paint by an inline head script to avoid a flash.
- Updates `theme-color` meta and `aria-pressed`/`aria-label`.

### Hero

- Eyebrow: "B.Tech CSE · Second year · GLA University".
- Name "Prince Kumar." with a rust full stop.
- One short intro paragraph.
- Four inline links: GitHub, LinkedIn, LeetCode, Email (mono, uppercase, thin underline,
  arrow glyphs `↗` / `→`).
- Aside "At a glance" card with dashed border: Based in, Degree, CPI, Focus, Status,
  then "Download résumé ↓".

### Section headings

Number (`01`–`05`) in rust mono, serif title, then a hairline filling the remaining width.
Sections: About, Education, Projects, Skills, Contact.

### Lists and rows

- Education rows use a top strong border, bottom hairline, and mono dates.
- Score tags are outlined rectangles, not pills.
- Skills use a 2×2 grid with a vertical divider; values are serif, not tags.

### Links and focus

- Inline links: thin underline, accent on hover.
- Keyboard focus: `outline: 2px solid var(--accent); outline-offset: 3px`.
- Skip-to-content link appears at the top when focused.

### Grain, selection, scrollbar

- Grain overlay described above.
- Selection uses accent background and page background text.
- Scrollbar is native (no custom styling).

---

## 5. Motion

- Theme change: background and text transition over `.2s`.
- Nav and link hovers: `.15s`.
- Project arrow nudges up-right 2px on hover.
- Smooth scrolling via CSS, disabled under `prefers-reduced-motion: reduce`.
- All transitions effectively disabled under reduced motion.
- No scroll-reveal animations, no parallax, no hover tilt.

---

## 6. Résumé download

- The PDF is embedded directly in `index.html` as a base64
  `data:application/pdf` URI, using the **exact original file**.
- Original size: **24,244 bytes**; base64 payload: **32,328 characters**.
- Link attributes: `download="Prince_Kumar_Resume.pdf"` and `type="application/pdf"`.
- On click, JavaScript decodes the base64, builds a `Blob` with type
  `application/pdf`, and downloads it as `Prince_Kumar_Resume.pdf`.
- If that fails, the plain `data:` link is used as a fallback.
- The PDF is not recreated or edited — it decodes byte-for-byte to the supplied
  `Prince_Kumar_Resume.pdf` (SHA-256 verified).
- Because the file is embedded, the download works offline and does not depend on
  how a local server or preview app reports file types.

---

## 7. Content map

| Area | Content |
|---|---|
| Name | Prince Kumar |
| Role line | B.Tech CSE · Second year · GLA University |
| Location | Mathura, Uttar Pradesh, India |
| Email | princekumar769603@gmail.com |
| Phone | +91 76960 34774 |
| GitHub | github.com/princekumar-01 |
| LinkedIn | linkedin.com/in/prince-kumar-399451443 |
| LeetCode | leetcode.com/u/princejaat |
| Education | B.Tech CSE, GLA University, 2025–2029, CPI 8.22; Intermediate, Army Public School, 2024–2025, 70%; High School, Army Public School, 2022–2023, 85% |
| Project | Online Food Delivery App (Java) |
| Skills | Java, C; data structures & algorithms; Git, GitHub, VS Code; problem solving, time management |
| Footer | © 2026 Prince Kumar · Mathura, India · Hand-written HTML, CSS & JS. No framework. |

Content order follows the résumé: Hero → About → Education → Projects → Skills → Contact.

---

## 8. Design rules (keep these intact)

1. No blue, indigo, violet, or teal.
2. No gradients, glows, glassmorphism, or drop shadows.
3. No rounded pill buttons; radius stays at 0–2px.
4. Serif for display, sans for reading, mono for labels and dates.
5. Rust accent used sparingly, never as a large fill except selection and the monogram.
6. Hairline rules and whitespace organise the page instead of boxed cards.
7. Dark mode is true black (`#070706`), not dark grey-blue.
8. Every interactive element needs a visible keyboard focus state.
9. Keep it a single HTML file with no external dependencies.

---

## 9. How to change things

- **Colours:** edit the variables at the top of the `<style>` block under `:root`
  and `:root[data-theme="dark"]`.
- **Fonts:** change `--serif`, `--sans`, `--mono`. No imports needed if using system fonts.
- **Content width:** change `--wrap`.
- **Accent:** change `--accent` in both themes; check contrast afterwards.
- **Résumé:** replace the base64 payload in the `.resume-link` href, or point the href
  back to `Prince_Kumar_Resume.pdf` and remove the click handler.
