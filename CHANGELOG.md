# Renewable Revolt — Site Changelog

Record of changes to renewablerevolt.org, newest first.
Baseline: **v10** (last version deployed to GitHub).

---

## v22 — 2026-11-25–26 (glow-homage across both live lines + native-speed memory spec)

Character art now carries the line-signature glow on **all three live machines** — the
grey-green world is shared, each line keyed by its own color (DESIGN-SYSTEM §7).  Plus a
memory-spec correction on the Coffee Lake pair.

- **Character art finalized — Gamer + Ringer now one bloodline.**  The Coffee Lake
  Ringer's portrait is locked (`knight_ringer.png`): the heavy, broad fighter from
  Andrew's scaled-back, positive-only prompt — grey-green midnight bayou, pale clouded
  moon over the shoulder, weathered dark plate, a blue-glowing war-axe knee-deep in black
  water, with the eyes rotated to that same blue (218°) so the glow reads as one color, not
  axe-blue over cyan eyes.  The Coffee Lake Gamer (`knight_gamer.png`) was re-matched to
  share that world: its swamp cast nudged off teal (~185°) onto the Ringer's grey-green
  (~171° median) and its axe and eyes re-blued, so the two read as the same knight — the
  Gamer leaner, the Ringer the heavy upgrade.  Same filenames, so no index markup change;
  the two files just swap in.  Produced on the locked glow-homage workflow (two-pass:
  darken to the mood, then blue the accents under a tight mask).  Verified: 0 JS errors,
  both images load, 0 overflow at 360/768/1280.
- **Marauder brought into the same world — Fleet green glow (`ship_marauder.png`).**  The
  ghost galleon's cool blue-slate night was smoothed to the knights' muted grey-green
  atmosphere (same dark, misty, pale-moon world) and darkened to match their mood
  (L ~0.123).  Its cyan gunports and waterline bioluminescence were rotated to **Fleet
  "gamer green"** (`--sig-fleet #00E676`, ~150°), the glow kept bright and saturated while
  the fog stays muted — so the ship reads as the same world as the Lost Lake knights but
  carries the Fleet's own green energy (blue knights, green ship).  Single hue-map
  (atmosphere → grey-green, bright/saturated glow → green) since the gunports and fog were
  nearly the same blue and couldn't be split by hue alone.  Same filename; original cyan
  art backed up in scratch.  Verified: 0 JS errors, image loads.
- **Banners brought into the same world + titles matched to the art.**  The two live banner
  illustrations (`cl_art.jpg`, `fleet_art.jpg`) were run through the same recolor as the
  characters: muted grey-green atmosphere, line-colored glow — Lost Lake's swamp with blue
  water glints (matching the knights), the Fleet's sea with green bioluminescent wakes
  (matching the ship).  Each banner's **title text** was then pointed at its line's character
  accent: **"Lost Lake" → character blue `#4588E6`** (was the washed-out `--sig-lostlake
  #8CCEE0`), **"X99 Fleet" → Fleet green `--sig-fleet #00E676`** (was the ghost-sea
  `#22AEC3`), so the title now reads in the same glow as its art.  Title color is live text,
  so this is the one small **`index.html`** change this round — scoped to the two banner
  titles only; the card top-borders and the body model-name tints still use the softer
  `--sig-lostlake`, a quick sitewide token sweep whenever full coherence is wanted.  Original
  banners backed up in scratch.  Verified: 0 JS errors, banners render.
- **Memory spec corrected to native 2666.**  Both Coffee Lake machines now list **32GB
  DDR4-2666** — the platform's rated speed.  The Gamer had read DDR4-3200 (an XMP /
  memory-overclock figure) and the Ringer carried no speed at all; 2666 is the real Coffee
  Lake ceiling and we don't overclock the RAM, so the spec now states what the machine
  actually runs.  Fixed everywhere it appears — **index, compare, and is-it-real** (Gamer
  and Ringer both).  The **X99 Marauder is untouched** (different platform, different
  memory ceiling — its generic "DDR4" is correct).  eBay listings updated separately by
  Andrew.
- *(Housekeeping: `knight_gamer_upgrade.png` is referenced nowhere — safe to delete on
  GitHub.  The Ringer's build-photo placeholder ("Picture coming soon") stays until the
  first unit is photographed.)*

---

## v21 — 2026-11-24 (lineup structure: lines + stacked models)

Systematized the lineup so adding models/lines is mechanical, not a rebuild (DESIGN-SYSTEM §9).

- **Lines → columns, models → stacked cards.**  `.classes` columns are now **lines**
  (`.class-line`), each with its banner as a one-time header and its model cards
  (`.class-col`) stacked beneath.  The banner is no longer baked into a model card; each
  model card carries the line's signature as a 3px top border.
- **Ordering rules (locked).**  Lines flow left→right: **Revenant · X79 Nightmare · Lost
  Lake · X99 Fleet** (the two live lines already in correct order).  Within a line, models
  sort by price, lowest on top.
- **Coffee Lake Ringer is now its own card** ($1,499), stacked under the Gamer, built from
  Andrew's existing Ringer copy (lifted out of the Gamer's accordion upgrade block, which
  was removed).  Until the first unit is built, it reuses the Gamer photo dimmed with a
  **"Picture coming soon"** overlay (`.machine-photo.soon`).
- Row-1 photos (Gamer / Marauder) stay size- and position-locked per §8; the Ringer sits
  below the Gamer as its own row.  Verified: 0 JS errors, 0 overflow at 360/768/1280.
- *(The old `.gamer-up*` CSS is now unused — safe cleanup later.)*
- **"Two machines" → lineup cleanup.**  With three machines live, swept stale copy sitewide: hero button + CTAs → "See the Lineup" (index, ai, rr-turbo); hero stat `2 Models ready now` → `3 Models in the lineup`; section title → "Three machines. Two different animals."; and count fixes on cooling/mission/revive/why ("both machines" → "every machine", "two" → "three").
- **Per Andrew's calls:** compare.html kept as the 2-way flagship spec sheet (unchanged); the **Is-It-Real prompt + fact sheet now cover all three** — "both machines" → "all three machines," and a **Coffee Lake Ringer** spec block added (i7-8700K / RTX 3060 12GB / 32GB, $1,499), grouped with the Gamer; the **hero prose stays "two machines"** (Gamer + Marauder) by design.  The Ringers are for sale on eBay now (5-business-day handling), being built 2026-11-25.
- **Truth-in-advertising pass on the will-it-revolt verdicts (2026-11-26).**  Folks read these literally, so two tier blurbs were tightened to stop implying bad habits or impossible loads.  **Green ("Revolts well")** dropped "keep a pile of tabs and apps open and it keeps up" — it now says the machine multitasks well but tells the reader to close finished tabs and bookmark the rest ("good habits keep any machine fast").  **Amber ("entry tier")** dropped "as long as you're not juggling a dozen heavy apps at once" (a dozen heavy apps chokes *any* machine) — it now states the honest limit: 100% usable one job at a time, slows if you're a tab fiend or stack two heavy apps (concrete example: a video call at the same time as a browser full of tabs).

---

## v20 — 2026-11-23–24 (per-line signature colors — Tier 1 infrastructure)

Foundational work to give each product line a signature color — set in firmware as the Nollie RGB controller's default fan color and echoed *subtly* into the website, closer to homage than branding.  The reader should feel smart making the connection; we never say "Lost Lake is blue."

- **Signature token layer (new `--sig-*` namespace).**  Added four per-line tokens to every page's `:root` (all 17): `--sig-fleet #00E676` (LOCKED, Nollie default), `--sig-nightmare #8B5CF6` (LOCKED), `--sig-lostlake #8CCEE0` (LOCKED this version), `--sig-revenant #E8601C` (PLACEHOLDER — tone not final, defined but not applied to live text).  Kept as a separate namespace so a line's color can move independently of the functional accents.
- **Reconciliation — two color layers, no global repoint.**  Functional tokens (`--green` gaming accent, `--cyan` AI/tools accent, `--purple`/`--plum`) keep their jobs untouched.  `--cyan #00E5FF` deliberately left alone, and `--sig-lostlake` is a softer, desaturated blue-cyan so the two never collide.  `--sig-fleet`/`--sig-nightmare` share hex values with `--green`/`--purple` but stay separate tokens; green now reads as both the gaming accent and the Fleet signature (accepted — they live in different contexts).
- **DESIGN-SYSTEM.md created** as the canonical source of truth for all tokens + the signature system, with lock/placeholder status and the Tier 1 / Tier 2 application rules.  (Tokens still live inline per page; this is the documentation to keep them in sync.)
- **Index cards — signature treatment finalized.**  Each card reads top-to-bottom in its line signature with a neutral body.  The 3px top border and the banner eyebrow carry the signature (Lost Lake cyan `--sig-lostlake`, X99 Fleet green `--sig-fleet`); the bold body text (kicker, hook heading, char-tag) drops the old per-model green/plum and returns to site-standard (`--dim` / `--text`).  Result: top border → eyebrow → product-photo fan color all agree, and the subtle eyebrow is no longer washed out by bold colored text directly beneath it.  (A new cyan-fan Lost Lake product photo is pending from Andrew to complete the match on that card.)
- **Flagged, not changed:** a legacy `--revenant #8b5cf6` token sits in the 7 themed pages' `:root`, defined but never referenced — dead, and a cleanup candidate (distinct from the new `--sig-revenant`).
- **Tier 2 deferred.**  Banner illustration tints (eyes, mist, weapons, water) are baked into flat JPGs, not CSS-recolorable — they need new art renders, held until Nightmare and Revenant prototypes exist.
- **Verified:** 0 JS errors, 0 overflow at 360px and 1280px across all 17 pages.

### 2026-11-24 — fan colors locked on the LEDs, site values reconciled

Andrew ran the firmware colors on the actual Nollie-controlled fans.  Key finding: **pale colors wash out on the LEDs** — the fans need deep, bold, saturated hues to glow, which is the opposite of what reads on a near-black webpage.  So each line now carries **two values: a fan hex (firmware) and a site hex**, and they need not match (DESIGN-SYSTEM §2 rewritten).

- **Nightmare — LOCKED.**  Fan `#9D1BE0` (the boldest-glowing royal purple of the test set — the one that stays most distinct on the LEDs).  Site signature returned to the **original royal purple `#8B5CF6`** — already live on GitHub and baked into every machine's banner art, so the site stays consistent with the art.  `--sig-nightmare` moved `#7863E3` → `#8B5CF6` across all 17 pages (token is staged, not yet wired to any live element, so zero visual change until the line ships).
- **Lost Lake — LOCKED.**  Fan `#1600C0` (darkest legible indigo on the LEDs).  That hex is 1.7:1 on `#07080c` — unreadable as text — so the **site signature keeps the original washed-out blue `#8CCEE0`** (no token change) and the **product photo carries the true fan color** on the index.
- **Lost Lake index photo replaced** — new blue-fan build shot (`img/photo/gamer-build.jpg`, 1100×682), cropped to the glowing fans and lightly optimized; the previous backup is in scratch.
- **Phantom + Revenant** — both future lines follow the same discipline: dial the tone on the fans first, then derive a legible site value.  No live text until then.

### 2026-11-24 — glow-homage framework (line art)

New model locked in DESIGN-SYSTEM §7: **theme the art consistently, then add the color homage after the fact** — nudge each piece's glowing accents toward the line color so the sharp viewer connects the art to the fans.  Homage, not a match.

- **Locked recolor process** (`glow_homage.py`, kept in scratch): a saturation-weighted hue-shift — only the saturated glow (eyes, runes, weapon, waterline) rotates to the target; the low-saturation atmosphere stays, so the theme survives.  Generalizes the first ship test (a plain global shift worked there only because the ship had little teal to bleed).  Reusable for the Ironclad + Dreadnought character pieces (already in the Fleet banner art).
- **Lost Lake characters** (`knight_gamer`, `knight_gamer_upgrade`): glow matched to the **banner blue, hue 193° / `#8CCEE0`** — so the character glow, the banner title, and the site accent are all the one Lost Lake blue.  (An earlier pass at the fan hue 247° purpled the art and a 228° royal read as a different, deeper blue; matching the banner unifies them.)  The **Ringer** uses a tight mask (weapon + eyes only) so it aligns with the Gamer's subtlety instead of washing the whole saturated scene blue.
- **Banner titles carry the homage, not the banner art** — reglowing the hazy `cl_art` banner over-purpled the whole frame, so banner art stays themed and the overlaid title text takes the color: Lost Lake title → `--sig-lostlake #8CCEE0`; X99 Fleet title → **`#22AEC3`** (the ghost-sea blue-green sampled from the Marauder art; green `--sig-fleet` stays on the sub-label + border).  Index only.
- **Product photos unified + Marauder isolated.**  New green Marauder build had its lit-room background removed and floated on the card's black (`marauder-build.jpg` → transparent `marauder-build.png`).  Both product photos standardized to a **4:3 frame showing the whole machine at an identical rendered size** (502×377 at desktop, matched at every breakpoint) via `.machine-photo{aspect-ratio:4/3}` + `object-fit:cover`.  The Gamer now uses its full 4:3 source (the earlier landscape crop was zoomed in); the Marauder square cut-out is padded to 4:3 on black.  A higher-res transparent cut-out was exported for the eBay listings so the site and eBay match.
- **Photo position locked (site requirement).**  Product photos now sit at the same vertical position across cards regardless of blurb length — the variable `.class-hook` is equalized (`equalizeHooks()` on load/resize/font-ready) so every photo starts at the same Y when cards are side by side (stacks < 768px).  Documented as a hard requirement in DESIGN-SYSTEM §8 (photo size + position) so Nightmare/Revenant cards drop in aligned.
- Original art + photo backed up before every change.  Verified: 0 JS errors, 0 overflow at 360/1280.
- **Tools-cyan reduction (Scope B — complete).**  Cyan (`#00E5FF`) had become a second body color (84 hits on cooling, the nav on every page, every eyebrow/stat/button); v20 reclaims it as a scarce "eyes-go-here" accent.  **(1) Buttons:** every filled primary button inverted to outlined across all 17 pages — `.btn-p` is now transparent + accent border + bold (cyan, or `--green`/`--purple` where a page themes it); no filled color blocks remain anywhere.  **(2) Nav:** standardized on all 17 pages — links `--muted` at rest, cyan on hover, amber for the active page, neutral outlined "Shop eBay" CTA (collapsed the old 3-font / 4-color inconsistency into one treatment).  **(3) Content:** eyebrows → `--dim`, stat numbers → `--text`, feature pills (`.badge.on`) → neutral outline, section labels / step numbers / bullet markers / chevrons / arrows / footer brand demoted to neutral; cooling's deep clean (decorative cyan → neutral).  **Kept (cyan earns these):** hero/section accent words, hover/focus states, hyperlinks, outlined buttons, the semantic `tag.tool` code, RR callouts, the compare "our column," and page graphics (cooling's fan, the lighting RGB spectrum).  **(4)** The "cyan is scarce" rule + nav/button standards are now locked into DESIGN-SYSTEM.md (§6).  Verified: 0 JS errors, 0 overflow at 360/1280 across all 17.
- **Search title/description reframed (v20 — done).**  The homepage `<title>` led with "Gaming PCs," burying the actual pitch.  Reordered to the brand's real priorities — privacy, affordability, local AI, then gaming: title is now **"Renewable Revolt — Demand more from your PC. Private local AI, no subscriptions."**  Meta description rewritten in the same voice, leading with ownership/privacy ("Stop renting your computer back from Big Tech… no subscriptions, no telemetry, no account"), then price (from $849), with gaming last ("And yes, they game").  (Note: search engines sometimes scrape body copy over the meta description — if the donation paragraph keeps surfacing, the next lever is the first visible paragraph.)
- **Brand/functional color separation (v20 — done).**  Now that the four line signatures are brands, their colors are pulled apart from the functional palette so brand use never blurs with UI use.  **Green:** functional `--green` moved from `#00e676` to a cooler, less-bold `#10B981` (186 token refs + 13 literals), leaving the vivid `#00E676` reserved for the **Fleet** signature — which also auto-fixed the is-it-real label blend.  **Purple:** functional/site `--purple` moved from `#8b5cf6` to `#9F63E3` (a distinct, warmer true-purple for the logo/nav identity), and **Nightmare** `--sig-nightmare` set to `#7863E3` (a blue-violet, clearly apart from the site purple, still unmistakably purple — chosen from a hue-ramp exploration rather than pinned to the old fan hex).  **Cyan/Lost Lake** were already distinct (`#00E5FF` tools vs `#8CCEE0` soft).  Both changes were clean token swaps because the `--sig-*` namespace was split from the functional tokens back in the signature work.  The brand-vs-functional rule and all new values are locked into DESIGN-SYSTEM.md (§1–3).  (The dead legacy `--revenant #8b5cf6` token still sits unused on 7 pages — remains a safe cleanup whenever wanted.)  Verified: 0 JS errors, 0 overflow at 360/1280 across all 17.
- **Model-name tinting (Tier 1 — done).**  The first prose mention of each model on each page now carries its line signature, bolded to register: **Marauder → Fleet green** (`--sig-fleet`), **Coffee Lake Gamer / Coffee Lake Ringer → Lost Lake cyan** (`--sig-lostlake`), via `.ln-fleet` / `.ln-lostlake` classes.  First mention only — repeat inline mentions stay neutral — across 10 pages (ai, compare, cooling, faq, index, is-it-real, mission, rr-ai, rr-turbo, why).  The copyable prompt `<pre>`, `<head>`, and scripts are protected, so only real prose/labels are tinted.  **is-it-real is now included** — with the tools cyan pulled back, the soft Lost Lake cyan no longer collides, so the pin is resolved.  Verified: 0 JS errors, 0 overflow at 360/1280.

## v17 — 2026-11-17
Mobile-nav fix across the whole site, plus two AI-prompt upgrades.

- **Mobile navigation fixed site-wide.** On phones the wide logo + "Shop eBay" CTA + hamburger overflowed the viewport, pushing the hamburger off-screen — the menu was unreachable (`toggleMenu()` itself was fine; this was pure layout overflow). Added a mobile nav rule to all 16 content pages: ≤768px tightens nav padding, shrinks the logo/CTA, and pins the hamburger (`flex-shrink:0`); ≤360px hides the CTA so the smallest phones still fit. Verified 320–414px — hamburger visible, menu opens on tap, no page overflow, zero JS errors.
- **is-it-real.html — final RRP + TCO prompt DEPLOYED.** Replaced the live Step 0–4 prompt with the product-chat-validated final (`is-it-real-prompt-RRP.md`, validated across ~20 skeptical-AI runs). Adds: an OPERATING STANCE preamble (incentive-map every source *both* ways — pro-"buy new" and pro-"buy mine," our own sheet included; never answer from training — verify against today's market; mechanism over "newer"; symmetry + steelman); Step 0 may read our compare/why pages under the same suspicion; a 4th report axis **Step 5(d) 3–5yr TCO** run symmetrically (subscriptions avoided, RAM-as-insurance, upgrade path/repairability, hidden cost of compromised components — and the newer box's remaining life/warranty/runway credited back); the socket-ceiling check now includes the **server-Xeon HEDT path** (corrects the earlier "HEDT = dead-end" error); Step 5b now also asks the cheapest way to confirm a deciding fact; Step 6 splits the frames-buyer vs TCO-buyer pick. Copy button simplified to plain innerText. **Updated same day:** added the **single-machine branch** — if a visitor pastes only our machine with no competitor, the prompt runs a standalone fitness audit + a 2–3-machine cross-shop shortlist (and says plainly if their use needs more than the machine gives) instead of stalling on a dangling "paste the competitor." This was the biggest gap the zero-context agent runs found, since most real visitors arrive with one machine and a mission.
- **upgrade.html Upgrade Advisor prompts reworked (deployed).** Ported the is-it-real discipline to the laptop + desktop prompts: (1) never price parts or repair labor from training — verify against current listings/quotes, give ranges + confidence (late-2026 shortage makes remembered prices too low); (2) "old is not a verdict" — replace a part only when it actually bottlenecks the user's use. Wi-Fi judged by streams, not the label (MIMO Wi-Fi 5 is fine; single-stream/older → 6/6E/7 is a real win). Desktop GPU: don't replace a working 4–6GB card unless it's bus-limited (PCIe x4 trap) — check interface width, not just VRAM. Aligned the page's Wi-Fi dropdown + worked example and flagged the worked-example prices as illustrative. Kept in sync with `RR-Upgrade-Advisor-prompts.md`.
- **compare.html — new "The Long Game" section (deployed, RRP-validated framing).** Added a forward-looking value section between Balance and the 3-year receipt: the Revolt win isn't today's FPS — it's TCO and device longevity. Three accordions, each scoped honestly after the RRP/TCO review flagged two earlier drafts as misleading: (1) **RAM insurance** — 32GB pre-bought now, the part getting hardest/costliest to add (both review agents rated this TRUE); (2) **the right GPU for today, room to grow** — a capable 1080p card with no compromise on RAM/cooling/PSU, and the Gamer's CPU swap scoped to *pairing with a future GPU so it isn't bottlenecked* (one generation: i7-8700/9700/i9-9900), NOT an open-ended platform "runway" (LGA1151 dead-ends at the i9-9900K); (3) **the real multi-core runway is the X99 Marauder** — LGA2011-3 takes recovered server Xeon E5-2600 v4 (up to 22 cores, once $4,000+, now tens of dollars), the e-waste thesis made concrete, scoped to multi-threaded workstation/content/local-AI work, explicitly NOT single-thread gaming. Closing callout reframes the private AI to **privacy, not dollars** (no account/telemetry/subscription) — the overstated "save $X on AI" implication removed. **Final-reframes update:** the Marauder accordion now shows BOTH HEDT upgrade branches per the product-chat doc — the balanced consumer-HEDT step (i7-6850K → i7-6900K / i7-6950X, more cores, single-thread comparable) and the max-core Xeon step — and the Office line tightened to "a perpetual Office 2019 Pro+ licence" (no "always current" implication). **TCO reconciled to match:** the "three-year receipt" no longer banks the cloud-AI subscription as hard dollars — it's now a conditional "only if you'd pay for one (~$240/yr)," so the honest comparison is **$949 owned vs $1,449 rented** (PC + Office), with AI value carried on privacy/ownership, not a guaranteed saving. (Per Andrew: Office 2019 Pro+ is full-featured and safe — no EOL/"it's unmaintained" language on the page, which would be FUD for a 365 subscription.) **VR honesty lines added** to both Honest-Limits accordions (the product-chat's Claim 4 / VR to-do): the Gamer (6GB 1660) and Marauder (8GB 1070) are stated plainly as **not headset/Quest-3-class VR machines**, and demanding VR flight sims (MSFS/DCS) are correctly attributed to the **single-thread CPU limit on the LGA1151 platform, not the graphics card**. (Pricing/SKU-model changes in those docs intentionally left out per Andrew.)
- **CL Gamer upgrade package added (index + compare).** Per Andrew's decision to offer an *upgrade package* rather than a new model: the Coffee Lake Gamer now has a **Full upgrade — $1,499 total** that swaps in an **i7-8700K (6C/12T) + RTX 3060 12GB** (same chassis, 32GB, cooler, and the existing 650W PSU — no PSU change needed). Added to the index Gamer card as an Upgrade spec row + a "Built to grow" prose line + a dedicated **visual upgrade section** at the bottom of the card's dropdown — new character art (`img/characters/knight_gamer_upgrade.png`, the upgraded cyan-glowing knight) with a cyan-accented highlight list (i7-8700K, RTX 3060 12GB → 1440p/DLSS/CUDA, the bigger local AI, and the VR floor for lighter sims) and a clean-swap note. (Replaced the earlier text-only footnote so the upgrade story isn't told twice.) The compare "Long Game" GPU accordion names this real package (1440p, DLSS, 12GB for the bigger local AI) in place of the earlier hypothetical 3070 Ti / i9-9900K example. (Pricing is Andrew's own explicit call, not from the product-chat docs.) The Gamer's honest-limits VR bullet now closes the loop: the upgrade's RTX 3060 12GB clears the graphics-card VR floor for lighter headset sims, while demanding MSFS/DCS in VR stays CPU-capped on LGA1151 — upgrade and caveat read as one consistent story.
- **sitemap.xml** — all lastmod refreshed to 2026-11-17 (every content page got the nav fix).
- **GitHub-alignment pass (repo changes → site links).** Matched the live site to the Nov 17 GitHub updates: fixed the **RR Tune-Up download** to its real release tag — `rr-turbo-update/releases/download/rr-tuneup-v1.0.0/RR-TuneUp.zip` (the site had `v1.0.0`, which would 404); updated **Will-It-Revolt's run step** from the stale `run.bat` to **`Will-It-Revolt.bat`** (matching the live GitHub release's "How to run it"; the download link was already correct — repo `Will-it-Revolt`, tag `v1.0.0`, asset `Will-It-Revolt.zip`); and repointed every **`R-R-Turbo` repo link → `rr-turbo`** (the repo rename) across compare, index, mission, revive, rr-turbo, and why, plus "R-R Turbo" → "RR Turbo" display text on recover/revive. The Apache→PolyForm relicense needs no site change (no page states the updater's license). *(Confirmed from GitHub screenshots: tag `v1.0.0`, asset `Will-It-Revolt.zip` — link good. Note for GitHub cleanup: the repo source file is still named `Run.bat`, so the zip's launcher, the release notes, and the site should all be made to agree on one name.)*

## v18 — in progress (the Coffee Lake Ringer — third model)
Adding the i7-8700K + RTX 3060 12GB machine as a third, **low-volume** model named the **Coffee Lake Ringer** — not a "bundle" (no headset/accessories included), and with **no head-to-head / no comparison** per Andrew.

- **GitHub fallback links under every download button (2026-11-21).** Added a small cyan "Link not working? Open the <product> release on GitHub →" line under each of the five direct-download buttons — RR Tune-Up and the 25H2 Update (rr-25h2.html), Will-It-Revolt (will-it-revolt.html), and both RR Checkup buttons (upgrade.html). Each points at that product's GitHub *release page* (the tag page, which is guaranteed valid because its asset resolves 200), so if a direct-asset link ever rots again — e.g. during a repo cleanup or retag — users (and auditing AIs) always have a working path to the file. Product named in each link so it stays unambiguous where a button sits in a row. Verified: 0 JS errors, no overflow at 360px, all five present.
- **RR Tune-Up download 404 — fixed (live-test finding, 2026-11-20).** The "Download RR Tune-Up" button on rr-25h2.html pointed at tag `rr-tuneup-v1.0.0` — the *suggested* tag from the release notes, which was never actually applied. The live release is tagged **`v1.0.0`** with asset **`RR-TuneUp.zip`**, so the button 404'd (my own error from the v17 GitHub-alignment pass — I pinned the suggested tag instead of the real one). Corrected the href to `.../releases/download/v1.0.0/RR-TuneUp.zip`. Verified against live GitHub: old URL → 404, new URL → 200. **Swept all four download links site-wide while here** — RR Tune-Up, the 24H2→25H2 Update (`24H2_to_25H2` / `rr-turbo-update-24H2-to-25H2.zip`), Will-It-Revolt (`v1.0.0`), and RR-Checkup (`v1.0.0`) — all now return 200.
- **Name lock + de-bundle (done).** Renamed all the v17.2 "VR Bundle" copy to **Coffee Lake Ringer** across index.html and compare.html, and removed every "bundle" (including a stray verb on compare). Framed as a separate, low-volume model listed and priced on its own — not an add-on to the $849 Gamer.
- **404.html — made lineup-agnostic (done; applies to v17 too).** Dropped the hardcoded count and model names: meta + body "We build **two machines** from proven hardware the industry wrote off—the Coffee Lake Gamer and the Marauder" → "We build **machines** from proven hardware the industry wrote off." Count-free so it never goes stale as the lineup changes (Andrew's call to future-proof it rather than hardcode "three").
- **1440p-agent-run punch-list — on-site fixes done (2 of 7).** Six independent AIs ran the live Is It Real prompt against the Ringer and all stayed honest, but every tier flagged the same credibility gaps on *our own* pages. Two were fixable on-site now without inventing facts: **(#5) 501(c)(3) made verifiable** — the EIN was static footer text on every page (so agents rated nonprofit status UNVERIFIED); it's now a dotted-underline link to the IRS Exempt-Organization lookup (`apps.irs.gov/app/eos/`) on all 17 pages, matching the link faq.html already carried. **(#4) hand-wavy photo caption tightened** — "Example build · config may vary" (index Gamer + Marauder shots) → "Representative photo · listed specs or better; exact part brands may vary," which kills the "will I get a downgrade?" read and discloses brand-level variance honestly (storage can only go *up* from the listed floor, per Andrew's sourcing). Verified: 0 JS errors, no overflow at 360px, EIN links present.
- **Punch-list — warranty + bench-verified now stated on-site (#1, #2; Andrew supplied the facts).** **(#1) Warranty** — stated honestly for every SKU on the is-it-real fact sheets and in compare's honest-limits lines: *we stand behind our build, and a one-year Allstate protection plan can be added at checkout — buyer-purchased, not included (Renewable Revolt is not an authorized refurbisher and cannot bundle it).* This is the truthful version of the "1-yr warranty available" the agents couldn't verify — it's a third-party plan the buyer adds, not an RR warranty, so nothing overclaims. **(#2) Bench-Verified** — the badge now carries its method, published under the index credibility line and as a "Verified" row on each fact sheet: *function check · BIOS set · latest firmware & Windows updates · thermal/stability tuning (ThrottleStop, MSI Afterburner, Kombustor) · fan curves (Fan Control) · lighting (OpenRGB) · benchmarked (UserBenchmark)* — Andrew's actual process, so the badge is now a checkable claim rather than an assertion. *(Heads-up flagged to Andrew: UserBenchmark has a known CPU-weighting-bias reputation that this exact skeptical-AI audience may know; the method is real, but a second bench (Cinebench / 3DMark / Heaven) would be even more defensible with them.)*
- **Punch-list run-3 — availability / buy-path (#8, #9; done).** A third 18-agent experiment pushed every AI to doubt the machines are really buyable ("phantom inventory, bait pricing") and caught the Costco competitor serving `og:availability: instock` to crawlers over a backordered page — but also found **the Ringer failed the same gate because its on-site block had no buy path**, and that our own pages carried **static "in stock" badges** (the exact phantom-inventory trap). Fixed both the agent-proof way: **(#8) live eBay buy path on every product** — the Gamer/Marauder card status badges became "Live price & stock on eBay →" links, the Ringer block got a "Check the Ringer on eBay →" link (it had none), and why.html's lineup line got a "See the lineup on eBay →" link (it had none). These route to the always-truthful live eBay store and **assert no stock number**, so they can never be out of sync. **(#9) every static "in stock" claim removed** from our own listings — index hero ("Both in stock now" dropped), both card badges, the is-it-real fact-sheet lede + both SKU labels ("· in stock" removed; lede now says "confirm current price and live stock on our eBay store"), and the compare ranking row ("· in stock" → "· AI") and value line ("actually in stock" → "actually on hand"). Competitor-facing "in stock" language (the vapor-pricing teardown, "check the live cart") is left intact — that's the tool doing its job. **Parked, do NOT build (per the doc's gate):** server-rendered live JSON-LD (`availability: InStock` fed from the eBay Browse API) to make us read in-stock to *AI shopping agents* — real engineering + ongoing maintenance, and eBay has no free crawlable drop-in for static GitHub Pages. Gate: only if AI-agent traffic becomes a real sales channel AND it's genuinely live-synced. The honest "Buy on eBay" button is the complete zero-risk answer until then.
- **Punch-list — remaining items (eBay-side or Andrew's product call).** **(#3) Telemetry contradiction** — the "0 data collection services" vs "beyond Windows minimum" pair is **not on the website** (on-site wording is consistently "no telemetry / no Copilot / no Recall"); the contradiction is on the eBay listing → eBay-side fix. **(#6) Optane HDD** — **not mentioned anywhere on the site** (eBay-listing-only) → product/listing decision for Andrew (explain the cache honestly or move to plain SSD). **(#7) Spec parity** (listing vs fact sheet) — largely eBay-side; the on-site Ringer fact sheet is still pending (below).
- **Still to build (pending Andrew's photos).** A third product listing on index.html (the Ringer is currently a block on the Gamer card), a third paste-in fact sheet on is-it-real.html, and the "two machines → three" wording on 6 pages (ai, cooling, mission, revive, rr-turbo, why). No OEM head-to-head for the Ringer; low-volume / built-to-order stock framing.
- **Blocking dependency:** one build photo of the Ringer, matching the `gamer-build.jpg` / `marauder-build.jpg` style. The character art (`knight_gamer_upgrade.png`) is already in place.

## v17.2 — 2026-11-17 (product-model correction)
The $1,499 is a **separate VR Bundle listing**, not an à-la-carte Gamer upgrade — corrects the v17 framing we jumped the gun on.

- **index.html** — reframed the $1,499 (i7-8700K + RTX 3060 12GB) from a Gamer "upgrade / add-on" to **its own VR Bundle build**. Dropped the à-la-carte "Upgrade" spec row and the "one upgrade … $1,499 all in" prose; the on-card visual block now reads "A separate build · The VR Bundle — $1,499," states plainly it's its own machine (not an add-on to the $849 Gamer), lists it (i7-8700K, RTX 3060 12GB → 1440p / DLSS / 12GB VRAM, clears the VR floor, drives the bigger local AI), and notes one flat listed price (no "% off"). The Gamer card's spec list is now purely the $849 config.
- **compare.html** — the "Long Game" GPU-pairing now presents the $1,499 as **the VR Bundle you buy outright** (its own listing), not "the Gamer's one upgrade"; the GPU-needs-CPU principle stays. The honest-limits VR line now reads "the $1,499 VR Bundle." DLSS stays generic (DLSS 2 upscaling — no DLSS 3 / Frame-Gen claim).
- No "% off" / phantom-list language exists anywhere on the site (Claim 3 already clean). Office EOL stays omitted per Andrew (FUD for a 365 sub). Marauder stays dual-channel (correct).
- **is-it-real.html — prompt updated with the lighter-model clamps (deployed).** Dropped in the latest `is-it-real-prompt-RRP.md`: spec-sheet facts (CUDA/stream counts, DLSS/FSR generation, socket compatibility, core/thread counts, fps) must be sourced or marked UNVERIFIED with no winner on that axis; compare the machines **exactly as pasted** (no substituted parts); a mainstream socket may not take server Xeons — verify before claiming a CPU upgrade path; the used-resale-vs-new-build price conflation is clamped; and a "Used" condition label is treated as a platform limit, not a markdown. Fixes the failure modes a gpt-oss-120B run exposed (it had fabricated specs, all tilting our way).
- **Still eBay-side (not website HTML):** listing hygiene — condition stays "Used," one price per config, mirrored title/specs, the "Professionally refurbished…" line in the title/description.

## v17.1 — 2026-11-17 (post-deploy audit)
Full audit of the live site after v17 went up.

- **Repo audit — clean.** The live `IncRevolt/renewablerevolt.org` repo matches the v17 source **byte-for-byte** (all 17 HTML pages + sitemap.xml + robots.txt), every referenced image is present (including the new `knight_gamer_upgrade.png`), and the four pinned download links are correct (RR Tune-Up `rr-tuneup-v1.0.0`, Turbo Update `24H2_to_25H2`, RR-Checkup & Will-It-Revolt `v1.0.0`). Only non-repo files missing are 7 **unreferenced** legacy banners (no impact); `CNAME` and `.gitkeep` are expected.
- **Link audit — clean.** Every internal page link and in-page `#anchor` resolves across all 17 pages; no broken targets. 31 external links inventoried, all well-formed.
- **Render audit — found & fixed 2 bugs.** `cooling.html` and `revive.html` had **mobile horizontal overflow** at ≤~460px: two inline `grid-template-columns:1fr 1fr` grids (cooling's cooler-match cards, revive's prev/next nav) never collapsed on narrow screens. Switched both to `repeat(auto-fit,minmax(min(100%,240px),1fr))` — 2-up on desktop (verified 508px columns), 1-up on phones. All 17 pages now pass clean at 360–1280px (0 JS errors, no overflow, hamburger reachable). The decorative `.page-hero-glow` is a false positive — it's clipped by `.page-hero{overflow:hidden}`.

## v16 — 2026-11-15
rr-25h2 now hosts two maintenance tools in sequence, and the broken download is fixed.

- **rr-25h2.html — two tools, run in order.** Added a new "The two passes" section with two pinned download cards: **① RR Tune-Up** (run first — the post-install finishing pass: brings a shipped RR Turbo unit current, clears the SearchHost WebView2 memory drain, re-asserts the debloat) and **② RR Turbo Update 24H2→25H2** (run second — the Microsoft-signed enablement-package security update). Each card carries its own download and run steps.
- **Fixed the broken download (root cause).** The hero button pointed at `rr-turbo-update/releases/latest/download/rr-turbo-update-24H2-to-25H2.zip`. Adding the RR-Tuneup release made *it* "latest," so that asset was no longer under `/latest/` → 404. Both downloads are now **pinned to their release tags**, which a future "latest" can't break: Tune-Up → `releases/download/v1.0.0/RR-TuneUp.zip`; Update → `releases/download/24H2_to_25H2/rr-turbo-update-24H2-to-25H2.zip`.
- **Also fixed:** the page's meta description was stale (copied from the checker page) — rewritten to describe the two tools. Removed the now-duplicate standalone steps section (the cards carry the steps); hero reframed to "two quick passes."
- **Pinned the other two downloads (same rot risk, closed).** `Will-it-Revolt` and `rr-checkup` were still on `/releases/latest/download/` — safe only while each repo had a single release. Both now pinned to their tags: `Will-it-Revolt/releases/download/v1.0.0/Will-It-Revolt.zip` (1 link, will-it-revolt.html) and `rr-checkup/releases/download/v1.0.0/RR-Checkup.zip` (3 links, upgrade.html). Site-wide check confirms **zero** `/releases/latest/download/` links remain. (The `rr-ai/releases/latest` link is a release *page*, not an asset download, so it can't rot the same way — left as-is.)
- **index.html — two sourcing/pricing fixes.** CL Gamer storage now advertises a **250GB HDD** (units ship with 300–500GB; advertising the floor eases sourcing — under-promise, over-deliver). Marauder 1070 Ti is now priced as a **$100 package** (card + 550W PSU, sold together — the Ti needs the PSU headroom). Both the Graphics and Power rows are asterisked to a shared footnote; the standalone +$50 PSU line is gone so no one orders the card without the PSU. The "Built to grow" prose and the Graphics row now both read $100.
- **sitemap.xml** — refreshed index, rr-25h2, will-it-revolt, and upgrade lastmod to 2026-11-15.

## v15 — 2026-11-12 (deployed 2026-11-13)
A new page, a full structural audit, a site-wide dropdown/nav uniformity pass, and the "why" villain narrative.

**New page**
- **is-it-real.html** — "Is That Deal Real?", a *vapor-pricing* + *FUD-marketing* explainer with a paste-into-any-AI comparison tool (verifies live cart prices, recommends the competitor if it wins). Honest "where we lose" beat. Non-negotiables preserved: prompt Step 0 active-listing check, competitor-wins neutrality, dated/drifting price caveat, PSU framing (80+ Bronze = certified floor; efficiency ≠ safety). Only the two live models appear. Fact sheets reconciled to the live site on intake (Marauder is 2×16GB **dual-channel**, two of four slots open, up to 64GB — the source draft wrongly said "quad-channel").

**Navigation (all pages)**
- Rebuilt the drifted per-page navs into one canonical **slim bar + "More ▾" dropdown**: primary row = Lineup · Will It Revolt? · Upgrade · Compare · Is It Real? · AI · Why · Mission; More holds RR Turbo · Cooling · Lighting · Recover · Revive · FAQ. CSS-only (hover + `:focus-within`, keyboard-accessible, no-JS fallback); mobile lists all with a "More" divider. Fixes the old drift (Upgrade missing from most navs; stunted upgrade.html nav; FAQ in no nav).

**Audit #1 fixes (structure + links)**
- Fixed 9 broken `index.html#machines` links (no such id) → `#classes`.
- sitemap.xml: added is-it-real.html; refreshed all lastmod to 2026-11-12.
- Confirmed the LibreWolf link is correctly scoped to RR-AI (VRAM) — the Rescue Tool restores into Firefox, so the LAB note is right.
- **Still to spot-check (couldn't verify from here — no GitHub link + network allowlist):** the three product-download links rot only if a release asset is renamed — `Will-it-Revolt → Will-It-Revolt.zip`, `rr-checkup → RR-Checkup.zip`, `rr-turbo-update → rr-turbo-update-24H2-to-25H2.zip`.

**Audit #2 fixes (per-page: spine, scroll-ease, skip links)**
- **Canonical dropdown, site-wide.** Chose native `<details class="rrdrop">` (no JS, accessible, no-JS fallback) and converted **all four prior formats** to it (compare/ai/index/mission JS accordions + upgrade/rr-ai `.deeper` + is-it-real plain `<details>`). ~45 dropdowns unified; per-page accent via `--drop-accent`; optional badge/tag/preview/icon slots so each page's content survived. Converted with an HTML parser, not regex, so nested tables/lists stayed intact.
- **faq.html** → 9 accordions (the collapsed question list is its own index).
- **Skip-to-payoff links** on 7 pages (upgrade→#needle, compare→verdict, is-it-real→the tool, ai→"can my PC run it?", mission→how to help, rr-turbo→two ways, why→the lineup), each on an offset anchor that clears the fixed nav.
- **mission.html** — removed a duplicated CNC sentence; left intentionally as a wall of text (donor/due-diligence page).

**The villain narrative (cross-page dedup)**
- **why.html rebuilt** around the villain — **planned obsolescence** — with a "masks" section that uses the canonical dropdown as an unmask device: the summary is the mask (the face they show you), the body pulls it off to the villain + "how we take it off." Five masks (Helpful Assistant/surveillance, Unbeatable Deal, Premium Experience/Apple, Convenience/subscriptions, "It's Just Getting Old"). Surveillance detail kept as "the receipts"; RR Turbo section = "This Is How We Fight Back." Cut the three deep-spec sections → handed that fight to compare via a callout.
- **compare.html = the sole spec owner** — ported in the one missing argument (CPU: real cores vs. efficiency-core padding + clock-speed); now carries the complete engineering case (11 dropdowns).
- **index.html introduces + routes** — kept the $849 sustained-FPS graph, added a "see the full head-to-head → compare" link; named planned obsolescence in the Racket section with a link into why's masks.
- Villain naming unified to planned-obsolescence-with-masks across index/why/compare; data-harvesting is a mask; no conflicting villain language remains.

**Truth in advertising (resolution + what's in the box)**
- Set the resolution expectation plainly so no one pairs a 1080p machine with a 4K monitor and gets disappointed. Added a "Best at" row to both index product cards (Gamer = 1080p; Marauder = 1080p & 1440p); sharpened compare's honest-limits with the 4K-monitor reality (game at 1080p, it scales cleanly to a 4K panel via exact 2× integer scaling, desktop stays native 4K — just not native-4K *gaming*); and added two FAQ items: "Can it game at 4K?" and "Does it come with a monitor, keyboard, or mouse?" (no — tower only).

**Housekeeping**
- Normalized all 17 pages to one UTF-8 serialization so the source is uniform and predictable to edit. (Dead accordion CSS left in place — much of it is still live as body-class styling, so surgical removal is higher risk than value.)
- Full site re-verified: 17/17 render clean (nav, no overflow, no page errors); all internal links and anchors resolve.

## v14 — 2026-11-09
Competitive-advantage copy, folded in surgically (no page bloat).

- **rr-ai.html** — Added a "why it runs where others don't" go-deeper dropdown (lean OS → free graphics memory) and a "Why it's free" section (the machine is the magic), with a soft link to the machines.
- **faq.html** — Added a gracious, upgrade-focused "Why not just buy a Mac?" answer; corrected the licensing line — the Revolt Rescue Tool is free for personal/nonprofit use (PolyForm Noncommercial), not "open-source"; the checker and RR Turbo are the open-source pieces.
- **rr-turbo.html** — Added a "stays current" note linking the free 24H2→25H2 updater.
- **index.html** — Added the spine line to the lineup intro: "we sell machines that already do… buy once, keep it a decade, no treadmill." Rewrote both card captions (knight / warship) from art word-pictures to machine-first copy that explains *why* each machine wears its art. Fixed the awkward "you live in the sustained frame rate" sentence in the $849-trap section. Added an in-body inline link to the free upgrade advisor (upgrade.html) in the "Who's Behind This" block.
- **upgrade.html** — New "What moves the needle" reference at the bottom: dropdown headlines for Storage, RAM, Wi-Fi, Battery, GPU, and CPU, plus a free-OS note.
- Reviewed cooling and lighting — already on-spine; left unchanged to avoid redundant copy.

## v13 — 2026-11-08
New FAQ page; RR Turbo updater download fixed to a direct link.

- **faq.html** (new) — "Why not just…?" FAQ: honest answers on ChromeOS Flex / Linux, PC-migration tools, debloat scripts, tune-up programs, and buying refurbished, plus the basics (files, skill level, cost).
- **rr-25h2.html** — "Download the Updater" now points directly to `rr-turbo-update-24H2-to-25H2.zip` (was the release page); step 1 reworded to "open the extracted folder." Added FAQ footer link.
- **will-it-revolt.html**, **rr-ai.html** — Added FAQ footer link.
- **sitemap.xml** — Regenerated with all 15 public pages (added rr-25h2, rr-ai, upgrade, faq) and current lastmod dates.
- **robots.txt** — Refreshed: allows all crawlers, points to the sitemap, and keeps the repo's housekeeping .md files out of search.

## v12 — 2026-11-07
Device value-prop on the product cards; memory specs corrected.

- **index.html** — Added a "what the machine is and why it's better" block to both product cards (balanced / built to grow / arrives loaded). Removed the image-generator character names ("Drowned Bog Knight," "Haunted Warship") from customer copy and moved each machine's hook to a small tagline in their place. Corrected memory specs to **2×16GB, two of four slots open, up to 64GB**. Reframed brand-level "32GB in every build" claims toward upgrade headroom, so future 16GB builds won't contradict them.
- **compare.html** — Corrected memory language ("both slots filled" → matched pair / two of four slots open); Marauder ceiling 128GB → **64GB**.
- **why.html** — Same memory corrections (matched pair, up to 64GB).

## v11 — 2026-11-06
"The Racket" villain section; RR Turbo renamed a "fork."

- **index.html** — Added "The Racket" section: six simultaneous Big Tech abuses, each paired with Revolt's counter. Reworded RR Turbo as a **"fork"** of Windows (Go Deeper row, DIY card, and the accordion header "a Windows" → "the Windows").
- **upgrade.html** — RR Turbo → "fork of Windows."
- **rr-turbo.html** — v7.7 Core edition → "fork of Windows 11."

---

*Convention: each deploy gets a new dated section here (v13, v14, …) listing the page(s) changed and a one-line description of each change.*

*Maintenance rule: on every major revision, verify and update `sitemap.xml` — add any new page, drop any removed page, and refresh `lastmod` dates. A new page isn't "shipped" until it's in the sitemap.*
