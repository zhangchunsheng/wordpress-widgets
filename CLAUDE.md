# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

A collection of WordPress widgets — small, embeddable UI components that can be integrated into WordPress sites. Widgets are self-contained HTML/CSS/JavaScript files.

## Architecture

- **Widget structure**: Each widget is a standalone HTML file with inline CSS and JavaScript
- **Styling**: Uses CSS custom properties (e.g., `var(--color-background-primary)`, `var(--border-radius-lg)`) to inherit WordPress theme styles
- **Data fetching**: Widgets fetch data from external APIs via JSONP callbacks to avoid CORS issues
- **No build step**: Widgets are vanilla HTML/CSS/JS — no compilation or bundling required

## Existing Widgets

### `daily_english_iciba.html`
Displays daily English quotes from 爱词霸 (iciba.com). Features:
- Date picker to query historical quotes
- JSONP callback pattern for cross-origin requests
- Responsive card layout with image and text content
- API endpoint: `https://sentence.iciba.com/index.php?c=dailysentence&m=getdetail`

## Development Patterns

- **JSONP for API calls**: Use callback pattern (`callback=icibaCb_&timestamp`) for external API requests
- **Scoped IDs**: Prefix all IDs with unique identifier (e.g., `dse-` for Daily English) to avoid WordPress theme conflicts
- **IIFE wrapper**: Wrap JavaScript in `(function(){ ... })();` to avoid global scope pollution
