# Data Translator

Source code for [datatranslator.co.uk](https://datatranslator.co.uk) — my personal portfolio site, built to showcase data analytics projects and case studies.

## Tech stack

- **[Hugo](https://gohugo.io/)** (v0.163.3, extended) — static site generator
- **[PaperMod](https://github.com/adityatelange/hugo-PaperMod)** — base theme, included as a git submodule
- **GitHub Pages** — hosting
- **GitHub Actions** — build and deployment
- **Ionos** — domain registrar and DNS

## Site structure

```
.
├── layouts/                # Custom layout overrides (theme is never edited directly)
├── assets/css/extended/    # Custom CSS (colours, fonts, link styling etc.)
├── content/
│   ├── about.md            # About page
│   └── projects/           # Project landing page + case studies
├── static/img/             # Images, referenced with verbatim paths
├── hugo.yaml               # Site configuration
└── TODO.md                 # Task backlog
```

**Customisation principle:** all styling and layout changes live in `layouts/`, `assets/css/extended/`, and `hugo.yaml` — never inside `themes/PaperMod/`. This means the theme can be updated (via the submodule) without losing any customisations.

## Local development

Clone the repo with submodules included:

```bash
git clone --recurse-submodules https://github.com/clarelgibson/data-translator.git
cd data-translator
```

If you've already cloned without submodules:

```bash
git submodule update --init --recursive
```

Run the local development server:

```bash
hugo server -D
```

Site will be available at `http://localhost:1313`.

## Adding new content

### A new case study / project

1. Create a new Markdown file in `content/projects/`, e.g. `content/projects/my-new-project.md`.
2. Add front matter following the pattern used in existing case studies (`date`, `draft`, `title`, `cover`, `categories`, `tags`).
3. Add any images to `static/img/` and reference them with the full path, e.g. `img/my-image.jpg`.
4. Write the content in Markdown below the front matter.
5. Set `draft: false` when ready to publish.

### Editing the About page

Edit `content/about.md` directly.

## Branding reference

| Element | Value |
|---|---|
| Navy (structural) | `#202C39` |
| Light grey (structural) | `#ECF0F4` |
| Teal (secondary/meta) | `#55868C` |
| Coral (hover accent only) | `#FF4F5C` |
| Amber (reserve) | `#EDAE49` |
| Heading font | Playfair Display, ExtraBold 800 |
| Body font | Poppins, Light 300 |

Colour and font definitions live in `assets/css/extended/`.

## Deployment

Pushes to `main` trigger a GitHub Actions workflow that builds the site with Hugo and deploys it to GitHub Pages.

## Domain

The custom domain (`datatranslator.co.uk`) is configured at Ionos and pointed at GitHub Pages. DNS, GitHub Pages settings, and the Hugo build are three independent parts of the chain — if something breaks, troubleshoot each separately rather than assuming a single cause.

## Licence

Content and code are © Clare Gibson unless otherwise credited (see individual case studies for third-party image attributions).
