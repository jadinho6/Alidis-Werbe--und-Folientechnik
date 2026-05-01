# CLAUDE.md – Alidis Werbe- & Folientechnik Website

## Project Overview

**Client:** Alidis Werbe- & Folientechnik  
**Location:** Bahnhofstrasse 30, 5615 Fahrwangen, Kanton Aargau, Schweiz  
**Contact:** +41 78 313 44 11 | info@alidis.ch  
**Industry:** Fahrzeugfolierung, Werbetechnik, Folientechnik  
**Target audience:** Privatpersonen und Gewerbebetriebe in der Region Aargau/Schweiz  
**Language:** Deutsch (Schweizer Kontext, kein DSGVO – DSG-konform)

---

## Tech Stack

- **Framework:** Plain HTML5 / CSS3 / Vanilla JavaScript (no build tools, no frameworks)
- **Structure:** Multi-page website (index.html + separate pages or single-page with anchor sections)
- **Fonts:** Google Fonts (loaded in `<head>`)
- **Deployment:** GitHub → Vercel
- **No backend** – contact form via Formspree or static mailto fallback (client to confirm)
- **No CMS** – static files only

### File Structure
```
alidis-website/
├── index.html
├── css/
│   └── styles.css
├── js/
│   └── main.js
├── images/
│   └── logo.svg (or logo.png – to be provided by client)
└── CLAUDE.md
```

---

## Brand Identity

### Logo
- **Mark:** A geometric icon – two nested/mirrored "D" shapes forming an abstract monogram. Clean, modern, architectural.
- **Wordmark:** "ALIDIS" in bold, heavy sans-serif uppercase
- **Tagline:** "WERBE- & FOLIENTECHNIK" in lighter weight, spaced uppercase
- **Logo usage:** Always use the SVG version when available. The logo mark alone can be used as a favicon or standalone decorative element.
- **Logo file:** `images/logo.svg` – recreate as inline SVG if no file is provided (see SVG spec below)

#### Logo SVG Spec (approximate, for recreation)
The mark consists of two concentric "D" outlines (like a bold italic D with a cutout inner D), forming an elegant monogram. Stroke-based, monochrome. Should work on both dark and light backgrounds.

### Color Palette

| Role | Name | Hex | Usage |
|------|------|-----|-------|
| Primary accent | Alidis Red | `#E8341A` | CTAs, highlights, headings accent, section markers |
| Background dark | Carbon Black | `#0D0D0D` | Hero, footer, dark sections |
| Background mid | Dark Charcoal | `#1A1A1A` | Cards, nav, alternating sections |
| Background light | Steel Gray | `#2B2B2B` | Subtle section contrast |
| Text primary | Pure White | `#FFFFFF` | All body text on dark backgrounds |
| Text secondary | Warm Gray | `#B0B0B0` | Subtitles, meta text, captions |
| Metallic accent | Silver Steel | `#C0C0C0` or `#A8A8A8` | Borders, icon strokes, decorative lines |
| Nav/UI accent | Deep Navy | `#0A1628` | Can be used for overlays or dark card variants |

**Rule:** Never use a white or light background as the main site background. The entire site lives in the dark palette. Light text on dark backgrounds throughout.

### Typography

```
Display / Hero headings:  "Barlow Condensed" – weight 700, 800 (uppercase, wide tracking)
Section headings:          "Barlow" – weight 700
Body text:                 "Barlow" – weight 400, 300
Accent / Labels:           "Barlow Condensed" – weight 600, uppercase, letter-spacing: 0.15em
```

Google Fonts import:
```html
<link rel="preconnect" href="https://fonts.googleapis.com">
<link href="https://fonts.googleapis.com/css2?family=Barlow:wght@300;400;600;700&family=Barlow+Condensed:wght@600;700;800&display=swap" rel="stylesheet">
```

**Typography rules:**
- Hero headline: Barlow Condensed 800, ~80–100px, uppercase, tight tracking
- Section titles: Barlow Condensed 700, ~42–52px, uppercase
- Body text: Barlow 400, 17–18px, line-height 1.7
- Buttons/labels: Barlow Condensed 700, uppercase, letter-spacing 0.12em
- NEVER use Inter, Roboto, or system fonts

---

## Design Direction

### Aesthetic Concept: "Industrial Precision"
The site should feel like a high-end automotive/industrial brand – dark, confident, technical. Think less "IT agency", more "premium automotive workshop meets modern design studio". The vehicle wrap industry is visual and tactile – the website should feel like it has texture and weight.

### Visual Language
- **Angular geometry:** Diagonal cuts (clip-path: polygon) on section transitions instead of curved waves
- **Speed lines:** Thin horizontal or diagonal lines as decorative elements, suggesting motion
- **Bold contrast:** Large type against dark backgrounds – high visual impact
- **Red as a weapon:** Use `#E8341A` sparingly but boldly – as underlines, left borders on cards, button backgrounds, hover states
- **Metallic touches:** Silver/gray borders and dividers referencing the brushed-steel business card aesthetic

### Section Transitions
Use diagonal clip-path cuts between sections to create a dynamic, forward-leaning feel:
```css
.section-diagonal-bottom {
  clip-path: polygon(0 0, 100% 0, 100% 90%, 0 100%);
}
.section-diagonal-top {
  clip-path: polygon(0 5%, 100% 0, 100% 100%, 0 100%);
  margin-top: -3vw;
}
```

---

## Page Structure & Content

### 1. Navigation (sticky)
- Background: `#0D0D0D` with subtle bottom border in `#E8341A` (2px)
- Logo left (mark + wordmark)
- Nav links right: Dienstleistungen | Galerie | Über uns | Kontakt
- CTA Button: "Offerte anfragen" – red background, white text
- Mobile: hamburger menu, full-screen overlay

### 2. Hero Section
- **Full viewport height** (100vh)
- **Background:** Dark gradient + subtle diagonal red accent line OR a placeholder for a vehicle wrap photo (with dark overlay)
- **Content:**
  ```
  [Small label, red] PROFESSIONELLE FOLIENTECHNIK IN DER SCHWEIZ
  [H1 giant] DEIN FAHRZEUG.
            DEINE MARKE.
            UNSER HANDWERK.
  [Subline] Von der Fahrzeugfolierung bis zur Schilderbeschriftung –
            Alidis macht Ihre Marke sichtbar.
  [CTA] Jetzt Offerte anfragen  →
  [Secondary CTA] Unsere Leistungen ↓
  ```
- **Animated entrance:** Headline slides up on load with staggered delay
- **Bottom of hero:** Diagonal cut into next section

### 3. Services Section ("Unsere Leistungen")
- Dark background `#1A1A1A`
- Section label: "WAS WIR ANBIETEN" (red, small caps, letter-spaced)
- Section title: "Leistungen, die überzeugen"
- **Layout:** 2×4 or 4×2 grid of service cards

**Service Cards – 8 items:**
| # | Service | Icon suggestion |
|---|---------|----------------|
| 1 | Werbetechnik | Megaphone / billboard |
| 2 | Fahrzeugfolierung | Car with wrap layers |
| 3 | Scheibentönung | Window tint film |
| 4 | Fahrzeugbeschriftung | Vehicle with text |
| 5 | Lackschutzfolie | Shield / protective layer |
| 6 | Fensterfolie | Window frame |
| 7 | Schilderbeschriftung | Sign / signage |
| 8 | Möbelfolierung | Furniture surface |

**Card design:**
- Background: `#2B2B2B`
- Left border: 3px solid `#E8341A`
- Icon: SVG line icon, color `#E8341A`
- Title: Barlow Condensed 700, white, uppercase
- Short description (1–2 sentences): Barlow 400, warm gray
- Hover: card lifts slightly (translateY -4px), border glow

### 4. Why Alidis ("Warum Alidis?")
- Background: `#0D0D0D`
- 3 or 4 value propositions in a horizontal row with large icons:
  - **Qualität** – Premium Materialien, langlebige Ergebnisse
  - **Präzision** – Saubere Verarbeitung, professionelle Montage
  - **Erfahrung** – Jahrelange Expertise in der Folientechnik
  - **Regional** – Ihr Spezialist im Kanton Aargau
- Style: Large number or icon top, bold title, short text below
- Divider elements: thin red horizontal lines

### 5. Gallery Section ("Unsere Arbeiten")
- Background: `#1A1A1A`
- Label: "GALERIE"
- Title: "Sehen Sie unsere Arbeit"
- **Layout:** Masonry or CSS grid, image tiles
- Placeholder: 6–9 placeholder containers with dark gray + dashed border + icon
- Add: `<!-- Replace with actual project photos from client -->`
- Lightbox: on click, show full image (pure CSS or minimal JS)
- Note: Client must supply photos of actual work (vehicle wraps, signage projects, etc.)

### 6. Contact Section ("Kontakt")
- Full-width, dark background `#0D0D0D`
- Left column: Contact info
  ```
  📞 +41 78 313 44 11
  ✉️ info@alidis.ch
  📍 Bahnhofstrasse 30, 5615 Fahrwangen
  ```
- Right column: Contact form fields:
  - Name (required)
  - E-Mail (required)
  - Telefon
  - Nachricht (textarea, required)
  - [Submit button] "Anfrage senden"
- Form styling: dark input fields, red focus border, red submit button
- Static form (no backend yet) – use `action="mailto:info@alidis.ch"` as fallback, note for future Resend integration
- Below form: embedded Google Maps iframe showing Fahrwangen location

### 7. Footer
- Background: `#0D0D0D`, top border `#E8341A` (1px)
- Logo + tagline left
- Links: Impressum | Datenschutzerklärung | AGB
- Copyright: `© 2025 Alidis Werbe- & Folientechnik. Alle Rechte vorbehalten.`
- Small text: Bahnhofstrasse 30, 5615 Fahrwangen

---

## Animations & Interactions

```css
/* Scroll-triggered fade-in for all major elements */
.reveal {
  opacity: 0;
  transform: translateY(30px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}
.reveal.visible {
  opacity: 1;
  transform: translateY(0);
}
```

Use IntersectionObserver in `main.js` to add `.visible` class when elements enter viewport.

**Additional effects:**
- Hero headline: staggered word-by-word animation on load
- Service cards: hover lift + red border glow (`box-shadow: 0 0 0 1px #E8341A`)
- Navigation: background darkens on scroll (add `.scrolled` class to nav)
- CTA button: red background with subtle right-arrow animation on hover

---

## Responsive Breakpoints

```css
/* Mobile first */
/* Base: 0–767px (mobile) */
/* Tablet: 768px–1023px */
/* Desktop: 1024px+ */
/* Wide: 1400px+ */
```

- Mobile nav: hamburger → full-screen dark overlay menu
- Services grid: 1 col mobile → 2 col tablet → 4 col desktop
- Hero font size scales down gracefully
- Gallery: 1 col → 2 col → 3 col

---

## SEO & Legal (Swiss)

### Meta tags (in `<head>`)
```html
<meta name="description" content="Alidis Werbe- & Folientechnik – Professionelle Fahrzeugfolierung, Scheibentönung, Werbetechnik und Schilderbeschriftung in Fahrwangen, Kanton Aargau.">
<meta property="og:title" content="Alidis Werbe- & Folientechnik | Fahrwangen, Aargau">
<meta property="og:description" content="Ihr Spezialist für Fahrzeugfolierung, Lackschutzfolie, Fahrzeugbeschriftung und Werbetechnik in der Schweiz.">
<meta property="og:image" content="images/og-preview.jpg">
<link rel="canonical" href="https://www.alidis.ch/">
```

### LocalBusiness Schema (JSON-LD)
```json
{
  "@context": "https://schema.org",
  "@type": "LocalBusiness",
  "name": "Alidis Werbe- & Folientechnik",
  "address": {
    "@type": "PostalAddress",
    "streetAddress": "Bahnhofstrasse 30",
    "postalCode": "5615",
    "addressLocality": "Fahrwangen",
    "addressRegion": "AG",
    "addressCountry": "CH"
  },
  "telephone": "+41783134411",
  "email": "info@alidis.ch",
  "url": "https://www.alidis.ch",
  "areaServed": "Schweiz"
}
```

### Legal pages needed (separate files):
- `impressum.html`
- `datenschutz.html`
- Use DSG-konform language (not DSGVO). If hosted on Vercel: mention USA data transfer in Datenschutzerklärung.

---

## Important Constraints

1. **DO NOT use a white or light background** anywhere on the site. The entire aesthetic is dark.
2. **DO NOT use Inter, Roboto, or Arial** as fonts. Use Barlow / Barlow Condensed only.
3. **DO NOT add an "Über uns" section** with personal biographical text. If added, keep it to 2–3 lines max and focused on the business, not the person.
4. **DO NOT use stock illustration SVGs** (like undraw.co style). Use minimal line icons or geometric shapes only.
5. **The logo mark** (the geometric D-shape icon) must appear in the nav, hero, and footer at minimum.
6. **Image placeholders** must clearly be marked with comments for the client to replace with real photos.
7. **Form** is static for now – do not integrate any backend without explicit instruction.
8. **Language:** 100% German. No English phrases in content (English only in comments/code).

---

## Claude Code Session Rules

- Work on **one section at a time**, starting with: Nav → Hero → Services → Why Alidis → Gallery → Contact → Footer → Legal pages
- After each section: stop and wait for review
- Do NOT touch already-approved sections when working on a new one
- All files stay in this single project folder
- This CLAUDE.md is the single source of truth – consult it before making any decision
- If unsure about a design choice: default to **darker, bolder, more angular**
