# 🎨 AWAY Digital — Master Design System & UI Directives (`design.md`)

Questo documento rappresenta la **guida definitiva ed autoritativa delle direttive UI, del Design System e delle regole di Craftsmanship** per l'intero prototipo digitale di **AWAY** (`prototype/sito/`). Tutte le modifiche, nuove pagine e componenti Dev/UX DEVONO rispettare rigorosamente questo documento.

---

## 1. 📍 Concept di Brand & Posizionamento UX

1. **Il Campo Fisico al PalaVillage (Torino)**:
   - AWAY è una rete di campi da padel panoramici immersivi a 360° **fisicamente ed unicamente installati all'interno del PalaVillage a Torino**.
   - I giocatori non prendono mai aerei fisici, ma la comunicazione sfrutta la suggestione ed il fascino del **viaggio multisensoriale**: proiezioni visive a 360° su vetri e pareti, audio 3D direzionale, nebulizzazione olfattiva d'essenze naturali e clima controllato per 90 minuti di gioco immersivo.
2. **Trasparenza e Tone of Voice**:
   - Linguaggio sportivo, agonistico, d'impatto ed evocativo, privo di ambiguità ingannevoli.

---

## 2. 🎨 Color Tokens & Regole Cromatiche Tassative

L'interfaccia adotta un canvas scuro in tonalità Charcoal con rigida separazione tra i ruoli dei colori:

```css
:root {
    /* Canvas & Backgrounds */
    --bg-color: #161616;           /* Deep Charcoal: Sfondo primario di canvas dell'intero sito web e della Hero */
    --color-surface-card: #222222; /* Card Canvas scuro per bento cards e contenitori principali */
    --color-surface-secondary: #262626; /* Charcoal chiaro per sfondi sezioni secondarie e hover */

    /* Typography & Contrast */
    --text-color: #FFFFFF;         /* Bianco puro per i titoli principali e testo ad alto contrasto */
    --text-muted: #909090;         /* Muted Gray per sottotitoli e meta-dati */

    /* Brand Accent Colors */
    --color-accent: #EE3810;       /* Brand Accent Orange: RISERVATO ESCLUSIVAMENTE AI BOTTONI DI CONVERSIONE PRIMARIA (TIER 1) */
    --color-secondary: #B3E5FF;    /* Soft Light Blue: Riservato a badge d'accento, pillole traslucide, highlight non-bottone e spunte */

    /* Neutrals & Borders */
    --color-neutral-dark: #3E3E3E; /* Dark Slate: Bordi card scure e divisori */
    --glass-border: 1px solid rgba(255, 255, 255, 0.12);

    /* Typography Fonts */
    --font-display: 'Maison Neue', system-ui, -apple-system, sans-serif;
    --font-mono: 'Maison Neue Mono', monospace;
}
```

### 🚫 Regola Tassativa sull'Uso dell'Arancione (`#EE3810`):
- **L'Arancione Brand (`#EE3810`) è riservato ESCLUSIVAMENTE ai Bottoni Primari di Conversione (Tier 1)**.
- **DIVIETO ASSOLUTO** di utilizzare l'arancione per elementi non-bottone (es. badge bento, numeri di step, cerchietti delle spunte, tag di testo, icone).
- Tutti gli elementi di highlight e badge non-bottone DEVONO utilizzare il **Blu Secondario di Brand (`#B3E5FF`)**.

---

## 3. 🔘 Architettura dei Bottoni a 3 Livelli (Strict 3-Tier Button System)

Ogni pulsante presente nel prototipo deve appartenere a uno (ed uno solo) dei tre livelli definiti:

| Livello | Nome & Variante | Stile Visivo (CSS) | Destinazione d'Uso |
| :--- | :--- | :--- | :--- |
| **Tier 1** | **Primary Conversion CTA** | Background `#EE3810`, testo `#FFFFFF`, border `#EE3810`, pillola `999px`. Hover: `#D62D07`. | Azioni di conversione primaria **SOLO**: Hero Primary CTA, Checkout (`.btn-checkout`), PalaVillage Campus CTA. |
| **Tier 2** | **Secondary Exploration CTA** | Background `#FFFFFF` (Pillola Bianca Solida), testo `#161616`, border `#FFFFFF`, pillola `999px`. Hover: `#F2F2F2`. | Azioni di selezione & esplorazione: Download App / Navbar CTA (`.cta-pill-white`), *SELEZIONA VIAGGIO* negli Accordion, form Newsletter nel footer, bottoni di navigazione secondaria. |
| **Tier 3** | **Tertiary / Outline CTA** | Background `#222222` (Vetro Scuro), testo `#FFFFFF`, bordo `1px solid rgba(255, 255, 255, 0.25)`, pillola `999px`. Hover: `#2A2A2A`. | Bottoni nelle sezioni Typography Statement, Skip/Personalizza Kit (`.btn-statement`, `.btn-outline`, `.btn-skip`). |

---

## 4. 🏷️ Uniformazione Pillole & Badge Glassmorphic (`#B3E5FF`)

Tutti i badge, tag e pillole non-bottone (`.bento-tag`, `.matrix-badge`, `.statement-index`, `.step-number-badge`) DEVONO avere lo stesso stile grafico traslucido:

```css
.bento-tag,
.matrix-badge,
.step-number-badge,
.statement-index {
    display: inline-flex !important;
    align-items: center !important;
    justify-content: center !important;
    padding: 0.45rem 1.25rem !important;
    background: rgba(255, 255, 255, 0.06) !important;
    background-color: rgba(255, 255, 255, 0.06) !important;
    color: #B3E5FF !important;
    border: 1px solid rgba(179, 229, 255, 0.4) !important;
    border-radius: 999px !important;
    font-family: var(--font-display) !important;
    font-size: 0.8rem !important;
    font-weight: 800 !important;
    letter-spacing: 0.05em !important;
    text-transform: uppercase !important;
    backdrop-filter: blur(12px) !important;
    -webkit-backdrop-filter: blur(12px) !important;
}

/* Icone e Spunte */
.feature-icon-pill {
    background-color: rgba(179, 229, 255, 0.18) !important;
    color: #B3E5FF !important;
    border: 1px solid rgba(179, 229, 255, 0.3) !important;
    border-radius: 50% !important;
}
```

---

## 5. 📐 Struttura Layout & Spaziature

1. **Maschera della Hero (`.hero-bg-mask`)**:
   - La foto di sfondo della Hero NON tocca mai i bordi estremi dello schermo edge-to-edge.
   - Mantiene la rientranza elegante: `width: calc(100% - 3.5rem)`, `max-width: 1360px`, centrata con `left: 50%; transform: translateX(-50%)` e bordi inferiori arrotondati `border-radius: 0 0 36px 36px`.
   - **Nessun testo descrittivo `<p>` o pillola trasparente** dietro i titoli della Hero: solo il titolo `<h1>` d'impatto ed i pulsanti d'azione.
2. **Padding delle Sezioni**:
   - Standardizzato a `7.5rem 2rem` (`120px` di padding verticale) per un ritmo di lettura equilibrato.
3. **Centratura Intestazioni di Sezione (`.section-header`)**:
   - **TUTTE le pre-sezioni DEVONO essere rigorosamente centrate**:
     ```css
     .section-header {
         text-align: center !important;
         margin-left: auto !important;
         margin-right: auto !important;
         max-width: 840px !important;
         margin-bottom: 3.5rem !important;
     }

     .section-header h2,
     .section-header p {
         text-align: center !important;
     }
     ```

---

## 6. ✨ Micro-dettagli UI & Craftsmanship (`make-interfaces-feel-better`)

1. **Text Wrapping Intelligente**:
   - `text-wrap: balance;` su tutti i titoli (`h1`, `h2`, `h3`, `h4`) per distribuire il testo in modo omogeneo sulle righe ed evitare spezzature asimmetriche.
   - `text-wrap: pretty;` sui paragrafi di descrizione per eliminare parole isolate (widows) a fine frase.
2. **Rendering Testo Nitido**:
   - `-webkit-font-smoothing: antialiased; -moz-osx-font-smoothing: grayscale; text-rendering: optimizeLegibility;` su sfondo Charcoal scuro.
3. **Numeri Tabulari Monospaziati**:
   - `font-variant-numeric: tabular-nums; font-feature-settings: "tnum";` a tutti i prezzi, contatori e specifiche per azzerare i balzelli di layout.
4. **Formula dei Raggi Concentrici**:
   - Per elementi annidati: $R_{outer} = R_{inner} + P$ (Raggio esterno = Raggio interno + Padding).
5. **Divieto Assoluto di Emoji (No Emojis Rule)**:
   - Severamente vietato l'uso di qualsiasi Emoji in tutti i testi dell'interfaccia (titoli, pillole, badge, bottoni). Utilizzare unicamente icone SVG inline o testo pulito.
6. **Zero Effetti Glow / Bagliori Neon**:
   - Vietati bagliori luminescenti colorati o ombre neon appariscenti.

---

## 7. 🛠️ Regole per File Figma-Optimized (`html.to.design`)

Quando occorre esportare o creare file per Figma:
1. **Single-File Architecture**: Tutto il codice (HTML, CSS, JS) deve risiedere in un unico file `.html` autonomo.
2. **Zero Dipendenze Esterne**: Nessun link a fogli di stile esterni o Google Fonts (solo font di sistema o script inline).
3. **Immagini & Media**: Utilizzare SVG inline, CSS placeholder o stringhe Base64 (`src="data:image/png;base64,..."`).
4. **Strutture Nascoste**: Elementi come modali o sottomenu devono rimanere presenti nel DOM per l'importazione dei frame in Figma.

---

*Ultimo aggiornamento: Luglio 2026 — AWAY Digital System Architecture*
