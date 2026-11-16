# design-optimizer — fixes applied (2026-11-16)

Audit: `design-optimization.md` (merged, PARTIAL: website-agent-readiness stopped at its G3 plan gate here because
the search-optimizer run already wrote that plan; viral-product-evaluator scored pricing from the site only).
The game-clone pipeline pre-authorized safe usability, accessibility and copy-clarity fixes that keep the approved
look and make no new claims (owner away). Applied:

| ID | Fix |
|---|---|
| D-01 | "Not out yet. This page will link to the App Store on launch day." under both "Coming soon" pills |
| D-03 | header nav stays visible below 820 px (FAQ, Support); "How it plays" is the hero's own button there |
| D-04 | JSON-LD `offers` with `PreOrder` removed (there is no pre-order) |
| D-05 | llms.txt: "to be listed on the App Store as…" |
| D-06, D-07 | deployed with this merge (sitemap, llms, robots, 404, shorter title/description, Twitter tags); root robots.txt and llms.txt list the site |
| D-08 | won screenshot alt and caption describe what it shows (HONEY thawed, best probe 100°), not a result sheet |
| D-10 | `twitter:image` (icon) on privacy and support |
| D-12 | hero fact "A new daily word" instead of the unexplained "Daily Core" |
| D-13 | home screenshot alt: "Expeditions (the Core sets)" |
| D-15 | header icon from 80/120 px files with `srcset` instead of the 256 px file |
| D-16 | final section's second button "See how it plays"; support link moved into the note under it |
| D-18 | "Optional in-app purchases" in the hero facts |

Left for the owner (restyle, layout or new content): D-09 share card with wordmark, D-02 share/save, D-11 self-hosted
fonts, D-14 move the screenshot higher on phones, D-17 a feeling-led opening line, D-19 split the features
section, D-20 a comparison line (4.3 copycat risk, not advised), D-21 testimonials/interactive sample. W-01 index.md
and W-02 (API/OAuth/MCP discovery) not applicable to a static page.

Owner check: the footer and the JSON-LD author now say "Luong Nguyen", matching the App Store copyright line used by
the 24 earlier games on this account (docs/APP-STORE-CONNECT.md). Change both if Thawscope ships under another seller.
