# Font of Web Cursor Plugin

Design inspiration, font discovery, and design token extraction for Cursor IDE. This plugin connects Cursor to the Font of Web MCP server, enabling AI-powered design workflows.

## Features

- **Design Inspiration Search**: Find visual design references from thousands of curated website screenshots
- **Font Discovery**: Search and research fonts used across the web
- **Design Token Export**: Extract colors, typography, and spacing from any website
- **Color Operations**: Convert, adjust, and analyze colors for design systems

## Installation

1. Copy the `.cursor-plugin` directory to your project root
2. Copy the `skills` directory to your project root
3. Copy `mcp.json` to your project root
4. Restart Cursor or reload the window

## Skills

### design-inspiration

Find design inspiration from millions of saved website screenshots. Search by semantic description, color palette, font pairings, or source domain.

```markdown
Use this skill when you need to:
- Find visual design references for a project
- Search for designs matching a specific aesthetic
- Discover color palettes and typography combinations
- Browse designs from specific websites
```

[Full skill documentation](skills/design-inspiration/SKILL.md)

### font-discovery

Discover and research fonts used across the web. Search font families by name and explore real-world usage examples.

```markdown
Use this skill when you need to:
- Find a specific font by name
- Research similar fonts to a known typeface
- Discover fonts used on popular websites
- Find font pairing suggestions
```

[Full skill documentation](skills/font-discovery/SKILL.md)

### token-export

Extract and export design tokens from any website. Get colors, typography, spacing, borders, and gradients.

```markdown
Use this skill when you need to:
- Extract a website's color palette
- Get typography scales and font usage
- Export design tokens for a design system
- Convert colors between formats
```

[Full skill documentation](skills/token-export/SKILL.md)

## MCP Tools

### search_design_inspiration

Search for design pins using semantic queries with optional filters.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| query | string | Yes | Semantic description of the design |
| color | string | No | Filter by dominant hex color |
| font_ids | string[] | No | Filter by font pairings |
| domain | string | No | Filter by source domain |
| limit | number | No | Max results (default: 5) |

### get_pin_details

Retrieve detailed information about a specific pin.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| pin_id | string | Yes | The unique pin ID |
| include_image | boolean | No | Include base64 preview image |

### display_pin

Display a pin as a visual card.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| pin_id | string | Yes | The pin ID to display |

### font_search

Search for font families by name.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| query | string | Yes | Font family name to search |

### export_domain_tokens

Export design tokens from a domain.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| domain_host | string | Yes | Domain to analyze |
| format | string | No | "css", "tailwind-v4", "dtcg", "json" |
| pin_limit | number | No | Pins to analyze (default: 10, max: 200) |

### batch_color_operations

Perform batch operations on colors.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| operations | object[] | Yes | Array of color operations |

**Available operations**: `hex2rgb`, `hex2oklch`, `rgb2hex`, `lighten`, `darken`, `saturate`, `desaturate`, `grayscale`, `invert`, `rotate`, `opacify`, `transparentize`, `mix`, `luminance`, `chroma`, `opacity`, `contrast`, `apcaContrast`, `readableColor`, `isValidColor`

### visualize_palette

Visualize a list of colors as an interactive palette.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| colors | string[] | Yes | List of hex colors to visualize |

### get_layout_data

Fetch LLM-generated layout analysis for a pin.

| Parameter | Type | Required | Description |
|-----------|------|----------|-------------|
| pin_id | string | Yes | The pin ID |

## Example Workflows

### Find design inspiration for a SaaS dashboard

```
1. Use design-inspiration skill
2. Search for "dark mode SaaS dashboard with sidebar"
3. Filter by color "#3b82f6" for blue accents
4. Get details on promising results
```

### Extract design tokens from a website

```
1. Use token-export skill
2. Export tokens from "linear.app" in Tailwind v4 format
3. Copy the @theme block to your CSS
```

### Research fonts for a project

```
1. Use font-discovery skill
2. Search for "Inter" to get the font ID
3. Search designs using that font for pairing inspiration
```

## Configuration

The MCP server is configured in `mcp.json`:

```json
{
  "mcpServers": {
    "fontofweb": {
      "url": "https://mcp.fontofweb.com/mcp",
      "transport": "http"
    }
  }
}
```

No authentication required for basic usage. Some features may require a Font of Web account for extended access.

## Links

- [Font of Web](https://fontofweb.com) - Main platform
- [Documentation](https://fontofweb.com/docs) - Full documentation
- [MCP Server](https://mcp.fontofweb.com/mcp) - MCP endpoint

## License

MIT
