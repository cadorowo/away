# Design Spec: Vetrina Minigiochi ed Esperienze sul Sito Web

## Obiettivo
Integrare una sezione dedicata ("Vetrina") all'interno della pagina `app.html` del sito web, con lo scopo di illustrare all'utente l'esistenza e il funzionamento delle esperienze virtuali e dei minigiochi offerti dalla Companion App di AWAY. La sezione si focalizzerà esclusivamente sull'aspetto dimostrativo (vetrina).

## 1. Struttura e Layout (Split 50/50)
La nuova sezione sarà posizionata in `wireframing/sito/app.html`, subito dopo la griglia `#app-features`. Il layout seguirà un approccio affiancato:
*   **Titolo Sezione:** Centrale, di grande impatto (es. "Oltre la Partita: Impara e Gioca").
*   **Contenitore Flex:** Un `div` con `display: flex; gap: 3rem; flex-wrap: wrap; justify-content: center;`.
*   **Blocchi:** Due contenitori di pari larghezza (es. `flex: 1; min-width: 300px;`) che si dispongono uno di fianco all'altro su desktop, e si impilano verticalmente su schermi piccoli (mobile).

## 2. Contenuto dei Blocchi

### 2.1 Blocco Sinistro: "Scopri il Mondo" (Curiosità)
*   **Mockup Visivo:** Un rettangolo verticale (simulazione smartphone) con sfondo grigio (`var(--gray-color)`). All'interno, un box testuale che simula un "Pop-up Curiosità" durante la partita:
    *   Testo simulato: *"💡 Fun Fact Islandese: Sapevi che..."*
*   **Contenuto Testuale (Sotto o a fianco del mockup):** 
    *   Titolo: "Scopri il Mondo" (o simile).
    *   Descrizione: L'app arricchisce l'esperienza sul campo offrendo trivia, fun fact geografici e curiosità sincronizzate con la mappa immersiva in cui si sta giocando.

### 2.2 Blocco Destro: "Allenamento e Minigiochi" (Azione)
*   **Mockup Visivo:** Un rettangolo verticale (simulazione smartphone) con un grande bottone CTA (es. "START TARGET") e un punteggio "Record: 1200".
*   **Contenuto Testuale:** 
    *   Titolo: "Sfida i Minigiochi".
    *   Descrizione: Il campo si trasforma in un videogioco gigante. I giocatori possono usare l'app per avviare minigiochi di precisione (Target) o riflessi (Speed) basati sulle proiezioni interattive, competendo nelle classifiche locali.

## 3. Conformità al Design System
*   **Grayscale:** Tutto rigorosamente in bianco e nero/grigio.
*   **Tipografia:** I placeholder grafici (mockup) useranno testo e font di default per mantenere il look "wireframe". La "X" (se usata) sarà in `monospace`.
*   **Componenti:** Verranno riutilizzate le classi CSS e le variabili CSS già presenti in `app.html` (es. `var(--border-color)`, `var(--bg-color)`).

## 4. Ambito di Implementazione
Le uniche modifiche richieste riguarderanno il file `/wireframing/sito/app.html`. Nessun nuovo file verrà creato. Non vi saranno logiche JavaScript complesse da implementare, trattandosi di wireframe statico.
