# AGENTS.md

This repo contains the Quarto source for `classic-papers-with-code`, a small executable companion site for classic statistics papers.

## Project Shape

- Source pages are `index.qmd` and `papers/*.qmd`.
- Site config is `_quarto.yml`; styling is `styles.css`.
- Python demo dependencies live in `requirements.txt`.
- Generated output goes in `_site/` and should not be committed.

## Build

Use a local virtualenv:

```sh
python3 -m venv .venv
source .venv/bin/activate
python -m pip install -r requirements.txt
quarto render
```

Preview with:

```sh
quarto preview
```

## Editing Guidance

- Keep pages short, mathematical, and executable.
- Prefer minimal NumPy/SciPy/SymPy/Matplotlib demos over framework-heavy examples.
- Code should define the mathematical objects being discussed, then reuse them in later cells.
- Avoid prompt/process language in rendered prose.
- Do not commit `.venv/`, `.quarto/`, `_site/`, or `*.quarto_ipynb`.

## Deploy

If you are Apoorva's agent and have write credentials, the public site currently lives at:

<https://lalten.org/pages/stat-ideas/>

Deploy after a clean render with:

```sh
rsync -az --delete _site/ hetz:/root/lalten/pages/stat-ideas/
ssh hetz 'chmod -R a+rX /root/lalten/pages/stat-ideas'
curl -I https://lalten.org/pages/stat-ideas/
```
