# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Overview

This is a static HTML website for [logikone.net](https://logikone.net), hosted via GitHub Pages. There is no build step, no package manager, and no test suite — changes to files are deployed automatically when pushed to the `master` branch.

## Structure

- `index.html` — single-page site using HTML 4.01 with a fixed layout
- `stylesheet.css` — CSS layout and background image styling
- `images/` — static image assets
- `CNAME` — GitHub Pages custom domain (`logikone.net`)
- `google9cc84680a6c3ea29.html` — Google site verification file
- `keybase.txt` — Keybase identity verification file
- `robots.txt` — crawler directives

## Deployment

Push to `master` → GitHub Pages serves the site automatically at logikone.net. No CI, no build process.