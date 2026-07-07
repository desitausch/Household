# Household

Projekte rund um unseren Haushalt – als kleine Web-Seite mit gemeinsamer
Navigationsleiste erreichbar.

## Projekte

| Projekt | Beschreibung |
|---|---|
| [`index.html`](index.html) | Startseite mit Navigation zu allen Projekten |
| [`putzplan/`](putzplan/) | Mobiles Dashboard für die Reinigungskraft: wöchentliche Aufgabenliste zum Abhaken, per Link teilbar. Siehe [`putzplan/README.md`](putzplan/README.md). |

## Struktur

- Jedes Projekt bekommt einen eigenen Ordner mit eigenem `README.md`.
- Neue Projekte werden auf der Startseite (`index.html`) und in der
  Nav-Bar verlinkt.
- Zugehörige GitHub-Actions-Workflows liegen in `.github/workflows/` und sind
  nach dem Projekt benannt (z.B. `putzplan-pages.yml` veröffentlicht die
  komplette Seite: Startseite + Putzplan).
