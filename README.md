# Kagenti Ecosystem Guide

Your central reference for the Kagenti open source ecosystem — what's being built, who it's for, and how to get involved.

👉 **[Launch the site →](https://pages.github.ibm.com/kagenti/ecosystem-guide/)**

---

## What you’ll find

The Ecosystem Guide is designed to help you quickly understand and navigate Kagenti.

### Start here
- **About Kagenti** — What the project is and why it exists  
- **Use Cases & Personas** — Who it’s for and the problems it solves  
- **Onboarding** — How to join the community and start contributing  
- **Workstreams** — Active areas of work, contributors, and progress  

### Reference
- **Key Dates** — Milestones and events  
- **Goals & OKRs** — Current priorities and direction  
- **Content** — Blogs, demos, and updates  
- **Resources** — Links, tools, and community channels  

---

## How this repo works

This repo powers the Ecosystem Guide site.

- `content/` → source of truth (edit here)
- `docs/` → generated site (served via GitHub Pages)

> ⚠️ `docs/` is build output — do not edit files there directly.

---

## Updating the site

1. Make changes in `content/`
2. Install dependencies (one-time): `pip install mkdocs-material`
3. Build the site: `mkdocs build`
4. Commit and push both `content/` and `docs/`

---

## Preview locally

```
mkdocs serve
```

Then open [http://127.0.0.1:8000/](http://127.0.0.1:8000/).

Live reload is enabled, so your changes appear instantly.

---

## Contributing

This is a living ecosystem map - contributions are welcome!

You might:
- Add new projects or workstreams
- Improve clarity or structure
- Keep content fresh and up to date

See CONTRIBUTING.md for guidelines.
