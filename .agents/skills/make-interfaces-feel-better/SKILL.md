---
name: make-interfaces-feel-better
description: Principles and micro-details that elevate UI craftsmanship (text-wrap balance/pretty, concentric radii, tabular numbers, antialiased typography, contextual icon animations, optical alignment, and layered shadows).
---

# Details That Make Interfaces Feel Better

A collection of micro-details and craftsmanship rules derived from Jakub Krehel's interface engineering guidelines to make web applications feel premium, crisp, and alive.

---

## 1. Text Wrapping (`text-wrap: balance` & `pretty`)
- **Titles & Headings (`h1`, `h2`, `h3`, `h4`)**: Always set `text-wrap: balance` to distribute title text evenly across lines and avoid unbalanced breaks.
- **Body Paragraphs & Descriptions (`p`, `span.desc`)**: Always set `text-wrap: pretty` to eliminate orphaned single words (widows) at the end of sentences.

```css
h1, h2, h3, h4 {
    text-wrap: balance;
}

p, .description {
    text-wrap: pretty;
}
```

---

## 2. Concentric Border Radius Formula
- Nested elements must share concentric radii so corners remain visually parallel.
- **Formula**: `Outer Radius = Inner Radius + Padding` ($R_{outer} = R_{inner} + P$).

```css
/* Example */
.card-outer {
    padding: 16px;
    border-radius: 24px; /* 8px + 16px */
}

.card-inner {
    border-radius: 8px;
}
```

---

## 3. Tabular Monospaced Numbers (`tabular-nums`)
- Always apply `font-variant-numeric: tabular-nums;` or `font-feature-settings: "tnum";` on prices, timers, counters, scores, dates, and metric stats.
- Prevents text layout shifting and horizontal jitter when values update dynamically.

```css
.price-val, .counter, .stat-number, .timer {
    font-variant-numeric: tabular-nums;
    font-feature-settings: "tnum";
}
```

---

## 4. Crisp Antialiased Typography
- Apply `-webkit-font-smoothing: antialiased; -moz-osx-font-smoothing: grayscale;` globally, especially on dark canvases (`#161616`) to make text render crisp, thin, and razor-sharp.

```css
body {
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-rendering: optimizeLegibility;
}
```

---

## 5. Contextual & Spring Icon Animations
- When icons toggle state (e.g., Copy -> Checkmark, Expand -> Collapse, Cart -> Added), animate `opacity`, `scale`, and `transform`.
- Use fast spring transitions (`transition: transform 0.2s cubic-bezier(0.16, 1, 0.3, 1), opacity 0.15s ease`).

```css
.icon-swap {
    transition: transform 0.2s cubic-bezier(0.16, 1, 0.3, 1), opacity 0.15s ease;
    will-change: transform, opacity;
}
```

---

## 6. Interruptible & Staggered Animations
- **Stagger Entering Items**: Apply staggered delays to list items, bento cards, and dropdown options (`animation-delay: calc(var(--index) * 50ms)`).
- **Subtle Fast Exits**: Keep exit transitions fast (120ms - 150ms) so popups and menus disappear instantly without blocking user actions.

---

## 7. Optical Alignment over Pure Geometry
- Align icons and visual elements optically based on visual center of mass (e.g. play triangles `▶`, arrow chevrons `↗`, badges) rather than relying strictly on bounding-box centering.

---

## 8. Layered Shadows & Subtle Translucent Outlines
- Replace heavy opaque borders with layered soft drop shadows (`box-shadow: 0 4px 12px rgba(0,0,0,0.2), 0 16px 40px rgba(0,0,0,0.4)`) and subtle translucent inner rings (`box-shadow: inset 0 0 0 1px rgba(255,255,255,0.1)`).
