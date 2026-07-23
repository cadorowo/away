# App Gestionale Staff Away — Design Spec

**Data:** 2026-07-14
**Progetto:** Away Digital — Wireframing
**Formato:** Dashboard desktop/tablet landscape (16:9)
**Ruoli:** Unico, accesso completo per tutto lo staff
**Navigazione:** Sidebar fissa a sinistra
**Stile:** Wireframe grayscale (coerente con il resto del progetto)

---

## Overview

App gestionale per lo staff di Away Digital. Consente di gestire prenotazioni, campi, destinazioni, eventi, clienti, codici promo e consultare report statistici. Interfaccia a dashboard con sidebar di navigazione, pensata per postazione reception/back-office.

---

## Sidebar di Navigazione

| Voce | Descrizione |
|---|---|
| **Dashboard** | Vista operativa d'insieme (home) |
| **Prenotazioni** | Calendario giornaliero/settimanale |
| **Campi** | Stato live + blocco/sblocco + accesso manuale porta |
| **Destinazioni** | Catalogo viaggi + richiesta nuove esperienze |
| **Eventi** | Creazione e gestione eventi speciali |
| **Clienti** | Anagrafica + storico partite |
| **Codici Promo** | Creazione e gestione voucher |
| **Report** | Incassi, occupazione, statistiche |

---

## 1. Dashboard (Home)

La schermata principale. Layout a colonne:

### Colonna sinistra (2/3)
- **Stato Campi Live** — 3 card affiancate (una per campo):
  - Stato: Libero / Occupato / Manutenzione
  - Destinazione attiva (es. "Hawaii Tropical Vibes")
  - Timer: "Si libera tra 12 min" oppure "Prossimo: 18:00 — Mario R."
  - Bottone rapido: "Sblocca Porta" (bypass emergenza)

### Colonna destra (1/3)
- **Prossime Prenotazioni** — Lista delle prossime 5-6 prenotazioni (nome, orario, campo, destinazione)
- **Notifiche / Attività Recenti** — Feed eventi (es. "Campo 2 sbloccato manualmente", "Nuova prenotazione", "Codice riscattato")

---

## 2. Prenotazioni (Calendario)

- **Vista Griglia Oraria** — Asse X = campi (1, 2, 3), Asse Y = fasce orarie (slot 90 min)
- Ogni cella: nome cliente, destinazione, stato (confermata/in corso/completata)
- **Toggle vista:** Giornaliera / Settimanale
- **Azione rapida:** Click su slot vuoto → crea prenotazione manuale (modale)
- **Filtri:** Per campo, per destinazione, per stato

---

## 3. Campi

Gestione operativa in tempo reale dei 3 campi:

- **Card per ogni campo:**
  - Stato live (Libero / Occupato / Manutenzione)
  - Destinazione caricata
  - Prenotazione attuale (cliente, orario inizio/fine)
  - Prossima prenotazione
  - **Azioni:** Sblocca Porta, Blocca Campo (manutenzione), Cambia Destinazione

---

## 4. Destinazioni

- **Catalogo** — Griglia card: placeholder immagine, nome, descrizione, stato (Attiva/Disattivata)
- **Azioni per destinazione:** Attiva/Disattiva, Modifica descrizione, Statistiche d'uso
- **Bottone "Richiedi Nuova Destinazione"** — Form modale: nome proposto, descrizione esperienza, motivazione

---

## 5. Eventi Speciali

- **Lista Eventi** — Tabella: nome, data, orario, campi, stato (Bozza/Pubblicato/Concluso)
- **Bottone "Crea Evento"** — Form:
  - Nome evento (es. "Notte Tropicale")
  - Descrizione
  - Data e fascia oraria (estendibile oltre 90 min)
  - Campi da riservare (1, 2 o tutti)
  - Prezzo speciale
  - Capacità massima partecipanti
- Gli slot occupati dall'evento si bloccano automaticamente nel calendario

---

## 6. Clienti

- **Tabella Anagrafica** — Nome, email, n° partite, ultima visita, timbri bacheca
- **Dettaglio cliente** (click su riga):
  - Storico prenotazioni
  - Bacheca Digitale (timbri, lato staff)
  - Codici promo utilizzati

---

## 7. Codici Promo

- **Lista Codici** — Tabella: codice, tipo, destinazione, stato (Attivo/Utilizzato/Scaduto), date
- **Bottone "Crea Codice"** — Form:
  - Tipo: Sconto % / Sconto fisso / Partita gratuita
  - Destinazione (specifica o qualsiasi)
  - Scadenza
  - Uso singolo o multiplo
  - Quantità da generare

---

## 8. Report

- **KPI Cards** — Incasso giornaliero, Incasso mensile, Tasso occupazione, Partite totali mese
- **Grafici:**
  - Occupazione per fascia oraria
  - Destinazioni più gettonate (classifica)
  - Andamento incassi settimanale/mensile
- **Filtri:** Per periodo, per campo, per destinazione

---

## Schermate da Wireframare

1. Dashboard (home)
2. Prenotazioni — Vista giornaliera
3. Prenotazioni — Modale crea prenotazione manuale
4. Campi — Stato live
5. Destinazioni — Catalogo
6. Destinazioni — Modale richiedi nuova
7. Eventi — Lista + Crea evento
8. Clienti — Lista + Dettaglio cliente
9. Codici Promo — Lista + Crea codice
10. Report — Dashboard statistiche

**Totale: 10 schermate**

---

## Note Tecniche

- Stile wireframe: grayscale, Courier New, bordi solid, placeholder con "X"
- Zero dipendenze esterne: tutto inline
- Formato frame: 16:9 landscape (1440×900px)
- File output: `figma_export_segreteria.html` nella cartella `wireframing/app_segreteria/`
