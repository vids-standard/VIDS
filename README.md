# vidsstandard.org

Official website for the **VIDS — Verified Imaging Dataset Standard**.

## Local Development

```bash
# Install dependencies
pip install mkdocs-material

# Serve locally with hot reload
mkdocs serve

# Build static site
mkdocs build
```

The site will be available at `http://127.0.0.1:8000`.

## Deployment

The site deploys automatically to GitHub Pages via the workflow in `.github/workflows/deploy.yml` on every push to `main`.

### Custom Domain Setup

1. In the GitHub repo (`vids-standard/VIDS`) → Settings → Pages, set the custom domain to `vidsstandard.org`.
2. At your DNS provider, add:
   - `A` records pointing to GitHub Pages IPs:
     ```
     185.199.108.153
     185.199.109.153
     185.199.110.153
     185.199.111.153
     ```
   - `CNAME` record: `www` → `vids-standard.github.io`
3. Enable "Enforce HTTPS" in GitHub Pages settings.

## Structure

```
docs/
├── index.md                          # Home page
├── CNAME                             # Custom domain
├── assets/
│   ├── logo.svg
│   ├── favicon.svg
│   └── extra.css
├── specification/
│   ├── index.md                      # Full VIDS Specification
│   ├── validation-rules.md
│   ├── directory-structure.md
│   ├── file-naming.md
│   └── profiles.md
└── validator/
    ├── index.md                      # Installation
    ├── quickstart.md
    └── cli-reference.md
```

## License

- Specification and documentation: [CC BY 4.0](https://creativecommons.org/licenses/by/4.0/)
- Tools and reference implementations: [Apache 2.0](https://www.apache.org/licenses/LICENSE-2.0)
