# StrikeIQ promo site

Static promotional website for the [Strike IQ](https://github.com/maxim-austin) Android bowling tracker (`com.strikeiq`), built for GitHub Pages. No build step, no framework — plain HTML/CSS with a small inline script.

**Live URL (once published):** https://maxim-austin.github.io/strike-iq-site/

## Structure

```
index.html                  Landing page (hero, features, analytics, roadmap, FAQ, download)
privacy.html                Privacy & Data Safety worksheet + public privacy policy
404.html                    Not-found page (GitHub Pages picks this up automatically)
robots.txt / sitemap.xml    SEO
assets/css/style.css        Design system (Strike IQ palette: #0E1116 / #181D25 / #FF6A2B / #2DD4BF)
assets/img/screens/*.webp   Real app screenshots (Pixel 7 Pro, status bar cropped, 720×1440)
assets/img/icons/           Favicon + touch icons (6-dot pin-rack logo redrawn as SVG)
assets/img/og-image.png     1200×630 Open Graph / Twitter card
.nojekyll                   Serve files as-is (no Jekyll processing)
```

## Publish to GitHub Pages

```bash
git init -b main
git add -A
git commit -m "StrikeIQ promo site"
gh repo create strike-iq-site --public --source=. --push
gh api -X POST repos/maxim-austin/strike-iq-site/pages -f 'source[branch]=main' -f 'source[path]=/'
```

Or via UI: repo **Settings → Pages → Deploy from a branch → main / (root)**.

## Preview locally

```bash
python3 -m http.server 4173
```

## When the Play listing goes live

Search `index.html` for the two `TODO` comments and swap the "Get notified at launch" mailto buttons for the real store link:
`https://play.google.com/store/apps/details?id=com.strikeiq`

## Privacy policy URL for Play Console

```
https://maxim-austin.github.io/strike-iq-site/privacy.html
```

The policy section itself can be deep-linked with `#privacy-policy`.

## Regenerating screenshots

Screenshots were captured from the installed app via `adb exec-out screencap`, then cropped (100 px status bar, 80 px gesture bar) and resized to 720 px wide WebP. Any 1080×2340 capture processed the same way will drop in seamlessly.
