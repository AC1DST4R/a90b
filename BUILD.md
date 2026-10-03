# A-90B Quest 3 — APK build

A plain Android WebView does NOT support WebXR, so a "wrapper APK" must be a
Trusted Web Activity (TWA) that opens your hosted HTTPS page in the Quest Browser engine.

## 1. Host this folder over HTTPS
GitHub Pages / Netlify / Cloudflare Pages. Confirm it loads and runs in the Quest Browser first.

## 2a. Easiest: PWABuilder
1. Go to pwabuilder.com and enter your hosted URL.
2. Choose the Meta Quest package option (or Android) and download the generated APK/AAB.

## 2b. Bubblewrap CLI
    npm i -g @bubblewrap/cli
    # edit twa-manifest.json: packageId, host, URLs
    bubblewrap init --manifest=https://YOUR-HOST/a90b/manifest.json
    bubblewrap build        # outputs app-release-signed.apk

## 3. Install on the Quest 3
Enable Developer Mode, then:
    adb install app-release-signed.apk
It appears under Library > Unknown Sources.

Notes: images/sounds load from your GitHub repo (cached after first run by sw.js).
Check Meta's current Horizon OS PWA docs for store-submission requirements.
