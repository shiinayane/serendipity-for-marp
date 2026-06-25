---
marp: true
theme: serendipity
paginate: true
footer: 'serendipity · feature demo'
---

<!-- _class: cover -->
<!-- _paginate: false -->
<!-- _footer: '' -->

# serendipity — feature demo

## one deck exercising every part of the theme

Yankai WANG · Suzumura Lab · The University of Tokyo
2026-06-25

---

<!-- _class: lead -->

# 1 · Text & typography

---

# Slide title is `#` (h1)

## A sub-heading is `##` (h2)

### And `###` is a quiet h3

Body text. **Bold is the only in-text emphasis**, *italic* is available, an
[inline link](https://marp.app) is underlined quietly, and `inline code` sits in a soft chip.

<span class="large">Large text</span> · normal · <span class="small">small text</span> ·
<span class="muted">muted secondary text</span>

- unordered lists use a quiet accent marker
- one idea per bullet

1. ordered lists work too
2. second item

---

# Callouts (one sober box)

A plain blockquote is the default callout:

> Score on what actually executed — not on what the model says.

Add an `#### heading` for a titled callout:

> #### Takeaway
> Colour is off by default. The box is panel-fill with one accent edge.

---

<!-- _class: info -->

# Opt-in colour — `info`

Colour is **never automatic**. Put a class on the slide only when you mean it.

> #### Note
> `<!-- _class: info -->` tints every callout on this slide.

The full set: `info` · `ok` · `warn` · `danger` — all low-saturation.

---

<!-- _class: danger -->

# Opt-in colour — `danger`

> #### Warning
> `<!-- _class: danger -->` — same mechanism, a different deliberate hue.

Use sparingly: one tinted slide should mean something.

---

<!-- _class: lead -->

# 2 · Layout

---

# Columns (simple flex)

<div class="cols">
<div>

**Two equal** — `class="cols"`

- markdown works inside
- equal width by default

</div>
<div>

**~60 / 40** — `class="cols uneven"`

- first child gets more room
- good for text + figure

</div>
</div>

**Three** — `cols-3`

<div class="cols-3">
<div>

column one

</div>
<div>

column two

</div>
<div>

column three

</div>
</div>

---

# Full-width table

| Work | Ground | Clarify | Safety | Execute | Monitor |
|---|:--:|:--:|:--:|:--:|:--:|
| Baseline A | ✓ |   |   | ✓ |   |
| Baseline B | ✓ | ✓ |   | ✓ | ✓ |
| **Ours** | ✓ | ✓ | ✓ | ✓ | ✓ |

> Booktabs-style rules, no width cap, accent header — `tbody` rows get hairlines.

---

# Image & caption

<div class="cols uneven">
<div>

![w:380 center](demo-fig.png)

<div class="caption">Figure 1. A centered image with a <code>.caption</code>.</div>

</div>
<div>

- `![w:380 center]` centers and sizes
- `![left]` / `![right]` float text around it
- no 50% width cap — images go full size

</div>
</div>

---

<!-- _class: nav -->
<!-- header: 'Motivation · **Method** · Results · Conclusion' -->

# Optional top nav

Add `<!-- _class: nav -->` plus a `header:` to get a quiet section bar
(bold the current one). Useful for longer talks.

> The bar is the panel fill with one accent underline — same restraint as everything else.

---

<!-- _class: lead -->
<!-- header: '' -->

# 3 · Customize

---

# Recolour with one line; tune with a few

Colour is the shared **Serendipity** palette. Switch the whole deck in front-matter:

```yaml
class: midnight    # dark · cool      (or  sunset  — dark · violet)
```

Density & fonts are the only knobs (`:root` in `serendipity.css`):

```css
--fs: 26px;   --pad: 54px;   --gap: 1.5rem;
```

> #### The point
> The palette is the single source of truth — every theme maps onto it. Restraint by default, power on demand.

---

<!-- _class: lead -->

# serendipity

restraint by default · power on demand
