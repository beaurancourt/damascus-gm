# damascus-gm

The GM-facing deployment of [Damascus](https://github.com/beaurancourt/damascus),
published to https://beaurancourt.github.io/damascus-gm/.

There is no application code here. The app lives in one codebase and builds
twice: the player site (Heroes + Library) is deployed from the `damascus` repo
itself, and this repo builds the same source with `npm run build:gm` to produce
the GM site (Library + Session). See the "Two sites, one codebase" section of
`CLAUDE.md` in the main repo.

The workflow in `.github/workflows/deploy.yml` checks out `beaurancourt/damascus`
at `damascus/main`, builds the GM variant, and publishes it to this repo's
GitHub Pages. It runs:

- whenever this repo is pushed to,
- on a daily schedule, so changes in the main repo reach this site,
- on demand via **Actions → Deploy GM site → Run workflow**.

Deploy the latest main-repo changes immediately with:

```
gh workflow run deploy.yml --repo beaurancourt/damascus-gm
```
