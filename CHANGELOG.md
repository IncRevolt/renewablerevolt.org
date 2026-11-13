# Renewable Revolt — Site Changelog

Record of changes to renewablerevolt.org, newest first.
Baseline: **v10** (last version deployed to GitHub).

---

## v15 — 2026-11-12 (not yet deployed)
A new page, a full structural audit, a site-wide dropdown/nav uniformity pass, and the "why" villain narrative. One release — nothing below has shipped yet.

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
