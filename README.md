# Kagenti Ecosystem Guide

The open source ecosystem for building, deploying, securing, and governing AI agents on Kubernetes.

**[View the site →](https://pages.github.ibm.com/Jenna-Winkler/ecosystem-guide/)**

## How this repo works

All content lives in `content/`. Edit the markdown files there and submit a PR.

The `docs/` folder is auto-generated build output that GitHub Pages serves. **Don't edit files in `docs/` directly.**

## To update the site

1. Edit files in `content/`
2. Run `pip install mkdocs-material` (one-time setup)
3. Run `mkdocs build`
4. Commit and push both `content/` and `docs/`

## To preview locally

```
mkdocs serve
```

Opens at http://127.0.0.1:8000/ with live reload.
