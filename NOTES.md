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

### 鏡 is commented out as of this pass

The 鏡 tenet is wrapped in an HTML comment in `index.html`, not deleted. Neither
rented studio is believed to have L-shaped mirrors any more, so the claim would
describe equipment that isn't in the room. Restore it only if a venue actually
has them — and reword 「装備してあります」 when you do.

The 設備 lede still says 「ポジションの確認をするための鏡」. That was left in: it
claims only that there are mirrors to check position in, which is true of any
rented dance studio, and makes no claim about their shape or who hung them.

### The rest of the block has the same shape of problem

The remaining 設備 text on `index.html` reproduces her 2016 text, which is
written from the position of someone who fitted out their own room:

> スタジオに対してL字に装備してあります
> バレエを踊りやすいリノリウムを使用しています

She now **rents** studio space rather than running her own. The venues are named
and published (天王台 / 柏, see Locations below), but she does not own the mirrors
or the floor and cannot claim to have installed them.

Her reasoning is unaffected — a square room, mirrors she can check position in,
a floor that is neither slippery nor grabby. What changes is the claim: from
*we built it this way* to *we book rooms that meet these conditions*. That
arguably reads stronger, since it says she turns down rooms that don't.

Needs rewording in her voice, not mine. The 特徴 bullet
「バレエを踊ることのできるスペースと環境」 on `philosophy.html` has the same
problem and should change with it.

**Naming the buildings made this more visible, not less.** A reader who sees
ハチヤビル and カプリコーンビル on `studios.html` and then reads
「リノリウムを使用しています」 on the homepage is being told she laid the floor in
two rented rooms in two different buildings. 「L字に装備してあります」 said the
same thing about the mirrors, which is why it is now commented out — the floor
line is the one still standing.

The upside of deleting `facilities.html` (below) is that there is now exactly one
place to fix: the `<ul class="tenets">` block in `index.html`.

## Everything here needs Miho's review before publishing

All Japanese copy is hers, and most of it is from 2016-2022. Nothing on these
pages should go live until she has read it back.

## No photographs, by decision

Every placeholder is gone, and so is the `.placeholder` CSS. The only image on
the site is the logo (plus the icon and OG card generated from it). There are no
studio photos, no classroom photos and no portrait.

`.figure` is still in `site.css` and unused, so a photo can be added later with
no CSS work:

```html
<figure class="figure">
    <img src="img/whatever.jpg" width="1200" height="800" alt="…">
    <figcaption>…</figcaption>
</figure>
```

The archive has eight studio photos at `../archive/img/gallery/`, but they show a
location she no longer has, so none of them are used — and they would be
classroom photos, which are ruled out regardless.

## Locations

Two venues, both rented rooms:

| Name on the site | Address | Station |
|---|---|---|
| 天王台スタジオ | 千葉県我孫子市天王台2-1-21 ハチヤビル2F | 天王台駅（JR常磐線）から徒歩5分 |
| 柏スタジオ | 千葉県柏市明原1-2-4 カプリコーンビル2F | 柏駅（JR常磐線・東武アーバンパークライン、東京メトロ千代田線直通）から徒歩10分 |

These appear in **three** places that must stay in agreement, because there is no
build step:

1. `studios.html` — one `.location` block per venue
2. `index.html` — the same blocks in the スタジオ section
3. `index.html` — the JSON-LD `@graph`, one `Place` node per venue

`contact.html` names them only as 「天王台 ／ 柏」 and links to `studios.html`, so
it is deliberately not a fourth copy. Copy a `.location` block to add a venue,
delete one to remove it; the grid reflows by itself and no count is hardcoded.

**Postal codes: deliberately omitted.** Not wanted on the site, and not in the
JSON-LD `PostalAddress` blocks either. Don't add them back.

Both walking times are confirmed and on the site. They came from Miho, not from
a map — leave them alone unless she corrects them.

千代田線 is written as **直通** on 柏 because that is what it is: 東京メトロ千代田線
trains through-run onto the 常磐線各駅停車 and reach 柏. The station is not a
千代田線 station in its own right. It is listed because it is the line a parent
commuting from central Tokyo would actually be on.

It is **not** on 天王台 for the same reason, in reverse: 各駅停車 normally
terminates at 我孫子, one stop short, so 天王台 is a 快速 station. A handful of
early-morning and late-night 各停 run through to 取手 via 天王台, which is too
marginal to put on a school's access line.

**Still missing:** a room / suite number, if either building has more than one
tenant on 2F.

Also worth knowing: the two addresses were given as 「2階」 and 「2F」. Both are
written **2F** on the site for consistency.

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

In place: canonical tags, Open Graph + Twitter card on all 5 pages, a
`DanceSchool` JSON-LD `@graph` on the homepage with a `Place` per venue,
`robots.txt`, `sitemap.xml`, `favicon.ico`, and a 512px app icon.

`img/og-card.png` (1200x630) and `img/icon.png` are generated from
`img/brand-logo.png` — the card is the logo on the site's ground colour, the
icon is the dancer cropped out of the mark. Regenerate them if the logo changes.

**The real limit is content, not markup.** Parents search "<place> バレエ教室",
not "バレエ教室". The venues now give the site something to rank for:

- 天王台 / 我孫子 / 柏 / 明原 appear in the body copy and the meta descriptions of
  `index.html`, `studios.html` and `contact.html`, and in `areaServed`.
- `studios.html` carries the compound 「クラシックバレエ教室」 in its lede, which
  fixes the old problem that `バレエ教室` was in the meta tags and in no page's
  body text. Her own prose says バレエ constantly and never the compound people
  actually type, so this is the one sentence where it lands naturally.
- The homepage JSON-LD is now `DanceSchool` (a `LocalBusiness` subtype) with a
  `Place` per venue, which is what the old note was waiting on.

**The one big thing still undone: a Google Business Profile per venue.** For a
local school this outweighs everything else in this section combined, and with
two confirmed addresses there is nothing blocking it. Note that a rented room
usually fails GBP's "staffed during stated hours" test, so expect to register as
a service-area business, or only claim a venue where she has regular scheduled
hours.

## Hosting — GitHub Pages

Static, no backend, no form handler, ~400KB. Pages fits it well. Nothing here
has been done yet; this is the pre-launch list.

### Terms of service

The clause worth knowing:

> GitHub Pages is not intended for or allowed to be used as a free web hosting
> service to run your online business, e-commerce site, or any other website
> that is primarily directed at either facilitating commercial transactions or
> providing commercial software as a service (SaaS).

A brochure site for a business is not the same as running a business on Pages —
organization sites are an explicitly supported category. This site has no
checkout, no payment processing, no booking flow and no SaaS, only information
and a `mailto:`. That is clear of the restriction.

It would become questionable if tuition payments or an online enrolment
transaction were added to the site. Enquiries by email that lead to payment
arranged elsewhere are not that.

**The wording is genuinely ambiguous, though.** "To run your online business"
can be read as covering any business site, not just transactional ones. The
reading above — that the trailing "primarily directed at facilitating
commercial transactions" defines the category — is supported by GitHub
documenting organization sites as a use case, and by how many company marketing
sites run on Pages. It is an interpretation, not a rule anyone can point at.

Soft limits: 1GB repo, 100GB bandwidth/month, 10 builds/hour. Not close to any.

### If the ambiguity isn't worth it

**Cloudflare Pages** or **Netlify**. Both free, both explicitly fine with
business sites, both deploy this repo unchanged with free HTTPS and a custom
domain. Cloudflare Pages has no private-repo plan restriction either, which
removes the GitHub Team question as well. Netlify adds native form handling if
a contact form is ever wanted.

Given the ToS reading is a judgement call and switching costs nothing, either
is a reasonable way to not have the question at all.

### Repository layout

Everything served lives in **`docs/`**. Everything else stays at the repo root
and is never published:

    docs/            <- the site, and only the site
      index.html  css/  js/  img/
      robots.txt  sitemap.xml  favicon.ico
      CNAME        www.ecoledeballetmk.com
      .nojekyll    turns Jekyll off; nothing here needs processing
    NOTES.md       <- this file, not served
    .gitignore

Named `docs/` because that is the one non-root folder GitHub Pages will publish
from when the source is a branch. Set it under **Settings > Pages > Build and
deployment**: source `Deploy from a branch`, branch `main`, folder `/docs`.

The point of the split is keeping `NOTES.md` off the public site — it names the
claims that are unverified and says the 設備 copy is inaccurate. Pages serves
whatever sits in the publishing source, and Jekyll would have turned it into
`/NOTES.html`.

Every path in the site is relative and internal, so the folder can be renamed
without breaking a link if you move to a host that allows any output directory.

### Before going live

- **A private repo does not make the site private.** Pages output is publicly
  reachable regardless — per-site access control is Enterprise only. The repo
  stays private; the site is open to anyone with the URL.
- **Pages from a private repo needs a paid plan.** Free publishes only from
  public repos. `ecoledeballetmk` is an org, so Team or above. Confirm before
  committing to Pages.

### Custom domain

`docs/CNAME` containing `www.ecoledeballetmk.com` — it has to sit in the
publishing source, not the repo root, or Pages never reads it. Plus DNS:
`www` as a CNAME to `<org>.github.io`, and A records at the apex pointing to
GitHub's Pages IPs so the bare domain redirects. Turn on **Enforce HTTPS** once
the certificate is issued — it is free and auto-renewing, but not on by default.

This has to match the canonical host already hardcoded in `sitemap.xml`,
`robots.txt` and every page's `canonical` tag, which is currently **www**.

### Smaller items

- **`mailto:` will be scraped.** Unavoidable on any host, but her inbox is the
  only contact channel on the site, so set up spam filtering before launch
  rather than after.
- **Google Fonts sends every visitor's IP to Google.** Self-hosting the two Zen
  families removes a third-party dependency, drops a render-blocking request,
  and sidesteps the question entirely. Not urgent, worth doing eventually.
- **No contact form is possible on Pages.** Email-only is the current design,
  which is fine. If a form is ever wanted, it needs a third party (Formspree
  and similar) or a different host — Cloudflare Pages and Netlify both handle
  forms natively and are otherwise equivalent for a site like this.

## Adding a page

Nav lives in every file (the cost of no build step). If you add a page, add the
`<li>` to all of them, set `aria-current="page"` on the one that matches, and add
a `<url>` to `sitemap.xml`.

## Removed: 設備 (`facilities.html`)

Deleted as a near-duplicate. It carried three items — スタジオ / 鏡 / 床 — and the
homepage 設備 section carried a condensed version of the same three. One screen of
content behind its own URL, ~90% of it repeated.

Her **full** archive wording is now the homepage block, replacing the condensation
that was there, so nothing of hers was lost — the page-lede became the
`.section-lede`, and the longer スタジオ paragraph and the heading
「バレエ用の床、リノリウム」 came across verbatim.

Also gone with it: the `.tenets + .prose` spacing rule that briefly existed for a
read-through link. `.note` is still in `site.css` and now unused by any page —
harmless, it is a generic utility.

## Removed: クラス案内 (`classes.html`)

Deleted, not hidden — class lists, timetables and fees are given by email only,
so a page saying 「準備中」 promised something that was never coming. Its nav item
is gone from all six remaining pages and its `<url>` is out of `sitemap.xml`.

Nothing was lost with it. Its lede — 年齢に応じたクラス編成, 少人数のクラス編成,
一人一人の身体に触れ正しいポジションに導くレッスン — is already on
`philosophy.html` as three of the 特徴 bullets, verbatim.

If a timetable is ever wanted, recreate the page rather than reviving the note.
`git log` has the original, including a commented-out `<table class="schedule">`
skeleton — but note that `site.css` has **no** table styles at all, `.schedule`
included, so that skeleton would have rendered as an unstyled browser table. A
timetable means writing the CSS too.
