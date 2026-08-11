# Repository Guidelines

## Project Structure & Module Organization

This is a small Flask site for the Valiance OSIS cabinet. `main.py` owns the
application and route-to-template mappings; add a route here when adding a
page. Jinja templates live in `templates/valiance/`, with `layout.html` as the
shared base. Page-specific files use names such as `e_questival.html`.

Static resources are under `static/valiance/`: stylesheets in `css/`, browser
scripts in `js/`, and images in `img/` (grouped by page or event). Keep a
page's template, CSS, JavaScript, and assets similarly named so they remain
easy to locate.

## Build, Test, and Development Commands

Use Python and the locked dependencies in `requirements.txt`:

```powershell
py -m pip install -r requirements.txt  # install Flask dependencies
py main.py                             # start the local server
```

Open `http://127.0.0.1:5000/` and manually check the changed page, including
desktop and narrow/mobile layouts. There is no build step, package manager,
or automated test suite. For route changes, run `py main.py` and visit the
route rather than relying only on a template edit.

## Coding Style & Naming Conventions

Follow the surrounding code. Python uses four-space indentation, Flask route
decorators, and short `snake_case` view names (for example, `e_questival`).
Keep route URLs and `url_for()` endpoints in sync. HTML uses two-space
indentation; preserve Jinja blocks and use `url_for('static', filename=...)`
for local assets. CSS and JavaScript are plain files; extend the relevant
page-specific file instead of introducing a framework or a bundler.

Use lowercase, descriptive filenames with underscores for page assets, such
as `e_luminance.css`; retain the existing image format and directory naming
where practical.

## Testing Guidelines

No coverage target or test framework is configured. Treat manual browser
verification as required: check the route returns successfully, the shared
navigation works, images load without 404s, and console errors are absent.
When changing `main.py`, also check `/` and at least one unaffected event
page to catch a shared routing or layout regression.

## Commit & Pull Request Guidelines

Recent history uses brief, lowercase descriptive subjects, commonly gerunds:
`fixing cooking form` or `adding route`. Keep each commit focused; avoid
committing generated local files, virtual environments, or unrelated asset
changes. Open pull requests with a short summary, linked issue when one
exists, testing notes, and screenshots for visible desktop or mobile changes.
