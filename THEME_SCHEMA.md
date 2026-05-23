# Trifecta Plugin Theme Schema

Plugin themes use the same color system as Trifecta's built-in custom themes.

## Canonical Format (`theme.json`)

```json
{
  "name": "My Theme",
  "version": "1.0.0",
  "primary":   "#cc5500",
  "secondary": "#0d1117",
  "tertiary":  "#252526",
  "hoverRing": "#ff6a00",
  "overrides": {},
  "respectUserOverrides": true
}
```

## Fields

| Field | Required | Description |
|-------|----------|-------------|
| `primary` | ✅ | Accent color — buttons, highlights, Life graph nodes, shape fills |
| `secondary` | optional | Canvas work area background (behind cards). Defaults to `#0d1117` |
| `tertiary` | optional | Sidebar + home screen + card backgrounds. Defaults to `#252526` |
| `hoverRing` | optional | Card glow border color on hover. Defaults to `primary` |
| `overrides` | optional | Per-area paint overrides (same as Paint Elements tool). Object or `{}` |
| `respectUserOverrides` | optional | If `true` (default), user's paint overrides are preserved on top of the theme. If `false`, the plugin's overrides fully replace them. |

## How It Works

The app derives all other visual values automatically from these 3 colors:

- Text colors (light or dark) based on luminance of `tertiary`
- Border opacities based on whether surfaces are dark or light
- Selection highlight tints based on `primary`
- Tooltip backgrounds from `tertiary`

You only need to pick 3 colors. The app handles the rest.

## Tips

- For a **dark theme**: `secondary` and `tertiary` should be dark (luminance < 0.15)
- For a **light theme**: `secondary` and `tertiary` should be light colors
- `primary` can be any accent color — it will automatically get white or black text on top of it depending on its luminance
- `hoverRing` is often a lighter or more saturated version of `primary`

---

# Trifecta Plugin Template Schema

Plugin templates inject structured content into the note editor. There are two subtypes.

## Regular Template (`template.json`)

Injects static HTML into the note editor. The user still chooses which canvas to save to.

```json
{
  "type": "regular",
  "name": "My Template Name",
  "content": "<h2>Section</h2><p>Your content here.</p>"
}
```

## Smart Template (`template.json`)

Routes the note directly to a specific canvas using the user's configured tool sections. No canvas picker is shown.

```json
{
  "type": "smart",
  "name": "My Smart Template",
  "canvasId": "personal"
}
```

Valid `canvasId` values: `"personal"`, `"social"`, `"professional"`, or any custom canvas ID the user has created.

## Rules

- `type` must be exactly `"regular"` or `"smart"` — anything else fails validation silently
- `content` is required for regular and must be a valid HTML string
- `canvasId` is required for smart
- `name` is optional but recommended (used as a fallback note title)
