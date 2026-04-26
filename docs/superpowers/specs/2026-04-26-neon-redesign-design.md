# Neon Sign Redesign Design

**Date:** 2026-04-26
**Project:** logikone.net

## Goal

Replace the current minimal dark card with a neon sign aesthetic — a calligraphy wordmark with mint glow, flicker-in animation, and ongoing random per-letter flickers, over a film grain background.

## Visual Style

- **Background:** `#050505` with a subtle SVG `feTurbulence` film grain overlay at ~3.5% opacity
- **Wordmark font:** Alex Brush (Google Fonts), ~5rem, color `#e8fff9`
- **Neon glow:** 6-layer `text-shadow` stack — two white-hot inner glows → two mint (`#a8f0d8`) mid glows → two fading mint halos at low opacity. Creates the look of a lit neon tube with a bright core.
- **Supporting text:** "Chris Larsen" in Courier New, `#9ab5ae`, small spaced caps
- **GitHub link:** Icon-only (22px inline SVG), color `#4a6a60`, lightens to `#9ab5ae` on hover. No text, no border.

## Animation

**On-load flicker-in (runs once):**
- Wordmark flickers in first (`@keyframes flicker`, delay 0.1s)
- Name flickers in behind it (`@keyframes flickerSub`, delay 0.8s)
- GitHub icon flickers in last (`@keyframes flicker`, delay 1.4s)

**Ongoing per-letter flicker (JS, runs indefinitely):**
- After initial animation settles (~2.2s), a `setTimeout` loop picks a random letter of "logik" every 800–4000ms
- Applies `@keyframes letterFlicker` (brief opacity dip and recover) to that letter's `<span>`
- Simulates a neon tube briefly losing contact

## Structure

The wordmark `<h1>` contains individual `<span class="letter">` elements — one per character — so JS can target them for per-letter flickering. The `<script>` block lives inline at the bottom of `<body>`.

## Files Changed

- `stylesheet.css` — `@import` Alex Brush from Google Fonts; film grain `body::after`; flicker `@keyframes`; `.card__wordmark` font/color/text-shadow/animation; `.card__name` and `.card__link` styles; `.card__link` hover state
- `index.html` — wordmark changed to "logik" with per-letter `<span>` markup; tagline (`<p class="card__tagline">`) and rule (`<hr class="card__rule">`) removed; GitHub link changed to icon-only; inline `<script>` for random letter flicker

## Out of Scope

- No other content sections
- No additional links
- No CSS framework or JS library
