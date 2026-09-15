# brockwc.github.io

Personal site for Brock Whitbread. Jekyll (built by GitHub Pages) with Tailwind CSS v4.

## Where things live

- Pages: `index.html`, `about.md`, `categories.md`
- Layouts: `_layouts/`, partials in `_includes/`
- Posts: `_posts/YYYY-MM-DD-slug.markdown` with front matter (`layout: post`, `title`, `date`, `categories`)
- Styles: utilities are used directly in the markup. Project-level styles and design tokens live in `css/tailwind.src.css`.
- `css/main.css` is generated. Do not edit it by hand.

## Local development

```sh
npm install        # once
npm run css:watch  # rebuild css/main.css while you edit templates
```

Serve the site (no Ruby needed, uses Docker with the same gem versions as GitHub Pages):

```sh
docker run --rm -u "$(id -u):$(id -g)" -e HOME=/tmp -v "$PWD":/srv/jekyll -p 4000:4000 jekyll/jekyll:pages jekyll serve --host 0.0.0.0
```

Then open http://localhost:4000

## Deploying

Compiled CSS is committed, so GitHub Pages needs no build step beyond its own Jekyll build.

Before committing markup or class changes: `npm run css:build`

Push to `main` to deploy.
