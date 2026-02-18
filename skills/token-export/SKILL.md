---
name: token-export
description: Extract and export design tokens (colors, typography, spacing) from any website. Export in CSS, Tailwind v4, or DTCG format.
---

# Token Export Skill

Extract and export design tokens from any website. Get colors, typography, spacing, borders, and gradients in your preferred format.

## When to Use

Use this skill when you need to:
- Extract a website's color palette
- Get typography scales and font usage
- Export design tokens for a design system
- Convert colors between formats (hex, RGB, oklch)
- Analyze spacing and layout patterns from websites

## Available MCP Tools

### export_domain_tokens

Export design tokens from a specific domain. Analyzes multiple pins from the domain to extract consistent design patterns.

**Parameters:**
- `domain_host` (required): Domain to export tokens from (e.g., "stripe.com", "linear.app")
- `format` (optional): Export format - "css", "tailwind-v4", "dtcg", or "json" (default: "json")
- `pin_limit` (optional): Number of pins to analyze, max 200 (default: 10)

**Format Details:**
- `json`: Raw internal structure with full data
- `css`: Basic CSS custom properties
- `tailwind-v4`: Tailwind CSS v4 @theme block
- `dtcg`: Figma-compatible Design Token Community Group format

**Example usage:**
```
Export tokens from stripe.com in Tailwind v4 format
Export tokens from linear.app in CSS variables format
Get design tokens from vercel.com
```

### batch_color_operations

Perform batch operations on colors - convert formats, adjust values, calculate contrast.

**Parameters:**
- `operations` (required): Array of color operations

**Operation Types:**
- `hex2rgb`: Convert hex to RGB
- `hex2oklch`: Convert hex to oklch
- `rgb2hex`: Convert RGB to hex
- `lighten`: Lighten a color (amount: 0-100)
- `darken`: Darken a color (amount: 0-100)
- `saturate`: Increase saturation (amount: 0-100)
- `desaturate`: Decrease saturation (amount: 0-100)
- `grayscale`: Convert to grayscale
- `invert`: Invert a color
- `rotate`: Rotate hue (degrees: 0-360)
- `opacify`: Add opacity (amount: 0-1)
- `transparentize`: Remove opacity (amount: 0-1)
- `mix`: Mix two colors (ratio: 0-1)
- `luminance`: Get relative luminance
- `chroma`: Get chroma value
- `opacity`: Get opacity value
- `contrast`: WCAG contrast ratio between two colors
- `apcaContrast`: APCA contrast (more accurate for text)
- `readableColor`: Get readable text color for background
- `isValidColor`: Validate color string

**Example usage:**
```
Convert #ff0000 to RGB
Lighten #3b82f6 by 20%
Get contrast ratio between #ffffff and #3b82f6
```

## Step-by-Step Workflow

### 1. Export Tokens from a Website

```
Use export_domain_tokens with:
- domain_host: "stripe.com"
- format: "tailwind-v4"
```

### 2. Analyze the Results

Review the exported tokens:
- **Colors**: Primary, secondary, accent, neutral palettes
- **Typography**: Font families, sizes, weights, line heights
- **Spacing**: Margin and padding scales
- **Borders**: Width, style, radius, colors
- **Gradients**: CSS gradient definitions

### 3. Process Colors

Convert or adjust colors as needed:

```
Use batch_color_operations with:
- operations:
  - { type: "hex2oklch", color: "#3b82f6" }
  - { type: "darken", color: "#3b82f6", amount: 10 }
  - { type: "contrast", color: "#ffffff", color2: "#3b82f6" }
```

### 4. Validate Accessibility

Check color contrast for accessibility:

```
Use batch_color_operations with:
- operations:
  - { type: "apcaContrast", color: "#ffffff", color2: "#1f2937" }
  - { type: "readableColor", color: "#3b82f6" }
```

## Export Format Examples

### CSS Format
```css
:root {
  --color-primary: #3b82f6;
  --color-secondary: #8b5cf6;
  --font-family-heading: "Inter", sans-serif;
  --font-size-base: 16px;
}
```

### Tailwind v4 Format
```css
@theme {
  --color-primary: #3b82f6;
  --color-secondary: #8b5cf6;
  --font-family-heading: "Inter", sans-serif;
}
```

### DTCG Format
```json
{
  "colors": {
    "primary": {
      "$value": "#3b82f6",
      "$type": "color"
    }
  }
}
```

## Tips for Token Export

- **More pins = better accuracy**: Increase pin_limit for more consistent token extraction
- **Use DTCG for Figma**: The dtcg format imports directly into Figma plugins
- **Check contrast**: Always validate text colors for accessibility
- **Iterate on colors**: Use batch operations to create color variations
