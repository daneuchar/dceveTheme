# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Theme Overview

This is **Horizon**, a Shopify theme (version 2.0.0) by Shopify. It follows the Shopify 2.0 theme architecture with JSON templates and modular sections/blocks.

## Architecture

### Core Directory Structure

- **`layout/`** - Theme wrapper templates
  - `theme.liquid` - Main layout file with `<head>` and `<body>` structure
  - `password.liquid` - Password-protected store layout

- **`templates/`** - JSON template files that define page structures
  - Composed of sections references (e.g., `product.json`, `collection.json`, `index.json`)
  - Use JSON format to assemble sections and configure their blocks

- **`sections/`** - Reusable theme sections
  - `section.liquid` & `_blocks.liquid` - Base section wrappers supporting `@theme` and `@app` block types
  - Major sections: `header.liquid`, `footer.liquid`, `product-list.liquid`, `hero.liquid`, `media-with-content.liquid`
  - Section groups: `header-group.json`, `footer-group.json`

- **`blocks/`** - Smaller reusable components used within sections
  - Prefixed with `_` for internal blocks (e.g., `_product-card.liquid`, `_divider.liquid`)
  - Public blocks: `button.liquid`, `video.liquid`, `menu.liquid`, etc.

- **`snippets/`** - Utility templates and smaller components
  - Core rendering: `section.liquid`, `background-media.liquid`, `border-override.liquid`
  - Components: `cart-drawer.liquid`, `product-card.liquid`, `header-drawer.liquid`, `icon.liquid`
  - ~100 snippet files for granular functionality

- **`assets/`** - Static assets (59 JS files, 3 CSS files)
  - `base.css` - Main stylesheet (~98KB)
  - `component.js` - Base Component class extending DeclarativeShadowElement for web components
  - `critical.js` - Render-blocking utilities (DeclarativeShadowElement, OverflowList, ResizeNotifier)
  - `events.js` - ThemeEvents namespace for custom events
  - Feature-specific JS: `cart-*.js`, `header-*.js`, `product-*.js`, `facets.js`, etc.

- **`config/`** - Theme configuration
  - `settings_schema.json` - Theme customizer settings definition
  - `settings_data.json` - Theme setting values
  - `markets.json` - Market configuration

- **`locales/`** - Internationalization files
  - Translation JSON files for 40+ languages
  - Schema translations (`.schema.json`) for theme editor

### Key Patterns

#### Component Architecture
- **Web Components**: Uses custom elements extending `Component` base class (from `component.js`)
- **Refs System**: Components use `ref` attributes to reference child elements, automatically collected in `this.refs`
- **Declarative Shadow DOM**: Critical components use shadow DOM for encapsulation
- **Event-Driven**: Custom theme events in `ThemeEvents` namespace (variant:selected, cart:update, etc.)

#### Section Rendering
1. Sections use `{% render 'section', section: section, children: children %}` pattern
2. Blocks are captured via `{% content_for 'blocks' %}` and passed as children
3. Sections support nested groups, layout configuration (flex direction, alignment, gaps)
4. Settings are defined in `{% schema %}` blocks as JSON

#### Liquid Patterns
- **Documentation**: Uses `{%- doc -%}` comments to document snippet parameters
- **Closest Context**: Uses `{{ closest.product }}` to access nearest product in template hierarchy
- **Render Pattern**: Extensive use of `{% render 'snippet-name', param: value %}`
- **Style Injection**: Inline styles rendered via snippets like `border-override.liquid`, `spacing-style.liquid`, `layout-panel-style.liquid`

#### Styling System
- **Color Schemes**: Defined via `settings_schema.json` and rendered in `color-schemes.liquid`
- **CSS Variables**: Heavy use of custom properties (e.g., `var(--font-primary--family)`, `var(--color-foreground)`)
- **Utility Classes**: Layout classes like `layout-panel-flex`, `spacing-style`, `border-style`
- **Component Styling**: Some components include `{% stylesheet %}` blocks for scoped CSS

## Development Workflow

### Working with Templates
- JSON templates in `templates/` reference sections by type (e.g., `"type": "product-information"`)
- Sections are configured with settings and blocks in the JSON structure
- Template inheritance: some templates have variants (e.g., `page.json`, `page.contact.json`)

### Working with Sections
- Section files contain Liquid markup + `{% schema %}` JSON block
- Schema defines settings, blocks, and presets
- Sections can be static or dynamic in the theme editor
- Use `section.settings.*` to access configured values

### Working with Blocks
- Blocks in `blocks/` directory are referenced by type (e.g., `"type": "button"` or `"type": "_product-card"`)
- Internal blocks (prefixed `_`) vs. theme blocks (no prefix)
- Blocks can nest other blocks via the `blocks` property

### Working with JavaScript
- Components extend the `Component` class from `component.js`
- Use `refs` to reference DOM elements instead of `querySelector`
- Dispatch custom events via `ThemeEvents` constants
- Critical JS (needed for initial render) goes in `critical.js`
- Feature JS is loaded asynchronously

### Theme Customization
- Global settings: modify `config/settings_schema.json`
- Theme editor: settings appear in Shopify admin
- Color schemes: configured in settings, applied via `color-{{ section.settings.color_scheme }}` classes
- Fonts: defined in `snippets/fonts.liquid`

## Important Conventions

### File Naming
- Internal blocks/snippets: prefix with `_` (e.g., `_product-card.liquid`)
- Public blocks: no prefix (e.g., `button.liquid`)
- Components: kebab-case matching custom element names (e.g., `cart-drawer.js` for `<cart-drawer>`)

### Settings Access
- Section settings: `section.settings.setting_id`
- Block settings: `block.settings.setting_id`
- Global settings: `settings.setting_id`

### Translation Keys
- Format: `t:names.section`, `t:settings.alignment`, `t:content.layout`
- Defined in `locales/*.json` files
- Schema translations in `locales/*.schema.json`

### Responsive Design
- Mobile-specific settings often include `_mobile` suffix
- Classes like `mobile-column` for responsive behavior
- CSS variables for breakpoint-based values

## Shopify Theme Development

This theme uses **Shopify CLI** for development. While this repository doesn't include package.json, typical Shopify theme development commands are:

```bash
# Development server with hot reload
shopify theme dev

# Push theme to Shopify store
shopify theme push

# Pull theme from Shopify store
shopify theme pull

# Check theme for issues
shopify theme check
```

## Testing & Validation

- Use Shopify Theme Check to validate Liquid syntax and best practices
- Test in Shopify theme editor (Design mode) for visual preview
- Verify responsive behavior across mobile/desktop breakpoints
- Test accessibility with keyboard navigation and screen readers
