# Away Wireframing Style Guide

This document defines the strict visual guidelines and code patterns for the AWAY wireframe system, ensuring visual and structural consistency across all pages and Figma exports.

---

## 1. Color Palette (Strict Grayscale)
Always use CSS variables to reference the design system tokens:
- `--bg-color: #FFFFFF;` (Primary canvas background)
- `--text-color: #000000;` (Primary text and borders)
- `--secondary-color: #F0F0F0;` (Light gray for placeholder fills, alternate sections, and card hovers)
- `--border-color: #000000;` (Standard black outline border)

---

## 2. Typography & Hierarchy
- **Body & Controls Font**: `'Maison Neue Mono', monospace` (for specific data points or tags where monospacing is needed).
- **Headings Font**: `'Maison Neue', sans-serif` (for clear, readable, clean interfaces).
- **Spacing Guidelines**:
  ```css
  h1, h2, h3, h4, h5, h6 {
      font-family: var(--font-display);
      font-weight: 900;
      text-transform: uppercase;
      letter-spacing: -0.03em;
      margin-bottom: 1rem;
  }
  h1 { font-size: 4rem; line-height: 1; }
  h2 { font-size: 3rem; line-height: 1.1; }
  h3 { font-size: 2rem; line-height: 1.2; }
  ```

---

## 3. Horizontal Dividers & Sectioning
Horizontal divider lines must span the **full width of the screen** (edge-to-edge).
1. **Section Borders**:
   - The `<section>` elements must have a padding of `6rem 2rem` (or custom padding) and a default bottom border: `border-bottom: 1px solid var(--border-color);`.
   - **Crucial**: Never place `max-width` directly on the `<section>` tag itself as it will truncate the border. Instead, wrap the section's inner content in a wrapper div with `max-width: 1200px;` (or `800px;` for text pages) and `margin: 0 auto;`.
2. **Last Section & Footer Interaction**:
   - The last `<section>` before the footer MUST have `style="border-bottom: none;"` to prevent a double line with the footer's top border.
   - The `<footer>` element must have `border-top: 1px solid var(--border-color);` and `margin-top: 2rem;` to sit cleanly below the last section.
3. **Footer Grid**:
   - The footer grid holding the links and logo must NOT have a bottom border.

---

## 4. Image & Graphic Placeholders
All images, graphics, maps, or player components must use standard solid box placeholders:
- **Border**: `2px solid var(--border-color)`
- **Background**: `var(--secondary-color)`
- **Core indicator**: A centered monospace uppercase `"X"` with `opacity: 0.5`.
- **Constraint**: Emojis (e.g. `📷`, `🎾`, `🌸`, `🌊`) are strictly forbidden as placeholders. Only the uppercase monospace `"X"` is allowed.
- **Example Code**:
  ```html
  <div style="width: 100%; height: 200px; border: 2px solid var(--border-color); background-color: var(--secondary-color); display: flex; align-items: center; justify-content: center;">
      <span style="font-family: monospace; font-size: 3rem; font-weight: bold; opacity: 0.5;">X</span>
  </div>
  ```

---

## 5. Destinazione Carousel Card Layout
Carousel cards must have identical sizes and perfectly aligned actions:
- **Card Sizing**: `.carousel-card { width: 320px; height: 520px; flex: 0 0 auto; display: flex; flex-direction: column; align-items: center; text-align: center; overflow: hidden; padding: 2rem; }`
- **Action Alignment (CSS Specificity)**:
  - To align the action button at the bottom of all cards, the price paragraph must use `margin-top: auto`.
  - **CSS Bug Prevention**: Make sure to use the correct selector `.carousel-card .carousel-price { margin-top: auto; }`. Do NOT double the class selector (e.g. `.carousel-card .carousel-card .carousel-price`).
- **Routing**: Buttons inside the destinations carousel (`Seleziona Viaggio`) must point to `upsell.html` instead of bypassing the funnel to `cart.html`.

---

## 6. Mega Menu Hover Dropdowns
Mega menu items must use a vertical alignment:
- **Card layout**: `.menu-card { display: flex; flex-direction: column; align-items: center; justify-content: center; background-color: var(--text-color); color: var(--bg-color); width: 160px; }` (styled as a primary black button)
- **Media**: A square `120px` by `120px` solid border box with a centered `X` positioned directly **above** the text label.
- **Figma Export sticky override**: When merging all files into the single `figma_export.html` template, the `header` element must have its sticky position overridden:
  ```css
  .figma-frame header {
      position: relative !important;
      top: auto !important;
  }
  ```

---

## 7. Interactive Elements: Buttons, Links & Form Fields

To maintain interactive consistency, all clickable controls and fields must follow these rules:

### A. Primary Buttons (`.btn`)
- **Visuals**: Solid black background with white text, uppercase lettering, bold, with a 1px solid black border.
- **Hover behavior**: Hover states are disabled. The button remains solid black.
- **CSS Specification**:
  ```css
  .btn {
      display: inline-block;
      padding: 1rem 2rem;
      background-color: var(--text-color);
      color: var(--bg-color);
      text-decoration: none;
      font-weight: bold;
      border: 1px solid var(--text-color);
      cursor: pointer;
      text-align: center;
      font-family: var(--font-main);
      /* where --font-main is 'Maison Neue Mono', monospace */;
      text-transform: uppercase;
      letter-spacing: 0.05em;
      font-size: 0.9rem;
  }
  ```

### B. Standard Text Links (`a`)
- **Visuals**: Standard underline with a 4px vertical offset:
  ```css
  a {
      color: var(--text-color);
      text-decoration: underline;
      text-underline-offset: 4px;
  }
  ```
- **Navigation overrides**: Anchors inside navbar menus (`nav a`, `.submenu a`, `.menu-card`) must strip text-decoration: `text-decoration: none;`

### C. Form Input Fields (`input[type="text"]`, `input[type="email"]`, `textarea`)
- **Visuals**: Solid 1px solid black border, padded, using the primary monospace font.
- **Constraint**: Do not use round corners (`border-radius`) or custom drop shadows during the wireframing phase. Everything must use square corners and straight lines.

---

## 8. Content & Routing Rules
To maintain correct user flows and content architecture:
1. **Contacts**: Do not create a dedicated contacts page. All "Contattaci" links, event buttons, or B2B requests must route to `aiuto.html`. Remove any "Contatti" text link from the global footers completely.
2. **Schools & Companies**: The presentation of educational programs and corporate team building must reside inside `servizio.html` (replacing the technology section).
3. **Gamification & Events**: The `app.html` page must focus purely on Gamification ("Passaporto & Punti") and clearly detail the community events (e.g., Tournaments, Clinics, Guest Matches) that can be unlocked using Travel Points.
4. **App CTA**: The reservation success screen must use "Scarica App" instead of "Vai alla tua App" to clarify the action.

---

## 9. Borders, Background & Hover Rules (Strict Guidelines)
To keep the layout clean, consistent, and ready for Figma:
1. **No Dashed Lines**: Dashed borders or solid lines are strictly forbidden on the site. All borders, outlines, and horizontal rulers (`<hr>`) must use `solid` styling.
2. **Component Backgrounds**:
   - **White Backgrounds**: All non-image elements, including sections, cards, forms, inputs, header navigation dropdowns, success screens, and interactive controls must have a white background (`var(--bg-color)` or `#FFFFFF`).
   - **Light Gray Backgrounds**: Only image and graphic placeholders (containing the monospace `"X"` character) are allowed to have a light gray background (`var(--secondary-color)` or `#F0F0F0`).
3. **Hover States**: All hover animations, transitions, and style changes (color inversions, scaling, etc.) are strictly disabled for non-navigation elements (including cards, buttons, lists, and forms). Hover effects are preserved ONLY for header/nav components (`.menu-card:hover`, `.nav-item:hover`, etc.) to demonstrate active site navigation structures.
4. **No Square Brackets**: Do not use square brackets (`[` and `]`) around placeholder texts or labels. All text placeholders must be written as raw, readable strings (e.g. "Titolo Sezione" instead of "[Titolo Sezione]").
5. **No Box Shadows**: Box shadows (`box-shadow`) are strictly forbidden on all containers, cards, dropdowns, and buttons. The interface must remain completely flat, using only solid borders to outline containers.
