# Image Assets — Shirey CPA Website

## Required Images

### scott-headshot.jpg
- **Used on:** Home page (bio teaser section), About page (hero)
- **Format:** JPEG, optimized for web
- **Recommended size:** At least 400x400px (displayed at 200x200 on desktop, 180x180 on About hero)
- **Crop:** The CSS applies `border-radius: 50%` for a circular crop — the source image should work well as a circle (head centered, some space around)
- **Where it goes in the code:**
  - `index.html`: Replace the `<div class="photo-placeholder">` in the bio-teaser section with `<img src="/images/scott-headshot.jpg" alt="Scott Shirey, CPA">`
  - `about.html`: Replace the `<div class="photo-placeholder">` in the about-hero section with `<img src="/images/scott-headshot.jpg" alt="Scott Shirey, CPA">`

### Optional: Hero Background Image
- **Used on:** Home page hero section (currently using a CSS gradient)
- **Format:** JPEG, optimized for web
- **Recommended size:** At least 1920x1080px
- **Subject:** Colorado high country landscape — warm tones, golden hour, mountain vistas
- **To implement:** In `css/styles.css`, update the `.hero` background property:
  ```css
  .hero {
      background: linear-gradient(rgba(44, 68, 85, 0.75), rgba(61, 90, 110, 0.8)),
                  url('/images/hero-mountain.jpg') center/cover no-repeat;
  }
  ```
  The overlay preserves text legibility while showing the landscape.

### Optional: QuickBooks ProAdvisor Badge
- **Used on:** Home page social proof strip
- **Format:** PNG with transparency
- **Size:** Badge as provided by Intuit (typically ~200px wide)
- **To implement:** Add an `<img>` tag in the trust-signals div on index.html

## Image Optimization Notes
- Run all images through an optimizer before deploying (TinyPNG, Squoosh, or similar)
- Target file sizes: headshot under 100KB, hero background under 300KB
- Use JPEG for photos, PNG for badges/logos with transparency
