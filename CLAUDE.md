# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a Jekyll-based static website for nostr.party, which provides:
- NIP-05 verification/hosting for Nostr identities
- Information about Nostr Web of Trust relay (wss://wot.nostr.party)
- A JSON-themed UI that displays site information

The site uses the `hacked-jekyll` theme and renders a custom JSON-like interface with typewriter effects.

## Development Commands

### Local Development
```bash
bundle install          # Install dependencies
bundle exec jekyll serve   # Run development server (usually at http://localhost:4000)
```

### Build
```bash
bundle exec jekyll build   # Build site to _site/ directory
```

## Architecture

### Content Management
- **_data/json.yml**: Primary data source for the home page content. Structured as key-value pairs that render in JSON format on the site
- **_layouts/home.html**: Custom layout that converts json.yml data into styled JSON output with conditional formatting (quotes, commas, etc.)
- **_layouts/default.html**: Base HTML wrapper with Typed.js integration for typewriter animation

### NIP-05 Identity Resolution
- **.well-known/nostr.json**: Standard Nostr NIP-05 identity mapping file
  - Maps user handles (e.g., "shawn", "hello", "_") to Nostr public keys (npub hex format)
  - Served with CORS headers via Netlify configuration

### Deployment
- Hosted on Netlify
- **netlify.toml**: Configures CORS headers for /.well-known/* paths (required for NIP-05 verification)

### Theme Customization
The site overrides the hacked-jekyll theme's home layout to create a custom JSON-styled interface with:
- Dynamic quote handling (keys/values/both/none)
- Optional comma separators
- Link handling with configurable target (_blank/_self)
- Typed.js animation for typed field
