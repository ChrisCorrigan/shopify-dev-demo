# Shopify Dawn-Performance Demo Store

This repository serves as a **proof-of-concept** for advanced Shopify Online Store 2.0 customization using the Dawn theme, and a portfolio for my work (Chris Corrigan) with ecomific.com for Shopify clients. 

It demonstrates: 

- how to add a bespoke hero section with a looping video background, dynamic font selection, and color controls—all managed via the Shopify Theme Editor. 

More to be added over time.

---

## 🚀 Introduction

The **Dawn-Performance** theme is a duplicate of Shopify’s default Dawn. This demo adds a custom **Video Hero** section to showcase:

- **Looping background video** with fallback image for mobile devices.
- **Section-level font picker** for the hero heading—leveraging Shopify’s built-in `font_picker` setting and `font_face` helper.
- **Color picker** to control the hero heading text color.
- **CSS component architecture**: styles scoped to `assets/component-video-hero.css` and loaded via the section.
- **Optimized asset delivery**: using Shopify’s `video_tag`, `file_url`, and CDN filters.

Each customization highlights best practices for Online Store 2.0 development, theme-check compliance, and version control integration.

---

## 🎨 Customizations

### 1. Video Hero Section (`sections/video-hero.liquid`)

- **Schema settings**: `hero_video` (video picker), `fallback` (image\_picker), `heading` (text), `heading_font` (font\_picker), `heading_color` (color).
- **Liquid logic**:
  - `video_tag` for autoplay, loop, muted video with `poster` fallback.
  - Inline `<style>` injection for `@font-face` and CSS overrides.
  - Conditional rendering based on `heading` presence.

### 2. Component CSS (`assets/component-video-hero.css`)

- Scoped styles for `.video-hero`, `.video-hero__video`, and `.video-hero__heading`.
- Responsive height caps (`max-height: 60vh` / `40vh`).
- Fluid font sizing using `clamp()`.
- CSS variables removed in favor of inline `<style>` overrides to avoid quoting issues.

### 3. Theme Integration

- Connected to GitHub for versioned theme code.
- Local development via Shopify CLI (`shopify theme dev`) or Dawn’s Vite pipeline (`npm run dev`).
- Manual sync commands provided for Windows and macOS.

---

## 🔧 Setup & Usage

### Prerequisites

- Node.js (16+)
- Shopify CLI v3
- Git & GitHub account

### Clone & Install

```bash
git clone https://github.com/<your-user>/shopify-dawn-performance.git
cd shopify-dawn-performance
npm install      # Dawn’s build dependencies
```

### Local Development

- **Hot-reload** (Shopify CLI):
  ```bash
  shopify theme dev --store <your-store>.myshopify.com
  ```
- **Vite & Bundling** (Dawn build):
  ```bash
  npm run dev
  ```

### Pushing Changes

- **Sync to Shopify**:
  ```bash
  shopify theme push --store <your-store>.myshopify.com --theme <theme-id>
  ```
- **Commit & Push to GitHub**:
  ```bash
  git add .
  git commit -m "feat: update video hero customization"
  git push origin main
  ```

---

## 📂 File Structure

```
├─ sections/
│  └─ video-hero.liquid       # Custom hero section schema & markup
├─ assets/
│  └─ component-video-hero.css # Styles for the video-hero section
├─ config/
│  └─ settings_schema.json    # Theme settings including typography pickers
├─ layout/
│  └─ theme.liquid            # Includes global CSS/JS and section load tags
└─ README.md                  # This documentation
```

---

## 🤝 Contributing

This repo is a personal demo; contributions are not expected. To adapt these patterns:

1. Duplicate the Video Hero code in your own Dawn-based theme.
2. Customize schema settings and CSS as needed.
3. Follow Shopify Theme Check and Git best practices.

---

## 📜 License

This project is released under the MIT License.

