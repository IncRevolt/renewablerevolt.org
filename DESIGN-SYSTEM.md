# Renewable Revolt — Design System Reference

**Canonical source of truth for color tokens and the per-line signature system.**
Last updated: 2026-11-24 (v20).

> **How tokens live today.**  The site is static (GitHub Pages, no build step), so
> every page defines its palette inline in its own `<style>:root{…}`.  There is no
> shared stylesheet.  This file is therefore the *documentation* source of truth —
> the list to copy from and keep pages in sync with — not a technical import.  When
> a token changes, it must be updated in each page's `:root` (see "Token block
> variants" below).  Collapsing to a shared stylesheet is a larger refactor, tracked
> separately.

---

## 1. Functional tokens (the working UI — leave their *meaning* alone)

These drive buttons, states, borders, headings, and emphasis across the site.

| Token | Value | Role |
|---|---|---|
| `--black` | `#07080c` | Page background |
| `--surface` | `#0e0f16` | Cards / panels |
| `--surface2` | `#141620` | Raised panels |
| `--border` | `#1e2035` | Hairlines, dividers |
| `--text` | `#e8edf2` | Body text |
| `--muted` | `#ccd8e4` | Secondary text |
| `--dim` | `#8a9ab8` | Tertiary / captions |
| `--purple` | `#9F63E3` | Primary brand accent (nav, logo) — distinct from Nightmare |
| `--royal` | `#7c3aed` | Deep purple |
| `--plum` | `#a855f7` | Bright purple (Marauder card theme) |
| `--green` | `#10B981` | **Gaming / action accent** (CTAs) — cooler, distinct from Fleet |
| `--cyan` | `#00E5FF` | **AI / tools accent — DO NOT REPOINT** |
| `--amber` | `#ffab00` | Warning / highlight |
| `--red` | `#ff4444` | Error / villain |

**Extended purple palette** (present only on the 7 "themed" pages — cooling,
is-it-real, lighting, mission, recover, revive, why): `--amethyst #9b59b6`,
`--imperial #6d28d9`.  These pages also carry a legacy `--revenant #8b5cf6` token
that is **defined but never referenced** — a dead token, cleanup candidate, and
*not* to be confused with the new `--sig-revenant` below.

Fonts: `--mono` Space Mono · `--sans` DM Sans · `--disp` Syne.

---

## 2. Per-line signature tokens (v20 — product-line identity)

Each product line carries a signature color with **two values that need not match**:

- **Fan hex** — the color set in firmware as the default on the Nollie RGB controller
  (the boot/loop canvas the fans power on to, before any per-customer profile).  Chosen
  to *glow* on the LEDs: deep, bold, saturated.  Pale colors wash out on the fans.
- **Site hex** — the `--sig-*` token in every page's `:root`, chosen to *read* on our
  near-black background (`#07080c`) and to echo the fan color without having to equal it.
  The signature should **feel like** the line, not color-match the firmware.

These are a **separate namespace** from the functional tokens in §1.

| Token (site) | Site hex | Fan hex (firmware) | Line | Status |
|---|---|---|---|---|
| `--sig-fleet` | `#00E676` | `#00E676` | X99 Fleet (workstation) | **LOCKED** — fan = site |
| `--sig-nightmare` | `#8B5CF6` | `#9D1BE0` | Nightmare (X79) | **LOCKED** (v20) |
| `--sig-lostlake` | `#8CCEE0` | `#1600C0` | Lost Lake (gaming) | **LOCKED** (v20) |
| `--sig-revenant` | `#E8601C` | *TBD — fans first* | Revenant | **PLACEHOLDER** |
| *(Phantom)* | *TBD* | *TBD — fans first* | Phantom | **FUTURE** |

Notes:
- **Fan-first, then derive the site value.**  Lock the firmware color on the LEDs, then
  pick the legible on-screen echo.  Nightmare's fan `#9D1BE0` (the boldest-glowing royal
  purple) pairs with the site's original royal purple `#8B5CF6` — the hex already live on
  GitHub and baked into every machine's banner art, so the site stays consistent with the
  art.  Lost Lake's fan `#1600C0` (deep indigo) is 1.7:1 on our background — unreadable as
  text — so the site keeps the original washed-out blue `#8CCEE0`, and the **product photo**
  carries the true fan color on the index.
- **Brand vs. functional are distinct colors**, never shared hexes: Fleet brand `#00E676`
  vs. functional green `#10B981`; Nightmare brand `#8B5CF6` vs. functional/site purple
  `#9F63E3`; Lost Lake brand `#8CCEE0` vs. tools cyan `#00E5FF`.  Never point a functional
  element at a `--sig-*` token, or a brand element at a functional one.
- `--sig-lostlake` stays clear of the electric `--cyan #00E5FF`; keep the two cyans out of
  the same eyeline.
- `--sig-revenant` and Phantom are **placeholders** — their tones get dialed on the fans
  first, then a legible site value is derived.  No live text until then.

---

## 3. Reconciliation principle

Two color layers coexist and never share a token:

1. **Functional** — what an element *does* (a CTA, a warning, a gaming accent).
2. **Signature** — which *line* an element belongs to.

The per-line banner hooks and model-name tints reference the signature tokens;
everything else keeps its functional token.  As of v20 the two layers also use
**distinct colors** (see §2), so a brand element and a functional one never collide
even on the same page.  `--cyan` is never repointed.

---

## 4. Application rules

**Tier 1 — in-code, subtle (live as of v20).**
- The per-line banner wordmark eyebrow (`.class-col.<line> .wm-sub`) carries the
  line signature.  Live today on the index: Lost Lake eyebrow → `--sig-lostlake`,
  X99 Fleet eyebrow → `--sig-fleet`.
- Line-name text ("Lost Lake", "X99 Fleet", model names) may take the signature on
  text-only pages via a signature span.  (Revenant held until its tone locks.)
- **Less is more.**  One signature touch per view, on the *identity* element.  Never
  on functional UI — buttons, links, states, and card structure stay in the
  functional palette.

**Tier 2 — artwork, deferred (pending Nightmare + Revenant prototypes).**
- The banner illustrations (eyes, mist, weapons, water) are baked into flat JPGs and
  are **not** CSS-recolorable; tinting them means re-rendering the art per line.
- **Uniformity within a line:** pick one carrier per line (all eyes, or all mist) and
  keep it consistent.  Keep it a hint, not a wash.

**Uniform inclusion:** if one live line-banner gets its signature, the others live at
the same time move with it; future lines join when they ship as banners.

---

## 5. The homage principle

The reader should *feel smart making the connection* — we never say "Lost Lake is
blue."  The color is a quiet echo of the firmware fan signature, closer to homage
than branding.  Overall Renewable Revolt aesthetic is unchanged.

---

## 6. Accent discipline — the tools cyan `#00E5FF` (v20)

Cyan is the **AI/tools accent and the scarce "eyes-go-here" color.**  It had drifted
into a second body color (it was the nav, every eyebrow, every stat, both button
fills); v20 reclaimed it.  The rule: **cyan earns attention by scarcity.**

**Cyan is reserved for:**
- Hero / section **accent words** (`.hero h1 span`, `.accent`, `.sec-h2 .accent`).
- **Interaction states** — hover and focus (`:hover`, `:focus`, `:focus-visible`).
- **Primary & secondary buttons** — *outlined only, never filled* (`.btn-p` bold,
  `.btn-s` regular; both transparent bg, cyan border + text; fill only on hover).
- Genuine **AI/tools identity** (the AI page, tool callouts, the semantic
  `tag.tool` honest/myth/**tool** code).
- The **RR callouts** (`.dcap.rr`, `.dl-card.rr`), the compare page's **"our column"**
  highlight, real **hyperlinks**, and page **graphics/diagrams** (e.g. cooling's
  positive-pressure fan, the lighting RGB spectrum).

**Cyan is NOT used for** (these are neutral — `--dim` / `--muted` / `--text` / `--border`,
or `--purple` for brand marks): nav links at rest, eyebrows, section labels, stat
numbers, feature pills, table headers, tier-card borders, step numbers, bullet
markers, chevrons, arrows, footer brand.  No filled cyan blocks anywhere.

### Nav standard (all 17 pages, v20)
- Links **muted** at rest → **cyan** on hover → **amber** for the active page.
- `.nav-cta` ("Shop eBay"): neutral outline (`--muted` text, `--border`), cyan on hover.

### Button standard
- `.btn-p` (primary) and `.btn-s` (secondary): **outlined** in the context accent
  (cyan by default; `--green` / `--purple` where a page themes it), cyan/accent fill
  on hover only.  `.btn-p` is bold to carry primary emphasis without a fill.

---

## 7. The glow-homage framework (v20 — art)

The evolved model for line art: **theme first, homage after.**

1. **Each line has a visual theme**, held consistent across all its art (characters +
   banners): Lost Lake = a misty swamp / glowing water; X99 Fleet = a ghost fleet on
   luminous seas; Nightmare / Revenant / Phantom / Ironclad / Dreadnought to follow.
2. **The homage is added after the fact** — the art's glowing accents are nudged toward
   the line's color so the sharp viewer connects the art to the fans and the page without
   being told.  **Homage, not a match.**  Vibes.

### The locked recolor process (`glow_homage.py`)
A **saturation-weighted hue-shift** of the luminous accent band: only the saturated glow
(eyes, runes, weapon edges, waterline, gunports) rotates to the target hue; the
low-saturation atmosphere stays put, so the theme survives.  Params: accent band hue
150–210°, S>0.22, V>0.33; move weight ramps 0→1 across S 0.30–0.62; S×1.08; V preserved.
This generalizes the first ship test (a plain global shift worked there only because the
ship carried little teal to bleed).

**Target hue is the line's *site/banner* blue, not the raw fan hex** — so the character
glow, the banner title, and the page accent are one color.  Lost Lake's fan is `#1600C0`
(247°, indigo), but the site/banner blue is `#8CCEE0` (**hue 193°**), and that is the glow
target.  (247° purples the art; a 228° royal reads as a separate, deeper blue.  Matching
the banner unifies the line.)  Saturated pieces (the Ringer) take a **tighter mask** — raise
`smin`/`vmin` and the `s_lo`/`s_hi` ramp — so only the hottest glow (weapon, eyes) moves and
the theme is untouched, matching the subtler pieces.

### Applied so far (v20)
- **Lost Lake characters** (`knight_gamer`, `knight_gamer_upgrade`): glow → 193° banner-blue,
  swamp kept; the Ringer on a tight mask (weapon/eyes only).  Future Ironclad + Dreadnought
  characters (already present in the Fleet banner art) use the same locked process at their
  line's target.
- **Banner titles carry the homage, not the banner art.**  Reglowing a hazy banner
  (cl_art) over-purples the whole frame, so the banner *art* stays themed and the overlaid
  **title text** takes the color: Lost Lake title → `--sig-lostlake #8CCEE0`; X99 Fleet
  title → **`#22AEC3`**, the ghost-sea blue-green sampled from the Marauder art (the Fleet
  art-accent; banner title only — the green `--sig-fleet` stays on the sub-label + border).
- Backups of all original art are kept before any recolor.

---

## 8. Product-photo standard (LOCKED site requirement)

Applies to every lineup card — the current two and every line added later (Nightmare,
Revenant, …).  Two cards must never disagree on photo size or photo position.

**Size & framing.**
- Every product photo is authored at **4:3** and shows the **whole machine** — no
  zoomed-in crop.  The card slot is `.machine-photo{aspect-ratio:4/3}` with
  `img{object-fit:cover}`; because the image is already 4:3, cover fills it with no crop.
- A photo shot in a lit room is **background-removed** (`rembg`) and the machine is padded
  onto a 4:3 field (black/transparent) so it still reads whole and floats on the card.
  Best capture is a **dark room** (no background to remove) — that produced the Gamer shot.
- A transparent cut-out is exported alongside so the **eBay** listing matches the site.

**Position.**
- The photo sits at the **same vertical position** across cards, independent of blurb
  length.  The variable-height `.class-hook` (kick + heading + blurb) is equalized to the
  tallest so every photo starts at the same Y when the cards are side by side (they stack
  below 768px, where alignment is moot).  Implemented by `equalizeHooks()` on
  load/resize/font-ready; any slack lands as trailing space at the card bottom.
- **Requirement:** keep this behavior when adding cards — do not give a card a fixed-height
  hook that breaks the equalizer, and keep every product image authored at 4:3.

---

## 9. Lineup structure & ordering (LOCKED site requirement)

**Lines flow horizontally, left to right, in a fixed order:**

> **Revenant · X79 Nightmare · Lost Lake · X99 Fleet**

As lines ship they slot into that order (Revenant + Nightmare join to the *left* of Lost
Lake).  The two live lines (Lost Lake, X99 Fleet) are already in correct relative order.

**Within a line, models stack vertically, sorted by price — lowest on top.**
Lost Lake: Coffee Lake Gamer ($849) above Coffee Lake Ringer ($1,499).

### Markup
```
.classes (grid)
  └─ .class-line.<line>            one column per line
       ├─ .class-banner            the line header (banner art + title) — ONCE per line
       └─ .class-col               a model card (hook + 4:3 photo + buy + accordion)
           .class-col              …another model, next price up
```
- The **banner appears once** per line, as the header; it is no longer inside a model card.
- Each **model card** carries the line's signature as a 3px top border
  (`.class-line.<line> .class-col{border-top:…}`), so stacked models still read as one line.
- Photo size + position rules from §8 still hold across every model card.

### Placeholder photos
A model without its own build photo yet reuses a sibling's photo dimmed, with a
**"Picture coming soon"** overlay: `.machine-photo.soon` + `<span class="photo-soon">`.
(Current: the Ringer borrows the Gamer shot until Andrew builds the first unit.)

### Open item when all four lines ship
Four lines side-by-side is tight on desktop — decide then between a 4-wide row and a 2×2
grid (`.classes` is `1fr 1fr` today).  Not a blocker for two lines.

*(Cleanup note: the old `.gamer-up*` CSS rules are now unused — the upgrade block became
the Ringer card — and are safe to delete whenever convenient.)*
