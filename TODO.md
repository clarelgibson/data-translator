# Data Translator — task backlog

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

## Now
- [ ] Make my name bigger on the home page 
- [ ] Add more of the primary accent colour into the site. Perhaps use for URL underlines.

## Next (agreed sequence)
- [ ] Is there a better layout for my Projects landing page so that more than one project could be displayed horizontally?
- [ ] Enforce a standard cover image aspect ratio via a cover.html partial override using Fill, so covers no longer need manual cropping. Decide the ratio first (current covers are 2.83:1, 3.2:1 and 4.0:1). Consider alongside the Projects landing page redesign.

## Someday / ideas
- [ ] Add school-admissions and COVID-19 projects (mentioned in CV)
- [ ] Optional: simple one-page CV PDF for passers-by, linked in nav/footer - similar to the one on [this site](https://perryw-2023.webflow.io)
- [ ] Add a project for the race across the world game I built with Claude Code
- [ ] Have Claude act as a data science tutor to guide me through a cluster analysis on the Seven Bins data, using the work I have already done as a starting point and taking it to a meaningful conclusion.
- [ ] Generate a true svg file for the logo as the one I have is a bitmap in disguise.
- [ ] Add social icons (Tableau Public, GitHub and LinkedIn) to my home page
- [ ] Restructure the experience section of my About page to be tabular - like the Perry site

## Removed (no longer needed)
- [ ] Build out template instructions for creating new projects (how will the portfolio site link to the place where the project is hosted, e.g. Tableau Public)
- [ ] Investigate dynamic image sizing for project posts. Currently I manually crop each image before uploading it to `static/img` but maybe there is a way to get Hugo to do the resizing for me?
- [ ] Adjust the project summary text for each project on the project landing page so that it displays just the content inside Goal/Detail from the initial table. I don't want to display the column headings in this preview text.