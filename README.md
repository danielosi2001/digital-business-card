# Digital Business Card — Daniel Osi

A personal digital business card built for **תרגיל 1**.

Live site: _add your GitHub Pages URL here_

## Requirements covered

| Requirement | Where |
|---|---|
| Full name and role | `.masthead` |
| Profile picture | `assets/profile.svg` (replace with your own) |
| Short paragraph about me | About section |
| GitHub link | Contact section |
| LinkedIn link | Contact section |
| Phone number | Contact section (`tel:` link) |
| Email address | Contact section (`mailto:` link) |
| Dark / light mode toggle | Hidden checkbox + `:has()` — `style.css` §2, §5 |
| Responsive layout | `clamp()`, CSS grid `auto-fit`, one media query at 620px |
| Semantic HTML | `header`, `main`, `section`, `article`, `dl`, `footer` |
| External stylesheet | `style.css` — no inline styles in the HTML |
| No JavaScript | The project contains zero `.js` files |

## Design direction — "Strata"

Full-stack means layers, so the page is organised as one: the Skills section is
drawn as a geological section through the stack, interface at the surface down to
platform at the base, each band a step deeper in tone. Team-lead practices are an
open band rather than a solid one, because they run through every layer instead of
sitting in one.

Palette is deep teal-black and cool grey-green paper, with ochre used in exactly two
places. Type is Bricolage Grotesque for the name, Public Sans for reading, and
JetBrains Mono for the technical labels.

## How the theme switch works without JavaScript

1. A hidden `<input type="checkbox" id="theme-toggle">` holds the theme state.
2. A `<label for="theme-toggle">` is the visible button — clicking a label toggles
   its checkbox natively, no script required.
3. `:root:has(#theme-toggle:checked)` redeclares the CSS custom properties.

Because every colour in the stylesheet is a variable, the whole page recolours from
that one rule — no component styles need to know a theme exists.

## Scroll effects without JavaScript

`animation-timeline` swaps the clock that normally drives a CSS animation for the
scroll position itself:

- `scroll(root block)` drives the progress line at the top of the page.
- `view()` drives each section's reveal and each stack band's entrance, because it
  measures that element's own progress across the viewport.

Both sit inside `@supports (animation-timeline: view())`, so a browser without the
feature falls back to the load animation and never hides content.

## Structure

```
digital-business-card/
├── index.html
├── style.css
├── README.md
└── assets/
    ├── profile.svg
    └── favicon.svg
```

## Mock data

The assignment states that content need not be real — the emphasis is on
implementation and design. Everything below is invented and safe to keep, edit,
or replace:

| Field | Current value |
|---|---|
| Email | `daniel@osi.dev` |
| Phone | `+972 54-812-3390` |
| GitHub | `github.com/danielosi2001` — real account |
| LinkedIn | `linkedin.com/in/danielosi` |
| Institution | Holon Institute of Technology |
| Course | Coding Academy |
| Projects | Mesh, Currents, Ledgerline |
| Portrait | `assets/profile.jpg` — GAN-generated face; no real person |

`assets/profile.svg` is kept as an illustrated alternative. To use it instead,
point the `src` in `index.html` at it and set `--photo-grade` to `none`.

## Before submitting

- **GitHub URL must be real** — it has to point at the repo you actually publish
- **Check the institution line** — it is a credential claim next to a real name
- Swap the portrait for a photo if you'd rather, by replacing `assets/profile.svg`
  or pointing the `src` in `index.html` at a new file
- Confirm the GitHub Pages link loads before submitting; a dead link counts as a
  non-submission under the assignment rules
