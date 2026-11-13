---
title: "Theme-Engine-Vertrag"
schema_version: "1.0"
version: "0.1.0"
last_updated: "2026-11-13T18:34:46Z"
tier: 3
ai_usage: "allowed"
status: "draft"
---

# Theme-Engine-Vertrag

## Umfang

Technologieunabhängiger Vertrag, keine bereits implementierte Engine. Theme ist die visuelle Identität; Modus ist die Helligkeitsvariante. Beide sind unabhängig auswählbar.

## Pflichtfunktionen

- Registrierung mehrerer Themes mit stabiler Kennung und lesbarem Namen.
- Laufzeitwechsel zwischen registrierten Themes ohne Seitenneustart.
- Vollständige Varianten `light` und `dark` für jedes aktivierbare Theme.
- Zugängliche Auswahl für Theme und Modus.
- Option `system` für die Moduspräferenz; aufgelöst wird sie zu `light` oder `dark`.
- Dokumentierter Produktdefault ohne Bindung an eines der Beispiel-Themes.

## Zustandsmodell

| Feld | Werte | Bedeutung |
| --- | --- | --- |
| Theme-ID | Registrierte stabile Kennung | Produkt- oder Beispiel-Theme |
| Moduspräferenz | `light`, `dark`, `system` | Explizite Wahl oder Systemfolge |
| Aufgelöster Modus | `light`, `dark` | Tatsächlich angewandte Variante |

Explizite Nutzerauswahl hat Vorrang vor gespeicherter Präferenz und Produktdefault. `system` folgt der Systempräferenz auch bei späterer Änderung; eine explizite Light-/Dark-Wahl wird davon nicht überschrieben. Ohne ermittelbare Systempräferenz gilt ein dokumentierter Produktdefault.

## Semantischer Tokenvertrag

Alle folgenden Tokens müssen pro Modus auf gültige Werte auflösbar sein. Gemeinsame, modusneutrale Werte dürfen geteilt werden.

| Gruppe | Verbindliche Tokenrollen |
| --- | --- |
| Flächen | `color.background`, `color.surface`, `color.surfaceElevated` |
| Text | `color.text`, `color.textMuted`, `color.textOnAccent` |
| Interaktion | `color.accent`, `color.accentHover`, `color.accentActive`, `color.border`, `color.focus` |
| Status | `color.success`, `color.warning`, `color.danger`, `color.info` |
| Typografie | `font.family`, `font.sizeBody`, `font.sizeHeading`, `font.lineHeight` |
| Abstand | `space.small`, `space.medium`, `space.large` |
| Form | `radius.control`, `radius.surface`, `shadow.surface` |
| Bewegung | `motion.duration`, `motion.easing` |

Für zusätzliche Statusflächen und Textpaarungen eigene semantische Rollen definieren und deren Kontrast prüfen. Primitive Farbpaletten sind optional; Komponenten dürfen nicht von ihnen oder einem Beispiel-Theme abhängen.

## Lebenszyklus und Fehler

1. Theme inklusive beider Modi, Tokenvollständigkeit und gültiger Werte vor Registrierung validieren.
2. Ungültige Themes mit ausdrücklicher Diagnose ablehnen, nicht teilweise aktivieren.
3. Bei gültigem Wechsel sämtliche Werte atomar anwenden und Fokus sowie Anwendungszustand erhalten.
4. Ungültige gespeicherte Kennungen sichtbar diagnostizieren und den dokumentierten Produktdefault verwenden.
5. Scheitert Persistenz, aktuelle Auswahl beibehalten und fehlende Speicherung verständlich melden.
6. Präferenzen optional lokal und ohne personenbezogene Zusatzdaten speichern; ohne Speicherzugriff muss die Auswahl in der laufenden Sitzung funktionieren.

Bei Webprodukten initiale Anwendung vor sichtbarem Rendern und eine passende native Farbschema-Angabe vorsehen, um falsche Startfarben zu vermeiden. Andere Plattformen verwenden gleichwertige Mechanismen. Konkrete Speicher- und Renderadapter sind Produktentscheidungen.

## Erweiterung und Kompatibilität

Neue Themes erfüllen denselben Vertrag. Entfernen oder Umbenennen von Tokens ist eine inkompatible Änderung mit Migration. Zusätzliche Tokens und Produkt-Themes sind erlaubt, solange Basiskomponenten weiterhin ohne konkrete Theme-Kenntnis funktionieren.

## Akzeptanzprüfungen im Produkt

| Fall | Nachweis |
| --- | --- |
| Theme Switching | Zwischen mindestens zwei gültigen Themes wechseln, ohne Reload oder Zustandsverlust |
| Modi | Jedes registrierte Theme in Light und Dark aktivieren |
| Systempräferenz | Systemänderung wirkt nur bei `system` |
| Vorrang | Explizite Auswahl überschreibt gespeicherte und voreingestellte Werte |
| Ungültiges Theme | Fehlende Tokens oder Modi werden mit Diagnose abgelehnt |
| Unbekannte gespeicherte ID | Diagnose und dokumentierter Default, kein stiller Teilzustand |
| Speicherung blockiert | Wechsel bleibt nutzbar; fehlende Speicherung wird gemeldet |
| Tastatur und Fokus | Auswahl vollständig bedienbar; Fokus bleibt erhalten |
| Kontrast | Grenzwerte in jedem Modus und relevanten Zustand gemessen |
| Nutzereinstellungen | Reduzierte Bewegung und Systemfarben funktionieren |
| Erweiterbarkeit | Zusätzliches Produkt-Theme ohne Komponentenänderung integrierbar |

Diese Prüfungen sind Anforderungen an eine spätere Implementierung; hier wird kein Laufzeit- oder Kontrasttest als bestanden behauptet.
