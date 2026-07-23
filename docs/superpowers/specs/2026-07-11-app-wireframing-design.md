# Design Spec: AWAY x PalaVillage App (Wireframing)

## Obiettivo dell'App
Un'applicazione mobile nativa che funge da ponte tra l'e-commerce (dove gli utenti acquistano pacchetti ed esperienze) e la struttura fisica (PalaVillage). L'app ha un duplice scopo: permettere la prenotazione di partite immersive (approccio "Destination-First") e fungere da "Telecomando" e strumento di gioco durante la partita vera e propria.

## 1. Architettura dell'Informazione (Tab Bar)
L'app si sviluppa su 4 macro-aree principali accessibili dalla barra di navigazione inferiore:

1. **Home**: La dashboard dinamica centrale.
2. **Prenotazioni**: Gestione degli appuntamenti passati e futuri, e area di riscatto codici.
3. **Passaporto**: L'elemento di gamification. Mantenendo la metafora del "viaggio", qui l'utente colleziona i "timbri" delle destinazioni in cui ha giocato (es. un timbro per le Hawaii, uno per l'Islanda), sbloccando eventuali achievement.
4. **Profilo**: Statistiche del giocatore, preferenze account e gestione dei "Kit" digitali o fisici associati all'utente.

## 2. La Home Dinamica (Dashboard)
La Home cambia radicalmente interfaccia in base allo stato dell'utente.

### Stato A: Nessuna partita attiva (Discovery & Booking)
*   **Hero Section / Riscatta Codice**: In cima, un input box molto evidente: *"Hai acquistato un viaggio sul sito? Inserisci il codice qui"*.
*   **Catalogo Destinazioni**: Uno scorrimento visivo delle location immersive disponibili (es. Perù, Marocco). L'utente sceglie dove vuole "viaggiare", legge i dettagli dell'esperienza e avvia da lì il flusso di prenotazione.

### Stato B: Partita in corso (Il "Telecomando")
*   La UI si trasforma per supportare il gioco agonistico.
*   **Tabellone Segnapunti**: Interfaccia per aggiornare rapidamente il punteggio (sincronizzato con i proiettori in campo).
*   **Replay**: Pulsante per richiedere il salvataggio o la riproduzione dell'ultima azione (tramite le telecamere del campo).
*   **Quick Actions**: Bottoni per chiamare l'assistenza, ordinare acqua o palle nuove senza uscire dal campo.

## 3. Flusso di Prenotazione e Integrazione E-commerce
*   L'utente naviga la Home e seleziona una Destinazione.
*   Seleziona la data e l'orario tra quelli disponibili.
*   **Checkout nell'App**: Se l'utente ha inserito un codice valido (acquistato sul sito) in precedenza o in questo momento, il costo viene azzerato o scalato. In alternativa, può pagare direttamente tramite l'app.
*   A prenotazione conclusa, l'appuntameto finisce nel tab "Prenotazioni".

## 4. Linee Guida di Costruzione e Regole Tecniche
Per garantire che l'app sia coerente e facilmente importabile in Figma (tramite plugin come `html.to.design`), l'implementazione tecnica DEVE seguire rigorosamente queste direttive:

### 4.1. Conformità Obbligatoria a style.md
L'agente è **OBBLIGATO** a consultare e applicare ogni singola regola descritta in `.agents/style.md` e in `AGENTS.md`. In particolare:
*   **Stile Visivo:** Rigoroso uso di bianco, nero e scala di grigi (niente colori brand, niente ombre complesse).
*   **Tipografia:** Solo `monospace` (Courier New) e font di sistema (`system-ui`, `-apple-system`). Niente Google Fonts.
*   **Placeholder:** Qualsiasi immagine, video o mappa deve essere un contenitore colorato (in scala di grigio) con bordi netti e una grande "X" testuale ben centrata.
*   **Layout:** Le linee divisorie (dividers) tra sezioni devono espandersi a tutta larghezza.

### 4.2. Struttura dei File HTML
Tutto il wireframing dell'app verrà sviluppato all'interno della cartella `wireframing/app/`. 
*   **Zero Dipendenze:** Non ci saranno fogli di stile `.css` esterni o file `.js` separati. Ogni file HTML conterrà il proprio blocco `<style>` e `<script>` per essere 100% autonomo e non "rompersi" durante l'export in Figma.
*   **Mobile-First Frame:** Le interfacce saranno racchiuse in un "mobile frame" (es. `max-width: 430px; margin: 0 auto; min-height: 100vh; position: relative;`) per simulare accuratamente le proporzioni di uno smartphone sullo schermo del computer.
*   **Componenti Fissi:** La Tab Bar di navigazione principale (Home, Prenotazioni, Passaporto, Profilo) sarà ancorata in basso (`position: absolute; bottom: 0;` oppure `fixed` nel mobile frame).

## 5. Elenco delle Pagine da Sviluppare
L'implementazione prevederà la creazione dei seguenti file in `wireframing/app/`:
1. `home.html` (Discovery, riscatto codice e catalogo destinazioni)
2. `telecomando.html` (La vista speciale "Partita in corso" con segnapunti e azioni)
3. `prenotazioni.html` (Storico partite e dettaglio prenotazione)
4. `passaporto.html` (La vista gamification con i timbri delle destinazioni giocate)
5. `profilo.html` (Statistiche giocatore e impostazioni)
6. `figma_export_app.html` (Un mega-file opzionale che raccoglie tutte le schermate affiancate per un'importazione massiva in Figma, se richiesto).
