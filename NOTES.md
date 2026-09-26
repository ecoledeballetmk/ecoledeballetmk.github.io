# rebuild — what still needs Miho's input

Plain static HTML/CSS. No build step, no dependencies. Open `index.html`, or
serve the folder with `python3 -m http.server 8000`.

All Japanese copy on these pages is hers, taken from the 2016–2022 archive in
`../archive/`. Nothing has been written on her behalf except short connective
labels and the contact instructions.

---

## Held out of the live pages — needs confirming before it goes back

Three of the eight 特徴 bullets from the old site are claims that may have
expired. They are **not** on `philosophy.html` right now. The original wording,
ready to paste back into the `<ul class="features">` list:

```html
<li>小林紀子バレエアカデミーとのジュニアアソシエイト制度</li>
<li>発表会など、費用の負担をかけない努力</li>
<li>振替制度</li>
```

- **小林紀子バレエアカデミーとのジュニアアソシエイト制度** — an affiliation with
  a third-party institution. Republishing this unverified is the riskiest of the
  three.
- **発表会など、費用の負担をかけない努力** — a cost commitment.
- **振替制度** — a make-up-lesson policy.

The other five bullets are statements about her own teaching and are on the page.

## Her profile stops at 1994

`profile.html` reproduces the timeline exactly as archived: 5歳 through 1994年
(小林紀子バレエシアター退団). That leaves roughly thirty years unaccounted for —
founding the school, teaching, any further RAD work. Worth extending.

## 設備 copy assumes she owns the studio — she doesn't

`facilities.html` reproduces her 2016 text, which is written from the position
of someone who fitted out their own room:

> スタジオに対してL字に装備してあります
> バレエを踊りやすいリノリウムを使用しています

She now **rents** studio space rather than running her own. The venues are
consistent, so they can be named and published, but she does not own the
mirrors or the floor and cannot claim to have installed them.

Her reasoning is unaffected — a square room, mirrors she can check position in,
a floor that is neither slippery nor grabby. What changes is the claim: from
*we built it this way* to *we book rooms that meet these conditions*. That
arguably reads stronger, since it says she turns down rooms that don't.

Needs rewording in her voice, not mine. Same applies to the 設備 block on
`index.html` and the 特徴 bullet 「バレエを踊ることのできるスペースと環境」
on `philosophy.html`.

## Everything here needs Miho's review before publishing

All Japanese copy is hers, and most of it is from 2016-2022. Nothing on these
pages should go live until she has read it back.

## Placeholders to replace

| Where | What |
|---|---|
| `studios.html`, `index.html` | Venue photo, and the real names/addresses for each location |
| `facilities.html` | Studio interior photo |
| `profile.html` | Portrait |
| `classes.html` | Class list and timetable — currently an honest "準備中" note |

Placeholder art is inline SVG, so there are no image files to clean up. Search
for `class="placeholder"` and replace the whole `<svg>` with an `<img>`.

The archive has eight real studio photos at `../archive/img/gallery/`, but they
show a location she no longer has, so none of them are used here.

## Locations

Deliberately unnamed: スタジオ A / スタジオ B. `studios.html` has one
`.location` block per venue — copy a block to add one, delete one to remove it.
The grid reflows by itself. No count is hardcoded anywhere.

## Contact

Email only, `info@ecoledeballetmk.com` — not live yet, you said you'd set it up.
No phone number appears anywhere on the site. `contact.html` states plainly that
phone enquiries aren't taken, so nobody goes looking for a number.

## Things that carried no data and were dropped

- The old contact form was server-side WordPress (contact-form-7). Static pages
  can't run it; the email link replaces it.
- Google Analytics (`UA-18154739-1`) — a dead Universal Analytics property.
- Twitter and Facebook links (`@ecoledeballetmk`) — not carried over; add them
  back if those accounts are still hers and still active.

## SEO

Canonical host is **`https://www.ecoledeballetmk.com`**. It is hardcoded in
`sitemap.xml`, `robots.txt`, and the `canonical` / `og:url` tag of every page.
If you end up serving from the apex instead, those are the places to change —
and redirect apex to www (or the reverse) so only one form is reachable.

In place: canonical tags, Open Graph + Twitter card on all 7 pages, an
`Organization` JSON-LD block on the homepage, `robots.txt`, `sitemap.xml`,
`favicon.ico`, and a 512px app icon.

`img/og-card.png` (1200x630) and `img/icon.png` are generated from
`img/brand-logo.png` — the card is the logo on the site's ground colour, the
icon is the dancer cropped out of the mark. Regenerate them if the logo changes.

**The real limit is content, not markup.** Parents search "<place> バレエ教室",
not "バレエ教室". With no venues on the site there is nothing to rank for those
queries, and no tag work substitutes for it. When the locations are settled:

1. Put the real venue name, address and nearest station on `studios.html`.
2. Switch the homepage JSON-LD from `Organization` to `LocalBusiness` and add
   `address` / `areaServed`. It is `Organization` today precisely because
   `LocalBusiness` without an address would be a fabrication.
3. Create a Google Business Profile per venue. For a local school this outweighs
   everything already done above.

Also worth knowing: the exact string `バレエ教室` appears in the meta
descriptions but in **no page's body copy**. Miho's prose says バレエ constantly
and never the compound people actually type. Worth one natural mention per page
once the locations give you a sentence to put it in.

## Adding a page

Nav lives in every file (the cost of no build step). If you add a page, add the
`<li>` to all of them, and set `aria-current="page"` on the one that matches.
