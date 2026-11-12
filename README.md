# Scott Weber & Line 47 website

Personal site for Scott Weber (design work) and Line 47 (music), built with
Jekyll and hosted on GitHub Pages.

## Run locally

```bash
bundle install
LANG=en_US.UTF-8 bundle exec jekyll serve
```

Then open http://localhost:4000.

`LANG=en_US.UTF-8` matters: without a UTF-8 locale the Sass build fails with
`Invalid US-ASCII character`.

## Where things live

| What | Where |
| --- | --- |
| Page shell (head, skip link, nav, footer) | `_layouts/base.html` |
| Navigation menus | `_data/navigation.yml` |
| Social, streaming, and label links | `_data/links.yml` |
| Organizations on /work/ | `_data/organizations.yml` |
| Rejection list on the "Unfortunately" article | `_data/unfortunately.yml` |
| Case studies | `_projects/` (`published: false` hides a draft) |
| Articles | `_articles/` |
| Styles | `_sass/` (imported by `assets/css/styles.scss`) |
