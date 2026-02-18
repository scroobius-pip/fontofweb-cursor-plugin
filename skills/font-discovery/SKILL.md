---
name: font-discovery
description: Discover and research fonts used across the web. Search font families and see usage examples.
---

# Font Discovery Skill

Discover and research fonts used across the web. Search font families by name and explore real-world usage examples from saved designs.

## When to Use

Use this skill when you need to:
- Find a specific font by name
- Research similar fonts to a known typeface
- Discover fonts used on popular websites
- Find font pairing suggestions
- Get font IDs for use in design inspiration searches

## Available MCP Tools

### font_search

Search for font families by name. Returns the top 5 most similar font families with their system IDs.

**Parameters:**
- `query` (required): The name of the font family to search for (e.g., "Roboto", "Inter", "Playfair Display")

**Returns:**
- Font family names
- Unique font IDs (required for filtering design searches)
- Similarity scores

**Example usage:**
```
Search for "Inter" to find the Inter font family
Search for "Playfair" to discover Playfair Display and similar serif fonts
Search for "system" to find system font stacks
```

## Step-by-Step Workflow

### 1. Search for a Font

Search by font name (partial names work):

```
Use font_search with query "Inter"
```

### 2. Get Font IDs for Design Search

Use the returned font IDs to find designs using those fonts:

```
1. Use font_search with query "Inter" → returns font_id "inter-123"
2. Use search_design_inspiration with:
   - query: "clean typography"
   - font_ids: ["inter-123"]
```

### 3. Discover Font Pairings

Search for multiple fonts to find designs with specific pairings:

```
1. Use font_search for "Inter" → font_id "inter-123"
2. Use font_search for "Poppins" → font_id "poppins-456"
3. Use search_design_inspiration with:
   - query: "modern website"
   - font_ids: ["inter-123", "poppins-456"]
```

## Common Font Searches

| Query | Purpose |
|-------|---------|
| `Inter` | Popular sans-serif for UI |
| `Roboto` | Google's material design font |
| `Playfair Display` | Elegant serif for headings |
| `Poppins` | Geometric sans-serif |
| `Open Sans` | Humanist sans-serif |
| `Montserrat` | Versatile display font |
| `Lato` | Warm sans-serif |
| `Source Sans` | Adobe's open source font |

## Tips for Font Discovery

- **Partial names work**: "Play" will find "Playfair Display"
- **Case insensitive**: "inter" and "Inter" return the same results
- **Use IDs for filtering**: Font IDs are required for design inspiration searches
- **Explore alternatives**: The search returns similar fonts, useful for finding alternatives
