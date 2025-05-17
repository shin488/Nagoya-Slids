# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a single-page HTML presentation about Nagoya city using the impress.js presentation framework (version 0.5.3). The presentation is in Japanese and covers:
- Nagoya overview (location, population, climate)
- History
- Tourist attractions
- Local cuisine ("Nagoya-meshi")
- Culture and festivals
- Summary with reference links

## Architecture

The project consists of a single file:
- `nagoya-impress.html`: Self-contained HTML presentation with embedded CSS and JavaScript
- Uses impress.js CDN (0.5.3) for presentation functionality
- Includes external images from Wikimedia Commons with proper attribution
- Styling with Google Fonts (Noto Sans JP)

## Development Commands

This is a static HTML file project with no build process. To work with it:

1. **View the presentation**: Open `nagoya-impress.html` directly in a modern web browser
2. **Modify content**: Edit the HTML directly, each `<div class="step">` represents a slide
3. **Navigation**: Use keyboard arrows or spacebar to navigate between slides

## Key Structure

The impress.js presentation format uses:
- `<div id="impress">`: Container for all slides
- `<div class="step" data-x="[position]" data-y="[position]">`: Individual slides
- Position attributes (`data-x`, `data-y`) define slide layout in 3D space
- Each step is positioned 1000 units apart on the x-axis

## Important Notes

- All external resources (CSS, JS, fonts) are loaded from CDNs
- Images are sourced from Wikimedia Commons with CC licenses noted
- The presentation is in Japanese language
- No local dependencies or build tools required