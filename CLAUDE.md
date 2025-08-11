# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a responsive email template development project using MJML (Mailjet Markup Language) for the Kaizen Ticketing system. The templates integrate with a .NET backend using Razor syntax for dynamic content.

## Development Commands

- `npm run dev` - Start development mode (watches files and serves with live reload)
- `npm run build` - Compile all MJML files from src/ to HTML in build/
- `npm run watch` - Watch MJML files for changes and auto-compile
- `npm run serve` - Copy images and start local server with browser-sync

## Architecture

### Template Structure
- **Source files**: `src/*.mjml` - MJML templates with Razor syntax
- **Output**: `build/*.html` - Compiled HTML files
- **Images**: `src/images/` - Email assets including icons and brand images (all have @2x versions for retina)

### Key Patterns
1. **Razor Integration**: Templates use `@inherits`, `@Model`, and Razor variables for .NET backend integration
2. **CSS Variables**: Define theme colors (primary, secondary, body-color, body-bg) at the top of each template
3. **Localization**: Use template strings like `%=notification_greeting=%` for multi-language support
4. **Responsive Design**: MJML handles email client compatibility automatically
5. **Image Handling**: All images should have both standard and @2x versions for retina displays

### Template Variables
Common variables defined in templates:
- Color scheme: `primary`, `secondary`, `bodyColor`, `bodyBG`
- Typography: `fontWeightBase`, `headingsFontWeight`, `btnFontWeight`, `googleFontName`
- Layout: `borderRadius`
- Configuration: `channelBaseUrl`

## Important Notes

- **No test framework** is currently configured
- **No linting tools** are set up
- When modifying templates, ensure Razor syntax is preserved for backend integration
- Images must be copied to build/ directory for local preview (handled by `npm run serve`)
- Bootstrap 5.3.7 is available but primarily used for CSS utility alignment with the main application