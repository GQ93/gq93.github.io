# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

Static academic personal website for Gang Qu, Ph.D. — hosted on GitHub Pages at gq93.github.io. Built on the LeCV Bootstrap template with extensive custom styling.

## Development

No build system, bundler, or package manager. The site is plain HTML/CSS/JS served directly by GitHub Pages. To preview locally, open `index.html` in a browser or use any static file server (e.g., `python3 -m http.server`).

Deploying is just pushing to `main` — GitHub Pages serves from the root.

## Architecture

**Pages:** Multi-page layout with `index.html` (home/landing) and `multipage-*.html` files for each section (about, experience, publication, research, talks, news). Each page is a standalone HTML file sharing the same nav bar and footer markup (no templating — changes to shared elements must be replicated across all pages).

**Styling layers (load order matters):**
- `css/bootstrap/` — Bootstrap 3 base
- `css/stylesheet.css` — main theme styles (compiled from `css/stylesheet.less`)
- `css/academic-override.css` — custom Apple-inspired overhaul that heavily overrides the theme; most visual tweaks go here

LESS source files live in `css/less/` and `css/*.less` but there is no automated LESS compilation configured. The compiled `.css` files are committed directly.

**JavaScript:** jQuery 1.11 + assorted plugins in `js/`. No custom application JS — interactivity comes from plugin initialization in inline scripts within the HTML files.

**Assets:**
- `images/` — photos, favicons, blog images
- `files/` — downloadable PDFs (CV, resume)
- `phpmailer/` — server-side PHP mail classes (contact form backend; not used by GitHub Pages static hosting)

## Key Conventions

- Font: Inter (loaded from Google Fonts), with Apple system font fallback stack
- The site uses Font Awesome 6 (`css/font-awesome/`) for icons
- Publications, news, and experience entries are hardcoded HTML — no data files or templates
- Structured data (JSON-LD schema.org Person) is embedded in `index.html` `<head>`
- SEO meta tags and Open Graph tags are in each page's `<head>`
