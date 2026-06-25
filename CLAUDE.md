# serendipity-for-marp — repo guide

A Marp theme coloured by the Serendipity palette. **Restraint by default, customization by a few
variables.** Read this before editing.

## Files

```
css/serendipity-palette.css   @theme serendipity-palette — colour tokens only (--se-*), 3 variants
css/serendipity.css           @theme serendipity         — the theme: @import palette + role map + layout
demo/demo.md                  feature demo (source of truth for "does it still look right")
demo/demo.pdf                 built demo
demo/bg-serendipity.png       demo background image (Serendipity-palette aurora)
demo/preview-*.png            README screenshots (light + midnight)
```

## The architecture (do not break)

1. **Palette is the single source of truth.** `serendipity-palette.css` defines `--se-*` tokens for
   three variants: `:root` = **Morning** (light, default); `section.midnight` and `section.sunset`
   override the same tokens for the dark variants.
2. **The theme only maps roles → tokens**, and does it **on the `section` selector** (not `:root`) so
   `var(--se-*)` re-resolves per slide — that is what makes `class: midnight` recolour everything.
   Never bake a palette colour into a rule; always go through a role var.
3. **Colour is never automatic.** Callout tints are opt-in (`_class: info|ok|warn|danger`).

### Role → token map (in `serendipity.css`, on `section`)

| role | token | role | token |
|---|---|---|---|
| `--accent`   | `--se-blue`       | `--bg`     | `--se-bg`        |
| `--ink`      | `--se-ink`        | `--panel`  | `--se-surface`   |
| `--ink-soft` | `--se-ink-2`      | `--line`   | `--se-line`      |
| `--muted`    | `--se-muted`      | `--c-info` | `--se-cornflower`|
| `--c-ok`     | `--se-teal`       | `--c-warn` | `--se-tangerine` |
| `--c-danger` | `--se-coral`      |            |                  |

`--accent` drives: top rule, foot band, title underline, list markers, links, callout border,
table header, `blockquote h4`. `--on-accent` (band text) is white; flipped to `--se-bg` on dark variants.

## Build / preview (run from repo root)

```bash
marp demo/demo.md -o demo/demo.pdf \
  --theme-set css/serendipity-palette.css css/serendipity.css --allow-local-files

# self-check: render pages and READ them (PDFs can't be eyeballed inline)
python3 -c "import fitz;d=fitz.open('demo/demo.pdf');[d[i].get_pixmap(matrix=fitz.Matrix(1.4,1.4)).save(f'/tmp/p{i+1:02d}.png') for i in range(d.page_count)]"
# (read /tmp/p*.png, then) rm -f /tmp/p*.png

# refresh README screenshots after a visual change (light + dark, the table slide)
# build a midnight copy with `class: midnight` and render the same page to demo/preview-midnight.png
```

## Conventions

- **Two `--theme-set` files, palette first.** The theme `@import 's the palette by @theme name.
- Slide title = `#` (h1). Sub-heading = `##`. One idea per slide.
- After any visual edit: rebuild, render every page, READ them, then refresh `demo/preview-*.png`.
- Keep it offline: system fonts only, no CDN / web-font `@import`.
- Non-colour knobs live in `:root` of `serendipity.css`; colour lives only in the palette.

## Gotchas

- `content: none` on a positioned pseudo-element is unreliable in Chromium — use `display: none`
  to hide `::before`/`::after` (see cover/lead overrides).
- Role vars must be declared on `section`, not `:root`, or variant switching won't cascade.
