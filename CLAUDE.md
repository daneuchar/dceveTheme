# Dceve Shopify Development Guide

This file provides comprehensive guidance to Claude Code (claude.ai/code) when working with this Shopify theme for **Dceve** - an art-focused apparel brand that connects artists with customers through themed, story-driven products.

---

## Project Overview

This project uses the **Horizon** Shopify theme (version 2.0.0) as its foundation. The theme follows Shopify 2.0 architecture with JSON templates and modular sections/blocks, customized for Dceve's unique brand and requirements.

---

# Part 1: Dceve Brand & Requirements

## Brand Identity

### Color Palette

| Color Name | Usage |
|------------|-------|
| **Purple Marine** | Primary accent color - CTAs, highlights, featured elements, active states |
| **Grey** | Secondary elements, borders, subtle backgrounds, disabled states |
| **Sea Salt** | Light backgrounds, cards, content areas, alternating sections |
| **White** | Primary background, clean spaces, text on dark backgrounds |
| **Humble Rust** | Warm accent, hover states, special highlights, notifications |
| **Black** | Primary text, headers, strong contrasts, footer background |

### Typography

| Font | Usage |
|------|-------|
| **Hepta Slab** | All headings (H1-H6), logo text, hero titles, promotional banners |
| **Lexend Tera** | Section titles, navigation labels, category names, button text |
| **Fira Sans** | Body content, descriptions, UI elements, form inputs, meta text |

---

## Site Architecture

### 1. Header

#### Navigation Structure

```
├── Logo → Home
├── Shop
│   ├── Themes (dropdown)
│   └── List by Artist
│       ├── Name
│       ├── Type
│       ├── Portfolio
│       └── Bio
├── Discover (dropdown)
├── About
│   ├── People
│   ├── Why Dceve
│   ├── Journey
│   └── The Vision
└── Links (utility navigation)
```

#### Icon Bar (Right Side)

```
├── Search
│   └── Filters
│       ├── By Collection
│       ├── By Type
│       ├── By Size
│       ├── By Artist
│       ├── By Price
│       └── By Reviews
├── Account
│   ├── Login
│   │   ├── OTP
│   │   ├── Social Media
│   │   └── Register via Email
│   └── Forgot Password
└── Cart
```

---

### 2. Themes Hub

#### Filter Options
- Zodiac
- Animals
- Mandalas
- Humanoid/AI
- New
- Trending
- Staff Picks

#### Sort Options
- Newest First
- Price: Low to High
- Price: High to Low
- Popularity
- Rating

#### Theme Display Components

```
Themes Grid
├── Theme Item Visual (Card)
└── Theme Detail Page
    ├── Theme Story
    ├── Product Grid
    ├── Filter Inside Theme
    ├── Artists in Theme
    └── Related Themes
```

---

### 3. Artists Section

#### Artists Hub Structure

```
Artists Hub
├── Hero/Copy Section
├── Featured Artists (Carousel)
└── Artist Directory
```

#### Artist Profile Page

```
Artist Profile
├── Hero Section
├── About
├── Artist Collections
└── Why Join? CTA
```

#### Become an Artist Portal

```
Become an Artist
├── Process Explanation
├── Submission Form
└── FAQ
```

#### Artist Dashboard (Phase 2)

```
Artist Dashboard
├── My Designs
├── Status Tracking
├── Sales Analytics
├── Payouts
└── Notifications
```

---

### 4. Discover Section

#### Discover Hub

```
Discover Hub
├── Quick Entry Points
├── Theme Stories
└── Behind the Art
```

#### Drops Section

```
Drops
├── Hero Section
└── Questions/FAQ
```


#### Stories Section

```
Stories
├── Story Detail Page
├── Drips (Content Drops)
└── Onsite Nav Story
```

#### About Subsection

```
About
├── Quality & Fabric
├── Care Instructions
├── Size Guide
├── Help Center
└── Contact
```

#### Account Management

```
Account
├── Login/Register
└── User Dashboard
    ├── Profile
    ├── Orders
    ├── Addresses
    ├── Wishlist
    ├── Saved Themes
    ├── Quiz Results
    ├── Referrals
    └── Artist Dashboard (if artist)
```

---

### 5. Cart & Checkout

```
Cart & Checkout
├── Cart
│   ├── Items List
│   ├── Bundle Suggestions
│   └── Free Shipping Threshold
└── Checkout
    ├── Payment Gateway (Razorpay)
    └── Order Confirmation
```

---

### 6. Footer

```
Footer
├── Brand
│   ├── Code: You Story
│   └── Vision & Philosophy
├── Support
│   ├── Help/FAQ
│   ├── Size Guide
│   ├── Care Instructions
│   ├── Shipping & Returns
│   └── Contact
├── Artists
│   ├── Become an Artist
│   ├── Artist Guidelines
│   └── Artist FAQ
├── Legal
│   ├── Privacy Policy
│   ├── Terms
│   ├── Refund Policy
│   ├── Shipping Policy
│   └── Returns and Exchange
└── Community
    ├── Social Links
    ├── Email Signup
    └── Visual Identity
```

---

### 7. Home Page

```
Home Page
├── Hero/Story Items
│   ├── CTA: Shop Now
│   └── CTA: Decode Your Code (Quiz)
├── Quick Categories
│   ├── New Drops
│   ├── Bestsellers
│   ├── Mandala
│   ├── Rebel
│   ├── GOAT
│   └── Sneak Peek
├── Featured Themes
├── Shop by Category
│   ├── T-Shirts
│   ├── Hoodies
│   ├── Bundles/Combos
│   └── Sale
├── Artist Spotlight
├── Featured Theme of Month
└── UGC + Social Proof
```

---

### 8. Shop Hub

```
Shop Hub
├── Filters Panel
│   ├── Category
│   ├── Size
│   ├── Colour
│   ├── Price
│   └── Theme Tags
├── Sorting Tools
├── Featured Listings
├── Product Grid
└── Collections
    ├── T-Shirts
    ├── Hoodies
    ├── Bundles
    ├── Sale
    └── New Arrivals
```

---

### 9. Product Detail Page (PDP)

```
Product Detail Page
├── Above the Fold
│   ├── Gallery (Multiple Images)
│   ├── Product Name
│   ├── Price
│   ├── Size Selector
│   ├── Colour Selector
│   ├── Add to Cart / Buy Now
│   ├── Shipping Promise
│   └── Story Block
├── Product Details
│   ├── GSM
│   ├── Printing Method
│   ├── Description
│   └── Availability/In Stock
├── Size & Fit Guide
├── Care Instructions
├── Theme Context
├── Artist Context
├── Related Products
└── Reviews
```

---

## Dceve-Specific Technical Requirements

### Shopify Configuration

1. Use **Shopify 2.0** theme architecture with JSON templates
2. Implement **metafields** for:
   - Theme associations
   - Artist profiles
   - Story content
   - Product attributes (GSM, printing method)
3. Create **metaobjects** for:
   - Themes
   - Artists
   - Stories

### Custom Sections to Develop

| Section | Description |
|---------|-------------|
| Theme Hub | Custom collection template with advanced filtering |
| Artist Profiles | Custom page template with artist metaobjects |
| Bundle Builder | Dynamic bundle creation with pricing |
| Artist Dashboard | Customer account extension (Phase 2) |

### Required Integrations

| Integration | Purpose |
|-------------|---------|
| Razorpay | Payment gateway |
| Klaviyo/Mailchimp | Email marketing & signup |
| Judge.me/Yotpo | Reviews |
| Social Media | Instagram feed, sharing |

### Performance Requirements

- Lazy loading for images
- Optimized theme assets
- Mobile-first responsive design
- Core Web Vitals compliance
- < 3s page load time

---

## Design Guidelines

### Visual Style

- Clean, gallery-like aesthetic
- Generous white space
- Art-forward imagery
- Subtle animations on hover
- Card-based layouts for products and themes

### Component Specifications

#### Buttons

```css
/* Primary Button */
.btn-primary {
  background: var(--purple-marine);
  color: var(--white);
  font-family: 'Lexend Tera', sans-serif;
  border-radius: 4px;
  padding: 12px 24px;
}

.btn-primary:hover {
  background: var(--humble-rust);
}

/* Secondary Button */
.btn-secondary {
  background: transparent;
  border: 1px solid var(--grey);
  color: var(--black);
  font-family: 'Lexend Tera', sans-serif;
}
```

#### Cards

```css
.card {
  background: var(--sea-salt);
  border: 1px solid var(--grey);
  border-radius: 8px;
  box-shadow: 0 2px 4px rgba(0,0,0,0.05);
}
```

#### Navigation

```css
.nav-link {
  font-family: 'Lexend Tera', sans-serif;
  color: var(--black);
}

.nav-link:hover {
  color: var(--humble-rust);
  text-decoration: underline;
}

.nav-link.active {
  color: var(--purple-marine);
}
```

---

## Development Phases

### Phase 1 (MVP)

- [ ] Home Page
- [ ] Shop Hub + Product Grid
- [ ] Product Detail Page
- [ ] Cart & Checkout
- [ ] Basic Theme filtering
- [ ] Header & Footer

### Phase 2

- [ ] Themes Hub (full functionality)
- [ ] Artist Profiles
- [ ] Discover section
- [ ] Quiz feature
- [ ] User Dashboard enhancements

### Phase 3

- [ ] Artist Dashboard
- [ ] Advanced filtering
- [ ] Bundle system
- [ ] Referral program

---

## Content Requirements

### Required Content Before Development

| Content Type | Description |
|--------------|-------------|
| Brand Copy | Brand story, philosophy, vision statements |
| Theme Content | Descriptions, stories, artwork for each theme |
| Artist Content | Bios, portfolios, profile images |
| Product Info | Size guide measurements, care instructions |
| Support Content | FAQ, shipping info, return policy |
| Legal Pages | Privacy policy, terms, refund policy |
| Media Assets | Product photography, theme artwork, lifestyle images |

---

## Success Metrics

Track the following KPIs:

- Conversion rate by theme
- Artist page engagement
- Average order value (AOV)
- Bundle attachment rate
- Return customer rate
- Page load times
- Mobile conversion rate

---

# Part 2: Horizon Theme Technical Documentation

## Theme Architecture

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

This theme uses **Shopify CLI** for development. Typical Shopify theme development commands:

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

---

## File Structure Reference

```
theme/
├── assets/
│   ├── base.css
│   ├── component-*.css
│   ├── component.js
│   ├── critical.js
│   ├── events.js
│   └── [feature-specific].js
├── blocks/
│   ├── _product-card.liquid
│   ├── _divider.liquid
│   ├── button.liquid
│   ├── video.liquid
│   └── menu.liquid
├── config/
│   ├── settings_schema.json
│   ├── settings_data.json
│   └── markets.json
├── layout/
│   ├── theme.liquid
│   └── password.liquid
├── locales/
│   ├── en.default.json
│   └── [language].schema.json
├── sections/
│   ├── header.liquid
│   ├── footer.liquid
│   ├── hero.liquid
│   ├── featured-themes.liquid (custom)
│   ├── artist-spotlight.liquid (custom)
│   ├── product-grid.liquid
│   └── section.liquid
├── snippets/
│   ├── product-card.liquid
│   ├── theme-card.liquid (custom)
│   ├── artist-card.liquid (custom)
│   ├── icon.liquid
│   ├── cart-drawer.liquid
│   └── section.liquid
└── templates/
    ├── index.json
    ├── product.json
    ├── collection.json
    ├── page.artist.json (custom)
    ├── page.theme.json (custom)
    └── ...
```

---

## Development Notes

1. **Mobile-First**: Design and develop for mobile first, then scale up
2. **Accessibility**: Ensure WCAG 2.1 AA compliance
3. **SEO**: Implement proper meta tags, schema markup, and semantic HTML
4. **Performance**: Optimize images, minimize CSS/JS, implement caching
5. **Testing**: Test across browsers (Chrome, Safari, Firefox, Edge) and devices
6. **Brand Consistency**: Always use Dceve's color palette and typography
7. **Component Reuse**: Leverage Horizon's existing components when possible, customize as needed
