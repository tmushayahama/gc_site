# gc_site

Published demo build of **GroundCheck** — independent verification of
agricultural goods before money moves: produce ready for collection, stock in a
warehouse, farm inputs at a dealer, farm progress, and market prices. Part of
the Diaspora Trust Platform suite.

Live: https://tmushayahama.github.io/gc_site/

## This repo is generated output

`dist/` is a Vite production bundle built from `groundcheck-site` in the
`trust-tools` monorepo. **Do not edit it by hand.** To publish a new version:

```bash
cd ../trust-tools
./scripts/deploy-gc-demo.sh
cd ../gc_site && git add -A && git commit -m 'deploy' && git push
```

Pushing to `main` triggers `.github/workflows/pages.yml`, which uploads `dist/`
to GitHub Pages.

The demo runs entirely in the browser — no backend. State is Redux + seed data
in `localStorage`, and the "Reset demo data" item in the account menu clears it.

## What to look at

Pick a persona on the landing page; the whole app reshapes around their side of
the story. Four are seeded:

- **Customer** — a produce buyer with a tomato claim that came back partially
  supported, a fertiliser claim that collapsed, and a request that expired
  because nobody could reach the site in time.
- **Verifier** — the person who goes and counts it. The submit form withholds
  the claimed figure until they have locked in their own count.
- **Spotter** — tier 1: asking prices in a market, two minutes, no site access.
- **Operator** — the exception queue, competence-gated verifier matching, and
  the decision-impact signals.

The report is the centrepiece. It answers four questions in order — what was
claimed, what was observed, what did not match, what supports it — and it will
not print a bare number or draw a lot-wide conclusion from a sample.
