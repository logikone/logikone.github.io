# Site Redesign Implementation Plan

> **For agentic workers:** REQUIRED SUB-SKILL: Use superpowers:subagent-driven-development (recommended) or superpowers:executing-plans to implement this plan task-by-task. Steps use checkbox (`- [ ]`) syntax for tracking.

**Goal:** Replace the empty layout shell at logikone.net with a minimal dark personal landing card.

**Architecture:** Two files only — `index.html` (HTML5 markup, centered card) and `stylesheet.css` (full-viewport flex layout, card typography, GitHub button). No JavaScript, no external dependencies.

**Tech Stack:** HTML5, CSS3 (flexbox), inline SVG icon

---

### Task 1: Rewrite stylesheet.css

**Files:**
- Modify: `stylesheet.css`

- [ ] **Step 1: Replace the entire contents of `stylesheet.css` with the following**

```css
*, *::before, *::after {
  box-sizing: border-box;
  margin: 0;
  padding: 0;
}

body {
  background-color: #0a0a0a;
  background-image: url(images/Shy_by_Apri1.jpg);
  background-repeat: no-repeat;
  background-attachment: fixed;
  background-position: right bottom;
  min-height: 100vh;
  display: flex;
  align-items: center;
  justify-content: center;
  font-family: 'Courier New', Courier, monospace;
}

.card {
  text-align: center;
}

.card__wordmark {
  font-size: 2.5rem;
  font-weight: 800;
  letter-spacing: 0.25em;
  color: #ffffff;
  text-transform: uppercase;
}

.card__name {
  font-size: 0.75rem;
  letter-spacing: 0.4em;
  color: #555555;
  margin-top: 0.5rem;
  text-transform: uppercase;
}

.card__rule {
  width: 40px;
  height: 1px;
  background: #333333;
  margin: 1.5rem auto;
  border: none;
}

.card__tagline {
  font-size: 0.75rem;
  letter-spacing: 0.3em;
  color: #888888;
  text-transform: uppercase;
}

.card__links {
  margin-top: 2rem;
}

.card__link {
  display: inline-flex;
  align-items: center;
  gap: 0.5rem;
  color: #aaaaaa;
  text-decoration: none;
  font-size: 0.8rem;
  letter-spacing: 0.05em;
  border: 1px solid #333333;
  padding: 0.5rem 1.1rem;
}

.card__link:hover {
  color: #ffffff;
  border-color: #666666;
}
```

- [ ] **Step 2: Commit**

```bash
git add stylesheet.css
git commit -m "redesign: rewrite stylesheet with dark minimal card layout"
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
    <div class="card__wordmark">LogikOne</div>
    <div class="card__name">Chris Larsen</div>
    <hr class="card__rule">
    <div class="card__tagline">Software Engineer</div>
    <div class="card__links">
      <a class="card__link" href="https://github.com/logikone" target="_blank" rel="noopener noreferrer">
        <svg width="16" height="16" viewBox="0 0 24 24" fill="currentColor" aria-hidden="true">
          <path d="M12 0C5.374 0 0 5.373 0 12c0 5.302 3.438 9.8 8.207 11.387.599.111.793-.261.793-.577v-2.234c-3.338.726-4.033-1.416-4.033-1.416-.546-1.387-1.333-1.756-1.333-1.756-1.089-.745.083-.729.083-.729 1.205.084 1.839 1.237 1.839 1.237 1.07 1.834 2.807 1.304 3.492.997.107-.775.418-1.305.762-1.604-2.665-.305-5.467-1.334-5.467-5.931 0-1.311.469-2.381 1.236-3.221-.124-.303-.535-1.524.117-3.176 0 0 1.008-.322 3.301 1.23A11.509 11.509 0 0112 5.803c1.02.005 2.047.138 3.006.404 2.291-1.552 3.297-1.23 3.297-1.23.653 1.653.242 2.874.118 3.176.77.84 1.235 1.911 1.235 3.221 0 4.609-2.807 5.624-5.479 5.921.43.372.823 1.102.823 2.222v3.293c0 .319.192.694.801.576C20.566 21.797 24 17.3 24 12c0-6.627-5.373-12-12-12z"/>
        </svg>
        github.com/logikone
      </a>
    </div>
  </div>
</body>
</html>
```

- [ ] **Step 2: Open `index.html` directly in a browser and verify**

  - Card is centered vertically and horizontally
  - Background is black with the photo visible in the bottom-right corner
  - "LogikOne" wordmark is large and white
  - "Chris Larsen" is small and grey below it
  - Horizontal rule divider is visible
  - "Software Engineer" tagline is below the rule
  - GitHub button shows the icon and link text
  - Hovering the button lightens the text and border

- [ ] **Step 3: Commit**

```bash
git add index.html
git commit -m "redesign: rewrite index.html as minimal dark landing card"
```

---

### Task 3: Push to deploy

**Files:** none

- [ ] **Step 1: Push to master**

```bash
git push origin master
```

- [ ] **Step 2: Verify at https://logikone.net (allow ~60 seconds for GitHub Pages to deploy)**

  - Page loads with dark background and centered card
  - Background photo visible bottom-right
  - GitHub link is clickable and opens `https://github.com/logikone`
