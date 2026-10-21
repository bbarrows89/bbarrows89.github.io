# Professional site (bbarrows89.github.io rebuild)

Thesis: **Identity security, made understandable.**

## What this is

The professional home base — not a playground draft. Four pages, no framework,
no build step, plain static files:

- `index.html` — thesis hero, three proof pillars (Build / Write / About), beliefs
- `essays/index.html` — essay listing
- `essays/breaking-id-jag-five-ways.html` — Essay 001 (director's cut of LinkedIn draft 001)
- `playground/index.html` — links the interactive pieces
- `playground/id-jag-failure-gallery/` — copied from the Auth Playground so the link works on the live site
- `about.html` — credibility, beliefs, contact door

## Publishing

This is designed to replace the current bbarrows89.github.io contents
(which is a legacy Jekyll/Gulp setup). Before pushing:

1. Finish the planned repo cleanup (close the 11 ancient Dependabot PRs + the
   Node CI PR #24 — decided 2026-10-03, still pending).
2. **Preserve the CNAME file** — the repo has a custom domain configured.
   Do not delete it in the replacement.
3. Push these files to `main`. GitHub Pages serves them directly; no build step.

## Content pipeline

Every other Monday a LinkedIn draft lands (cron `biweekly-linkedin-draft`).
Strong posts get expanded into essays here; essays embed the relevant
playground piece. LinkedIn = distribution, site = permanent home,
GitHub = proof of work.

## Build notes

- 2026-10-21: scaffolded from the positioning sketch. Replaces draft 001's
  "tinkerer" framing with the expert thesis. First essay seeded from LinkedIn
  draft 001.
