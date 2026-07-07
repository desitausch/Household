# Putzplan

Mobiles Dashboard für die Reinigungskraft: zeigt jede Woche die anstehenden
Aufgaben, die sich abhaken lassen. Die Haken setzen sich montags automatisch
zurück, die Aufgabenliste aktualisiert sich von selbst. Der Link zur Seite
wird einmalig per WhatsApp geteilt.

## Dateien

| Datei | Zweck |
|---|---|
| `index.html` | Die Dashboard-Seite (komplett eigenständig, keine Abhängigkeiten) |
| `tasks.json` | Die Aufgabenliste – **hier werden Aufgaben gepflegt** |
| `ANLEITUNG.md` | Anleitung zum Ändern der Aufgaben |

## Veröffentlichung

Der Workflow `.github/workflows/putzplan-pages.yml` veröffentlicht die
komplette Seite (Startseite + dieser Ordner) über GitHub Pages – automatisch
bei jedem Push auf `main`, der `index.html`, `putzplan/` oder den Workflow
ändert. Live-Adresse:

```
https://desitausch.github.io/Household/
```

Der Putzplan selbst liegt unter `…/Household/putzplan/`.

## Funktionsweise

- Erledigt-Haken werden im Browser des Handys gespeichert (localStorage),
  pro Kalenderwoche – dadurch wöchentlicher Neustart ohne Server.
- `tasks.json` wird beim Öffnen und danach alle 5 Minuten neu geladen.
- Zusatzaufgaben mit `"woche": "JJJJ-WNN"` erscheinen nur in dieser
  Kalenderwoche; ohne Wochenangabe bleiben sie, bis sie gelöscht werden.
