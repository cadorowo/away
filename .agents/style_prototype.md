# Away High-Fidelity Prototyping Style Guide (Sito Web)

Questo documento definisce le specifiche visive, il design system e le regole tecniche per lo sviluppo del prototipo ad alta fedeltà (High-Fidelity) del **sito web di Away** all'interno della cartella `prototype/sito/`.

---

## 1. Palette Cromatiche & Mappatura dei Ruoli UI

Utilizzare rigorosamente le variabili CSS per ogni elemento dell'interfaccia:

```css
:root {
    /* Canvas & Background Rule */
    --bg-color: #161616;           /* CHARCOAL (#161616): Sfondo primario di canvas dell'intero sito web e della Hero */
    --color-primary: #161616;      /* Deep Charcoal: Sfondo di riferimento e contenitori principali */
    
    /* Text & Contrasts on Dark Canvas */
    --text-color: #FFFFFF;         /* Bianco puro per i testi principali su sfondo Charcoal */
    --text-muted: #909090;         /* Muted Gray per sottotitoli e meta-dati */

    /* Brand & Accent Colors */
    --color-secondary: #B3E5FF;    /* Soft Ice Blue: Badge, tag categorie (Padel/Travel), highlights, selezioni attive */
    --color-accent: #EE3810;       /* Electric Coral Red: CTAs primarie ("Prenota Ora", "Acquista"), notifica promo */

    /* Neutrals & Structure */
    --color-neutral-dark: #3E3E3E; /* Dark Slate: Bordi card scure, sfondi container secondari, divisori */
    --color-neutral-mid: #909090;  /* Muted Gray: Prezzi barrati, placeholder input, dettagli secondari */
    --color-neutral-light: #262626;/* Charcoal chiaro per sfondi card, sezioni secondarie e hover */
    --color-surface-card: #222222; /* Card Canvas scuro con bordi definiti */
    --color-surface-white: #FFFFFF;/* Dettagli ad elevato contrasto */

    /* Typography Tokens */
    --font-display: 'Maison Neue', system-ui, -apple-system, sans-serif;
    --font-mono: 'Maison Neue Mono', monospace;

    /* Border Radius & Geometry */
    --radius-pill: 999px;
    --radius-lg: 24px;
    --radius-md: 16px;
    --radius-sm: 10px;

    /* Shadows & Elevations (Strictly NO Glow Effects) */
    --shadow-sm: 0 4px 12px rgba(0, 0, 0, 0.2);
    --shadow-md: 0 10px 30px rgba(0, 0, 0, 0.4);
    --shadow-lg: 0 20px 45px rgba(0, 0, 0, 0.6);

    /* Glassmorphism & Blur */
    --glass-bg: rgba(22, 22, 22, 0.85);
    --glass-blur: blur(16px);
    --glass-border: 1px solid rgba(255, 255, 255, 0.12);
}
```

---

1. **Cornici Stondate per le Immagini (`border-radius: 28px` / `32px`) & Zero Gradienti**:
   - Rimosse le maschere ed i gradienti sfumati scuri sovrapposti alle immagini per mantenere colori nitidi e brillanti.
   - Tutte le immagini nelle sezioni Hero, Bento Grids e Card sono racchiuse all'interno di **cornici stondate ad alto impatto** (`border-radius: 28px` o `32px`), definite da un sottile bordo in trasparenza (`border: 1px solid rgba(255, 255, 255, 0.15)`) ed un'elevazione morbida (`box-shadow: 0 16px 40px rgba(0, 0, 0, 0.4)`).
2. **Nessun Effetto Glow**:
   - Effetti di bagliore (`text-shadow glow`, `box-shadow` luminescenti neon o auree colorate) sono **rigorosamente vietati**.
3. **Invarianza dei Contenuti & Sperimentazione di Layout (Displaying Diversity)**:
   - I contenuti informativi e le informazioni chiave devono rimanere invariati rispetto alla UX/IA originale, ma l'agente DEVE sempre sperimentare e applicare layout visivi innovativi e diversificati per displayare tali contenuti (es. Bento Grids, layout split asimmetrici, timeline a pillola, card interattive con badge, caroselli 3D, ecc.).
4. **Divieto Assoluto di Emoji (No Emojis Rule)**:
   - È severamente vietato l'uso di qualsiasi Emoji in tutti i testi dell'interfaccia (titoli, sottotitoli, pillole, badge, bottoni). Utilizzare unicamente icone SVG o testo pulito.

---

## 3. Specifiche Reference Glassmorphic Navbar (Struttura a 3 Elementi)

La navigazione principale adotta l'esatto layout di riferimento a 3 blocchi con **Central Glass Pill Menu**:

- **Layout a 3 Blocchi (`header.glass-header`)**:
  - **Posizionamento Sticky ("Accompagna lo Scroll")**: `position: sticky; top: 1.5rem; z-index: 1000; margin: 0 auto; width: calc(100% - 4rem); max-width: 1320px;` (La Navbar fluttua in modo trasparente ed accompagna fluidamente lo scroll dell'utente su tutta la pagina).
  1. **Sinistra**: Logo AWAY (`.header-logo .logo`, `font-size: 2.2rem`, `font-weight: 900`, `#FFFFFF`).
  2. **Centro (Glass Pill Container `.glass-pill-nav`)**:
     - Contenitore a pillola in vetro ultra-trasparente senza bordi: `background: rgba(255, 255, 255, 0.08); backdrop-filter: blur(24px) saturate(200%); -webkit-backdrop-filter: blur(24px) saturate(200%); border: none; box-shadow: 0 12px 32px rgba(0, 0, 0, 0.35); border-radius: 999px; padding: 0.65rem 2.25rem;`
     - Voci di navigazione separate da divisori verticali in trasparenza (`<span class="nav-divider">|</span>`).
     - **Voci di Navigazione Mantenute Identiche**: `Servizio` | `Destinazioni` (con Mega-Menu Dropdown fotografico) | `App` | `Partner` | `PalaVillage` | `Aiuto`.
  3. **Destra (Azioni `.header-actions`)**:
     - Bottone Carrello Circolare in Vetro (`.cart-btn`, `width: 44px`, `height: 44px`, `border-radius: 50%`).
     - Bottone Pillola Bianco (`.cta-pill-white`, `background-color: #FFFFFF`, `color: #161616`, `border-radius: 999px`) con cerchio icona freccia nera integrato (`<span class="cta-arrow">↗</span>`).

---

## 4. Tipografia, Craftsmanship e Micro-dettagli UI (`make-interfaces-feel-better`)

- **Headings & Titoli**: `'Maison Neue', sans-serif`, font-weight 700 o 900, uppercase con letter-spacing `-0.03em`, colore `#FFFFFF` (senza text-shadow).
- **Text Wrapping (`make-interfaces-feel-better`)**:
  - Applicare sempre `text-wrap: balance;` su tutti i titoli (`h1`, `h2`, `h3`) per distribuire uniformemente il testo sulle righe ed evitare spezzature asimmetriche.
  - Applicare sempre `text-wrap: pretty;` sui paragrafi di descrizione per evitare parole isolate (widows) a fine frase.
- **Rendering Testo & Monospaced Numbers**:
  - Applicare `-webkit-font-smoothing: antialiased; -moz-osx-font-smoothing: grayscale;` per un rendering dei font nitido e sottile su fondo Charcoal scuro.
  - Applicare `font-variant-numeric: tabular-nums; font-feature-settings: "tnum";` a tutti i prezzi, contatori, numeri di specifiche e dati per evitare balzelli di layout.
- **Dati, Tag e Codici**: `'Maison Neue Mono', monospace`.
- **Raggi Concentrici**: `Outer Radius = Inner Radius + Padding` ($R_{outer} = R_{inner} + P$).
- **Dimensioni**:
  - `h1`: `4.5rem` (Mobile: `2.5rem`) - Line height `1.05`
  - `h2`: `3rem` (Mobile: `2rem`) - Line height `1.1`
  - `h3`: `1.75rem` - Line height `1.2`
  - `body`: `1rem` - Line height `1.6`

---

## 5. Bottoni, Componenti e Forme (Pill Style)

### Bottoni Primari (`.btn-primary` / `.btn`)
- **Background**: `var(--color-accent)` (`#EE3810`)
- **Color**: `#FFFFFF`
- **Border-Radius**: `var(--radius-pill)` (`999px`)
- **Padding**: `1rem 2.25rem`
- **Font**: `'Maison Neue', sans-serif`, `font-weight: 700`, `text-transform: uppercase`, `letter-spacing: 0.05em`.
- **Hover**: `transform: translateY(-2px); background-color: #D62D07;`

### Bottoni Secondari & Ice Blue (`.btn-secondary`)
- **Ice Blue Badge/Button**: Background `var(--color-secondary)` (`#B3E5FF`), testo `#161616`, border-radius `999px`.

---

## 6. Elevazione, Ombre e Glassmorphism Card

1. **Card Prodotto & Destinazioni**:
   - `background-color: var(--color-surface-card);` (`#222222`)
   - `border-radius: var(--radius-lg);` (`24px`)
   - `border: 1px solid rgba(255, 255, 255, 0.1);`
   - `box-shadow: var(--shadow-md);`
   - `overflow: hidden;`

---

## 7. Immagini e Fotografia (High-Res Unsplash Photography)

- **Hero Background & Visual Component**: **Charcoal Puro (`#161616`)** senza immagine di sfondo. L'effetto visivo principale è dato dalle **3D Rotating Destination Cards**: mazzo di card 3D rotanti ed inclinate in prospettiva (`perspective: 1400px`) che mostrano le destinazioni (*Hawaii, Islanda, Marocco, Perù*) con rotazione continua ed interazione mouse GSAP.
- **Catalogo Destinazioni (`destinazioni.html`)**: **Accordion Image Cards (Horizontal Expansion)**. Carosello ad espansione orizzontale fluida (`flex: 3.5` vs `flex: 1`) dove la card attiva rivela fotografia a schermo intero, glass badge in alto e bottone pillola bianco `SELEZIONA VIAGGIO ↗`.
- **Destinazioni & Padel Resort**: Fotografie ad alta risoluzione selezionate da Unsplash per card e gallerie.
- **Aspect Ratio & Crop**:
  - Card Destinazioni: `width: 100%; height: 260px; object-fit: cover; border-radius: var(--radius-md);`

---

## 8. Funnel di Navigazione del Sito (`prototype/sito/`)

- `index.html`: Homepage con Hero Charcoal pulita, GSAP cursor trail, carosello destinazioni, kit Away, promo app & servizi.
- `destinazioni.html`: Catalogo completo destinazioni con filtri attivi.
- `dettaglio-destinazione.html`: Scheda viaggio padel con gallery foto, programma ed inclusione kit.
- `configuratore-kit.html` & `configuratore-kit-solo.html`: Personalizzazione racchetta/kit away.
- `cart.html`, `cart-destinazione.html`: Carrello acquisti reattivo con riepilogo.
- `checkout.html`, `checkout-destinazione.html`, `checkout-entrambi.html`, `checkout-kit.html`: Flow di pagamento step-by-step.
- `upsell.html`: Offerte aggiuntive post-selezione.
- `success.html`: Schermata di conferma ordine con CTA "Scarica App".
- `servizio.html`, `palavillage.html`, `partner.html`, `app.html`, `aiuto.html`: Pagine istituzionali, B2B e supporto.
