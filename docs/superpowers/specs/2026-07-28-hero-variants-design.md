# Hero Variants Showroom — Design

**Date:** 2026-07-28
**Status:** Draft — awaiting user review

## Problem

The site owner rejected the current hero section. The specific objection on record is the
blurred "wave streak" background (`index.html:266-292`) — wide curving SVG paths with a
28px blur behind a 3-slide carousel. No other objection has been stated, so the rest of the
current hero is treated as open-to-change but not known-bad.

We need to put several distinct hero directions in front of the owner so he can pick one,
rather than guessing at a single replacement.

## Constraints

- **Asset-free.** No product photography, no video, no stock imagery. Typography, gradients,
  geometry, CSS and SVG only. Confirmed with the user.
- **No wave language.** No blurred organic streaks, no soft curving gradient ribbons, nothing
  that reads as the thing he rejected. This is the one hard constraint.
- **Existing brand system.** Navy (`#08296C` family), teal (`#45C0BE`), gold (`#C9A84C`),
  orange (`#E89B3C`). Kufam for headings/branding, Cairo for body, Aref Ruqaa for artistic
  taglines. Per `GEMINI.md`.
- **Arabic RTL.** `lang="ar" dir="rtl"`, logical properties (`start`/`end`), correct icon
  mirroring. Must hold at 390px and 1440px.
- **Nothing published.** No push, no deploy. The owner reviews via screenshots.
- **`index.html` untouched.** The live page does not change until he picks a winner.

## Delivery

A standalone `hero-options.html` in the repo root, built and run locally only.

- Fixed chooser bar at the top: `خيار ١` … `خيار ٦`, plus the concept's Arabic name.
- Clicking a number swaps the full-screen hero in place. Number keys `1`–`6` and arrow keys
  also switch, for fast A/B comparison.
- All six variants exist in the DOM; only the active one is visible. Carousel JS runs only
  on the active variant so background variants don't animate unseen.
- The real nav bar renders over every variant, and a sliver of the "من نحن" section shows
  beneath, so each hero is judged in context rather than in isolation.
- Carries `<meta name="robots" content="noindex">` as a safety net in case it is ever pushed
  by accident.
- Committed locally so the work is not lost. **Never pushed** — GitHub Pages deploys `main`
  to `tammgroup.sa`, so pushing would publish it.

Screenshots are the actual deliverable to the owner: six desktop captures at 1440×900 and
six mobile captures at 390×844. He will most likely view them on a phone, so the mobile set
is the one to send first; the desktop set is for anyone reviewing on a laptop.

> **Amendment (2026-07-28):** After a first pass, the set was narrowed to three variants —
> the Islamic tessellation, the minimal editorial, and the category tiles (originally ٢, ٥, ٦;
> renumbered ١–٣). The gold frame, precision grid and diagonal split were dropped. Delivery
> changed from screenshots-only to publishing `hero-options.html` on tammgroup.sa (noindex,
> unlisted) so the owner can browse the options himself. More variants may be added later.
>
> **Amendment 2 (2026-07-28):** Three creative variants added — ٤ المسرح الذهبي (CSS/SVG
> trophy under a spotlight cone with a sweeping glint), ٥ الزجاج التفاعلي (frosted-glass card
> over color orbs, 3D pointer tilt with specular sheen; idle drift on touch), ٦ سماء التميز
> (interactive constellation canvas, pauses when its panel is hidden). Two intermediate ٥
> concepts (engraved plaque, kinetic type marquee) were built and rejected during review.

## The six variants

Shared across all of them: `min-h-screen`, the existing nav overlaid, the same primary CTA
(`اكتشف خدماتنا` → `#services`) and secondary CTA (`تواصل معنا` → `#contact-footer`), and
`prefers-reduced-motion` respected on every animation.

Static variants use the current slide-1 copy — `تم... لأن الانطباع يدوم` over
`نصمم لحظات التقدير ونصنع الذكريات التي تبقى`. Carousel variants keep all three existing
taglines unchanged.

### ١ — الإطار الذهبي (Gold plaque frame) · static

Flat navy-700 `#051941`, nothing behind the content. A gold hairline frame inset from the
viewport edge, with a small ornament at each corner. Inside the frame, top to bottom: the
TAMM logo mark, the headline, the subline, the two CTAs.

The frame reads as an award plaque or certificate — the object the business actually sells.
On load the frame rules draw themselves in via `stroke-dashoffset` and the content fades up
behind them. The existing gold shimmer stays on one word of the headline.

### ٢ — الزخرفة الإسلامية (Islamic tessellation) · carousel

Flat navy-800 `#03102B` under a tiled eight-point girih star pattern in teal at ~5% opacity,
120px tile. A wide, very low-opacity gold radial sits behind the headline to lift it off the
pattern — a centred vignette, not a directional streak.

Keeps all three slides, the dots and the arrows. The slide transition changes from a
horizontal slide to a crossfade with a 12px rise, which reads calmer and further distances it
from the motion he rejected.

### ٣ — الشبكة الهندسية (Precision grid) · carousel

Navy-900 `#020816` under a crisp 1px teal grid at 4% opacity, 64px cells — sharp lines, no
blur anywhere. One gold and one teal accent line cross at an off-centre point, and small
measurement ticks run along the bottom edge.

The vocabulary is drafting, engraving and precision, which is what a shields-and-trophies
workshop does. A dark radial vignette at the edges keeps the grid from competing with the
type. Carousel and its existing horizontal slide transition are kept as-is.

### ٤ — التقسيم القطري (Diagonal split) · static

Two flat colour fields divided by a clean diagonal via `clip-path`: navy-700 against
teal-900 `#0E2626`. Hard edge, no gradient, no feathering.

A large flat shield (درع) silhouette sits in the teal field at ~8% white, cropped by the
diagonal so it reads as texture rather than illustration. Content is start-aligned in a
`max-w-2xl` column rather than centred, which is the biggest structural departure from the
current hero.

### ٥ — الحد الأدنى (Minimal editorial) · static

Near-flat `#020816`. A small teal kicker with wide letter-spacing, then a very large Aref
Ruqaa headline running up to `text-8xl` at `lg`, then a single gold hairline rule, then one
primary CTA and one quiet text link. A scroll cue at the bottom.

Maximum restraint — the confident, expensive-looking option. It lives or dies on the
typography, which is the point.

### ٦ — بطاقات الفئات (Category tiles) · static

Two columns at `lg`. Headline, subline and a single CTA on the start side; a 2×2 grid of
category tiles on the end side — دروع تذكارية، كؤوس، ميداليات، هدايا مخصصة — each a bordered
card with a teal line icon that lifts and turns its border orange on hover. Flat navy-700
background, no pattern.

The only variant that puts product categories above the fold. It is the least "designed" and
the most likely to actually convert, which is why it belongs in the set alongside ٥.

## Non-goals

- Changing `index.html` or any section below the hero.
- Publishing, pushing or deploying anything.
- Copywriting. Existing taglines are reused verbatim.
- Building the winning variant into the live page — that is the follow-up task once the owner
  picks, and it is out of scope here.

## Success criteria

- Six heroes, each visually distinct enough that the owner can tell them apart from a
  thumbnail.
- Not one of them uses a blurred wave, streak or ribbon.
- All six render correctly RTL at 390px and 1440px, with no horizontal overflow.
- Both carousel variants advance, loop and respond to their dots and arrows.
- Twelve screenshots produced: six mobile, six desktop.
