# SCHO at USC website — notes for Claude

Site for Southern California Healthcare Outreach (SCHO), a USC student group that helps underserved LA communities with health insurance (English/Spanish). Keep UX simple and accessible.

- Live: https://aseethar-alt.github.io/SCHOWEBSITE/ (GitHub Pages deploys from `main`)
- Preview artifact: https://claude.ai/artifact/35STsPKH2aGXGHi9gtxoUH (publish `index.html` with every asset in `images/`, `fonts/`, `docs/` passed in `files`, or pictures go missing)

## Push rules
- Never push to `main` unless the user explicitly says "push" / "commit to github" in the current conversation.
- Deploy: `git push origin HEAD:main`, then check `gh api 'repos/aseethar-alt/SCHOWEBSITE/actions/runs?per_page=1'` until success.
- The user reverts design experiments often: keep changes small and easy to undo.

## Structure
- Single `index.html` with inline CSS/JS and hash routing: pages are `<div class="page" data-route="X">`; guide pages use `data-nav="resources"`.
- Design tokens: `--bg #FFF9E6`, `--cardinal #9D2235`, `--gold #E8A400`, `--ink #1A1414`, `--ink-faint #6B615C`.
- Fonts: Alpino (headings), Pally (body), Satoshi (hero h1), Montserrat Bold (full-width "Southern California Healthcare Outreach" title; matches the logo). Self-hosted in `fonts/`.
- Home hero: full-width Montserrat title (JS `fitHeroName()` stretches it to the content width), then a rounded photo box (`images/hero-group.jpg`, ceiling cropped) with the h1 and "Established 2019 @ USC" overlaid in white; then the "Who we are" band, then the 4 black stat circles.
- Members Only login: the Drive URL is AES-GCM encrypted in the `VAULT` object (ask the user for the login; don't write it into the repo).

## Open decisions (ask the user)
- "@ USC" gold-on-beige contrast is low.
- Spanish version (needs a human translation reviewer).
- Phone number; replace mailto contact form with a Google Form.
- Content pages still pending: see `TODO.md`.
