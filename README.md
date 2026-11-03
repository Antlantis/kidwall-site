# KidWall website (draft, not deployed)

Static one-page site plus guides for **KidWall** (App Store id 6815543258). It uses plain HTML and one CSS file. There's no JavaScript (other than JSON-LD data blocks), no web fonts, no trackers and no analytics.

**Target:** the existing GitHub Pages repo https://github.com/Antlantis/kidwall-site (branch `main`), live at **https://antlantis.github.io/kidwall-site/**. That URL is already the App Store `sellerUrl`, so the listing doesn't need a resubmission. All canonical, Open Graph, JSON-LD and sitemap URLs use this base. If you move to a custom domain later, find and replace `https://antlantis.github.io/kidwall-site/` in `index.html`, `guides/*.html`, `sitemap.xml` and `robots.txt`.

## Structure and status relative to the repo (checked Nov 3, 2026, commit f93a231)

| Path | Status | Notes |
|---|---|---|
| `index.html` | **NEW** | The landing page. The repo has no index.html today, so GitHub Pages currently renders `README.md` ("# kidshield-site"), which is the blank page. |
| `assets/style.css` | **NEW** | Shared styles (light and dark mode, mobile-first breakpoints at 820px and 420px). |
| `assets/download-on-the-app-store.svg` | **NEW** | Apple's official US black badge, downloaded from developer.apple.com/assets/elements/badges/download-on-the-app-store.svg. Use it unmodified, per Apple's [App Store marketing guidelines](https://developer.apple.com/app-store/marketing/guidelines/). |
| `assets/icon-512.jpg`, `favicon.png`, `apple-touch-icon.png` | **NEW** | The app icon (artworkUrl512 from the iTunes Lookup API), resized. |
| `assets/screen-1.jpg` … `screen-7.jpg` | **NEW** | App Store iPhone screenshots 1–7 from `../shots/`. Frames 8 (setup) and 9–10 (paywall, welcome) are left out, per growth plan §3. |
| `guides/index.html` | **NEW** | The guides list. |
| `guides/how-to-limit-screen-time-on-iphone.html` | **NEW** | The first parent guide. |
| `sitemap.xml`, `robots.txt` | **NEW** | See the robots.txt caveat below. |
| `privacy.html` | **EXISTING, unchanged** | Byte-identical copy from the repo. Linked from the footer, privacy section and FAQ. Keep the URL, because the App Store description links to it. |
| `support.html` | **EXISTING, unchanged** | Byte-identical copy. Linked from the FAQ and footer. |
| `README.md` (this file) | **CHANGED** | Replaces the repo's one-line README (`# kidshield-site`). If you'd rather not publish these notes, keep the old README or rename this one. Jekyll will render it at `/README.html`. |
| `preview.png`, `preview-mobile.png` | Local only | Headless Chrome renders. **Don't commit them.** |

**To deploy (Anthony's call, not done):** copy everything except `preview*.png` into the repo root and push to `main`.

### Caveats
- **robots.txt:** GitHub Pages *project* sites live under `/kidwall-site/`, and crawlers only read `https://antlantis.github.io/robots.txt`. This file only takes effect if you move to a root or custom domain. Submit `sitemap.xml` in Google Search Console instead.
- **support.html is partly out of date for v1.2.** It says "pairing code" where the listing now says "family code", and its "Order of setup" describes the old flow ("Parent phone" → PIN → Remote Control) rather than v1.2's step-by-step setup. I left it unchanged as instructed. It's worth a refresh.
- **Rating** (5.0 from 4 ratings) is hard-coded in the hero fine print and in the JSON-LD. Update or remove both when it changes, because Google expects the markup to match the visible text.
- **Badge:** Apple's guidelines ask for the official artwork, unaltered, with clear space around it, and a link to the App Store product page. Both requirements are met.

## Every factual claim and its source

Abbreviations: **DESC** = App Store description (`lookup.json` → `results[0].description`, also https://apps.apple.com/us/app/kidwall/id6815543258). **LOOKUP** = `lookup.json` (https://itunes.apple.com/lookup?id=6815543258&country=us, fetched Nov 3, 2026). **LISTING** = `listing.json` summary (App Store page, fetched Nov 3, 2026). **PRIV** = https://antlantis.github.io/kidwall-site/privacy.html (effective Oct 7, 2026). **SUP** = https://antlantis.github.io/kidwall-site/support.html. **COMP** = `competitors.json`.

### Landing page (index.html)
| Claim | Source |
|---|---|
| Parental controls for kids' iPhones and iPads, run from your own phone | DESC line 1 |
| Built on Apple's Screen Time technology; approved with your Apple Account so it can't simply be deleted | DESC |
| Card per kid device (open / paused / bedtime / out of time) | DESC "From your phone" |
| Pause all apps instantly | DESC |
| "Ask for more time" button; answer +15 / +30 / +60 min or No | DESC + release notes (LOOKUP `releaseNotes`), and screenshot 2 |
| Daily limit with warning; bedtime, different each night; block apps and categories 24/7 | DESC |
| Web filter: Apple's filter + KidWall lists + your sites; other browsers hidden | DESC |
| Prevents deleting apps, in-app purchases, passcode/account changes | DESC |
| Place arrival/leave alerts; map location when turned on; alerts and Activity | DESC |
| Second parent phone with same family code | DESC "Both parents" |
| Rated 5.0, 4 ratings | LOOKUP `averageUserRating`=5, `userRatingCount`=4 |
| Requires iOS 18 or later; iPhone and iPad | LOOKUP `minimumOsVersion` 18.0, `features` iosUniversal; DESC |
| Version 1.2, 8.1 MB, rated 4+, Lifestyle (JSON-LD) | LOOKUP |
| Free; Premium $4.99/mo, $39.99/yr; 7-day free trial | LOOKUP `price` 0; LISTING `in_app_purchases_from_page`; DESC |
| One subscription covers your Family Sharing group | DESC |
| Premium needed for remote control, alerts, location, place alerts, multi-parent; without it kids' devices keep current rules | DESC |
| Renewal and cancel terms (24 h, Settings › your name › Subscriptions) | DESC |
| "$39.99/yr is less than any 12-month plan listed by seven popular paid parental control apps on the US App Store (Nov 3, 2026)" | COMP: lowest 12-month IAP per app: Kidslox $49.99, OurPact $69.99, Bark $49.99 (Jr) / $99.99, Qustodio $54.99, Circle $89.99, FamiSafe $59.99, Kids360 $49.99. See the caveats below. |
| Encrypted with family code before leaving phone; we can't read it | DESC "Private by design" |
| End-to-end, AES-256-GCM, synced via Apple iCloud (CloudKit); unreadable to Apple | PRIV ("Security", "The short version") |
| No ads, no tracking | DESC; PRIV |
| No analytics/tracking SDKs, no accounts/sign-in, never sold or shared | PRIV "What we don't do" |
| Can't read chats in any app; doesn't collect messages, browsing history, keystrokes, photos, contacts, per-app usage history | Release notes (LOOKUP); DESC "no reading messages"; PRIV |
| ntfy/webhook alerts are optional, off by default, and not encrypted by KidWall | PRIV "Optional alert services" |
| Privacy label: Data Not Linked to You (Precise Location, Name, Device ID, Other Usage Data), App Functionality | LISTING `privacy_label_page` |
| Needs child Apple Account in your Family Sharing group | DESC; SUP |
| Game & chat safety guides in the app | DESC / release notes |
| Support email ant.sd.shield@gmail.com | SUP, PRIV (already public) |
| Screenshot captions | Wording from growth plan §3, checked against DESC features |

**Pricing caveats.** Google Family Link and Screen Time Labs are free with no IAP, so the claim is limited to *paid* apps. Kidslox also lists a **6-month plan at $19.99**, which works out to $39.98 a year, one cent under KidWall. That's why the page says "12-month plan" rather than "cheapest yearly". The App Store shows only an app's top in-app purchases, so a competitor could have an unlisted cheaper plan. Re-check before you advertise this line.

### Guide (how-to-limit-screen-time-on-iphone.html)
| Claim | Source |
|---|---|
| iOS 27 redesign: Time Allowances, Screen Time Schedules; manage from parent device; Family Sharing + Child Account; Settings › Family › child › Screen Time; passcode must be set on parent's own device | https://support.apple.com/en-us/108806 (published Oct 26, 2026) |
| Time Allowances steps; Schedule steps; Block App/Website; Filtering (Limit Adult Websites / Approved Websites Only); Ask to Buy steps; blocked app is dimmed, not deleted; default-on ages | https://support.apple.com/en-us/105121 (published Oct 26, 2026) |
| Upgrade needs every device used in the last 90 days on version 27; View Family Devices; Software Update; Get Started; Legacy Devices keep old Screen Time | https://support.apple.com/guide/child-safety/update-family-devices-parental-controls-jrzvk3ml3unm/web |
| iOS 26 Downtime, Block at Downtime, App Limits, Always Allowed steps; 5-minute reminder; limits can be ignored by default; hourglass icon | https://support.apple.com/guide/iphone/set-schedules-with-screen-time-iphb0c7313c9/26/ios/26 |
| Section 5 tips | Editorial advice, not factual claims |
| KidWall paragraph | DESC, LOOKUP, LISTING (as above) |

## Left out on purpose (unverified or not applicable)
- No testimonials, user counts, awards or press quotes. None exist in the data.
- "Cheapest yearly plan among competitors" is softened to "less than any 12-month plan listed by seven popular paid apps". See the pricing caveats.
- "$4.99/mo undercuts Bark, Circle, Kids360, OurPact" (growth plan) isn't used: Kidslox lists $3.99/mo and OurPact Plus lists $1.99.
- "Can't be deleted" is phrased as "can't simply be deleted" / "not on their own", matching DESC.
- No privacy-label claim about "Data Used to Track You", because `listing.json` only records the Not Linked category.
