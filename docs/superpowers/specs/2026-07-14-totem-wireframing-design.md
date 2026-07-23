# Totem Wireframing Design Spec

## Overview
This document outlines the UI flow and structural design for the Totem interface wireframes of the AWAY Digital project. The Totem is a physical kiosk situated at the location, allowing users to interact with their reservations, start their journey, and leave feedback.

## Visual Rules & Guidelines
- **Mode:** Wireframing (High focus on Information Architecture, minimal visual distractions).
- **Architecture:** Single-file HTML (`figma_export_totem.html`) for easy export to Figma via the `html.to.design` plugin. No external CSS/JS dependencies.
- **Typography:** Maison Neue (Light weight 300 by default), except for specific placeholders which use `monospace`.
- **Palette:** Grayscale (Black, White, Gray tones) with solid or dashed borders.
- **Placeholders:** Images are represented by dashed boxes containing a large `X` in `monospace` font.

## Screen Flow & Content

### 1. Standby / Espositore (Idle State)
When the Totem is inactive, it serves as a digital billboard.
- **Visual:** A large carousel of immersive images (simulated with standard placeholders).
- **Messaging:** "Scopri nuove dimensioni. Scarica l'app per prenotare il tuo prossimo viaggio."
- **Actions:** 
  - A prominent QR code to download the companion app.
  - An instruction area indicating where to scan an existing reservation QR code.

### 2. Riepilogo Viaggio (Check-in)
Triggered when a user successfully scans their booking QR code.
- **Visual:** Clean, action-oriented interface.
- **Data Points:** 
  - Nome Viaggiatore (e.g., "Benvenuto, [Nome]")
  - Nome Destinazione (e.g., "Tokyo Cyberpunk")
  - Durata del viaggio (e.g., "60 minuti")
- **Action:** A prominent, large button reading "Inizia il Viaggio".

### 3. Avvio Viaggio
A brief transitional screen displayed immediately after pressing "Inizia il Viaggio".
- **Visual:** Minimalist layout.
- **Messaging:** "Buon viaggio!".

### 4. Viaggio in Corso
The persistent state shown on the Totem outside the room while the experience is ongoing.
- **Visual:** High contrast, focus strictly on the remaining time.
- **Data Points:**
  - Giant Countdown Timer (e.g., `45:00`).
  - Current Destination Label (e.g., "In viaggio verso: Tokyo").
- **Action:** A static QR code at the bottom/side prompting bystanders to "Scarica l'app per scoprire altre dimensioni".

### 5. Fine Viaggio & Feedback
Triggered when the timer reaches zero.
- **Visual:** A welcoming conclusion screen.
- **Messaging:** "Bentornato!".
- **Action:** 
  - Immediate interactive 5-star touch widget allowing users to rate their experience directly on the Totem.
  - Follow-up call to action to continue the journey via the app.

## Implementation Details
The screens will be structured within a single HTML file under `wireframing/totem/figma_export_totem.html`. Each screen will be contained within a `.figma-frame` div, replicating the layout strategy used in the main site's wireframing file to ensure seamless Figma integration.
