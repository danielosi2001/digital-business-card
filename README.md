# Digital Business Card — Daniel Osi

A personal digital business card built for **תרגיל 1**.

Live site: **https://danielosi2001.github.io/digital-business-card/**
Repository: https://github.com/danielosi2001/digital-business-card

## Requirements covered

| Requirement | Where |
|---|---|
| Full name and role | `.masthead` |
| Profile picture | `assets/profile.jpg` |
| Short paragraph about me | About section |
| GitHub link | Contact section |
| LinkedIn link | Contact section |
| Phone number | Contact section (`tel:` link) |
| Email address | Contact section (`mailto:` link) |
| Dark / light mode toggle | Hidden checkbox + `:has()` in `style.css` |
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

## Content status

Most of the card is now real. What is still stand-in:

| Field | Status |
|---|---|
| Name, role, about | Real |
| Experience | Real — company names and dates not yet added |
| SHRAGA | Real — tech stack listed is partial |
| Contact (email, phone, GitHub, LinkedIn) | Real |
| Education | **Unverified** — institution and course are placeholders |
| The stack: Application, Data rows | **Unverified** — carried over from the draft |
| Portrait | Synthetic. `assets/profile.jpg` is a GAN-generated face, not a real person |

`assets/profile.svg` is kept as an illustrated alternative. To use it instead,
point the `src` in `index.html` at it and set `--photo-grade` to `none`.

## Before submitting

- **Check the institution line** — it is a credential claim next to a real name
- Swap the portrait for a photo if you'd rather, by replacing `assets/profile.svg`
  or pointing the `src` in `index.html` at a new file
- Confirm the GitHub Pages link loads before submitting; a dead link counts as a
  non-submission under the assignment rules
