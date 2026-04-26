# Site Redesign Design

**Date:** 2026-04-25
**Project:** logikone.net

## Goal

Replace the current empty layout shell with a minimal dark personal landing card.

## Visual Style

- Background: solid `#0a0a0a` with `Shy_by_Apri1.jpg` retained as a fixed background image, positioned bottom-right
- Typography: monospace font stack, spaced caps for labels
- Color palette: white wordmark, mid-grey name/tagline, dark-grey rule and border, light-grey link text
- No JavaScript, no external frameworks or CDN dependencies

## Page Structure

Single centered card, vertically and horizontally centered in the viewport.

Card contents (top to bottom):
1. **LOGIKONE** — large bold monospace wordmark (white)
2. **Chris Larsen** — small spaced caps (mid-grey)
3. Thin horizontal rule (dark-grey divider)
4. **Software Engineer** — small spaced caps tagline (mid-grey)
5. GitHub link button — `github.com/logikone` with inline SVG GitHub icon, outlined button style

## Files Changed

- `index.html` — rewritten to HTML5; old float-based wrapper divs replaced with a single flexbox centering layout; `<base href>` pointing to old domain removed
- `stylesheet.css` — rewritten; old float layout removed; new styles: full-viewport flex centering, card typography, GitHub button

## Out of Scope

- No navigation, no projects section, no contact form
- No additional social links beyond GitHub
- No JavaScript or animations
