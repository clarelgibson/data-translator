# Data Translator — task backlog

## Now

- [ ] Have Claude act as a data science tutor to guide me through a cluster analysis on the Seven Bins data, using the work I have already done as a starting point and taking it to a meaningful conclusion.

## Next

- [ ] Create custom 404 page. Copy `themes/PaperMod/layouts/404.html` to `layouts/404.html`. Customise the content/message to match your branding (keep it brief, offer links back to home, about, projects). Test by visiting `/nonexistent-page/` locally.
- [ ] Add call-to-action at end of About page. After the Career Highlights closing `</div>`, add a brief paragraph inviting readers to the projects, e.g. "You can explore the projects where I've applied these skills on the [Projects](/projects/) page." or a link button.
- [ ] Create Colophon page at `content/colophon.md`. Explain the tech stack (Hugo v0.163.3, PaperMod theme, GitHub Pages + Actions, Ionos DNS), credit PaperMod and the theme author, list self-hosted fonts and their sources (google-webfonts-helper), credit photo attributions from the project case studies, link to the GitHub repo. Set `draft: false` and add a link from About page or footer.
- [ ] Add footer navigation. Edit `themes/PaperMod/layouts/partials/footer.html` (copy to `layouts/_partials/footer.html` to avoid overwriting on theme updates). Add links to `/about/`, `/projects/`, `/colophon/`, and GitHub repo. Keep it minimal (one line or simple list).
- [ ] Expand About page intro. Add 2–3 sentences after the opening paragraph that articulate your approach to data translation, e.g. "I believe good data insights should be intuitive and accessible. My approach is to ask clear questions, find the right data, and present findings in a way that drives action." or similar. Keep it under 50 words so the page doesn't become a novella.
- [ ] Add lightweight analytics (optional). If you want visitor metrics: sign up for [Plausible Analytics](https://plausible.io) (5-min setup, GDPR-friendly, no cookie banner needed). Add the script tag to `layouts/partials/extend_head.html`. Alternatively, use Google Analytics if you prefer (more heavyweight, requires cookie consent).
- [ ] Regenerate favicons (favicon.ico, favicon-16x16.png, favicon-32x32.png, apple-touch-icon.png in hugo.yaml lines 45 to 48) from the proper vector master to give crisper small icons, and add an SVG favicon for modern browsers.

## Later

- [ ] Standardise project cover aspect ratio. Already in backlog (deferred from Projects redesign phase). Decide on one ratio (Perry uses roughly 3:1; 2:1 or 16:9 are common alternatives). Once chosen, implement via a `cover.html` partial override using Hugo's `Fill` to crop covers automatically. Update all three existing project covers to that ratio.
- [ ] Add featured project flag or visual distinction. Decide which of your three projects (Cyclistic, Tesla, Seven Bins) is your strongest. Add a `featured: true` field to its front matter, then update `layouts/list.html` to render featured projects with a "Featured" badge, star icon, or top-row positioning on the Projects landing page.
- [ ] Add Skills or Tools section to About page (optional). After Career Highlights, add a section listing your main tools (R, Tableau, SQL, Python, Hugo, etc.) as a simple bulleted list or icon grid. Decide on format and placement; could also live in the summary table as a row instead.
- [ ] Integrate blog or writing section (if applicable). If you maintain a blog (e.g. on Medium, your old surreydatagirl site, or Substack), decide whether to: (a) link from About to external blog, (b) create a /writing/ page with links to your pieces, or (c) import past articles as posts into this Hugo site. Start by auditing what content exists and where it lives.
- [ ] Build case study for england-school-admissions (Tableau dashboard + R pipeline; mentioned in CV). Check external links and update branding from surreydatagirl to Data Translator.
- [ ] Build case study for uk-food (FSA hygiene data, R analysis, geospatial visualisation). Update branding references to Data Translator.
- [ ] Build case study for tableau-public-autorefresh (R + Google Sheets + GitHub Actions + Tableau pipeline; demonstrates data engineering). Slightly different spine structure needed (heavier on method/build, lighter on findings).
- [ ] Audit COVID-19 project and check completeness before deciding if it's portfolio-ready.
- [ ] Build makeover-monday gallery or lighter project entry (collection of Tableau Public viz makeovers; for breadth of visualisation skill).
- [ ] Add a project for the race across the world game I built with Claude Code
- [ ] Use `_brand.yml` to declare logo, colour palette and typography to all future Quarto docs and push the palette into `ggplot`
- [ ] Make a template github repo for data analysis projects, including license, appropriate .gitignore, quarto template with dt branding and directory structure (CSS files included if needed) 

## Done
- [X] Step 1: content (About done; Projects landing + 3 case studies remaining)
- [X] the Experience block becomes part of the current "content" step (it's just more of the About page)
- [X] Branding: colours, then fonts, then logo/favicon
- [X] GitHub Actions deployment
- [X] DNS at Ionos (point domain at GitHub; fix redirect)
- [X] Write documentation for GitHub (README) - ensure that I have a guide to adding new content in the future
- [X] Add a photo to the profile page
- [X] Tighten up structure, consistency and content of each project write-up. Ask Claude to give a critical review in the role of a potential employer.
- [X] Rewrite front matter and figure shortcodes to allow for image optimization
- [X] Migrate the hand-written summary block for Project write-ups to front matter and using Hugo archtype
- [X] Repeat steps to convert Seven Bins to the new scaffold
- [X] Repeat steps to convert Tesla to the new scaffold - we need to amend the render hook first to work with the .svg file.
- [X] Update the README to give instructions on how to create a new project now that I have changed the process. Be sure to include a reference to the command needed to create a new project: `hugo new content projects/<name>`
- [X] Change body font from Poppins to Work Sans
- [X] Make my name bigger on the home page 
- [X] Add more of the primary accent colour into the site. Perhaps use for URL underlines.
- [X] Projects landing page redesign (new chat — distinct phase).
      Tackle as one connected piece, in this order:
  1. Decide the standard cover aspect ratio first. Current covers are
     2.83:1, 3.2:1 and 4.0:1; needs to be one ratio before cards can sit
     neatly side by side. Candidates to weigh: 2:1, 16:9, 3:1.
  2. Enforce the chosen ratio via a cover.html partial override using
     Fill, so covers crop automatically and no longer need manual cropping.
  3. Redesign list.html for a horizontal multi-card layout, building on
     the project_summary.goal field already feeding the cards.
- [X] Generate a true svg file for the logo as the one I have is a bitmap in disguise.
- [X] Add social icons (Tableau Public, GitHub, Kaggle, LinkedIn and email) to my home page
- [X] Restructure the experience section of my About page to be tabular - like the [Perry site](https://perryw-2023.webflow.io/info)

## Removed (no longer needed)
- [ ] Build out template instructions for creating new projects (how will the portfolio site link to the place where the project is hosted, e.g. Tableau Public)
- [ ] Investigate dynamic image sizing for project posts. Currently I manually crop each image before uploading it to `static/img` but maybe there is a way to get Hugo to do the resizing for me?
- [ ] Adjust the project summary text for each project on the project landing page so that it displays just the content inside Goal/Detail from the initial table. I don't want to display the column headings in this preview text.
- [ ] Optional: simple one-page CV PDF for passers-by, linked in nav/footer - similar to the one on [this site](https://perryw-2023.webflow.io)