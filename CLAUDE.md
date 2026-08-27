# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## What this is

"Getting Up to Speed on AI Policy", a curated AI policy reading list by Jaxson Khan,
drawn from the PPG2012H course at the Munk School. Static site, email capture, thank-you page.

`netlify.toml` names the target domain as canadaaipolicy.com. Run `netlify status`
for the site ID.

## Build and deploy

No build step, no dependencies, no tests.

```bash
python3 -m http.server 8000   # local preview
git push                      # deploys (Netlify auto-deploy from main)
```

## Architecture

- `index.html` is the reading list, the whole site.
- `thanks.html` is the post-signup destination.
- `og-image.html` is a source template used to render `og-image.png`. It is not linked
  from the site and is not meant to be deployed as a page.
- `favicon.svg` is inline SVG, no PNG fallback.

## Netlify forms

The signup uses `<form data-netlify="true">`. Netlify only detects that form at deploy
time when HTML post-processing is on, which is why `netlify.toml` sets
`build.processing.skip_processing = false`. Do not turn processing off, and do not move
the form into JavaScript-injected markup, or submissions stop being captured with no
visible error on the page.

`pretty_urls = true` means `/thanks` serves `thanks.html`. Link without the extension.

## Conventions

The reading list is editorial content. When adding an entry, match the existing
structure in `index.html` and keep annotations to the same length and tone as neighbours.
