# Viral Evaluation — Thawscope landing site

```
Result: PARTIAL — game codebase out of scope (pricing principles scored from site claims only); repo sync skipped by orchestrator rule
Virality Score: 56/100 — Needs work
Product: Thawscope — offline iPhone word puzzle; guesses land on a thermal scope by closeness in meaning, warm guesses thaw a frozen word (coming soon, no store link)
Evaluated: evidence-dir (live page.html, head.json, screenshots) + local site /home/lam/Documents/projects/thawscope-site/.claude/worktrees/s9-site (index.html, privacy.html, support.html, 404.html, assets/share-card.jpg)
Orchestrated by: design-optimizer
Checks owned: virality, meta-tags

PASS: 10/32   PARTIAL: 16/32   FAIL: 6/32
```

Source tags: **[local]** = file in the s9-site worktree (newer than live); **[live]** = evidence-dir capture of https://nguyenvanlamm.github.io/thawscope-site/.

Assumptions (owner away, recorded not asked): audience = adults who play daily word puzzles on iPhone; primary goal = understand the game and remember it for launch; free-to-play with optional purchases, no ads, no tracking, no accounts is deliberate; no store link exists yet.

## Scorecard

### A. Pricing & monetization
```
FAIL  #1  No free plan ··········· "All 120 levels and the Daily Core are free" (index.html FAQ L231) [local]; deliberate F2P
FAIL  #8  Hard paywall ··········· full game free, optional purchases only (FAQ L231) [local]; deliberate
PASS  #12 Popcorn pricing ········ 3 optional SKUs named: Flare Bundle, Supply Drop, Field Journal (FAQ L231) [local]
PART  #16 Pricing impossible to miss  pricing lives in a collapsed <details> "Is Thawscope free?"; nav = How it plays/FAQ/Support, no pricing link; hero fact "120 free levels" helps [local]
PASS  #27 No subscription ········ no subscription mentioned; purchases read as one-time (FAQ L231) [local]  ⚠ site claim only, game code not checked
PART  #32 Priced above competitors  free, no prices shown; category norm (daily word games) is free  ⚠ needs real IAP prices
```

### B. Hero & headline
```
PASS  #20 Sellable from hero ····· h1 + lede + phone screenshot explain the loop with zero scroll (desktop.png) [live]  ⚠ "want it" needs human eyes
PASS  #7  Fifth-grader headline ·· "Every word you type shows which way is warmer" — plain words, hot/cold-game metaphor [local+live]
PART  #18 Emotional headline ····· mild intrigue ("warmer than what?"), no laugh/wow  ⚠ emotional pull needs eyes
PART  #17 Memorable headline ····· 9 words, concrete but loose; the sticky word "thaw" is not in it  ⚠ recall needs eyes
PASS  #3  Numbers not adjectives · hero facts "120 free levels"; body "10 Core sets", "20 to 30 probes", "0° to 100°" [local]
PART  #24 Human desire ··········· top copy describes the mechanic ("Each level freezes one English word…"); no payoff line (the "getting warmer" thrill, a daily ritual)  ⚠ judgment
```

### C. Message clarity & focus
```
PASS  #11 Does one thing ········· one word-guessing loop; Flares/Picks/Batteries/streak all serve it  ⚠ judgment
PASS  #30 ≤10-word description ··· eyebrow "Word puzzle · iPhone · offline" + 9-word h1 [local]
PART  #6  One idea per screen ···· section "A path longer than one puzzle a day" packs progression, Daily Core, probe scarcity, three tools and 3 screenshots (index.html L187-224)  ⚠ judgment
PART  #22 One CTA ················ primary ".soon" is an inert <span> "Coming soon to the App Store"; clickable buttons are "See how it plays" (hero) and "Get help or send feedback" (final) — two different secondaries [local+live]
FAIL  #28 CTA says what happens next  primary is a status, not an action; nothing to do on the page to "remember for launch" [local+live]; pre-launch constraint
```

### D. Proof & differentiation
```
PART  #21 Empathy before selling · one token pain line: "A run of cold guesses still points somewhere." (L163) [local]  ⚠ judgment
PASS  #9  Copy only you could write  Crack/Thin ice/Slush/Meltwater, "sugar 84°", Flare/Pick/Battery — un-pasteable [local]  ⚠ judgment
FAIL  #14 Customer language ······ pre-launch; no player voice anywhere  ⚠
PART  #26 No weak words ·········· "about twice as close" (L206); "up to three stars" (L194) is a factual max [local]
FAIL  #29 Testimonials ··········· none (pre-launch) [local+live]
FAIL  #31 Compares to competitors  no comparison to semantic-guess games (Contexto, Semantle) [local+live]
PART  #19 Never seen before ······ semantic-distance guessing exists; 2-D scope with direction + thawing letters is the twist  ⚠ novelty needs eyes
```

### E. Show, don't tell
```
PASS  #10 Shows product first ···· gameplay screenshot beside h1 on desktop, right under CTAs on mobile (desktop.png, mobile.png) [live]
PART  #25 Try before buying ······ static screenshots only (game.webp, home.webp, won.webp); no interactive sample [local]
PART  #15 Founder presence ······· footer "© 2026 Luong Nguyen" [local] / "© 2026 Thawscope" [live]; no face or voice  ⚠
```

### F. Visual & shareability
```
PART  #2  Three colors ··········· frost/graphite/orange + thermal ramp + ice-blue pills; orange marks bullets and step numbers, while the primary CTA is graphite [local CSS L42-46, L69-72]
PART  #4  Shareable footer ······· closing "The first probe lands in seconds" + inert badge + support button; footer is legal/credits  ⚠ judgment
PART  #5  OG image as thumbnail ·· share-card.jpg present, 1200×630, og:image:alt set; but no name, no words, ~half the canvas empty, scope labels unreadable at feed size [local asset]  ⚠ punch needs eyes
PASS  #23 Memorable name ········· "Thawscope" = thaw + scope, two known words, says itself  ⚠ judgment
```

### G. Distribution context
```
PART  #13 Rides a wave ··········· daily word puzzles are a live habit and the site shows "Daily Core" + streak, but it never links itself to that habit  ⚠ judgment
```

## Top fixes (ordered by impact × ease)

1. **Redesign the share card as a thumbnail** — fixes #5 (meta-tags) · needs owner (asset redesign; keep approved palette)
   Now: `assets/share-card.jpg` [local] = small icon left + small gameplay screenshot right on frost, no text; at 300 px wide only the icon reads.
   Change: same 1200×630 frame, frost #F3F5F7 background, graphite headline in large type "Every guess shows which way is warmer" + wordmark "Thawscope" + "Coming soon to iPhone", the thermal ramp as the one accent, and one enlarged crop of the scope with 2–3 big readable probes (e.g. "sugar 84°", "sweet 70°"). Keep the important content in the middle 630×630 so square crops still work.
   Why: links shared in chats show only the card; today it says neither the name nor the idea.

2. **Deploy the local head to live** — fixes meta-tags drift · safe (already built, same look/copy)
   Now [live]: description 237 chars ("Thawscope is an offline word puzzle for iPhone. Type any word: …"), 67-char title, no twitter:title/description/image.
   Change: publish the s9-site branch; local has a 152-char description, 55-char title and full twitter:* tags.
   Why: search snippets and X cards cut long text; the fixed version already exists.

3. **Fix the summary-card crop on privacy/support** — fixes #5 (meta-tags) · safe
   Now [local]: `privacy.html` / `support.html` use `<meta name="twitter:card" content="summary">` with the 1200×630 og:image; a centre square crop (x 285–915) shows mostly empty frost with slivers of the icon and the screenshot (checked by cropping the asset).
   Change: add `<meta name="twitter:image" content="https://nguyenvanlamm.github.io/thawscope-site/assets/icon-256.png">` (square, ≥144 px) on those two pages, or switch them to `summary_large_image`.
   Why: a shared support/privacy link should still show the brand.

4. **Give the "coming soon" moment a job: remember it** — fixes #28, #22, #4 · safe (reuses an existing claim; no new feature)
   Now: inert badge "Coming soon to the App Store" + "Get help or send feedback" as the final action; the FAQ already says "This page will link to it on launch day."
   Change: under both badges add one line: "Search ‘Thawscope’ on the App Store at launch — this page will link to it that day." In the final section, make the secondary "See how it plays" (or drop the support button there; Support stays in nav/footer). At launch, replace the badge with "Download Thawscope free on the App Store".
   Why: the goal is recall; a name to search for is the only action possible pre-launch, and one secondary action instead of two.
   Note: an email/notify list would be stronger but is a new feature — needs owner.

5. **Add a payoff line to the hero** — fixes #24, #18, #17, #21 · safe (copy only; layout untouched)
   Now: lede opens "Each level freezes one English word at the centre of a thermal scope."
   Change: open the lede with the feeling, then the mechanic, e.g. "No more blind guessing: even a cold word tells you where to turn. Each level freezes one English word…" (reuses the existing claim "A run of cold guesses still points somewhere"). Optional h1 test: "Guess a word. Watch it get warmer." — headline change needs owner (approved mockup).
   Why: sell the thrill of closing in, not the instrument.

6. **Split the crowded features section** — fixes #6 · needs owner (layout change)
   Now: L187-224 mixes progression, Daily Core, probe limits, three tools and three screenshots.
   Change: move the screenshots strip into its own section ("Home, in play, thawed") or move "Three tools for when you are stuck" into How it plays.
   Why: one idea per screen keeps scanning fast.

7. **Name the category it beats** — fixes #31, #13 · needs owner (new comparative claim, 4.3 copycat risk)
   Now: no reference to the daily semantic-guess habit.
   Change: one line in How it plays: "If you play a daily guess-the-word game, Thawscope adds a direction: related words point the same way." (category, not brand names).
   Why: readers switch when they see what's different from what they already play.

8. **Pricing in one glance** — fixes #16 · safe
   Now: purchases only inside the collapsed FAQ item.
   Change: turn the hero fact into "120 free levels · no ads" (already true) and keep the FAQ; optionally list the three purchases in the Features card "Three tools for when you are stuck" with "optional purchase".
   Why: "is it free?" is the first question for a word-game player.

Remaining low-impact misses: #26 "about twice as close" (needs the exact game value — owner); #2 accent not on the CTA (restyle — needs owner); #25 interactive sample, #15 maker note, #14/#29 player quotes after launch (all new content/claims — needs owner); #1/#8/#32 are deliberate F2P choices.

## What's already working
- #7/#30: plain 9-word headline plus a 5-word eyebrow says what it is.
- #3: concrete numbers (120 levels, 10 sets, 20–30 probes, 0°–100°).
- #10/#20: real gameplay screenshot right next to the headline.
- #9: copy only this game could have (thaw stages, probe temperatures, field kit).
- #11: one loop, every feature serves it.
- #12/#27: three optional purchases, no subscription mentioned, no ads.
- #23: a two-word compound name that explains itself.
- meta-tags [local]: canonical, og:* with 1200×630 image + alt + type + locale, twitter summary_large_image with title/description/image on index; 404 is noindex.

## Caveats
- Low-confidence (human eyes): #5 card punch, #18/#17/#24 headline feel, #20 desirability, #19 novelty, #13 wave, #15 maker presence, #11/#6/#4/#21/#9/#23 judgment, #32 needs real IAP prices.
- #1/#8/#27/#12 scored from site claims only — the Flutter game source was out of scope, so billing code was not checked.
- Deliberate deviations: free-to-play, no store link yet (pre-launch), no testimonials yet. They lower #1/#8/#14/#28/#29 by design; read the score in that light.
- No fix proposes sharing results, accounts, tracking or an email list; any such idea is marked needs owner.
- Repo sync (stash/pull) was not run: the orchestrator forbids git changes, and the owner is away. The report was written to the given output-dir, which is untracked (`?? .reports/design-optimizer/`).
- Share-card crop check: a local PIL crop of the asset (centre 630×630), not a real platform preview.
