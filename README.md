# Classic Papers With Code

Quarto source for a small companion site to Leda Liang's journal-club collection, [Statistical Ideas that Changed the World](https://ledaliang.github.io/journalclub/).

The site rewrites selected classic statistics papers as short, executable notes. Each page includes a core mathematical object, a compact Python demo, and links to mature implementations when useful.

Published site: <https://lalten.org/pages/stat-ideas/>

## Contents

- `index.qmd`: homepage and paper index.
- `papers/*.qmd`: one Quarto page per paper.
- `_quarto.yml`: Quarto website configuration.
- `styles.css`: local styling.
- `requirements.txt`: Python packages used by the executable examples.

Generated output lives in `_site/` after rendering and is intentionally ignored by git.

## Build From A Fresh Clone

Install Quarto first:

```sh
brew install quarto
```

Create a local Python environment:

```sh
python3 -m venv .venv
source .venv/bin/activate
python -m pip install --upgrade pip
python -m pip install -r requirements.txt
python -m ipykernel install --user --name classic-papers-with-code --display-name "Python (classic-papers-with-code)"
```

Render the site:

```sh
quarto render
```

Preview locally:

```sh
quarto preview
```

## Deploy To Lalten

Render first, then sync the generated site directory to the lalten static-pages tree:

```sh
quarto render
rsync -az --delete _site/ hetz:/root/lalten/pages/stat-ideas/
ssh hetz 'chmod -R a+rX /root/lalten/pages/stat-ideas'
curl -I https://lalten.org/pages/stat-ideas/
```

The expected public URL is <https://lalten.org/pages/stat-ideas/>.

## Notes

The source site began as an internal Quarto companion to the STAT 319 journal-club materials. The original journal-club site by Leda Liang is the canonical collection of summaries, slides, and source papers: <https://ledaliang.github.io/journalclub/>.
