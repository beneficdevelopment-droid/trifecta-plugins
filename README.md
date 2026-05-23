# Trifecta Plugin Registry

This repository is the official plugin registry for the Trifecta desktop application.

Plugins listed here are fetched directly by the Trifecta app at runtime. Do not browse this repository to install plugins — open Trifecta and use the built-in plugin browser instead.

## For Users

To install plugins:

1. Open the Trifecta desktop app
2. Navigate to the Plugin Browser section
3. Browse available plugins and install directly from within the app

## For Developers

Want to submit a plugin? See [CONTRIBUTING.md](CONTRIBUTING.md) for the full submission process.

In short: fork this repo, add your plugin files under `plugins/your-plugin-id/`, add an entry to `index.json`, and open a Pull Request. An automated validator will check your submission.

## Repository Structure

- `index.json` — Main registry file (fetched by the app)
- `plugins/` — Plugin files organized by plugin ID
- `.github/workflows/validate-plugin.yml` — Automated PR validator
