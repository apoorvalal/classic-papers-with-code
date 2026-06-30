# AGENTS.md

This repo contains the Quarto source for `classic-papers-with-code`, a small executable companion site for classic statistics papers.

## Project Shape

- Source pages are `index.qmd` and `papers/*.qmd`.
- Site config is `_quarto.yml`; styling is `styles.css`.
- Python demo dependencies live in `pyproject.toml` and `uv.lock`.
- Generated output goes in `_site/` and should not be committed.

## Build

Use uv for Python dependencies and commands:

```sh
uv sync
uv run quarto render
```

Preview with:

```sh
uv run quarto preview
```

Add or update Python dependencies with `uv add`.

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
uv run quarto render
rsync -az --delete _site/ hetz:/root/lalten/pages/stat-ideas/
ssh hetz 'chmod -R a+rX /root/lalten/pages/stat-ideas'
curl -I https://lalten.org/pages/stat-ideas/
```
