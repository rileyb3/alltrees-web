# alltrees.app — landing site

Static marketing + deep-link site for AllTrees. Deployed on Vercel, separate
from the Expo app repo.

## Files
- `index.html` — landing page (logo, tagline, App Store button, Open Graph tags)
- `.well-known/apple-app-site-association` — iOS Universal Links
- `.well-known/assetlinks.json` — Android App Links
- `vercel.json` — serves the Apple file as `application/json`
- `og.png` — **TODO**: add a 1200×630 preview image (used by link unfurls)

## Before this fully works — replace these placeholders
1. `.well-known/apple-app-site-association` → replace `REPLACE_WITH_APPLE_TEAM_ID`
   with your Apple Team ID (developer.apple.com/account → Membership details).
2. `.well-known/assetlinks.json` → replace `REPLACE_WITH_ANDROID_SHA256_FINGERPRINT`
   once you have an Android build (only needed for Android; harmless until then).
3. Add `og.png` (1200×630) so shared links show a rich preview.

## Deploy
1. Push this folder to a **new** GitHub repo (e.g. `alltrees-web`).
2. In Vercel: New Project → import that repo → Framework Preset: **Other** → Deploy.
3. Project → Settings → Domains → add `alltrees.app` → paste the DNS records it
   gives you into Porkbun.

## Verify
- `https://alltrees.app/.well-known/apple-app-site-association` returns the JSON
  with `Content-Type: application/json`.
- Apple's CDN caches this; after the app ships with associated domains, test a
  real `https://alltrees.app/u/<username>` link on a device.
