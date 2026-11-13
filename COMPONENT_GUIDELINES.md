---
title: "Komponentenrichtlinien"
schema_version: "1.0"
version: "0.1.0"
last_updated: "2026-11-13T18:34:46Z"
tier: 3
ai_usage: "allowed"
status: "draft"
---

# Komponentenrichtlinien

## Vertrag je Komponente

Zweck, semantische Rolle, Eingaben, Ereignisse, Zustände, Tastaturverhalten und Tokenabhängigkeiten dokumentieren. Plattformnative Semantik vor nachgebauten Interaktionsmustern bevorzugen.

## Zustände

Normal, Hover, Fokus, Aktiv, Ausgewählt, Deaktiviert, Laden, Leer und Fehler berücksichtigen, soweit zutreffend. Zustände dürfen nicht nur farblich erkennbar sein. Fehler verständlich und assistiven Technologien zugänglich melden.

## Theme-Neutralität

- Semantische Farb-, Typografie-, Abstands-, Radius- und Bewegungstokens verwenden.
- Keine Prüfungen wie „wenn ER Neon“ im Komponentenverhalten.
- Keine fest eingebauten Light-/Dark-Farben.
- Theme- und Moduswechsel dürfen Eingaben, Navigation und Fokus nicht zurücksetzen.
- Effekte müssen bei deaktivierter Transparenz oder Bewegung weiter verständlich bleiben.

## Barrierefreiheit

Zugängliche Namen, konsistente Fokusreihenfolge und programmatisch erkennbare Zustände vorsehen. Dialoge, Menüs und andere komplexe Muster gemäß den Konventionen der Zielplattform implementieren. Labels und Fehlermeldungen nicht durch Platzhaltertexte ersetzen.

## Prüfmatrix

Jede relevante Komponente in allen freigegebenen Theme-/Modus-Kombinationen und Zuständen prüfen. Tastatur, Screenreader, Zoom, lange Inhalte, reduzierte Bewegung und Systemfarben einbeziehen. Grenzwerte aus den [Designprinzipien](DESIGN_PRINCIPLES.md) messen; Ergebnisse im Produktrepository festhalten.
