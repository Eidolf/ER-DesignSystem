---
title: "Designprinzipien"
schema_version: "1.0"
version: "0.1.0"
last_updated: "2026-11-13T18:34:46Z"
tier: 3
ai_usage: "allowed"
status: "draft"
---

# Designprinzipien

## Standards statt festem Erscheinungsbild

Gemeinsame Regeln sichern Verhalten, Semantik und Qualität. Farbe, Formensprache und visuelle Identität sind austauschbar. Kein Beispiel-Theme ist Voraussetzung für Produktkonformität.

## Leitlinien

1. **Theme-neutral:** Komponenten kennen semantische Tokens, keine Theme-Namen.
2. **Modi als Grundfunktion:** Theme Switching sowie Light und Dark Mode sind verpflichtend.
3. **Zugänglich:** WCAG 2.2 AA als Ziel, Tastaturbedienung und sichtbaren Fokus einplanen.
4. **Verständlich:** Inhaltshierarchie, Benennungen und Interaktionsmuster konsistent halten.
5. **Robust:** Zoom, kleine Ansichten, lange Texte und Nutzereinstellungen berücksichtigen.
6. **Reduziert:** Effekte dienen dem Inhalt, nicht umgekehrt.
7. **Offen:** Verträge textuell dokumentieren; keine Framework- oder Anbieterbindung.

## Messbare Ziele

- Textkontrast mindestens 4,5:1, für großen Text mindestens 3:1 gemäß WCAG-Definition.
- Erforderliche nichttextuelle UI-Indikatoren mindestens 3:1 gegenüber angrenzenden Farben.
- Bedeutung niemals ausschließlich über Farbe vermitteln.
- Alle interaktiven Funktionen per Tastatur bedienen; Fokus nicht verdecken.
- Bei 200 Prozent Textvergrößerung und 400 Prozent Zoom angemessenen Reflow prüfen.
- Bewegungsreduktion und erzwungene Systemfarben respektieren.

## Konformität

Jede freigegebene Kombination aus Theme und Modus separat prüfen. Diese Prinzipien allein sind kein Barrierefreiheitsnachweis. Anforderungen und Prüfungen konkretisiert die [Theme Engine](THEME_ENGINE.md).
