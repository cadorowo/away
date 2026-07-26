# Regole Generali e Coerenza Visiva

L'agente DEVE garantire che tutte le pagine del progetto siano visivamente e strutturalmente coerenti tra loro a seconda della modalità di lavoro:

1. **Modalità Wireframing** (cartella `wireframing/`):
   - Consultare e seguire rigorosamente: → [style.md](file:///Users/cadowo/Library/Mobile%20Documents/com~apple%20Docs/Documents/projects/vibes/away%20digital/.agents/style.md)
   - Stile rigorosamente in scala di grigi, layout essenziale, placeholder con "X".

2. **Modalità Prototyping High-Fidelity** (cartella `prototype/sito/`):
   - Consultare e seguire rigorosamente: → [style_prototype.md](file:///Users/cadowo/Library/Mobile%20Documents/com~apple%20Docs/Documents/projects/vibes/away%20digital/.agents/style_prototype.md) e [design.md](file:///Users/cadowo/Library/Mobile%20Documents/com~apple%20Docs/Documents/projects/vibes/away%20digital/design.md)
   - Sfondo Canvas Charcoal (`#161616`), palette brand (`#161616`, `#B3E5FF`, `#EE3810`, `#3E3E3E`, `#909090`, `#F2F2F2`), tipografia Maison Neue, Pill shapes (`999px` / `24px` radius), elevazioni con box-shadow, glassmorphism e foto reali ad alta risoluzione da Unsplash.

3. **Invarianza dei Contenuti & Sperimentazione di Layout**:
   - I contenuti informativi e i messaggi chiave devono rimanere invariati rispetto alla UX/IA definita, ma l'agente DEVE sempre proporre e sperimentare modi visivi e di layout diversi ed innovativi per mostrare/displayare tali contenuti (es. Bento Grids, griglie asimmetriche, card interattive, timeline a pillola, layout split, ecc.).

4. **Divieto Assoluto di Emoji (No Emojis Rule)**:
   - È severamente vietato l'uso di Emoji in qualsiasi testo, titolo, badge, bottone o componente UI dell'interfaccia. Utilizzare esclusivamente icone SVG inline o testo pulito senza simboli emoji.

5. **Micro-dettagli UI & Craftsmanship (`make-interfaces-feel-better`)**:
   - Consultare e seguire la skill: → [make-interfaces-feel-better](file:///Users/cadowo/Library/Mobile%20Documents/com~apple%20Docs/Documents/projects/vibes/away%20digital/.agents/skills/make-interfaces-feel-better/SKILL.md)
   - Utilizzare sempre `text-wrap: balance` sui titoli (`h1`, `h2`, `h3`) e `text-wrap: pretty` sui paragrafi.
   - Numeri tabulari (`font-variant-numeric: tabular-nums`) per prezzi, timer e contatori.
   - `-webkit-font-smoothing: antialiased` per rendering testo nitido e sottile.
   - Raggi concentrici ($R_{outer} = R_{inner} + P$).

---

# Regola per il Brainstorming Estensivo (Focus sui Contenuti)

Quando si utilizza la skill `brainstorming`, l'agente DEVE adottare un approccio di esplorazione profonda (Deep-Dive) concentrandosi sui **CONTENUTI** e sulle **FUNZIONALITÀ**:

1. **Focus sul "Cosa", non sul "Come"**: Fai domande su quali informazioni, dati, funzionalità e messaggi chiave devono essere presenti in ogni pagina. Evita domande su stile visivo, colori, layout o estetica.
2. **Esplora ogni singola sezione nel dettaglio**: Analizza ogni singola pagina/sezione ponendo molteplici domande sui contenuti che ospiterà e sul valore che porterà all'utente.
3. **Esplora ogni opzione di contenuto**: Valuta le alternative sui messaggi da comunicare e sui dati da mostrare, analizzando pro e contro di ogni scelta informativa prima di passare oltre.
4. **Pazienza e Metodo**: Procedi iterativamente, una sezione alla volta. Continua a fare domande sui contenuti di una sezione finché la sua struttura informativa non è completamente definita (una o poche domande per messaggio).

# Regola per la Generazione di File Ottimizzati per Figma (html.to.design)

Quando l'utente richiede o si evince la necessità di creare file per Figma (es. tramite il plugin `html.to.design`), l'agente DEVE generare file "Figma-Optimized" e supportare due modalità di design:

## 1. Regole per File Figma-Optimized
- **Single-File Architecture**: Tutto il codice (HTML, CSS, JS) deve risiedere in un unico file `.html` autonomo (es. `figma_export.html`).
- **Zero Dipendenze Esterne**: 
  - Non usare link a fogli di stile esterni o script esterni.
  - Non caricare font da web (es. Google Fonts). Utilizza solo font di sistema (es. `system-ui, -apple-system, sans-serif` oppure `monospace`).
- **Gestione Immagini e Media**:
  - Evitare i tag `<img>` o `background-image` che puntano a URL esterni.
  - Al loro posto, usa placeholder creati interamente in CSS (es. div colorati con bordi tratteggiati), SVG inline (codice `<svg>` diretto), oppure immagini convertite stringhe Base64 (`src="data:image/png;base64,..."`).
- **Strutture Nascoste**: Assicurati che elementi come modali o sottomenu siano presenti nel DOM, in modo che Figma li possa importare come layer/frame.

## 2. Le Due Modalità di Generazione UI (Modes)

### Modalità Wireframing
- **Obiettivo**: Focus sulla struttura (Information Architecture) e sulla User Experience, senza distrazioni visive.
- **Stile Visivo**: Rigorosamente bianco, nero e scala di grigi (`style.md`).

### Modalità Prototyping (High-Fidelity)
- **Obiettivo**: Mostrare il look and feel definitivo, pronto per essere presentato a stakeholder o per diventare un prototipo interattivo.
- **Stile Visivo**: Implementazione completa del Design System (`style_prototype.md`). Palette cromatiche, bottoni pill, ombre elevate, glassmorphism e immagini reali ad alta risoluzione.
