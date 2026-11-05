# KidWall website

The website for [KidWall](https://apps.apple.com/us/app/kidwall/id6815543258), a parental control app for iPhone and iPad. It's live at **https://antlantis.github.io/kidwall-site/** (GitHub Pages, branch `main`).

## Pages

| Page | What it is |
|---|---|
| `index.html` | Home page. Its address is the App Store listing's developer website. |
| `guides/` | Parent guides, starting with how to limit screen time on a child's iPhone |
| `support.html` | Help and troubleshooting. The App Store listing's Support URL. |
| `privacy.html` | Privacy policy. Linked from the App Store listing and from the app. |
| `assets/` | Styles, the app icon, App Store screenshots and Apple's App Store badge |
| `sitemap.xml` | Submitted in Google Search Console |
| `robots.txt` | Only takes effect if the site moves to its own domain |
| `googled21fdb729c043518.html` | Google Search Console verification. Don't delete or rename it. |

Keep the `support.html` and `privacy.html` addresses as they are: the App Store listing links to both, and the app links to `privacy.html`.

Full URLs (canonical, Open Graph, JSON-LD and the sitemap) use `https://antlantis.github.io/kidwall-site/`. If the site moves, replace that in `index.html`, `guides/*.html`, `privacy.html`, `sitemap.xml` and `robots.txt`. When you change a page, update its `<lastmod>` in `sitemap.xml`.

The site is plain HTML and one CSS file, with no trackers, analytics or web fonts.

## Contact

ant.sd.shield@gmail.com
