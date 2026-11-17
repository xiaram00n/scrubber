# Scrubber

A single-file, fully client-side privacy tool. Live at **https://xiaram00n.github.io/scrubber/**.

Everything runs on your device. The page's Content Security Policy blocks all network access (`connect-src 'none'`) — after the page loads, nothing can leave your device.

## What it does

### File / image tab
- **Inspect only** — decodes and displays embedded metadata (EXIF incl. GPS coordinates, camera/lens serials, owner names, XMP history, thumbnails, PNG text chunks, PDF/Office document properties) and changes nothing.
- **Inspect & scrub** — shows the BEFORE report, then builds a clean copy by re-encoding from pixels only, verifies it against a strict structural whitelist, and only then offers Save / Share. JPEG or PNG output; HEIC/AVIF sources are converted so no iPhone signature remains.
- **Pixel treatment** levels (metadata-only / Light / Strong / Maximum) add noise/resize/blur against sensor-noise fingerprinting.
- **Text-like files** (.txt, .md, .json, …) are cleaned like pasted text and can be saved as clean files.
- **PDF / Office / audio / video** trigger a hard desktop-gate: findings are shown, no save is offered, and desktop tools are named. A false "clean" is worse than no tool.
- **Copy buttons everywhere** — clean image to clipboard (paste directly into apps, no file saved), and every report.

### Pasted text tab
Removes zero-width/invisible characters, bidi overrides, variation selectors, homoglyphs, smart punctuation, and link tracking parameters. Flags emails, phone numbers, dates, handles, paths, and tokens for your own judgment — wording itself can identify you. Includes full link analysis and a "Copy all cleaned text" output.

### Link check tab
Sanitizes links (tracking params, embedded credentials, token fragments) and flags structural risk signals: homoglyph/punycode domains, embedded `user:pass@`, raw/hex IPs, executable downloads, brand-in-subdomain impersonation, shorteners, dangerous schemes. Validates .onion v3 format and warns on v2/malformed addresses. Optional Tor lane-crossing check. Bundled known-scam/phishing blocklist snapshot (Block List Project, dated in the UI — a snapshot, not a live check).

## Honest limits
- "No warning signs" is never "safe" — destinations are unverified.
- No tool removes what's visible in the content itself (faces, signs, screens, voices).
- On iOS, save via **Save to Files**, not Save Image — Photos re-wraps images with its own metadata.

## Files
- `index.html` — the entire tool. That's all there is; host it anywhere or open it locally.

## Repo ZIP
GitHub: **Code → Download ZIP** always packages the current state of this repo.
