# CLAUDE.md

This file provides guidance to Claude Code (claude.ai/code) when working with code in this repository.

## Project Overview

This is a professional website for Dr. Darrell S. Rigel, a world-renowned dermatologist and co-creator of the ABCDE melanoma detection method. The site is a single-page application built with vanilla HTML, CSS, and JavaScript - no build tools, no frameworks, no dependencies beyond CDN resources.

## Architecture

**Technology Stack:**
- Pure HTML5 with semantic markup
- CSS3 with modern features (Grid, Flexbox, custom properties)
- Vanilla JavaScript (ES6+)
- External CDN resources: Font Awesome icons, Google Fonts (Inter)

**File Structure:**
- `index.html` - Single-page website with all content sections
- `styles.css` - Complete styling including responsive design and animations
- `script.js` - Interactive functionality, animations, and navigation
- `images/` - Professional photos and logos
- `images/originals/` - Source images before optimization
- `notes.md` - Development notes and content planning

## Key Design Principles

**Cinematic/Immersive Design:**
The site uses a dark, modern aesthetic with:
- Full-viewport hero section with background image and gradient overlays
- Parallax scrolling effects for depth
- Intersection Observer API for scroll-triggered animations
- Fade-in and translateY animations on section reveals
- Grayscale-to-color transitions on image hovers (commented out but ready to enable)

**Performance Optimizations:**
- Debounced scroll event handlers to reduce CPU usage
- Intersection Observer for efficient element visibility detection
- Lazy loading support for images
- Minimal JavaScript footprint with no external libraries
- CSS transitions instead of JavaScript animations where possible

**Sections:**
1. Hero - Full-screen introduction with CTA buttons
2. About - Two-column layout with image and bio, animated statistics counter
3. Expertise - 3-column grid of expertise areas with icons
4. Consulting - Pharmaceutical consulting and business leadership info
5. Affiliations - Timeline-style layout alternating left/right
6. Photo Gallery - 3-column grid with hover captions
7. Achievements - Grid showcase of awards and honors
8. Contact - Professional contact information and links

## Development Workflow

**Local Development:**
1. Open `index.html` directly in a browser, or
2. Use a local server (e.g., `python -m http.server 8000` or VS Code Live Server)
3. No build process required

**Making Changes:**
- Content changes: Edit `index.html` directly
- Styling changes: Edit `styles.css`
- Interactive features: Edit `script.js`
- Images: Add to `images/` directory and reference in HTML

**Testing:**
- Test responsiveness at breakpoints: 768px (mobile), 1024px (tablet), 1200px+ (desktop)
- Verify animations trigger correctly on scroll
- Check mobile menu functionality (hamburger navigation)
- Test keyboard navigation (Escape closes mobile menu)
- Verify smooth scrolling between sections

## Code Patterns

**Animation Pattern:**
Elements start with `opacity: 0` and `transform: translateY(30px)` in CSS. The Intersection Observer adds a `.visible` class when elements enter viewport, triggering CSS transitions to `opacity: 1` and `transform: translateY(0)`.

**Statistics Counter:**
The about section includes animated counters (40+ years, 1000+ presentations, 305+ publications). The `animateValue()` function in script.js handles the counting animation using `requestAnimationFrame`. Counters trigger when the `.stats-container` becomes visible via Intersection Observer.

**Navigation:**
- Fixed navbar that becomes opaque on scroll
- Active section highlighting based on scroll position
- Smooth scrolling with offset for fixed header (80px)
- Mobile hamburger menu with animated bars
- Closes on link click, outside click, or Escape key

**Responsive Strategy:**
Mobile-first CSS with breakpoints at 768px and 1024px. Grid layouts collapse to single columns on mobile. The hamburger menu displays as a full-screen overlay on mobile devices.

## Content Guidelines

**Professional Tone:**
- Formal medical/academic language
- Emphasis on achievements, credentials, and expertise
- Current affiliations prominently featured (Cooper Clinic, UT Southwestern, NYU Langone, NY Yankees)

**Image Management:**
- Original images stored in `images/originals/`
- Optimized images in `images/` root
- Images should be web-optimized (compressed, appropriate dimensions)
- Naming convention: lowercase with hyphens (e.g., `dr-rigel-speaking.png`)

**SEO Considerations:**
- Semantic HTML structure throughout
- Descriptive alt text on all images
- Meta descriptions in head section
- Schema.org markup ready for implementation if needed

## Common Tasks

**Adding a New Section:**
1. Add section to `index.html` with appropriate semantic tags
2. Include navigation link in navbar
3. Add styling in `styles.css` following existing patterns
4. Add Intersection Observer logic in `script.js` if animations needed
5. Test smooth scrolling and active link highlighting

**Updating Statistics:**
Modify the `data-value` attributes on `.stat-number` elements in the About section. The JavaScript will automatically animate to the new values.

**Adding Gallery Images:**
1. Optimize image and add to `images/` directory
2. Add `.gallery-item` div in the Photo Gallery section
3. Include descriptive caption in `.gallery-caption`

**Modifying Colors/Theme:**
The site uses a dark theme with minimal color palette:
- Background: `#000` and `#0a0a0a` (near black)
- Text: White with varying opacity (0.7 to 1.0)
- Accents: White borders with low opacity
- Buttons: Glass-morphism effect with backdrop-filter

## Browser Compatibility

Target browsers: Chrome 60+, Firefox 60+, Safari 12+, Edge 79+. The site uses modern CSS and JavaScript features including:
- CSS Grid and Flexbox
- CSS custom properties (not currently used but supported)
- Intersection Observer API
- ES6+ JavaScript features
- backdrop-filter (for glass-morphism effects)

## Accessibility

- Semantic HTML structure throughout
- ARIA labels on interactive elements
- Keyboard navigation support
- Focus indicators for keyboard users (inherits browser defaults)
- Screen reader friendly navigation
- High contrast text (white on black)
- Responsive text sizing with `clamp()`

## Notes

- The site has no database or backend - all content is static
- No form submissions (contact is via external links and phone numbers)
- Stats counter animation has backup trigger via scroll listener if Intersection Observer doesn't fire
- Custom cursor effect is desktop-only (disabled on mobile via media query)
- Parallax effects are subtle to maintain performance and avoid motion sickness
- Loading screen displays briefly on page load for professional polish
