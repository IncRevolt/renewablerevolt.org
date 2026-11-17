# "Is That Deal Real?" — comparison prompt, RRP-integrated (paste-ready)

**Source:** website-maintenance chat's RRP integration, with two small symmetry refinements from the product/strategy chat (2026-11-17).
**What changed from the prior version:** added the Revolt Research Process (RRP) as an Operating Stance before Step 0, and a claims-table step (5b). Two refinements below keep it RRP-symmetric:
- Stance point 1 now names **both** incentives (pro-"buy new" *and* pro-"buy mine," Renewable Revolt included), not just the pro-new one.
- Step 5b now asks for **the cheapest way to confirm** a deciding fact before buying (the RRP's "Act / cheapest decisive test").
- **Added a TCO metric — Step 5(d):** total cost of ownership over 3–5 years (subscriptions avoided, RAM as pre-purchased insurance, upgrade path / repairability), run **symmetrically** so it also credits the newer machine's remaining life, warranty, and future-upgrade runway. This is the axis where longevity lives, separate from today's frame rate.
- **Step 0 now lets the AI read Renewable Revolt's "compare" and "why" pages** for the full value case — under the same suspicion as any seller's marketing.
- **Upgrade-path check now includes the server-Xeon path for HEDT sockets** (X79 / X99 / LGA2011-x): decommissioned Xeons are a cheap, growing multi-core upgrade a mainstream socket can't match — scoped to workstation / multi-thread / local-AI, not single-thread gaming. Corrects the "HEDT = dead-end socket" error the earlier runs made.
- **TCO now weighs the hidden future cost of compromised hard-to-add components** (RAM, cooling, PSU headroom) — applied symmetrically, against whichever machine cut them.
- **Added a single-machine branch (2026-11-17):** if the buyer pastes only the Renewable Revolt machine with no competitor, the prompt runs a standalone fitness audit plus a cross-shop shortlist instead of stalling. Closes the gap the zero-context agent runs exposed — a buyer describing their mission (not cross-shopping a named box) was left with a dangling "paste the competitor" and no usable answer.

All of this morning's hardware fixes are preserved (made-to-order Step 0, 4K use case, Fortnite 40fps floor, cooling demoted, bidirectional cost-to-match, the PCIe x4 trap, RAM-channel scoring, RT/DLSS as a check, low-confidence→range, explicit paste-both).

Drop the block below into the page's `<pre>` paste-in box.

---

```
You are helping me choose between two specific desktop PCs. Be rigorous and neutral, and recommend whichever actually wins for me — including the competitor. Follow every step in order.

OPERATING STANCE — read this before Step 0, and hold it through every step.
1. Every input here is trying to sell me something. The competitor's ad, its star rating and reviews, "best-of" lists, influencer takes, AND the Renewable Revolt fact sheet I paste in are all incentivized sources. For each claim, ask who benefits if I believe it — who profits when the answer is "just buy a new one," AND who profits when the answer is "buy mine instead" (the Renewable Revolt sheet included). Hold both machines to the same suspicion; the seller's own sheet is not exempt.
2. Do NOT answer from training or "common knowledge." It is late 2026: GPU, RAM, and SSD prices are in an AI-driven shortage and run several times higher than your training data, and "which card/CPU is good" from memory lags the current market. Treat every price, every spec, and every "that part is too old" claim as UNVERIFIED until you check a primary source today — a live cart, the manufacturer's spec sheet, a benchmark you can cite. When you can't verify, say "unverified," give a range, and state your confidence. Never present a confident number you didn't check.
3. Hunt the mechanism, not the label. For each claim that matters, say what physically or economically has to be true for it to hold: VRAM capacity sets model/texture size, memory channels set bandwidth, PCIe lane width sets how a card degrades when VRAM spills, cooling sets sustained clocks. "Newer," "higher number," and "next-gen" are marketing, not mechanisms. A spec counts only if it changes MY result.
4. Stay symmetric and steelman. Apply identical scrutiny to the ad's scares and to the fact sheet's boasts. Make each machine's strongest honest case before you criticize it. If your own brand familiarity tilts you, say so. Separate checkable facts (prices, dates, core counts, benchmark numbers) from interpretation, and label anything you couldn't trace to a source as UNVERIFIED.

STEP 0 — Confirm both machines are real and buyable today.
• Renewable Revolt machine: confirm an ACTIVE listing at renewablerevolt.org or the eBay store (ebay.com/usr/renewable-revolt-inc). If the model is described as limited or made-to-order and you can't find a standing listing, do NOT disqualify it — say "availability unverified, confirm with the seller" and continue, judging it on its merits at the stated price. Only treat a model sold as in-stock as disqualified if you can't confirm it.
• Renewable Revolt value case: you may also read Renewable Revolt's "compare" and "why" pages (linked from the site) to understand the machine's full value proposition — its upgrade path, included RAM, and no-subscription stance. Treat those pages as incentivized marketing like any seller's and verify their claims against primary sources; the Operating Stance applies to them too.
• Competitor: find its CURRENT in-stock price in an actual cart today — not an advertised, cached, or "sale" price. If you cannot reach a live cart (bot wall, script, or mobile), label the price "advertised, not cart-verified" and say so — do not present it as confirmed.
• If only ONE machine is pasted (no competitor): do NOT stall or demand a second machine before helping. Run a standalone fitness audit instead — confirm the one machine (above), get my use case (Step 1), judge it on what governs that use (Steps 2–5), and in Step 6 tell me plainly whether it fits my use, where its ceiling is, and name 2–3 specific classes of machine I should cross-shop it against (by GPU / CPU / platform class, not brand). Then invite me to paste one for the full both-directions comparison. A one-machine honest fit-check is a complete, useful answer — the head-to-head is the upgrade, not the price of entry.

STEP 1 — Ask me my primary use case before you compare, because it changes what matters. Pick one and wait for my answer (if I don't pick, assume G):
  A) 1080p / esports / everyday gaming
  B) 1440p, 4K, or high-refresh flat-screen gaming
  C) Racing or lighter sims in VR (iRacing, Assetto Corsa)
  D) Demanding flight sims in VR (MSFS, DCS)
  E) Local AI / running models offline
  F) Photo / video editing
  G) General multitasking / all-rounder

STEP 2 — Compare on what actually governs MY use case first:
  • A (1080p): enough VRAM — 3GB is the floor for esports/older titles, 6–8GB for comfortable modern AAA, more is wasted at 1080p — plus 8GB system RAM minimum (16GB recommended) and cooling for consistent clocks. At 1080p the CPU is usually the limiter, not VRAM. Judge by a consistent frame-rate floor, not peak FPS: a usable budget 1080p machine should hold 40 fps+ consistently as the absolute floor in a demanding mainstream title like Fortnite.
  • C / D (VR/sims): the two factors that govern are raw GPU throughput and CPU single-thread speed (sims are single-thread-bound, and frametime consistency, not peak FPS, is what keeps a headset comfortable), with 12GB VRAM as the capacity floor. Adequate cooling supports sustained clocks but is not the bottleneck — don't weight it as a governing factor.
  • E (local AI): VRAM capacity — it sets the model size you can run; a 12GB card runs bigger models than a newer 8GB one — backed by system RAM.
  • F (photo/video): CPU cores, lots of system RAM, fast NVMe storage, and enough VRAM for accelerated effects.
  • B (1440p / 4K / high-refresh): raw GPU throughput leads, with enough CPU. At 4K specifically, VRAM capacity (12GB+ so textures don't spill) matters alongside throughput, and DLSS does real work.
  • G: overall balance — no single bottleneck.

STEP 3 — Price every spec gap and every "cheap/easy upgrade" at TODAY's live cost. Never price RAM, GPUs, or storage from memory — late 2026 is an AI-driven DRAM shortage and any remembered price is several times too low.
  • For any RAM, GPU, or storage gap, pull AT LEAST 3 live listings of the SAME part, in stock right now, and use the median (or lowest in-stock). If you can't find 3, say how many you found and flag the price as low-confidence. Do not invent listings. When you can't cart-verify or can't find 3 listings, give a price RANGE and state your confidence — never a single confident number you couldn't verify.
  • Compute cost-to-match in BOTH directions, not one: what would each machine cost to reach the other's spec on every axis where it trails — RAM capacity AND channel config, GPU, CPU/platform. State plainly which gaps are cheap drop-in upgrades and which need a full platform swap (CPU + board + RAM) or can't be practically closed at all. A one-directional "the competitor must pay $X to match my RAM" — without also stating what this machine would pay to match the competitor's GPU and CPU — is a biased comparison. Run it both ways.

STEP 4 — Judge the hardware honestly, in BOTH directions:
  • A GPU is decided by enough VRAM for the use case + enough raw throughput to hit the target framerate — NOT by "it's the newest card." Newness alone is not a reason.
  • Check whether ray tracing matters for MY use before you count it: it's essentially off in VR and optional at 1080p, so a card's ray-tracing edge is usually irrelevant to a sim/VR/esports buyer. Check whether each machine supports DLSS upscaling — genuinely useful for hitting headset or high-resolution framerate, less needed at native 1080p.
  • The PCIe-lane trap: watch out for cards like the RX 6500 XT that throttle because of limited PCIe lanes (x4). A narrow x4 card with low VRAM (4GB) chokes badly on an older PCIe 3.0 board once VRAM spills, while a full x16 card degrades gracefully — same VRAM number, very different behavior. Always check the GPU's interface width (x4 vs x16), not just its VRAM.
  • RAM channels: check single vs dual vs quad. Single-channel (one stick, or a lone 1x16) is a real penalty — roughly half the memory bandwidth, felt in 1% lows and frametime consistency — score it down. Dual-channel (both slots filled, matched) is the baseline. Quad-channel matters only for workstation/local-AI. A "16GB" that is 1x16 single-channel scores BELOW 16GB as 2x8 dual-channel. Don't infer the channel count from the capacity label — a "16GB" prebuilt is very often a single 1x16 stick; confirm the actual number of sticks before scoring.
  • "The parts are too old" is marketing fear for a light-use box and a correct, decisive call for a demanding one. Rate each such claim for MY use case, not as a blanket scare to dismiss.

STEP 5 — Report FOUR things separately; never merge them into one score:
  (a) raw performance for my use case;
  (b) hardware price-to-match, using the live prices from Step 3;
  (c) bundled software (Windows edition, Office, offline AI) as its own line I can weight at $0 if I don't need it. Software is a tiebreaker, never a performance offset — it cannot close a GPU or CPU gap.
  (d) Total cost of ownership over 3–5 years, run BOTH ways — this is where longevity and upgrade path live, separate from today's frame rate:
     • Subscriptions avoided or incurred: does either machine push me toward a paid cloud subscription I'd otherwise skip — productivity (~$70–100/yr) or cloud AI (~$120–240/yr)? Count it over the window. A perpetual office suite and a private offline AI avoid both — but check the office version's support status (Office 2019 is end-of-support, so credit it as working, not maintained).
     • RAM as pre-purchased insurance: RAM is the hardest, most expensive part to add later, and DDR4 is being phased out, so it only gets scarcer. Price live what it would actually cost to add RAM later to whichever machine ships with less — RAM included now is bought at today's price against tomorrow's.
     • Upgrade path and repairability: can I extend the machine's life by dropping in a bigger GPU later (needs PSU wattage + the right power connectors + physical case clearance — standard ATX, not a sealed/proprietary OEM box) and by swapping the CPU within the same socket? Check the socket's REAL ceiling, including server/workstation CPUs, not just consumer ones: a mainstream socket (e.g., LGA1151) tops out at a consumer chip like the i9-9900K — one generation of headroom — but an HEDT socket (LGA2011 / 2011-3, X79 / X99) has two upgrade branches a mainstream socket lacks: higher-core same-generation consumer HEDT chips (e.g. Broadwell-E i7-6900K / 6950X — more cores while keeping single-thread comparable, at a higher but falling price), and cheap decommissioned server Xeons (up to ~18–22 cores for tens of dollars as data centers retire them — maximum cores but lower single-thread). Both benefit workstation, content, and multi-threaded or CPU-offloaded local-AI work; neither raises single-thread gaming. Don't call an HEDT socket a dead-end without checking these paths.
     • Hidden future cost of compromised components: a machine that hit its price by shipping less RAM (costly to add later in this shortage, especially phased-out DDR4), a weaker cooler (thermal throttling and shorter component life), or a proprietary / low-headroom PSU (blocks a future GPU) carries real future costs a fully-specced machine avoids. Credit a machine that didn't cut the hard-to-add parts — apply this to whichever machine compromised, both ways.
     • The honest other side: weigh all of that against the newer machine's advantages — more remaining hardware life, a warranty, and often a LONGER future consumer-CPU runway on a mainstream socket. Don't let the TCO lens hide the newer box's longevity and warranty edge.
     State the 3–5 year TCO for both machines, naming the one or two factors that dominate it (often: subscriptions avoided and the cost of adding RAM later, versus remaining hardware life).

STEP 5b — For each claim that actually drives the verdict (on EITHER machine), rate it TRUE / PARTLY TRUE / UNVERIFIED / FALSE with your confidence, name the ONE piece of evidence that would flip it, and the cheapest way to confirm it before you buy. If a deciding fact is unverified — a price you couldn't cart-check, a channel count you couldn't confirm — say so and mark the verdict provisional until it's confirmed. Don't let an unverified claim carry the decision silently.

STEP 6 — Give your verdict for MY use case, naming the one or two specs that actually decide it. Lead with the bottom line in one sentence, then the specs behind it. Say whether the verdict assumes I optimize for raw performance today or for total cost of ownership over the machine's life — these can point to different machines, so name which priority you're answering for, and give the TCO buyer and the frames buyer each a clear pick if they'd differ. Recommend whichever wins — including the competitor, if it does. If only one machine was pasted, give the standalone fit verdict (does it fit my use, and where is its ceiling) and the 2–3-machine cross-shop shortlist instead of a head-to-head winner — and say plainly if my use needs more than this machine can give, even though that machine is the one on the page.

Paste the Renewable Revolt machine's fact sheet (from this page), and — if you have one — the competitor's listing or ad, and name the one you're cross-shopping. If you only have the one machine, that's fine: paste it alone and I'll run the standalone fitness check and tell you what to go compare it against.
```

---

*Numbers in the examples (RX 6500 XT, DDR5) are a Nov 17 2026 snapshot — re-verify before the Black Friday push. The RRP is Andrew's Revolt Research Process; this prompt is a consumer-facing application of it.*
