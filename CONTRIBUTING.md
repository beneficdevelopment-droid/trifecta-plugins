# Contributing to the Trifecta Plugin Registry

This guide walks you through the process of submitting a plugin to the Trifecta Plugin Registry.

## Step 1 — Fork the Repository

1. Click the **Fork** button in the top-right of this repository
2. GitHub will create a copy of the repo under your account
3. Make any necessary changes to your fork

## Step 2 — Create Your Plugin Folder

In your fork, navigate to `plugins/` and create a new folder using your plugin's ID as the folder name. The ID should be lowercase, hyphen-separated, and unique.

Example: `plugins/my-awesome-theme/`

## Step 3 — Add Your Plugin Files

Add one or more files inside your plugin folder. At minimum, you must include `manifest.json`. Depending on your plugin type, you may also include other files:

- `manifest.json` — Required for all plugin types
- `theme.json` — For theme plugins
- `index.html` — For toolbar-tool plugins
- `template.json` — For note-template plugins

## Step 4 — Update index.json

Add a new entry to the `plugins` array in `index.json` in the root of the repo. Each entry must include:

- `id` — Must match your folder name
- `name` — Human-readable plugin name
- `type` — One of: `theme`, `toolbar-tool`, or `note-template`
- `version` — Valid semver string (e.g., `1.0.0`)
- `version` — A valid plugin description
- `pricing` — Object with at least a `model` field
- `files` — Mapping of filenames to their public GitHub Pages URLs

Use the existing sample entries as a reference.

## Step 5 — Open a Pull Request

1. Push your changes to your fork
2. Go to the original `trifecta-plugins` repository
3. Click **Pull requests** > **New pull request**
4. Select your fork and branch
5. Submit the PR with a clear description of your plugin

## Step 6 — Wait for Validation

An automated GitHub Action runs on every PR. It checks:

- `manifest.json` exists and parses as valid JSON
- The `id` field matches the folder name
- The `type` field is one of `theme`, `toolbar-tool`, or `note-template`
- The `version` field is valid semver
- Any `permissions` field only contains values from the allowed list

If validation passes, a success comment is posted on your PR. If it fails, a comment will detail exactly what went wrong so you can fix it.

## Allowed Permissions

If your plugin requires permissions, the following values are allowed:

`canvas.read`, `canvas.addNode`, `canvas.updateNode`, `canvas.focusNode`, `canvas.showToast`, `canvas.getTheme`, `canvas.isOnline`, `canvas.realestate`, `storage.read`, `storage.write`, `network`
