# Putzplan-Dashboard – Kurzanleitung

## Was ist das?

Eine kleine Web-Seite (`index.html`), die der Reinigungskraft jede Woche ihre
Aufgaben anzeigt. Die Oberfläche ist **auf Englisch** (die Reinigungskraft
spricht Englisch); auch die Aufgabentexte in `tasks.json` sollten deshalb auf
Englisch sein. Abgehakte Aufgaben setzen sich **jeden Montag automatisch
zurück**.

Der Link zur Seite kann einmalig per WhatsApp geschickt werden – am besten
speichert sie ihn als Lesezeichen oder legt ihn über „Zum Startbildschirm
hinzufügen" wie eine App aufs Handy.

## Haken auf allen Geräten sichtbar (Sync)

Wenn in `tasks.json` bei `syncUrl` eine Firebase-Datenbank-Adresse eingetragen
ist, werden die Haken **zwischen allen Geräten geteilt**: Hakt die
Reinigungskraft etwas ab, sieht man das auf jedem anderen Handy, das die Seite
offen hat (Aktualisierung alle ~20 Sekunden und bei jedem Öffnen).

Ist `syncUrl` leer, gelten die Haken nur auf dem jeweiligen Gerät.

## Aufgaben ändern

Alle Aufgaben stehen in der Datei **`putzplan/tasks.json`** (auf Englisch).
Es gibt zwei Bereiche:

### 1. `woechentlich` – die festen Aufgaben (jede Woche gleich)

```json
{ "id": "w1", "text": "Vacuum and mop all floors" }
```

Einfach Zeilen hinzufügen, ändern oder löschen. Jede Aufgabe braucht eine
eindeutige `id` (z.B. `w7`, `w8`, …).

### 2. `zusatz` – punktuelle Extra-Aufgaben

Zwei Möglichkeiten:

```json
{ "id": "z5", "text": "Clean the oven inside", "woche": "2026-W29" }
```
→ wird **nur in dieser Kalenderwoche** angezeigt und verschwindet danach von selbst.

```json
{ "id": "z6", "text": "Clean the living room windows" }
```
→ ohne `woche` bleibt die Aufgabe stehen, bis sie aus der Datei gelöscht wird.

Wichtig: Jede `id` darf nur einmal vorkommen, sonst teilen sich zwei Aufgaben
einen Haken.

## Wie kommt eine Änderung aufs Handy?

Die Datei `putzplan/tasks.json` im Repository ändern (direkt auf GitHub im
Browser möglich: Datei öffnen → Stift-Symbol → speichern). Die Seite wird
danach automatisch neu veröffentlicht; die Handys laden die Aufgabenliste
spätestens alle 5 Minuten neu.

## Veröffentlichung

Der Workflow `.github/workflows/putzplan-pages.yml` baut die Seite bei jedem
Push auf `main` und legt sie auf den `gh-pages`-Branch; GitHub Pages liefert
sie unter https://desitausch.github.io/Household/ aus.
