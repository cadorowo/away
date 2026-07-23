# Away App - Home Page Redesign (Wireframe)

## Obiettivo
Riorganizzare l'architettura dei contenuti della Home page (`home.html`) per renderla più personale, focalizzata sulla gamification e capace di ispirare l'utente attraverso suggerimenti mirati, rispettando le regole visive del wireframe (scala di grigi, nessun border-radius, placeholder standard).

## Flusso dei Contenuti (Dall'alto verso il basso)

### 1. Header App
- Rimane invariato (Logo a sinistra, icona notifiche a destra).
- Switcher di simulazione "Partita Attiva" rimane presente per scopi di prototipazione.

### 2. Benvenuto Personale [NUOVA SEZIONE]
- **Elementi visivi**: Placeholder per foto profilo (quadrato/cerchio wireframe).
- **Testo principale**: Saluto personalizzato (es. "Bentornato, [Nome]").
- **Stato Prossima Partita**: 
  - Se è in programma: Mostra solo *Destinazione* e *Data/Ora* (es. "Prossima tappa: Islanda - 12 Nov, 18:30").
  - Se vuoto: Messaggio di call-to-action (es. "Nessun viaggio in vista. Pianifica la tua prossima fuga.").

### 3. Progressi e Gamification [NUOVA SEZIONE]
- **Scopo**: Rendere tangibile l'avanzamento dell'utente prima ancora di mostrargli lo shop/catalogo.
- **Elementi visivi**: Contatore in evidenza dei "Punti Passaporto" accumulati (es. "450 Punti") e possibilmente un'icona wireframe dell'ultimo trofeo o dello status corrente.

### 4. Ispirazione Personalizzata (Consigliato per te) [NUOVA SEZIONE]
- **Scopo**: Suggerire una destinazione facendo leva sulla leva del collezionismo.
- **Contenuto**: Una singola card destinazione in grande evidenza.
- **Copywriting**: Orientato al completamento (es. "Esplora il Perù per completare il set di trofei e guadagnare il badge misterioso").
- **Azione**: Pulsante per visualizzare il dettaglio di quel viaggio specifico.

### 5. Catalogo Destinazioni (Carosello)
- **Scopo**: Esplorazione generale.
- **Layout**: Carosello orizzontale (stile attuale) contenente le altre destinazioni (es. Hawaii, Marocco, Islanda se non consigliata sopra).
- **Titolo**: "Scegli il tuo viaggio" o "Altre destinazioni".

### 6. Eventi della Community
- **Posizionamento**: Subito sotto le destinazioni.
- **Contenuto**: Eventi speciali (Tornei, Masterclass) il cui sblocco è esplicitamente legato all'uso dei Punti Passaporto (mostrati nella sezione 3).

### 7. Utilities (Fondo pagina)
- **Scopo**: Pulire la navigazione principale relegando le azioni accessorie in fondo.
- **Contenuti**:
  - *Kit Sensoriali*: Carosello/Card per l'acquisto di kit offline.
  - *Riscatta Codice*: Form di testo per inserire un codice regalo.
- **Design**: Separati visivamente tramite bordi solidi come da stile wireframe.

## Regole di Stile & Constraint
- Il design deve essere implementato modificando l'attuale `home.html` (e possibilmente le versioni varianti se necessario).
- Tutto deve seguire rigidamente lo `style.md` (bianco, nero e grigio, nessun colore, box placeholder con "X" per immagini).
- Nessuna libreria esterna, tutto con HTML semantico e CSS vanilla all'interno del tag `<style>`.

## Passi successivi
Una volta approvata questa specifica, si procederà con il piano di implementazione (modifica di `home.html` per iniettare i nuovi blocchi e riordinare l'esistente).
