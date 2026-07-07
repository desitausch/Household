# Putzplan-Dashboard – Kurzanleitung

## Was ist das?

Eine kleine Web-Seite (`index.html`), die der Reinigungskraft ihre Aufgaben
anzeigt. Die Oberfläche ist **auf Englisch** (die Reinigungskraft spricht
Englisch); auch die Aufgabentexte in `tasks.json` sollten deshalb auf
Englisch sein.

Der Link zur Seite kann einmalig per WhatsApp geschickt werden – am besten
speichert sie ihn als Lesezeichen oder legt ihn über „Zum Startbildschirm
hinzufügen" wie eine App aufs Handy.

## Die vier Aufgaben-Rhythmen

| Bereich in `tasks.json` | Anzeige | Haken setzen sich zurück |
|---|---|---|
| `everyVisit` | „Every visit" | **jeden Tag** (für 3 Besuche/Woche) |
| `weekly` | „Once a week" | jeden **Montag** |
| `biweekly` | „Every 2 weeks" | jeden **zweiten Montag** |
| `oneTime` | „One-time tasks" | **nie** – bleiben abgehakt, bis die Zeile gelöscht wird |

Eine Aufgabe sieht immer so aus (die `id` muss überall eindeutig sein):

```json
{ "id": "w6", "text": "Clean the bathtub" }
```

Zeilen einfach hinzufügen, ändern oder löschen – direkt auf GitHub im
Browser (Datei öffnen → Stift-Symbol → speichern). Die Seite wird danach
automatisch neu veröffentlicht; die Handys laden die Liste spätestens alle
5 Minuten neu.

Der Text in `hinweis` erscheint als grüne Info-Box oben auf der Seite
(z.B. allgemeine Erwartungen an die Reinigungskraft).

## Haken auf allen Geräten sichtbar (Sync)

Wenn bei `syncUrl` eine Firebase-Datenbank-Adresse eingetragen ist, werden
die Haken **zwischen allen Geräten geteilt**: Hakt die Reinigungskraft etwas
ab, sieht man das auf jedem anderen Handy (Aktualisierung alle ~20 Sekunden
und bei jedem Öffnen). Ist `syncUrl` leer, gelten Haken nur auf dem
jeweiligen Gerät.

## Veröffentlichung

Der Workflow `.github/workflows/putzplan-pages.yml` baut die Seite bei jedem
Push auf `main` und legt sie auf den `gh-pages`-Branch; GitHub Pages liefert
sie unter https://desitausch.github.io/Household/ aus.
