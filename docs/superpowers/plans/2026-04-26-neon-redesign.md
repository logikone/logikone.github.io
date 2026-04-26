# Neon Sign Redesign Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the current minimal card with a neon sign aesthetic — Alex Brush calligraphy wordmark "logik" in mint neon glow with flicker-in animation and ongoing random per-letter flickers, over a film grain background.

**Architecture:** Two files only — `stylesheet.css` (Google Fonts import, film grain, keyframes, updated card classes) and `index.html` (wordmark split into per-letter spans, tagline/rule removed, icon-only GitHub link, inline script for random flicker). No external JS, no build step.

**Tech Stack:** HTML5, CSS3 (text-shadow neon glow, keyframes), vanilla JS (random letter flicker), Google Fonts (Alex Brush), SVG (inline film grain, GitHub icon)

---

### Task 1: Rewrite stylesheet.css

**Files:**
- Modify: `stylesheet.css`

- [ ] **Step 1: Replace the entire contents of `stylesheet.css` with the following**

```css
@import url('https://fonts.googleapis.com/css2?family=Alex+Brush&display=swap');

*, *::before, *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background-color: #050505;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Courier New', Courier, monospace;
  position: relative;
}

body::after {
  content: '';
  position: fixed;
  inset: 0;
  background-image: url("data:image/svg+xml,%3Csvg viewBox='0 0 200 200' xmlns='http://www.w3.org/2000/svg'%3E%3Cfilter id='n'%3E%3CfeTurbulence type='fractalNoise' baseFrequency='0.9' numOctaves='4' stitchTiles='stitch'/%3E%3C/filter%3E%3Crect width='100%25' height='100%25' filter='url(%23n)' opacity='0.035'/%3E%3C/svg%3E");
  background-size: 200px 200px;
  opacity: 0.6;
  pointer-events: none;
  z-index: 0;
}

.card {
  text-align: center;
  position: relative;
  z-index: 1;
}

@keyframes flicker {
  0%   { opacity: 0; }
  5%   { opacity: 0.8; }
  6%   { opacity: 0; }
  10%  { opacity: 0.9; }
  11%  { opacity: 0; }
  20%  { opacity: 0; }
  21%  { opacity: 1; }
  100% { opacity: 1; }
}

@keyframes flickerSub {
  0%   { opacity: 0; }
  10%  { opacity: 0.6; }
  11%  { opacity: 0; }
  18%  { opacity: 0; }
  19%  { opacity: 0.8; }
  20%  { opacity: 0; }
  30%  { opacity: 0; }
  31%  { opacity: 1; }
  100% { opacity: 1; }
}

@keyframes letterFlicker {
  0%   { opacity: 1; }
  10%  { opacity: 0.1; }
  15%  { opacity: 1; }
  20%  { opacity: 0.25; }
  25%  { opacity: 1; }
  60%  { opacity: 1; }
  62%  { opacity: 0.15; }
  65%  { opacity: 1; }
  100% { opacity: 1; }
}

.card__wordmark {
  font-family: 'Alex Brush', cursive;
  font-size: 5rem;
  font-weight: 400;
  color: #e8fff9;
  text-shadow:
    0 0 2px #ffffff,
    0 0 6px #ffffff,
    0 0 12px #a8f0d8,
    0 0 25px #a8f0d8,
    0 0 45px rgba(168, 240, 216, 0.5),
    0 0 80px rgba(168, 240, 216, 0.2);
  animation: flicker 0.8s ease 0.1s both;
  opacity: 0;
  display: flex;
  justify-content: center;
}

.card__wordmark .letter {
  display: inline-block;
}

.card__wordmark .letter.flickering {
  animation: letterFlicker 0.3s ease forwards;
}

.card__name {
  font-size: 0.75rem;
  letter-spacing: 0.4em;
  color: #9ab5ae;
  margin-top: 0.5rem;
  text-transform: uppercase;
  animation: flickerSub 0.7s ease 0.8s both;
  opacity: 0;
}

.card__links {
  margin-top: 1.6rem;
}

.card__link {
  display: inline-block;
  color: #4a6a60;
  text-decoration: none;
  line-height: 1;
  animation: flicker 0.6s ease 1.4s both;
  opacity: 0;
}

.card__link:hover {
  color: #9ab5ae;
}

.card__link:focus-visible {
  outline: 2px solid #9ab5ae;
  outline-offset: 3px;
}
```

- [ ] **Step 2: Commit**

```bash
git add stylesheet.css
git commit -m "neon: rewrite stylesheet with Alex Brush font, mint glow, film grain, flicker keyframes"
```

---

### Task 2: Rewrite index.html

**Files:**
- Modify: `index.html`

- [ ] **Step 1: Replace the entire contents of `index.html` with the following**

```html
<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>LogikOne</title>
  <link rel="stylesheet" href="stylesheet.css">
</head>
<body>
  <div class="card">
    <h1 class="card__wordmark">
      <span class="letter">l</span><span class="letter">o</span><span class="letter">g</span><span class="letter">i</span><span class="letter">k</span>
    </h1>
    <p class="card__name">Chris Larsen</p>
    <nav class="card__links">
      <a class="card__link" href="https://github.com/logikone" target="_blank" rel="noopener noreferrer" aria-label="GitHub profile">
        <svg width="22" height="22" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
          <path d="M12 0C5.374 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/>
        </svg>
      </a>
    </nav>
  </div>
  <script>
    const letters = document.querySelectorAll('.card__wordmark .letter');
    function randomFlicker() {
      const letter = letters[Math.floor(Math.random() * letters.length)];
      if (!letter.classList.contains('flickering')) {
        letter.classList.add('flickering');
        letter.addEventListener('animationend', () => letter.classList.remove('flickering'), { once: true });
      }
      setTimeout(randomFlicker, 800 + Math.random() * 3200);
    }
    setTimeout(randomFlicker, 2200);
  </script>
</body>
</html>
```

- [ ] **Step 2: Open `index.html` directly in a browser and verify**

  - Page background is very dark (`#050505`) with subtle film grain visible
  - "logik" flickers in as a mint neon calligraphy sign
  - "CHRIS LARSEN" fades in below in small spaced caps
  - GitHub icon appears last, dim, brightens on hover
  - After ~2 seconds, individual letters of "logik" occasionally flicker randomly
  - No leftover tagline, rule, or button border visible

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "neon: rewrite index.html with logik wordmark, per-letter spans, icon-only github link"
```

---

### Task 3: Push to deploy

**Files:** none

- [ ] **Step 1: Push to master**

```bash
git push origin master
```

- [ ] **Step 2: Verify at https://logikone.net (allow ~60 seconds for GitHub Pages)**

  - Neon sign loads and flickers in
  - Random per-letter flickers visible after 2 seconds
  - GitHub icon links correctly to https://github.com/logikone
