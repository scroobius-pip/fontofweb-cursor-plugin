---
name: design-inspiration
description: Find design inspiration from millions of saved website screenshots. Search by description, color, fonts, or domain.
---

# Design Inspiration Skill

Find design inspiration from millions of curated website screenshots. Search by semantic description, color palette, font pairings, or source domain.

## When to Use

Use this skill when you need to:
- Find visual design references for a project
- Search for designs matching a specific aesthetic or style
- Discover color palettes and typography combinations
- Browse designs from specific websites or domains
- Get inspiration for layouts and UI patterns

## Available MCP Tools

### search_design_inspiration

Search for design pins using semantic queries with optional filters.

**Parameters:**
- `query` (required): Semantic description of the design (e.g., "minimalist landing page", "dark mode dashboard", "elegant typography")
- `color` (optional): Filter by dominant hex color (e.g., "#ff0000")
- `font_ids` (optional): Filter by font pairings. Use font IDs from font_search
- `domain` (optional): Filter by source domain (e.g., "awwwards.com")
- `limit` (optional): Maximum results to return (default: 5)

**Example usage:**
```
Search for "clean SaaS pricing page" with blue accent colors
Search for dark mode dashboard designs
Find minimalist portfolio sites
```

### get_pin_details

Retrieve detailed information about a specific pin including colors, fonts, and layout analysis.

**Parameters:**
- `pin_id` (required): The unique numerical ID of the pin
- `include_image` (optional): Include base64-encoded preview image

**Returns:**
- Color palette with hex values and usage frequencies
- Font families and their usage
- Layout analysis and design tokens
- Source URL and metadata

### display_pin

Display a pin as a visual card for immediate preview.

**Parameters:**
- `pin_id` (required): The ID of the pin to display

## Step-by-Step Workflow

### 1. Search for Inspiration

Start with a semantic search query describing the design style you're looking for:

```
Use search_design_inspiration with query "modern e-commerce product page"
```

### 2. Refine with Filters

Narrow results using color or font filters:

```
Use search_design_inspiration with:
- query: "modern e-commerce product page"
- color: "#2563eb" (blue accent)
- limit: 10
```

### 3. Explore Specific Pins

Get detailed information about interesting results:

```
Use get_pin_details with pin_id "12345"
```

### 4. Visual Preview

Display pins directly in the conversation:

```
Use display_pin with pin_id "12345"
```

## Tips for Effective Searches

- **Be descriptive**: "minimalist SaaS dashboard with sidebar navigation" works better than "dashboard"
- **Combine filters**: Use color + domain or fonts + query for precise matching
- **Iterate**: Start broad, then refine based on results
- **Explore domains**: Search designs from award-winning sites like awwwards.com or dribbble.com
