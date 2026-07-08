# Data Translator

Source code for [datatranslator.co.uk](https://datatranslator.co.uk), my personal portfolio site, built to showcase data analytics projects and case studies.

## Tech stack

- **[Hugo](https://gohugo.io/)** (v0.163.3, extended): static site generator
- **[PaperMod](https://github.com/adityatelange/hugo-PaperMod)**: base theme, included as a git submodule
- **GitHub Pages**: hosting
- **GitHub Actions**: build and deployment
- **Ionos**: domain registrar and DNS

## Site structure

```
.
├── archetypes/
│   └── projects/           # Directory archetype used by `hugo new content projects/<name>`
│       └── index.md
├── layouts/                # Custom layout overrides (theme is never edited directly)
│   ├── _markup/            # render-image.html: responsive image render hook
│   ├── _partials/          # extend_head.html
│   ├── _shortcodes/        # summary.html: renders project_summary as a table
│   └── list.html           # Projects landing page
├── assets/css/extended/    # Custom CSS (colours, fonts, figures, tables)
├── content/
│   ├── about.md            # About page
│   └── projects/           # _index.md (landing page) + one bundle folder per case study
│       └── <project-name>/
│           ├── index.md    # Front matter and write-up
│           └── *.jpg       # Images live in the bundle, next to the content
├── static/
│   ├── fonts/              # Self-hosted webfonts
│   ├── img/                # Site-wide images only (headshot, logo)
│   └── favicon*, site.webmanifest
├── hugo.yaml               # Site configuration
└── TODO.md                 # Task backlog
```

**Customisation principle:** all styling and layout changes live in `layouts/`, `assets/css/extended/`, and `hugo.yaml`, never inside `themes/PaperMod/`. This means the theme can be updated (via the submodule) without losing any customisations.

Current layout overrides:

- `layouts/_markup/render-image.html`: turns plain Markdown images into responsive, captioned figures (see below)
- `layouts/_shortcodes/summary.html`: renders the `project_summary` front matter as a semantic table
- `layouts/list.html`: Projects landing page; shows each project's `project_summary.goal` as its preview text, falling back to Hugo's `.Summary` if the field is absent

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

Each project is a Hugo [leaf bundle](https://gohugo.io/content-management/page-bundles/): a folder containing `index.md` plus any images the write-up uses.

1. **Scaffold the bundle:**

   ```bash
   hugo new content projects/<project-name>
   ```

   This uses the directory archetype at `archetypes/projects/` to create `content/projects/<project-name>/index.md` with the front matter skeleton, the summary shortcode and the standard section headings already in place. The folder name becomes the URL slug, so use lowercase words separated by hyphens.

2. **Fill in the front matter:**

   - `title` is pre-populated from the folder name; adjust if needed.
   - `cover`: add a cover image to the bundle folder and set `image` (filename only), `alt` and `caption`. The caption supports Markdown links for photo attribution. Covers are handled by the theme, not the render hook: they are resized for `srcset` but displayed at their **native aspect ratio**, so crop covers to a wide banner shape (roughly 3:1) before adding them. (A TODO task exists to enforce a standard ratio automatically via a `cover.html` partial override.)
   - `project_summary`: complete `goal`, `role`, `tools`, `data` and `links` (each link is a `name`/`url` pair; remove any that don't apply). These render as the summary table at the top of the page via the `summary` shortcode, and `goal` doubles as the preview text on the Projects landing page, so write it to stand alone.
   - `tags`: lowercase, as a YAML list.

   > **Why `project_summary` and not `summary`?** Hugo reserves `summary` for its own `.Summary` page variable and strips it from `.Params`, so a front matter field named `summary` would silently disappear. Don't rename it.

3. **Add body images** by dropping them into the bundle folder and referencing them with plain Markdown:

   ```markdown
   ![Alt text describing the image](my-chart.png "Optional caption")
   ```

   The image render hook handles the rest automatically:

   - Raster images (JPG, PNG) are resized to a set of responsive widths (480/720/1080/1440px) and served with `srcset`, so browsers download only what they need. Images are never upscaled beyond their original width, so body images need no cropping or resizing before adding them; just avoid tiny originals. (Cover images are the exception; see step 2.)
   - SVGs are resolution-independent, so they skip the resize pipeline and render at their natural size.
   - In both cases the image is wrapped in a `<figure>`, with the caption (the quoted title text) rendered as a `<figcaption>`.
   - Images referenced from outside the bundle (e.g. external URLs) fall back to a plain `<img>` with no optimisation, so keep project images in the bundle.

4. **Write the content** under the scaffolded headings, which follow the standard case study spine. Rename the flexible sixth section (`Outcome` in the archetype) to suit the project, e.g. Recommendations, Conclusion or The tool.

5. **Publish** by setting `draft: false`. Preview drafts locally with `hugo server -D` before pushing.

### Editing the About page

Edit `content/about.md` directly. The profile photo lives in `static/img/`.

### Editing the Projects landing page intro

Edit `content/projects/_index.md`.

## Branding reference

| Element | Value |
|---|---|
| Navy (structural) | `#202C39` |
| Light grey (structural) | `#ECF0F4` |
| Teal (secondary/meta) | `#55868C` |
| Coral (hover accent only) | `#FF4F5C` |
| Amber (reserve) | `#EDAE49` |

Fonts are self-hosted in `static/fonts/` and declared in `assets/css/extended/fonts.css`, which is the source of truth for families and weights (currently Playfair Display 700 for headings, Poppins 300/300 italic/600 for body text).

## Deployment

Pushes to `main` trigger a GitHub Actions workflow that builds the site with Hugo and deploys it to GitHub Pages.

## Domain

The custom domain (`datatranslator.co.uk`) is configured at Ionos and pointed at GitHub Pages. DNS, GitHub Pages settings, and the Hugo build are three independent parts of the chain. If something breaks, troubleshoot each separately rather than assuming a single cause.

## Licence

Content and code are © Clare Gibson unless otherwise credited (see individual case studies for third-party image attributions).
