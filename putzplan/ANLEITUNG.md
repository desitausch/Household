# Putzplan-Dashboard – Kurzanleitung

## Was ist das?

Eine kleine Web-Seite (`index.html`), die der Reinigungskraft jede Woche ihre
Aufgaben anzeigt. Sie kann jede Aufgabe abhaken. Die Haken werden auf ihrem
Handy gespeichert und setzen sich **jeden Montag automatisch zurück**.

Der Link zur Seite kann einmalig per WhatsApp geschickt werden – am besten
speichert sie ihn als Lesezeichen oder legt ihn über „Zum Startbildschirm
hinzufügen" wie eine App aufs Handy.

## Aufgaben ändern

Alle Aufgaben stehen in der Datei **`putzplan/tasks.json`**. Es gibt zwei
Bereiche:

### 1. `woechentlich` – die festen Aufgaben (jede Woche gleich)

```json
{ "id": "w1", "text": "Böden saugen und wischen (alle Räume)" }
```

Einfach Zeilen hinzufügen, ändern oder löschen. Jede Aufgabe braucht eine
eindeutige `id` (z.B. `w7`, `w8`, …).

### 2. `zusatz` – punktuelle Extra-Aufgaben

Zwei Möglichkeiten:

```json
{ "id": "z5", "text": "Backofen innen reinigen", "woche": "2026-W29" }
```
→ wird **nur in dieser Kalenderwoche** angezeigt und verschwindet danach von selbst.

```json
{ "id": "z6", "text": "Fenster im Wohnzimmer putzen" }
```
→ ohne `woche` bleibt die Aufgabe stehen, bis sie aus der Datei gelöscht wird.

Wichtig: Jede `id` darf nur einmal vorkommen, sonst teilen sich zwei Aufgaben
einen Haken.

## Wie kommt eine Änderung aufs Handy?

Die Datei `putzplan/tasks.json` im Repository ändern (direkt auf GitHub im
Browser möglich: Datei öffnen → Stift-Symbol → speichern). Nach der
Veröffentlichung lädt die Seite die Aufgaben alle 5 Minuten neu und immer,
wenn sie geöffnet wird – die Reinigungskraft muss nichts tun.

## Veröffentlichung

Der Workflow `.github/workflows/putzplan-pages.yml` übernimmt die
Veröffentlichung über GitHub Pages automatisch. Aktuell ist er pausiert,
weil GitHub Pages für private Repos einen Bezahl-Plan voraussetzt – Details
und Status stehen in `putzplan/README.md`.
