# Alexandra A. Rodriguez — academic site

Jekyll site for GitHub Pages.

## Publish
1. In this repository: Settings → Pages → Source: "GitHub Actions".
2. Set the custom domain to `alexandraarodriguez.com` and ensure your domain's DNS points to GitHub Pages. Enable Enforce HTTPS when available.
3. Push to `master`. The workflow in `.github/workflows/jekyll.yml` builds and deploys the site.

Keep `baseurl: ""` for the custom domain, regardless of the repository name.

## Set up
- **_config.yml**: name, tagline, social links, Formspree ID.
- **Photo**: replace `assets/images/portrait.png` or update `portrait` in `_config.yml`.
- **CV**: `cv_file` in `_config.yml` links to the Google Docs PDF export. Edits to the same document appear in subsequent downloads.
- **Contact form**: sign up at formspree.io, create a form pointing to your email, paste its ID into `formspree_id`. Your email never appears on the site.

## Adding content
Edit `_data/navigation.yml` to change the shared menu on Home and every sub-page.

Everything lives in `_data/`:
- `research.yml`: projects, summaries, dates, and status.
- `publications.yml`, `presentations.yml`, `teaching.yml`: add entries with a `date`.
- `writing.yml`: blog posts and op-eds.
- `media.yml`: interviews and features you've appeared in (tag each with a type).
- Policy page: add `policy: true` to entries in `presentations.yml`, `media.yml`, or `writing.yml` to feature them on `/policy/`.
- Bio text: edit `about.md`.

Images are optional everywhere; without one, a soft striped placeholder shows.

## Home page "Recent work" rule
The home page shows the newest dated entry from each category: Research, Publications, Presentations, Teaching, Writing, and Media. Empty categories are omitted. If a category has no dated entries, its first entry is shown with its status instead of a date. The list updates whenever the site rebuilds.

Research uses only projects marked `current: true`, labeled “In progress.” When ongoing projects have no dates, place the project to feature first in `_data/research.yml`. Use `home_date_label` to customize an entry’s date label on the home page without changing its category page.

Entries with only a month, season, or year use the first day of the relevant period as a sorting key in `date`. Use `date_label` to display the original date wording without implying an exact day. Media entries without URLs display without links; manuscripts in preparation retain that status.

## Preview locally
Use a modern Ruby (3.1 or newer), rather than macOS's bundled Ruby 2.6. Check with `ruby --version`.

Install dependencies after changing the Gemfile:

```sh
bundle install
```

Start the preview:

```sh
bundle exec jekyll serve --livereload --host localhost
```

Open http://localhost:4000. Page and style changes rebuild automatically. After changing `_config.yml`, stop the server with Ctrl+C and run the preview command again. Local preview uses localhost for site links; keep the production domain in `_config.yml`.

If Bundler reports missing gems, run `bundle install` again. If port 4000 is already in use, stop the previous server or add `--port 4001` and open http://localhost:4001.
