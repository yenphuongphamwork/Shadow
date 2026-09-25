---
name: video-testimonial-artifact-export
description: "The Luis Benz + Tomislav Mozanic video testimonials — from thank-you gift to going live on the homepage, and today's rework splitting them into their own section"
metadata:
  node_type: memory
  type: project
  originSessionId: ae4a8ea3-8586-41df-ae88-54e4113fc39f
  modified: 2026-09-25
---

**Origin:** buyer Luis Benz (luisbenz@web.de, Germany) recorded a video testimonial for Teeinblue; she processed a €200 thank-you gift for him (2026-09-15). A second testimonial from Tomislav Mozanic (Owner of Life-Decor) exists too. Both ended up embedded on the homepage as the two "video finale" YouTube embeds inside the `tib-success-stories` section (`video_1_url` = `youtu.be/VEkApgI49Bs` = Luis Benz, `video_2_url` = `youtu.be/HpWR2lCFhOk` = Tomislav Mozanic).

**Problem found (2026-09-25, her review with screenshots):**
1. The videos only appeared via a scroll-jacked crossfade at the very end of the success-stories filmstrip (682vh of pinned scroll) — buried, needed a lot of scrolling, and shouldn't share a section with the customer-stories case-study cards.
2. The section header ("65%... Discover how top POD stores...") was visibly misaligned (further right) than the story card below it.
3. The two videos rendered oversized (2000px container, edge-to-edge on a `4vw` pad) — visibly wider/differently-margined than every other homepage section (which use 1200–1500px containers).
4. No "watch more" path if more testimonial videos get added later.

**Root causes found:**
- Alignment bug: `sections/tib-success-stories.liquid` had a redundant `#tibx-scope .tib-stories-header{padding:0 4vw;}` override that only padded the header, not the swiper — both already inherited the same `4vw` from the parent `#tibx-scope` wrapper, so the extra rule double-padded the header only. Removed it; header and card now share the exact same left edge (verified via `getBoundingClientRect` in-browser: both at `257.59375px` at 1440px viewport).
- Sizing bug: the video grid used an ad hoc `max-width:2000px;padding:0 4vw` instead of the theme's real container system.

**Fix shipped to TEST theme only (`teeinblue-partner`, theme `198236930129`), 2026-09-25 — not yet on live theme `82115067985`:**
- New standalone section `sections/tib-video-testimonials.liquid`: plain static section (no scroll-jack), block-based (`type: "video"`, so more testimonials can be added as blocks later — partially solves the "no path to more videos" gap), `container_width` setting defaulting to **1200px** to match its immediate neighbors (`tib-integration-grid`, `tib-infinite-reviews`, both 1200px) — verified in-browser both containers land at identical `left:120px / right:1320px` at 1440px viewport.
- Placed right after `tib_success_stories_9YdBkm` and before `tib_infinite_reviews_3aRjUz` in `config/settings_data.json`'s `content_for_index` (new section key `tib_video_testimonials_9QwZk1`), carrying over the same two real video URLs.

**Corrected 2026-09-25 after her first round of review:**
- **`tib-success-stories.liquid` reverted entirely to match live**, not just "cleaned up" — turns out the whole scroll-jack filmstrip (682vh pinned scroll, the header/card alignment bug, everything) only ever existed on the TEST theme; the live theme's version of this file is the plain, un-hacked original swiper (confirmed byte-for-byte: fetched `sections/tib-success-stories.liquid` from theme `82115067985` and it has zero `tibx`/filmstrip/video references). She asked to leave this section exactly as live — so the test theme's copy was overwritten with the live theme's actual file content, discarding the filmstrip experiment completely rather than trying to preserve/fix it. **Lesson: when she says "leave X as the current live version," check what's *actually* live via the API rather than assuming the test-theme's more-elaborate version is the baseline being preserved.**
- **CTA destination corrected**: not YouTube channel (my first guess, which she'd initially agreed to) — she clarified visitors who want to watch more videos AND read reviews in depth should go to the existing **Wall of Love page** (`https://teeinblue.com/pages/wall-of-love`, confirmed live, has 2 *different* testimonial videos — `TzJm-lR-fLQ`, `aQXxICWYklE` — plus a long list of written reviews). Button relabeled "Watch more videos & reviews", `target="_blank"` removed since it's an internal page now, not external YouTube.
- **Trust badges removed for real**: she first asked (via someone she called "sếp"/boss) to drop the "4.9 Shopify App Store" / "4.8 TrustPilot" badge chips from the `tib-infinite-reviews` section entirely, framed as wanting the video to sit before the running-reviews row (already true structurally — video-testimonials sits between success-stories and infinite-reviews). Built an A/B duplicate first per her request to compare side-by-side, then she confirmed removal — duplicate deleted, badges removed from the one real `tib_infinite_reviews_3aRjUz` instance (`badge_1_text`/`badge_2_text` set to `""`, not just omitted — Shopify falls back to the schema's own default text if a `richtext` setting key is missing entirely, so it must be an explicit empty string to actually hide).

**Not yet done:** she hasn't given final sign-off on this latest round yet. Once she does, apply the same changes (success-stories revert, new video section + order, badge removal) to the live theme `82115067985` — do not touch live until confirmed. See [[tib-shopify-theme-reference]] for store/theme IDs and API mechanics, [[genai-features-page-stats-project]] for the sibling Features-page task using the same test-theme workflow.
