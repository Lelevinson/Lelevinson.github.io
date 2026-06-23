# lelevinson.github.io — Personal Portfolio

**Live:** https://lelevinson.github.io/

A single-page portfolio. **No build step** — it's one `index.html` using Tailwind CSS (Play CDN) +
vanilla JS, plus a couple of small CDN libraries (AOS, GLightbox). Edit the file, refresh, done.

## Preview locally
Open `index.html` in a browser. A few things (the YouTube embed) prefer `http`, so if needed run any
static server from this folder, e.g. `npx serve`.

## How to edit — you only touch content
Layout, responsiveness (mobile included), light/dark mode, and the animations are all generalized, so
**adding content "just works"**: text wraps, cards reflow to one column on phones, and everything picks
up the theme automatically. Where each thing lives in `index.html`:

| Want to change…        | Section                     | How                                                                                  |
|------------------------|-----------------------------|--------------------------------------------------------------------------------------|
| **A project**          | `<section id="work">`       | Copy one `<article class="card-lift …">` block; edit title / text / tags / links.    |
| **A research item**    | `<section id="research">`   | Copy one `<article …>` block.                                                        |
| **A skill group**      | `<section id="skills">`     | Copy one card `<div class="card-lift …">`.                                           |
| **A credential/award** | `<section id="certs">`      | Copy one `<a class="cred …">` row (real link/PDF), or a plain `<div>` for no link.   |
| **An experience/role** | `<section id="experience">` | Copy one card `<div>` (or the featured `<article>` for a highlighted one).           |
| **About / hero text**  | `<section id="about">`, hero | Just edit the text in place.                                                        |
| **Contact + socials**  | `<section id="contact">` + hero icons | Edit the `href`s.                                                          |
| **Files (certs/imgs)** | `assets/`, `assets/certs/`  | Drop the file, point the link at it.                                                 |

Reusable bits: a tag is `<span class="chip">…</span>`; a small label is `<p class="eyebrow …">`.

## Updates itself automatically (don't worry about these)
- **Responsive / mobile** — grids are `lg:grid-cols-N` and collapse to 1 column on phones; a new card just flows in.
- **Light/dark mode** — colors are CSS variables (`--c-accent`, `--c-ink`, `--c-paper`, `--c-surface`) at the top
  of `<style>`. Use the theme classes (`text-ink`, `bg-surface`, `text-accent`, …) and it themes itself.
  Change `--c-accent` once to re-skin the whole site.
- **The Claude-Code mascot peek** — auto-attaches to every `<section>` (desktop: on hover, phones: on scroll).
  A new section gets one for free.

## The ONE thing to also update if you add a *whole new section*
(Adding content to an existing section needs nothing extra.) If you add a new `<section id="something">`:
1. add a link in the desktop nav — `<div id="nav-links">`
2. add the same link in the mobile menu — `<div id="mobile-menu">`
3. add `'something'` to the scrollspy list in the `<script>` (the `['work','research',…]` array)

Everything else adapts on its own.
