# PROMPT — Genera Wireframe App Gestionale Staff Away Digital

## CONTESTO

Stai lavorando al progetto **Away Digital** — una piattaforma per campi da padel con esperienze sensoriali immersive ("viaggi" tematici come Hawaii, Tokyo ecc.). Devi creare i wireframe per l'**app gestionale usata dallo staff** (reception/back-office).

I file vanno salvati nella cartella:
```
/Users/cadowo/Library/Mobile Documents/com~apple~CloudDocs/Documents/projects/vibes/away digital/wireframing/app_segreteria/
```

## STRUTTURA FILE

Devi creare **11 file** totali:

### 10 file HTML separati (una pagina ciascuno)
Ogni file è un singolo file `.html` autonomo, navigabile nel browser, con tutto il CSS inline nel `<style>`. Ogni pagina simula il layout dashboard completo (sidebar + area principale) dentro un `#app-frame` centrato di 1440×900px.

1. `dashboard.html` — Dashboard (Home)
2. `prenotazioni.html` — Prenotazioni (Vista Giornaliera)
3. `prenotazioni-modale.html` — Prenotazioni con Modale Crea Prenotazione
4. `campi.html` — Campi (Stato Live)
5. `destinazioni.html` — Destinazioni (Catalogo)
6. `destinazioni-modale.html` — Destinazioni con Modale Richiedi Nuova
7. `eventi.html` — Eventi Speciali
8. `clienti.html` — Clienti (Lista + Dettaglio)
9. `codici-promo.html` — Codici Promozionali
10. `report.html` — Report e Statistiche

### 1 file Figma export (raccoglie tutti i frame)
`figma_export_segreteria.html` — Canvas scuro con tutti e 10 i frame visibili uno sotto l'altro, ottimizzato per il plugin html.to.design. Questo file **duplica** il contenuto dei 10 file singoli dentro i `.figma-frame` container.

---

## DIRETTIVE STILISTICHE OBBLIGATORIE

Queste regole sono **INVIOLABILI** e hanno la precedenza su qualsiasi altra istruzione:

### Regola 1: Modalità Wireframing
- **Rigorosamente bianco, nero e scala di grigi.** Nessun colore.
- Bordi netti e visibili, esclusivamente `solid`. **MAI `dashed` o `dotted`.**
- Nessuna ombra complessa (`box-shadow`), niente gradienti, niente colori di brand.
- Tipografia monospace (`"Courier New", Courier, monospace`) per il body text, `system-ui, -apple-system, sans-serif` per i titoli display.

### Regola 2: Placeholder
- Per le immagini, usare **rettangoli con sfondo grigio `#F0F0F0`** e una grande **"X"** al centro in `Courier New` / monospace.
- **Niente emoji** per immagini, mappe, icone o player.
- Le icone devono essere **SVG inline** disegnate con `stroke`, non emoji né font icon.

### Regola 3: File Figma-Optimized
- **Single-File Architecture:** Tutto (HTML, CSS) in un unico file `.html` autonomo.
- **Zero Dipendenze Esterne:** Nessun link a fogli di stile esterni, nessun script esterno, nessun Google Font. Solo font di sistema.
- **Nessun `<img>` o `background-image` con URL esterni.** Solo SVG inline o placeholder CSS.
- **Strutture nascoste (modali):** Devono essere presenti nel DOM (non hidden via JS), visibili come layer separati per Figma.

### Regola 4: Bordi e Divider
- Le linee di divisione delle sezioni (`border-bottom`) vanno a **tutta larghezza** del frame.
- Il contenuto è limitato in larghezza tramite wrapper interni con padding.

### Regola 5: Allineamenti
- I bottoni e gli elementi in colonna/riga devono sempre allinearsi in modo **orizzontale uniforme**.
- Usare `display: flex` con `align-items` e `gap` per garantire coerenza.

---

## DESIGN SYSTEM CSS

Usa queste variabili CSS come base. Sono le stesse usate nel progetto app mobile:

```css
:root {
    --bg-color: #FFFFFF;
    --text-color: #000000;
    --secondary-color: #FFFFFF;
    --border-color: #000000;
    --font-main: "Courier New", Courier, monospace;
    --font-display: system-ui, -apple-system, sans-serif;
}
```

### Componenti CSS da usare:

**Bottone primario (nero):**
```css
.btn {
    display: flex;
    padding: 0.75rem 1.5rem;
    background-color: var(--text-color);
    color: var(--bg-color);
    font-weight: bold;
    border: 1px solid var(--text-color);
    cursor: pointer;
    font-family: var(--font-main);
    text-transform: uppercase;
    letter-spacing: 0.05em;
    font-size: 0.8rem;
    justify-content: center;
    align-items: center;
    gap: 0.5rem;
}
```

**Bottone secondario (outline):**
```css
.btn-secondary {
    display: flex;
    padding: 0.75rem 1.5rem;
    background-color: var(--bg-color);
    color: var(--text-color);
    font-weight: bold;
    border: 1px solid var(--border-color);
    cursor: pointer;
    font-family: var(--font-main);
    text-transform: uppercase;
    letter-spacing: 0.05em;
    font-size: 0.8rem;
    justify-content: center;
    align-items: center;
}
```

**Placeholder immagine:**
```css
.placeholder-media {
    width: 100%;
    height: 180px;
    border: 2px solid var(--border-color);
    background-color: #F0F0F0;
    display: flex;
    align-items: center;
    justify-content: center;
}
.placeholder-x {
    font-family: var(--font-main);
    font-size: 3rem;
    font-weight: bold;
    opacity: 0.5;
    color: var(--text-color);
}
```

**Titoli:**
```css
h1, h2, h3, h4 {
    font-family: var(--font-display);
    font-weight: 900;
    text-transform: uppercase;
    letter-spacing: -0.03em;
    margin-bottom: 0.75rem;
    color: var(--text-color);
}
```

**Input:**
```css
input, select, textarea {
    width: 100%;
    padding: 0.8rem;
    font-family: var(--font-main);
    font-size: 0.85rem;
    border: 1px solid var(--border-color);
    margin-bottom: 0.75rem;
    background-color: var(--bg-color);
    outline: none;
}
```

**Badge stato (nero su bianco / bianco su nero):**
```css
.badge {
    display: inline-block;
    padding: 0.2rem 0.6rem;
    font-size: 0.65rem;
    font-weight: bold;
    text-transform: uppercase;
    font-family: var(--font-main);
    letter-spacing: 0.05em;
}
.badge-dark { background-color: var(--text-color); color: var(--bg-color); }
.badge-light { background-color: var(--bg-color); color: var(--text-color); border: 1px solid var(--border-color); }
```

---

## STRUTTURA DEI FILE SINGOLI

Ogni file HTML singolo (es. `dashboard.html`) ha questa struttura:

```html
body {
    background-color: #E0E0E0;
    display: flex;
    justify-content: center;
    align-items: center;
    min-height: 100vh;
}
#app-frame {
    width: 1440px;
    height: 900px;
    background-color: var(--bg-color);
    border: 2px solid var(--border-color);
    overflow: hidden;
    display: flex;
}
```

La sidebar è un componente che deve essere **identico** in tutti i 10 file, con solo la voce attiva che cambia.

---

## STRUTTURA DEL FILE FIGMA EXPORT

Il file `figma_export_segreteria.html` è un **canvas Figma-like** che mostra tutti i frame su sfondo scuro:

```css
body {
    background-color: #1A1A1A;
    color: #FFFFFF;
    padding: 4rem 2rem;
}
```

- **Titolo canvas:** "AWAY — APP GESTIONALE STAFF" in magenta `#FF00FF`
- **Sottotitolo:** "Wireframe Export — 10 Frame — Figma Optimized"
- **Griglia frame:** `display: flex; flex-wrap: wrap; gap: 4rem; justify-content: center;`
- Ogni frame è racchiuso in un container con:
  - **Titolo frame** in magenta (es. "1. Dashboard")
  - **Frame** di dimensione **1440×900px**, bordo `4px solid #FF00FF`, sfondo bianco, `overflow: hidden`
- Il contenuto di ogni frame è **lo stesso** dei file singoli, copiato dentro il `.figma-frame`

---

## LAYOUT COMUNE DI OGNI FRAME

Ogni frame ha il layout seguente:

```
┌──────────────────────────────────────────────────┐
│ SIDEBAR (220px)  │  AREA PRINCIPALE (1220px)     │
│                  │                                │
│ ┌──────────────┐ │ ┌────────────────────────────┐ │
│ │ LOGO "AWAY"  │ │ │ HEADER: Titolo + Azioni    │ │
│ ├──────────────┤ │ ├────────────────────────────┤ │
│ │ Dashboard    │ │ │                            │ │
│ │ Prenotazioni │ │ │   CONTENUTO PAGINA         │ │
│ │ Campi        │ │ │                            │ │
│ │ Destinazioni │ │ │                            │ │
│ │ Eventi       │ │ │                            │ │
│ │ Clienti      │ │ │                            │ │
│ │ Codici Promo │ │ │                            │ │
│ │ Report       │ │ │                            │ │
│ └──────────────┘ │ └────────────────────────────┘ │
└──────────────────────────────────────────────────┘
```

**Sidebar:**
- Larghezza: 220px, sfondo bianco, bordo destro `1px solid var(--border-color)`
- Logo "AWAY" in alto: `font-family: var(--font-display); font-weight: 900; font-size: 1.5rem; text-transform: uppercase;`
- 8 voci di navigazione, ciascuna con:
  - Icona SVG inline (24×24px, stroke) a sinistra
  - Label testuale a destra
  - Voce attiva: `border-left: 3px solid var(--text-color); background-color: #F0F0F0; font-weight: bold;`
  - Voci inattive: `border-left: 3px solid transparent;`

**Icone SVG per la sidebar** (usa queste esatte):
- Dashboard: casa (`M3 9l9-7 9 7v11a2 2 0 0 1-2 2H5a2 2 0 0 1-2-2z`)
- Prenotazioni: calendario (`rect x=3 y=4 w=18 h=18` + linee)
- Campi: layout/grid (`rect` multipli)
- Destinazioni: bussola (`circle cx=12 cy=12 r=10` + `polygon`)
- Eventi: stella (`polygon points="12 2 15.09 8.26 22 9.27..."`)
- Clienti: utenti (`path M17 21v-2a4 4 0 0 0-4-4H5...` + circles)
- Codici Promo: tag/ticket (`path + polyline`)
- Report: bar chart (`line + rect` multipli)

---

## I 10 FRAME DA CREARE

### Frame 1 — Dashboard (Home)
Sidebar: voce "Dashboard" attiva.

Layout a 2 colonne (70% / 30%):

**Colonna sinistra:**
- Titolo sezione: "Stato Campi"
- 3 card affiancate (una per campo), ciascuna con:
  - Header: "CAMPO 1" / "CAMPO 2" / "CAMPO 3" (h4, uppercase)
  - Badge stato: "OCCUPATO" (badge-dark) o "LIBERO" (badge-light)
  - Riga: "Hawaii Tropical Vibes" (testo piccolo)
  - Riga: "Si libera tra 12 min" o "Prossimo: 18:00 — Mario R." (testo piccolo, opacity 0.7)
  - Bottone piccolo: "Sblocca Porta" (btn, width auto)
- Bordo `1px solid var(--border-color)` su ogni card, padding `1rem`

**Colonna destra:**
- Sezione "Prossime Prenotazioni":
  - 5 righe lista, ogni riga: "18:00 — Mario R. — Campo 3 — Hawaii"
  - Bordo bottom `1px solid var(--border-color)` tra le righe
- Sezione "Attività Recenti":
  - 4-5 righe feed: "14:32 — Campo 2 sbloccato manualmente"
  - Testo piccolo (0.75rem), opacity 0.7 sul timestamp

---

### Frame 2 — Prenotazioni (Vista Giornaliera)
Sidebar: voce "Prenotazioni" attiva.

- Header: Titolo "Prenotazioni" + navigazione data (← "Lun 14 Luglio 2026" →) + toggle "Giorno | Settimana" + bottone "+ Nuova Prenotazione"
- Griglia tabellare:
  - Prima colonna: fasce orarie (09:00, 10:30, 12:00, 13:30, 15:00, 16:30, 18:00, 19:30, 21:00)
  - Colonne successive: Campo 1 | Campo 2 | Campo 3
  - Celle occupate: sfondo `#F0F0F0`, testo "Mario R. — Hawaii"
  - Celle libere: sfondo bianco, testo "Disponibile" in opacity 0.4
  - Cella in corso: sfondo nero `var(--text-color)`, testo bianco `var(--bg-color)`
  - Tutte le celle: bordo `1px solid var(--border-color)`, padding `0.75rem`

---

### Frame 3 — Modale Crea Prenotazione
Sfondo: riprodurre Frame 2 con opacity 0.3.

Modale centrato (larghezza ~500px):
- Bordo `2px solid var(--border-color)`, sfondo bianco, padding `2rem`
- Titolo: "Nuova Prenotazione Manuale" (h3)
- Campi form: Cliente (input text), Seleziona Campo (input/select), Destinazione (input/select), Data (input), Fascia Oraria (input/select)
- 2 bottoni in riga: "Conferma Prenotazione" (btn) + "Annulla" (btn-secondary)

---

### Frame 4 — Campi (Stato Live)
Sidebar: voce "Campi" attiva.

3 card grandi in riga orizzontale (ciascuna ~33%):
- Header grande: "CAMPO 1" (h3) + badge stato
- Sezione "Destinazione Attiva": nome + placeholder immagine piccolo (100px altezza)
- Sezione "Prenotazione Attuale": nome cliente, "Inizio: 16:30 — Fine: 18:00", barra progresso (div con width percentuale, sfondo nero, altezza 6px)
- Sezione "Prossima Prenotazione": "18:00 — Mario R."
- Barra Azioni: 3 bottoni affiancati: "Sblocca Porta" (btn) + "Manutenzione" (btn-secondary) + "Cambia Destinazione" (btn-secondary)

---

### Frame 5 — Destinazioni (Catalogo)
Sidebar: voce "Destinazioni" attiva.

- Header: "Destinazioni" + bottone "+ Richiedi Nuova Destinazione"
- Griglia 3 colonne di card:
  - Placeholder immagine (rettangolo grigio `#F0F0F0` con "X", altezza 140px)
  - Nome: "Hawaii — Tropical Vibes" (h4)
  - Descrizione: 1-2 righe testo piccolo
  - Badge: "ATTIVA" (badge-dark) o "DISATTIVATA" (badge-light)
  - Riga stat: "127 partite giocate" (piccolo, opacity 0.7)
  - 2 bottoni piccoli in riga: "Disattiva" (btn-secondary) + "Modifica" (btn-secondary)
- Mostrare 6 card (2 righe × 3 colonne): Hawaii, Tokyo, Islanda, Sahara, Amazzonia, Santorini

---

### Frame 6 — Modale Richiedi Nuova Destinazione
Sfondo: riprodurre Frame 5 con opacity 0.3.

Modale centrato (~500px):
- Titolo: "Richiedi Nuova Destinazione" (h3)
- Campi: Nome proposto (input), Descrizione esperienza (textarea, altezza 100px), Motivazione (textarea, altezza 80px)
- 2 bottoni: "Invia Richiesta" (btn) + "Annulla" (btn-secondary)

---

### Frame 7 — Eventi Speciali
Sidebar: voce "Eventi" attiva.

Layout 2 sezioni verticali:

**Sezione superiore:**
- Header: "Eventi Speciali" + bottone "+ Crea Evento"
- Tabella:
  - Colonne: Nome | Data | Orario | Campi | Stato | Azioni
  - 3 righe esempio:
    1. "Notte Tropicale" | 20 Lug | 20:00–23:00 | Campo 1, 2 | PUBBLICATO (badge-dark) | "Modifica"
    2. "Aperitivo & Padel" | 25 Lug | 19:00–22:00 | Tutti | BOZZA (badge-light) | "Modifica"
    3. "Torneo Estivo" | 10 Lug | 15:00–21:00 | Tutti | CONCLUSO (badge-light, opacity 0.5) | "Vedi"

**Sezione inferiore (form):**
- Titolo: "Crea Nuovo Evento" (h3)
- 2 colonne di campi:
  - Sinistra: Nome (input), Descrizione (textarea), Data (input), Orario Inizio (input), Orario Fine (input)
  - Destra: Campi da riservare (3 checkbox: Campo 1 / 2 / 3), Prezzo (input, es. "€ 25,00"), Capacità Max (input, es. "20")
- 2 bottoni: "Pubblica Evento" (btn) + "Salva Bozza" (btn-secondary)

---

### Frame 8 — Clienti
Sidebar: voce "Clienti" attiva.

Layout master-detail (60% / 40%):

**Pannello sinistro:**
- Header: "Clienti" + barra ricerca (input con placeholder "Cerca cliente...")
- Tabella:
  - Colonne: Nome | Email | Partite | Ultima Visita | Timbri
  - 7 righe dati esempio
  - Riga selezionata (#3): sfondo `#F0F0F0`

**Pannello destro (dettaglio del cliente selezionato):**
- Nome grande (h3): "MARCO BIANCHI"
- Email: "marco.bianchi@email.com"
- Sezione "Bacheca Digitale": griglia 3×2 di cerchi (placeholder timbri, bordo solid, sfondo `#F0F0F0`, 50×50px) — 4 con "X" (timbrati), 2 vuoti
- Sezione "Ultime Partite": 3 righe (es. "12 Lug — Hawaii — Campo 3")
- Sezione "Codici Utilizzati": 2 righe (es. "AWAY-HAWAII-123 — Riscattato il 10 Lug")

---

### Frame 9 — Codici Promo
Sidebar: voce "Codici Promo" attiva.

- Header: "Codici Promozionali" + bottone "+ Crea Codice"
- Filtri: 4 bottoni pill in riga: "Tutti" (attivo, sfondo nero, testo bianco) | "Attivi" | "Utilizzati" | "Scaduti"
- Tabella:
  - Colonne: Codice | Tipo | Destinazione | Stato | Creato | Scadenza
  - 6 righe esempio con badge stato: ATTIVO (badge-dark), UTILIZZATO (badge-light), SCADUTO (badge-light, opacity 0.5)
- Form "Crea Codice" (sotto la tabella, separato da border-top):
  - 2 colonne:
    - Sinistra: Tipo (select), Valore (input, es. "15%"), Destinazione (select)
    - Destra: Scadenza (input date), Uso (2 radio: Singolo / Multiplo), Quantità (input, es. "10")
  - Bottone: "Genera Codici" (btn)

---

### Frame 10 — Report
Sidebar: voce "Report" attiva.

Layout 3 livelli:

**Livello 1 (top) — KPI:**
- 4 card affiancate, ciascuna con:
  - Label piccola (0.7rem, opacity 0.7): "INCASSO OGGI" / "INCASSO MESE" / "OCCUPAZIONE" / "PARTITE MESE"
  - Valore grande (h2): "€ 1.260" / "€ 18.740" / "72%" / "134"
  - Bordo `1px solid var(--border-color)`, padding `1.5rem`

**Livello 2 (centro) — Grafici:**
- 2 placeholder grafici affiancati (50%/50%):
  - Sinistra: placeholder rettangolare (altezza 200px, sfondo `#F0F0F0`, "X" al centro) con titolo sopra "Occupazione per Fascia Oraria"
  - Destra: stesso placeholder con titolo "Andamento Incassi Settimanale"

**Livello 3 (bottom) — Classifica + Filtri:**
- Colonna sinistra: tabella ranking (1. Hawaii — 47 partite, 2. Tokyo — 38, 3. Islanda — 29, ecc.)
- Colonna destra: filtri (3 select: Periodo / Campo / Destinazione) + bottone "Applica Filtri"

---

## CHECKLIST FINALE

Prima di consegnare, verifica:

### File singoli (×10)
- [ ] 10 file `.html` separati nella cartella `app_segreteria/`, ciascuno autonomo
- [ ] Ogni file ha tutto il CSS inline nel `<style>`, nessuna dipendenza esterna
- [ ] Ogni file mostra il layout completo (sidebar + area principale) dentro un frame 1440×900px
- [ ] La sidebar è identica in tutti i file, con la voce attiva corretta per ogni pagina
- [ ] I file modali (`prenotazioni-modale.html`, `destinazioni-modale.html`) mostrano la modale sovrapposta al contenuto sottostante con sfondo semitrasparente

### File Figma export (×1)
- [ ] `figma_export_segreteria.html` contiene tutti e 10 i frame
- [ ] Canvas scuro `#1A1A1A` con titoli magenta `#FF00FF`
- [ ] Ogni frame è 1440×900px con bordo `4px solid #FF00FF`

### Stile (tutti i file)
- [ ] Colori solo bianco `#FFFFFF`, nero `#000000`, grigio `#F0F0F0` all'interno dei frame
- [ ] Font: `Courier New` (body) e `system-ui` (display/titoli) — nessun Google Font
- [ ] Bordi **esclusivamente `solid`**, mai `dashed` o `dotted`
- [ ] Placeholder immagini: rettangoli grigio `#F0F0F0` con "X" grande in Courier New
- [ ] Nessuna emoji per icone — solo SVG inline con `stroke`
- [ ] Tutti i dati esempio sono in italiano e coerenti con il contesto Away Digital
