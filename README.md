# nostr.party

A Jekyll-based static website providing Nostr services with a unique JSON-themed interface.

## What is nostr.party?

nostr.party is a service provider for the Nostr protocol, offering:

- **NIP-05 Verification**: Host your Nostr identity at a custom address (e.g., `yourname@nostr.party`)
- **Web of Trust Relay**: Connect to `wss://wot.nostr.party` for WoT-filtered Nostr content
- **Clean, Minimal UI**: A terminal-inspired JSON interface with typewriter effects

## Live Site

Visit [https://nostr.party](https://nostr.party) to see the site in action.

## Features

- **NIP-05 Identity Hosting**: Provides `.well-known/nostr.json` endpoint for Nostr identity verification
- **JSON-Styled Interface**: Custom Jekyll layouts that render content as formatted JSON
- **Typewriter Animation**: Uses Typed.js for animated text display
- **CORS-Enabled**: Proper headers for Nostr client integration

## Development

### Prerequisites

- Ruby (with Bundler)
- Jekyll 4.4.1

### Getting Started

1. Install dependencies:
   ```bash
   bundle install
   ```

2. Run the development server:
   ```bash
   bundle exec jekyll serve
   ```

3. Visit `http://localhost:4000` in your browser

### Building for Production

```bash
bundle exec jekyll build
```

The site will be generated in the `_site/` directory.

## Project Structure

```
.
├── _data/
│   └── json.yml          # Main content data (displayed as JSON on homepage)
├── _layouts/
│   ├── default.html      # Base HTML template with Typed.js
│   ├── home.html         # Custom JSON-styled layout
│   └── 404.html          # Error page layout
├── .well-known/
│   └── nostr.json        # NIP-05 identity mappings
├── _config.yml           # Jekyll configuration
└── netlify.toml          # Netlify deployment config (CORS headers)
```

## Editing Content

The main site content is managed through `_data/json.yml`. This file uses a structured format that gets rendered as styled JSON on the homepage. Add or modify entries to update the site content.

Example structure:
```yaml
- key: name
  value: nostr.party
- key: description
  value:
    - line 1
    - line 2
  typed: true  # Enables typewriter effect
```

## Adding NIP-05 Identities

Edit `.well-known/nostr.json` to add new Nostr identity mappings:

```json
{
  "names": {
    "username": "hex_public_key_here"
  }
}
```

## Deployment

The site is configured for Netlify deployment with automatic CORS header handling for the `.well-known/` directory.

## Theme

This site uses the [hacked-jekyll](https://github.com/tocttou/hacked-jekyll) theme with custom layout overrides.

## Learn More About Nostr

- [nostr.com](https://nostr.com) - About the Nostr protocol
- [nostrapps.com](https://www.nostrapps.com) - Directory of Nostr applications
- [Nostr Documentary](https://www.youtube.com/watch?v=aA-jiiepOrE)

## License

See LICENSE file for details.
