# AGENTS.md — Away App · Prototipo High-Fidelity

Questo documento è la guida normativa autoritativa per la creazione e modifica di tutte le schermate del prototipo mobile ad alta fedeltà dell'app Away (`prototype/app/`). Qualsiasi agente che lavora su questi file DEVE leggere e rispettare integralmente queste regole prima di scrivere qualsiasi riga di codice.

---

## 0. Documenti di Riferimento Obbligatori

Prima di iniziare qualsiasi lavoro, leggere nell'ordine:

1. [`design.md`](file:///Users/cadowo/Library/Mobile%20Documents/com~apple~CloudDocs/Documents/projects/vibes/away%20digital/design.md) — Design System autoritativo (token, bottoni, badge, tipografia, regole tassative)
2. [`.agents/style_prototype.md`](file:///Users/cadowo/Library/Mobile%20Documents/com~apple~CloudDocs/Documents/projects/vibes/away%20digital/.agents/style_prototype.md) — Specifiche visive HiFi (palette, glassmorphism, pill shapes, ombre)
3. [`.agents/skills/make-interfaces-feel-better/SKILL.md`](file:///Users/cadowo/Library/Mobile%20Documents/com~apple~CloudDocs/Documents/projects/vibes/away%20digital/.agents/skills/make-interfaces-feel-better/SKILL.md) — Micro-dettagli UI craftsmanship

---

## 1. Architettura dei File

- **Modalità**: High-Fidelity Prototyping — dark canvas, Design System completo, nessun elemento wireframe residuo.
- **Sorgente dei wireframe**: `wireframing/app/<nome>.html` (usare come riferimento per struttura e contenuti, mai per lo stile).
- **Output**: `prototype/app/<nome>.html` (sovrascrivere il file esistente).
- **Self-contained**: ogni file è autonomo — tutto il CSS risiede nel `<style>` inline, nessuna dipendenza esterna.
- **Font locali**: i `@font-face` puntano a `../../fonts/` — mantenere i percorsi invariati.
- **Link di navigazione**: tutti gli `href` tra pagine puntano ai file in `prototype/app/`, mai a `wireframing/app/`.

---

## 2. Token CSS — Sostituire Integralmente il `:root`

```css
:root {
    /* Canvas & Backgrounds */
    --bg-color:               #161616;
    --color-surface-card:     #222222;
    --color-surface-secondary:#262626;

    /* Typography */
    --text-color:             #FFFFFF;
    --text-muted:             #909090;

    /* Brand Accent */
    --color-accent:           #EE3810;   /* SOLO bottoni Tier 1 */
    --color-secondary:        #B3E5FF;   /* badge, pillole, highlight */

    /* Neutrals */
    --color-neutral-dark:     #3E3E3E;
    --glass-border:           1px solid rgba(255, 255, 255, 0.12);

    /* Fonts */
    --font-display:           'Maison Neue', system-ui, -apple-system, sans-serif;
    --font-mono:              'Maison Neue Mono', monospace;

    /* Border Radius */
    --radius-pill:            999px;
    --radius-lg:              24px;
    --radius-md:              16px;
    --radius-sm:              10px;

    /* Shadows */
    --shadow-sm:              0 4px 12px rgba(0, 0, 0, 0.2);
    --shadow-md:              0 10px 30px rgba(0, 0, 0, 0.4);
    --shadow-lg:              0 20px 45px rgba(0, 0, 0, 0.6);

    /* Glassmorphism */
    --glass-bg:               rgba(22, 22, 22, 0.85);
    --glass-blur:             blur(16px);
}
```

---

## 3. Shell dell'App

### Body
```css
body {
    background-color: #0D0D0D; /* più scuro del canvas per far emergere il frame */
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
    padding: 2rem 0;
}
```

### #app-frame
```css
#app-frame {
    width: 100%;
    max-width: 430px;
    height: 932px;
    background-color: var(--bg-color);
    border: 1px solid rgba(255, 255, 255, 0.15); /* sostituisce il bordo 2px nero wireframe */
    border-radius: 48px;                          /* simula i bordi del telefono */
    box-shadow: 0 40px 80px rgba(0, 0, 0, 0.8);
    position: relative;
    display: flex;
    flex-direction: column;
    overflow: hidden;
}
```

---

## 4. Componenti Fissi (condivisi da ogni pagina)

### Status Bar
```css
.status-bar {
    height: 44px;
    padding: 0 1.75rem;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background-color: var(--bg-color);
    border-bottom: 1px solid rgba(255, 255, 255, 0.06);
    flex-shrink: 0;
    font-size: 0.8rem;
    font-weight: 700;
    color: var(--text-color);
    font-family: var(--font-mono);
    font-variant-numeric: tabular-nums;
}
```

### Header App
```css
header {
    padding: 1rem 1.5rem;
    min-height: 64px;
    display: flex;
    justify-content: space-between;
    align-items: center;
    background: rgba(22, 22, 22, 0.9);
    backdrop-filter: blur(20px);
    -webkit-backdrop-filter: blur(20px);
    border-bottom: 1px solid rgba(255, 255, 255, 0.08);
    flex-shrink: 0;
}

.page-title {
    font-family: var(--font-display);
    font-size: 1.4rem;
    font-weight: 900;
    color: var(--text-color);
    text-transform: uppercase;
    letter-spacing: -0.05em;
    text-decoration: none;
}

.icon-btn {
    background: none;
    border: none;
    cursor: pointer;
    color: var(--text-color);
    opacity: 0.7;
    display: flex;
    align-items: center;
    justify-content: center;
    transition: opacity 0.2s ease;
}
.icon-btn:hover { opacity: 1; }
```

### Tab Bar
```css
.tab-bar {
    position: absolute;
    bottom: 0;
    left: 0;
    right: 0;
    height: 80px;
    background: rgba(22, 22, 22, 0.95);
    backdrop-filter: blur(24px);
    -webkit-backdrop-filter: blur(24px);
    border-top: 1px solid rgba(255, 255, 255, 0.08);
    display: flex;
    z-index: 100;
}

.tab-item {
    flex: 1;
    display: flex;
    flex-direction: column;
    align-items: center;
    justify-content: center;
    text-decoration: none;
    color: var(--text-muted);  /* #909090 — stato inattivo */
    font-size: 0.6rem;
    font-weight: 700;
    font-family: var(--font-mono);
    text-transform: uppercase;
    letter-spacing: 0.04em;
    gap: 5px;
    position: relative;
    padding-top: 6px;
}

.tab-item.active {
    color: var(--text-color);  /* #FFFFFF — stato attivo */
}

/* Indicatore pillola accent sopra l'icona */
.tab-item.active::before {
    content: '';
    position: absolute;
    top: 0;
    width: 24px;
    height: 2px;
    background: var(--color-accent);  /* #EE3810 */
    border-radius: 999px;
}
```

---

## 5. Sistema a 3 Tier di Bottoni (Tassativo)

Il bottone sbagliato in un flusso è un errore di design critico. Assegnare il tier in base all'azione, non alla posizione.

### Tier 1 — Conversione Primaria
Usare per: PRENOTA, CHECKOUT, PAGA, CONFERMA, VEDI PRENOTAZIONE, ACCEDI AL CAMPO.

```css
.btn-primary {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    padding: 1rem 2.25rem;
    background-color: var(--color-accent);  /* #EE3810 */
    color: #FFFFFF;
    border: none;
    border-radius: var(--radius-pill);
    font-family: var(--font-display);
    font-size: 0.85rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    cursor: pointer;
    text-decoration: none;
    transition: background-color 0.2s ease, transform 0.15s ease;
}
.btn-primary:hover {
    background-color: #D62D07;
    transform: translateY(-1px);
}
```

### Tier 2 — Esplorazione Secondaria
Usare per: SCOPRI DI PIÙ, SELEZIONA KIT, PRENOTA UN ALTRO VIAGGIO, SCARICA APP.

```css
.btn-secondary {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    padding: 1rem 2.25rem;
    background-color: #FFFFFF;
    color: #161616;
    border: none;
    border-radius: var(--radius-pill);
    font-family: var(--font-display);
    font-size: 0.85rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    cursor: pointer;
    text-decoration: none;
    transition: background-color 0.2s ease;
}
.btn-secondary:hover { background-color: #F2F2F2; }
```

### Tier 3 — Outline / Terziario
Usare per: ANNULLA, SKIP, PERSONALIZZA, INDIETRO.

```css
.btn-outline {
    display: inline-flex;
    align-items: center;
    justify-content: center;
    width: 100%;
    padding: 0.9rem 2rem;
    background: rgba(255, 255, 255, 0.06);
    color: #FFFFFF;
    border: 1px solid rgba(255, 255, 255, 0.25);
    border-radius: var(--radius-pill);
    font-family: var(--font-display);
    font-size: 0.85rem;
    font-weight: 700;
    text-transform: uppercase;
    letter-spacing: 0.05em;
    cursor: pointer;
    text-decoration: none;
    backdrop-filter: blur(8px);
}
```

---

## 6. Card e Contenitori

### Card Standard
```css
.card {
    background-color: var(--color-surface-card);  /* #222222 */
    border-radius: var(--radius-lg);               /* 24px */
    border: 1px solid rgba(255, 255, 255, 0.08);
    box-shadow: var(--shadow-md);
    overflow: hidden;
}
```

### Card Glassmorphic (su sfondo immagine)
```css
.card-glass {
    background: rgba(22, 22, 22, 0.75);
    backdrop-filter: blur(20px);
    -webkit-backdrop-filter: blur(20px);
    border: 1px solid rgba(255, 255, 255, 0.15);
    border-radius: var(--radius-lg);
}
```

### Regola Raggi Concentrici (obbligatoria)
Raggio esterno = Raggio interno + Padding.

Esempi:
- Card `border-radius: 24px`, `padding: 16px` → figlio interno `border-radius: 8px`
- Card `border-radius: 16px`, `padding: 12px` → figlio `border-radius: 4px`

---

## 7. Badge e Pillole (non-bottone)

Usare per: tag destinazione, badge punti, status, categorie.
L'arancione `#EE3810` è vietato qui — solo `#B3E5FF`.

```css
.badge {
    display: inline-flex;
    align-items: center;
    padding: 0.35rem 0.9rem;
    background: rgba(255, 255, 255, 0.06);
    color: var(--color-secondary);              /* #B3E5FF */
    border: 1px solid rgba(179, 229, 255, 0.4);
    border-radius: 999px;
    font-family: var(--font-mono);
    font-size: 0.7rem;
    font-weight: 800;
    letter-spacing: 0.06em;
    text-transform: uppercase;
    backdrop-filter: blur(12px);
    -webkit-backdrop-filter: blur(12px);
}
```

---

## 8. Placeholder Immagini

### Placeholder CSS Dark (default — zero dipendenze esterne)
Sostituisce i `<div>` con `X` grigio del wireframe:

```html
<div class="img-placeholder">
    <svg width="32" height="32" viewBox="0 0 24 24" fill="none" stroke="#3E3E3E" stroke-width="1.5">
        <rect x="3" y="3" width="18" height="18" rx="4"/>
        <circle cx="8.5" cy="8.5" r="1.5"/>
        <polyline points="21 15 16 10 5 21"/>
    </svg>
</div>
```

```css
.img-placeholder {
    width: 100%;
    background: linear-gradient(135deg, #222222 0%, #1a1a1a 50%, #262626 100%);
    border-radius: var(--radius-md);
    border: 1px solid rgba(255, 255, 255, 0.06);
    display: flex;
    align-items: center;
    justify-content: center;
}
```

### Immagini Reali da Unsplash (per schermate destinazione)
Quando la schermata è specifica per una destinazione (Hawaii, Islanda, Marocco, Perù), usare immagini Unsplash reali:

```html
<img
    src="https://images.unsplash.com/photo-XXXXXXXXXX?w=800&q=80"
    alt="[Destinazione]"
    style="width:100%; height:100%; object-fit:cover; border-radius: var(--radius-md);"
/>
```

---

## 9. Campi Input e Form

```css
input, textarea, select {
    width: 100%;
    padding: 0.9rem 1rem;
    background: rgba(255, 255, 255, 0.05);
    border: 1px solid rgba(255, 255, 255, 0.12);
    border-radius: var(--radius-md);
    color: var(--text-color);
    font-family: var(--font-mono);
    font-size: 0.9rem;
    outline: none;
    transition: border-color 0.2s ease;
}
input:focus {
    border-color: rgba(179, 229, 255, 0.5);
}
input::placeholder {
    color: var(--text-muted);
    opacity: 0.6;
}
```

---

## 10. Tipografia (Regole Obbligatorie)

```css
h1, h2, h3, h4 {
    font-family: var(--font-display);
    font-weight: 900;
    color: var(--text-color);
    text-transform: uppercase;
    letter-spacing: -0.03em;
    text-wrap: balance;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
}

p, .body-text {
    font-family: var(--font-mono);
    color: var(--text-muted);
    text-wrap: pretty;
    line-height: 1.6;
    -webkit-font-smoothing: antialiased;
}

/* Numeri tabulari — prezzi, punti, contatori, orari */
.price, .points, .counter, .time, .stat {
    font-variant-numeric: tabular-nums;
    font-feature-settings: "tnum";
    font-family: var(--font-mono);
}
```

### Scala Tipografica Mobile
| Tag | Size | Line-height |
|-----|------|-------------|
| h2  | 1.8rem | 1.1 |
| h3  | 1.4rem | 1.2 |
| h4  | 1.1rem | 1.3 |
| p   | 0.85rem | 1.6 |
| label/badge | 0.7rem | 1 |

---

## 11. Separatori e Spaziature

- **Nessun** `border-bottom: 1px solid #000` (wireframe)
- Separatori sottili tra sezioni: `border-bottom: 1px solid rgba(255, 255, 255, 0.06)`
- Padding interno sezioni: `padding: 1.5rem`
- Gap tra card: `gap: 1rem`
- `main` deve avere `padding-bottom: 90px` per non essere coperto dalla tab bar

---

## 12. Layout Sperimentale (Obbligatorio — almeno 1 pattern per pagina)

I contenuti del wireframe non cambiano. Cambia il modo di presentarli. Sperimentare con:

| Pattern | Pagine Suggerite |
|---------|-----------------|
| **Bento Grid asimmetrico** | home, punti, minigiochi |
| **Hero card full-width con overlay glass** | home, dettaglio-viaggio, accesso-campo |
| **Timeline verticale pill** | prenotazioni, dettaglio-storico, notifiche |
| **Tab filter pill glassmorphic** | prenotazioni, punti, minigiochi |
| **Split layout orizzontale** | profilo, checkout, metodo-pagamento |
| **Progress ring CSS** | punti, profilo |
| **Carosello orizzontale card dark** | home (kit), prenotazioni (destinazioni) |
| **Full-bleed image + overlay** | nfc-boarding-pass, accesso-campo, telecomando |
| **Step indicator orizzontale pill** | checkout, seleziona-kit, nuova-prenotazione |

---

## 13. Divieti Assoluti

| Vietato | Alternativa corretta |
|---------|---------------------|
| Emoji in qualsiasi testo UI | Icone SVG inline |
| `border: 2px solid #000` | `border: 1px solid rgba(255,255,255,0.08)` |
| `border-radius: 0` | Minimo `var(--radius-sm)` — tutto ha raggi |
| `box-shadow` con colori neon/glow | Solo ombre nere: `rgba(0,0,0,0.X)` |
| `#EE3810` su badge, icone, numeri | `#B3E5FF` per elementi non-bottone |
| Valori hex o px raw | Sempre token `var(--)` |
| `background: #F0F0F0` (grigio wireframe) | `var(--color-surface-card)` o `var(--bg-color)` |
| `color: #000000` | `var(--text-color)` o `var(--text-muted)` |

---

## 14. Self-Check Prima di Salvare (Obbligatorio)

Rileggere il file generato e verificare:

- [ ] Nessun `#000000`, `#FFFFFF` hardcoded — solo token `var(--)`
- [ ] Nessun `border: 2px solid #000` residuo dal wireframe
- [ ] Nessun `border-radius: 0`
- [ ] Tutti i bottoni hanno il tier corretto (Tier 1 = arancione, Tier 2 = bianco, Tier 3 = outline)
- [ ] `text-wrap: balance` su tutti i titoli h1/h2/h3/h4
- [ ] `text-wrap: pretty` su tutti i paragrafi p
- [ ] Numeri, prezzi e punti hanno `font-variant-numeric: tabular-nums`
- [ ] Nessuna emoji nel testo dell'interfaccia
- [ ] Raggi concentrici rispettati per gli elementi annidati
- [ ] Link di navigazione puntano a `prototype/app/`, non a `wireframing/app/`
- [ ] Il `<title>` della pagina è aggiornato

---

*Ultimo aggiornamento: Luglio 2026 · AWAY Digital App — High-Fidelity Prototype*
