# gleon-rs.github.io

The product site of gleon, served at <https://gleon.rs> by GitHub Pages.

Plain HTML and CSS: no build step, no JavaScript, no third-party requests. What is in `main` is what
the site serves.

| File                        | What it is                                                           |
| --------------------------- | -------------------------------------------------------------------- |
| `index.html`                | The page.                                                            |
| `404.html`                  | Served by Pages for unknown paths (absolute asset paths on purpose). |
| `styles.css`                | Tokens for light and dark (system theme), layout, components.        |
| `fonts/`                    | Bricolage Grotesque, variable, latin subset, with its `OFL.txt`.     |
| `favicon.svg`               | The icon, light and dark.                                            |
| `og.png`                    | The 1200x630 social card, rendered from `og/card.html`.              |
| `CNAME`                     | `gleon.rs`, the custom domain.                                       |
| `.nojekyll`                 | Serves the files as they are, without Jekyll.                        |
| `robots.txt`, `sitemap.xml` | For search engines.                                                  |
| `.well-known/security.txt`  | Where to report a vulnerability (RFC 9116), as in `SECURITY.md`.     |

## Preview

Open `index.html` in a browser, or serve the folder:

```bash
npx serve .
```

To render the social card again after changing `og/card.html`, take a 1200x630 screenshot of it in
light mode with headless Chrome:

```bash
chrome --headless=new --hide-scrollbars --allow-file-access-from-files --blink-settings=preferredColorScheme=1 --window-size=1200,630 --screenshot=og.png "file://$PWD/og/card.html"
```

## Checks

`.github/workflows/check.yaml` validates the pages with `html-validate` (rules in
`.htmlvalidate.json`) and checks every link with lychee, on pull requests, on `main` and weekly.
Run the validation locally the same way:

```bash
npx --yes html-validate@11.17.0 index.html 404.html og/card.html
```

Dependabot keeps the pinned actions up to date. The `html-validate` version in `check.yaml` is
bumped by hand, to a release at least a week old. `.well-known/security.txt` expires on
November 1, 2027: renew its `Expires` line before then.

## Contributing

Every fact on the page comes from the public READMEs and the license of
[gleon-rs/gleon](https://github.com/gleon-rs/gleon) and
[gleon-rs/flutter](https://github.com/gleon-rs/flutter): commands, release assets, supported
platforms, benchmark numbers and license terms. A change there and the matching change here go
together.

## License

The font is under the SIL Open Font License 1.1 (`fonts/OFL.txt`). gleon and gleon.rs are
trademarks of Roman Cinis.
