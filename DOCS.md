# Notes on this profile

## What this repo is

`HarianthK/HarianthK` — a repo named after the account, so GitHub renders its
README at the top of the profile page. That naming is the entire mechanism;
there is no setting to switch on.

## Palette

Every colour comes from the portfolio's `app/globals.css` dark theme, converted
OKLCH → sRGB hex because GitHub widgets accept hex only.

| Role | OKLCH (portfolio) | Hex |
| --- | --- | --- |
| Ground | `oklch(0.13 0.012 70)` | `#0a0704` |
| Card | `oklch(0.17 0.014 70)` | `#130e09` |
| Border | `oklch(0.28 0.02 70)` | `#2f271e` |
| Text | `oklch(0.97 0.008 80)` | `#f8f5ef` |
| Muted text | `oklch(0.7 0.018 75)` | `#a59d92` |
| Amber (primary) | `oklch(0.81 0.14 78)` | `#f2b54a` |
| Copper (accent) | `oklch(0.7 0.13 48)` | `#df8352` |
| Steel (tech nodes) | `oklch(0.72 0.12 225)` | `#39b4dd` |

Snake contribution ramp, level 0 → 4:
`#1f1913, #683b18, #985b1a, #c7852a, #f2b54a`

If the portfolio palette ever changes, these are the copies that go stale.

## Why the header is hand-written SVG

The glowing headers going around are not a widget — there is no service that
produces one. They are SVG committed to the repo. GitHub strips inline `<svg>`
from Markdown, so it has to be referenced as `<img src="assets/header.svg">`,
and inside an `<img>` an SVG gets no JavaScript and no external resources.

What does survive: CSS animations, `@keyframes`, and filter primitives. The glow
is `feGaussianBlur` at two radii merged back over the source via `feMerge` —
a wide soft halo plus a tight one, which reads as bloom rather than blur.

Animation uses CSS rather than SMIL specifically so `prefers-reduced-motion`
can switch it off. SMIL has no equivalent escape hatch.

Fonts fall back to whatever the viewer has. Georgia and a monospace stack are
safe on Windows and macOS; a Linux viewer gets a generic serif. Embedding a real
face would mean base64-ing it into the file, which is not worth the weight.

The graph nodes are the portfolio's knowledge-graph motif, carried over so the
two pages read as one identity.

## The snake

`Platane/snk/svg-only@v3` renders the contribution grid as an animated SVG and
`crazy-max/ghaction-github-pages@v5` pushes it to an `output` branch, which the
README then references by raw URL. The SVG never lands on `main`.

**The one manual step:** Settings → Actions → General → Workflow permissions →
*Read and write*. Without it the push step fails with a 403, and that is the
single most common reason these setups quietly stop working. `permissions:
contents: write` in the workflow is necessary but not sufficient on its own.

`color_dots` takes exactly five colours, lowest to highest. The `#` characters
sit inside a YAML block scalar, so they are literal and not comments.

## Stats cards

Currently pointed at the public `github-readme-stats` instance. That deployment
shares one 5k/hour GitHub API quota across every user of it and returns 503
during busy periods — the broken image everyone eventually sees.

Fix when it starts happening: fork `anuraghazra/github-readme-stats`, deploy to
Vercel, add a `PAT_1` env var with a classic token, and swap the two
`github-readme-stats.vercel.app` hostnames in the README for the new one.

`bg_color=00000000` is transparent — eight-digit hex, alpha last. That is what
lets the cards sit on GitHub's own background in either theme.

## Deliberately not here

Trophy case, streak counter, profile-view counter, tech-badge wall, typing-SVG
headline. Recruiter-facing guidance consistently reads these as filler that
hides signal, and the custom header already does the job a typing SVG would.

## Known quirks

- GitHub proxies images through camo and caches them. An edited `header.svg` can
  take a few minutes to show the change; a hard refresh usually does it.
- Animated SVG through camo has been reported flaky in some Firefox versions.
  The header degrades to a static frame rather than breaking.
- The activity graph is the most decorative element on the page and the first
  thing to cut if it ever reads as long.
