# Classic Papers With Code

Quarto source for a small companion site to Leda Liang's journal-club collection, [Statistical Ideas that Changed the World](https://ledaliang.github.io/journalclub/).

The site rewrites selected classic statistics papers as short, executable notes. Each page includes a core mathematical object, a compact Python demo, and links to mature implementations when useful.

Published site: <https://lalten.org/pages/stat-ideas/>

## Contents

- `index.qmd`: homepage and paper index.
- `papers/*.qmd`: one Quarto page per paper.
- `_quarto.yml`: Quarto website configuration.
- `styles.css`: local styling.
- `pyproject.toml`: Python packages used by the executable examples.
- `uv.lock`: locked Python dependency resolution.

Generated output lives in `_site/` after rendering and is intentionally ignored by git.

## Build From A Fresh Clone

Install Quarto first:

```sh
brew install quarto
```

Install the Python dependencies from `pyproject.toml` / `uv.lock`:

```sh
uv sync
```

Render the site:

```sh
uv run quarto render
```

Preview locally:

```sh
uv run quarto preview
```

Add or update Python dependencies with `uv add`, for example:

```sh
uv add scipy
```

## Deploy To Lalten

Render first, then sync the generated site directory to the lalten static-pages tree:

```sh
uv run quarto render
rsync -az --delete _site/ hetz:/root/lalten/pages/stat-ideas/
ssh hetz 'chmod -R a+rX /root/lalten/pages/stat-ideas'
curl -I https://lalten.org/pages/stat-ideas/
```

The expected public URL is <https://lalten.org/pages/stat-ideas/>.

## Notes

The source site began as an internal Quarto companion to the STAT 319 journal-club materials. The original journal-club site by Leda Liang is the canonical collection of summaries, slides, and source papers: <https://ledaliang.github.io/journalclub/>.
