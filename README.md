# Serendipity for Marp

A **sober, layout-capable** [Marp](https://marp.app) theme, coloured by the
[Serendipity palette](https://github.com/Serendipity-Theme/color-palette).

Built on one principle: **restraint by default, customization by a few variables.**
It sits between the two extremes — more layout power than minimalist themes, none of the
kitchen-sink flashiness — and every colour comes from one shared palette so all your decks
stay consistent.

| Morning (light) | Midnight (dark) |
|---|---|
| ![light](demo/preview-light.png) | ![dark](demo/preview-midnight.png) |

See [`demo/demo.pdf`](demo/demo.pdf) for every feature on one deck.

## Install

Copy the two CSS files into your project (or add this repo as a submodule). The theme
`@import`s the palette, so **pass both to `--theme-set`, palette first**:

```bash
marp deck.md -o deck.pdf \
  --theme-set serendipity-palette.css serendipity.css --allow-local-files
```

On **Overleaf/VS Code (Marp extension)**: register both CSS paths in the Marp themes setting.

In your deck's front-matter:

```yaml
---
marp: true
theme: serendipity
paginate: true
# class: midnight     # optional: dark variant (or: sunset)
---
```

## Two files, one idea

- **`serendipity-palette.css`** — the colour tokens (`--se-*`), the single source of truth.
  Three variants: **Morning** (light, default), **Midnight** (dark/cool), **Sunset** (dark/violet).
- **`serendipity.css`** — the theme. It maps semantic roles onto the palette and defines the
  layout. Recolouring never means editing theme rules — you swap the variant.

Switch the whole deck's palette with one front-matter line: `class: midnight` or `class: sunset`.

## Features

- **Cover** (`_class: cover`) and **section dividers** (`_class: lead`)
- **Columns** — `class="cols"` (equal), `class="cols uneven"` (~60/40), `class="cols-3"`
- **Full-width tables** (booktabs-style) and **full-width images** — no width caps
- **One sober callout** — a blockquote; add `#### Title` for a titled box; opt-in tints via
  `_class: info | ok | warn | danger` (colour is never automatic)
- **Signature accent foot band** + thin top rule; optional top nav (`_class: nav` + `header:`)
- `.muted` / `.small` / `.large`, image `.caption`, `![center|left|right]` image alignment
- **Offline, CJK-safe fonts** (system stack + Hiragino/Noto fallback) — no CDN, no web fonts

## Customize

Colour: switch the variant, or edit the tokens in `serendipity-palette.css`.
Density & fonts: the knobs in `:root` at the top of `serendipity.css`:

```css
--fs: 26px;   --pad: 54px;   --gap: 1.5rem;   --foot-h: 34px;
```

To add a new variant, copy a `section.<name> { --se-* … }` block in the palette file.

## Credits & licence

Colours from [Serendipity-Theme/color-palette](https://github.com/Serendipity-Theme/color-palette) (MIT).
This theme is released under the [MIT licence](LICENSE).
