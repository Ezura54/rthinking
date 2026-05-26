# Web Knowledge Graph

This folder contains a deployable web viewer for the psych knowledge graph.

## 1) Build graph data

From project root:

```bash
python scripts/build_web_graph.py
```

This generates:

- `web-graph/data/graph.json`
- `web-graph/data/meta.json`

The export is privacy-safe by default:

- removes local file paths and emails
- keeps only approved node/edge fields
- deduplicates nodes/edges
- does not expose absolute source path in meta

## 2) Run locally

```bash
python -m http.server 8766 --directory web-graph
```

Then open:

- `http://127.0.0.1:8766/index.html`

## 3) Deploy to GitHub Pages

Recommended structure in repository root:

- `web-graph/index.html`
- `web-graph/data/graph.json`
- `web-graph/data/meta.json`

Deploy options:

1. GitHub Pages from `main` branch, `/web-graph` folder
2. GitHub Actions deploy job that publishes `web-graph/` as static site

Before each deploy, run `python scripts/build_web_graph.py` to refresh data.
