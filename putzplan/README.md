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

- Oberfläche auf Englisch (Sprache der Reinigungskraft); Aufgabentexte in
  `tasks.json` daher ebenfalls auf Englisch.
- Erledigt-Haken: Ist in `tasks.json` eine `syncUrl` (Firebase Realtime
  Database) eingetragen, werden die Haken über alle Geräte geteilt – die
  Seite schreibt Änderungen per REST dorthin und fragt den Stand alle ~20
  Sekunden sowie beim Öffnen ab. Ohne `syncUrl` gelten die Haken nur lokal
  auf dem Gerät (localStorage).
- Wöchentlicher Neustart: Der Erledigt-Stand hängt an der Kalenderwoche und
  beginnt montags automatisch leer.
- `tasks.json` wird beim Öffnen und danach alle 5 Minuten neu geladen.
- Zusatzaufgaben mit `"woche": "JJJJ-WNN"` erscheinen nur in dieser
  Kalenderwoche; ohne Wochenangabe bleiben sie, bis sie gelöscht werden.
