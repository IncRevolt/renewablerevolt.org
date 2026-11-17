# Renewable Revolt — Site Changelog

Record of changes to renewablerevolt.org, newest first.
Baseline: **v10** (last version deployed to GitHub).

---

## v17 — 2026-11-17
Mobile-nav fix across the whole site, plus two AI-prompt upgrades.

- **Mobile navigation fixed site-wide.** On phones the wide logo + "Shop eBay" CTA + hamburger overflowed the viewport, pushing the hamburger off-screen — the menu was unreachable (`toggleMenu()` itself was fine; this was pure layout overflow). Added a mobile nav rule to all 16 content pages: ≤768px tightens nav padding, shrinks the logo/CTA, and pins the hamburger (`flex-shrink:0`); ≤360px hides the CTA so the smallest phones still fit. Verified 320–414px — hamburger visible, menu opens on tap, no page overflow, zero JS errors.
- **is-it-real.html — final RRP + TCO prompt DEPLOYED.** Replaced the live Step 0–4 prompt with the product-chat-validated final (`is-it-real-prompt-RRP.md`, validated across ~20 skeptical-AI runs). Adds: an OPERATING STANCE preamble (incentive-map every source *both* ways — pro-"buy new" and pro-"buy mine," our own sheet included; never answer from training — verify against today's market; mechanism over "newer"; symmetry + steelman); Step 0 may read our compare/why pages under the same suspicion; a 4th report axis **Step 5(d) 3–5yr TCO** run symmetrically (subscriptions avoided, RAM-as-insurance, upgrade path/repairability, hidden cost of compromised components — and the newer box's remaining life/warranty/runway credited back); the socket-ceiling check now includes the **server-Xeon HEDT path** (corrects the earlier "HEDT = dead-end" error); Step 5b now also asks the cheapest way to confirm a deciding fact; Step 6 splits the frames-buyer vs TCO-buyer pick. Copy button simplified to plain innerText. **Updated same day:** added the **single-machine branch** — if a visitor pastes only our machine with no competitor, the prompt runs a standalone fitness audit + a 2–3-machine cross-shop shortlist (and says plainly if their use needs more than the machine gives) instead of stalling on a dangling "paste the competitor." This was the biggest gap the zero-context agent runs found, since most real visitors arrive with one machine and a mission.
- **upgrade.html Upgrade Advisor prompts reworked (deployed).** Ported the is-it-real discipline to the laptop + desktop prompts: (1) never price parts or repair labor from training — verify against current listings/quotes, give ranges + confidence (late-2026 shortage makes remembered prices too low); (2) "old is not a verdict" — replace a part only when it actually bottlenecks the user's use. Wi-Fi judged by streams, not the label (MIMO Wi-Fi 5 is fine; single-stream/older → 6/6E/7 is a real win). Desktop GPU: don't replace a working 4–6GB card unless it's bus-limited (PCIe x4 trap) — check interface width, not just VRAM. Aligned the page's Wi-Fi dropdown + worked example and flagged the worked-example prices as illustrative. Kept in sync with `RR-Upgrade-Advisor-prompts.md`.
- **compare.html — new "The Long Game" section (deployed, RRP-validated framing).** Added a forward-looking value section between Balance and the 3-year receipt: the Revolt win isn't today's FPS — it's TCO and device longevity. Three accordions, each scoped honestly after the RRP/TCO review flagged two earlier drafts as misleading: (1) **RAM insurance** — 32GB pre-bought now, the part getting hardest/costliest to add (both review agents rated this TRUE); (2) **the right GPU for today, room to grow** — a capable 1080p card with no compromise on RAM/cooling/PSU, and the Gamer's CPU swap scoped to *pairing with a future GPU so it isn't bottlenecked* (one generation: i7-8700/9700/i9-9900), NOT an open-ended platform "runway" (LGA1151 dead-ends at the i9-9900K); (3) **the real multi-core runway is the X99 Marauder** — LGA2011-3 takes recovered server Xeon E5-2600 v4 (up to 22 cores, once $4,000+, now tens of dollars), the e-waste thesis made concrete, scoped to multi-threaded workstation/content/local-AI work, explicitly NOT single-thread gaming. Closing callout reframes the private AI to **privacy, not dollars** (no account/telemetry/subscription) — the overstated "save $X on AI" implication removed. **Final-reframes update:** the Marauder accordion now shows BOTH HEDT upgrade branches per the product-chat doc — the balanced consumer-HEDT step (i7-6850K → i7-6900K / i7-6950X, more cores, single-thread comparable) and the max-core Xeon step — and the Office line tightened to "a perpetual Office 2019 Pro+ licence" (no "always current" implication). **TCO reconciled to match:** the "three-year receipt" no longer banks the cloud-AI subscription as hard dollars — it's now a conditional "only if you'd pay for one (~$240/yr)," so the honest comparison is **$949 owned vs $1,449 rented** (PC + Office), with AI value carried on privacy/ownership, not a guaranteed saving. (Per Andrew: Office 2019 Pro+ is full-featured and safe — no EOL/"it's unmaintained" language on the page, which would be FUD for a 365 subscription.) **VR honesty lines added** to both Honest-Limits accordions (the product-chat's Claim 4 / VR to-do): the Gamer (6GB 1660) and Marauder (8GB 1070) are stated plainly as **not headset/Quest-3-class VR machines**, and demanding VR flight sims (MSFS/DCS) are correctly attributed to the **single-thread CPU limit on the LGA1151 platform, not the graphics card**. (Pricing/SKU-model changes in those docs intentionally left out per Andrew.)
- **CL Gamer upgrade package added (index + compare).** Per Andrew's decision to offer an *upgrade package* rather than a new model: the Coffee Lake Gamer now has a **Full upgrade — $1,499 total** that swaps in an **i7-8700K (6C/12T) + RTX 3060 12GB** (same chassis, 32GB, cooler, and the existing 650W PSU — no PSU change needed). Added to the index Gamer card as an Upgrade spec row + a "Built to grow" prose line + a dedicated **visual upgrade section** at the bottom of the card's dropdown — new character art (`img/characters/knight_gamer_upgrade.png`, the upgraded cyan-glowing knight) with a cyan-accented highlight list (i7-8700K, RTX 3060 12GB → 1440p/DLSS/CUDA, the bigger local AI, and the VR floor for lighter sims) and a clean-swap note. (Replaced the earlier text-only footnote so the upgrade story isn't told twice.) The compare "Long Game" GPU accordion names this real package (1440p, DLSS, 12GB for the bigger local AI) in place of the earlier hypothetical 3070 Ti / i9-9900K example. (Pricing is Andrew's own explicit call, not from the product-chat docs.) The Gamer's honest-limits VR bullet now closes the loop: the upgrade's RTX 3060 12GB clears the graphics-card VR floor for lighter headset sims, while demanding MSFS/DCS in VR stays CPU-capped on LGA1151 — upgrade and caveat read as one consistent story.
- **sitemap.xml** — all lastmod refreshed to 2026-11-17 (every content page got the nav fix).
- **GitHub-alignment pass (repo changes → site links).** Matched the live site to the Nov 17 GitHub updates: fixed the **RR Tune-Up download** to its real release tag — `rr-turbo-update/releases/download/rr-tuneup-v1.0.0/RR-TuneUp.zip` (the site had `v1.0.0`, which would 404); updated **Will-It-Revolt's run step** from the stale `run.bat` to **`Will-It-Revolt.bat`** (matching the live GitHub release's "How to run it"; the download link was already correct — repo `Will-it-Revolt`, tag `v1.0.0`, asset `Will-It-Revolt.zip`); and repointed every **`R-R-Turbo` repo link → `rr-turbo`** (the repo rename) across compare, index, mission, revive, rr-turbo, and why, plus "R-R Turbo" → "RR Turbo" display text on recover/revive. The Apache→PolyForm relicense needs no site change (no page states the updater's license). *(Confirmed from GitHub screenshots: tag `v1.0.0`, asset `Will-It-Revolt.zip` — link good. Note for GitHub cleanup: the repo source file is still named `Run.bat`, so the zip's launcher, the release notes, and the site should all be made to agree on one name.)*

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
