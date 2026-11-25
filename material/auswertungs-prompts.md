# Auswertungs-Prompts für die Pipeline (Lab 5.1)

Fiktives Unternehmen, alle Firmen, Personen und Zahlen erfunden.

Fünf Prompts für die Auswertung der Datenbank `Deals` mit einem KI-Assistenten: ein Prompt zum Einlesen, danach die vier Auswertungsfragen. Sie funktionieren in ChatGPT, Claude, Perplexity und Microsoft 365 Copilot.

**Einsatz im KI-Assistenten:**

1. Neuen Chat öffnen.
2. Die CSV-Datei der Datenbank `Deals` hochladen (Export aus Notion, Anleitung in [Lab 5.1](../m05-sales-analytics/l01-pipeline-analysis.md), oder direkt [`notion/nordwind-deals.csv`](notion/nordwind-deals.csv)). Klappt der Upload nicht (Tageslimit kostenloser Konten), den Dateiinhalt unter den Prompt kopieren.
3. Prompt 5.1a senden, danach 5.1b bis 5.1e nacheinander im selben Chat.
4. Zahlen in Notion per Filter nachprüfen: Pflicht sind 5.1b (6 gestockte Deals) und 5.1d (13 Verluste an RaumPilot), 5.1c und 5.1e sind Erweiterung (Prüfwege und Schritte für den erweiterten Filter in Lab 5.1).

Alle Prompts nennen den **Stichtag der Übungsdaten 01.12.2026**. Ohne diesen Satz rechnet die KI mit dem heutigen Datum, und „überfällig“ oder „seit 30 Tagen kein Kontakt“ ergeben andere Deals. Jeder Prompt verlangt den Rechenweg, damit sich eine Zahl gegenprüfen lässt.

## Prompt 5.1a – Daten einlesen und zählen

```text
Du bist Vertriebsanalyst. Im Anhang (oder unten als Text) steht die Datenbank „Deals“ aus unserem CRM als CSV. Jede Zeile ist ein Deal.
Wichtige Spalten: Phase (Qualifiziert, Bedarfsgespräch, Demo, Angebot versendet, Verhandlung, Gewonnen, Verloren), Höchste Phase, Wert (Euro, erstes Vertragsjahr), Wahrscheinlichkeit (Prozent), Abschlussdatum, Letzter Kontakt, Segment, Wettbewerber, Verlustgrund, Produkte, Verantwortlich.
Stichtag der Übungsdaten ist der 01.12.2026. Rechne nie mit dem heutigen Datum.

Lies die Daten ein und antworte nur mit vier Zahlen: Anzahl Zeilen, offene Deals (Phase vor Gewonnen und Verloren), gewonnene Deals, verlorene Deals. Zeige kurz, wie du gezählt hast. Rechne noch nichts weiter aus.
```

## Prompt 5.1b – Gestockte Deals

```text
Stichtag der Übungsdaten ist der 01.12.2026.

Finde alle offenen Deals (Phase nicht Gewonnen und nicht Verloren), die gestockt sind. Gestockt heißt: Abschlussdatum liegt vor dem 01.12.2026 ODER Letzter Kontakt liegt vor dem 01.11.2026 (mehr als 30 Tage ohne Kontakt).

Ausgabe als Tabelle: Deal | Phase | Wert | Grund (Datum und Tage seit dem letzten Kontakt bis zum Stichtag) | Verantwortlich. Sortiere nach Wert, absteigend.
Zeige den Rechenweg: welche der beiden Bedingungen jeder Deal erfüllt. Nenne darunter Anzahl und Summe Wert.
Nutze nur Zeilen aus der Datei und erfinde keine Deals.
```

## Prompt 5.1c – Abschlussquote je Segment

```text
Stichtag der Übungsdaten ist der 01.12.2026.

Berechne die Abschlussquote je Segment, nur aus den abgeschlossenen Deals (Phase Gewonnen oder Verloren). Abschlussquote = gewonnene Deals ÷ abgeschlossene Deals.

Ausgabe als Tabelle: Segment | abgeschlossen | gewonnen | verloren | Abschlussquote in %. Letzte Zeile: Gesamt.
Zeige den Rechenweg je Zeile (Beispiel: 4 ÷ 8 = 50,0 %). Nenne danach in zwei Sätzen das auffälligste Muster.
```

## Prompt 5.1d – Gründe für verlorene Deals

```text
Stichtag der Übungsdaten ist der 01.12.2026.

Werte alle Deals mit Phase Verloren aus. Die Kategorie des Verlustgrunds steht in der Spalte Verlustgrund vor dem Gedankenstrich.
1. Tabelle: Verlustgrund (Kategorie) | Anzahl.
2. Tabelle: Wettbewerber | Anzahl verlorener Deals | verlorener Wert.
3. In welchen Segmenten liegen die Verluste mit der Kategorie „Preis“, und an welchen Wettbewerber gingen sie?

Zeige die Zählung nachvollziehbar (Deals je Kategorie als Liste). Fasse das Muster in drei Sätzen zusammen und nenne eine Frage, die der Vertrieb klären sollte. Erfinde keine Gründe, die nicht in der Datei stehen.
```

## Prompt 5.1e – Kunden mit Ausbaupotenzial

```text
Stichtag der Übungsdaten ist der 01.12.2026.

Prüfe alle Deals mit Phase Gewonnen auf Ausbaupotenzial. In der Spalte Produkte steht nach dem Semikolon, was der Kunde nicht gekauft hat. Ausbaupotenzial heißt: Book Basic statt Book Pro, kein Nordwind Care oder fehlende Bausteine (Panel 10, Kamera-Sets).

Ausgabe als Tabelle: Firma | Segment | gekauft | Ausbauchance | Verantwortlich.
Begründe jede Zeile mit dem Text aus der Spalte Produkte. Nenne darunter, wie viele der gewonnenen Kunden Ausbaupotenzial haben und wie viele nicht.
```

## Erwartete Ergebnisse

| Prompt | Prüfwert | Prüfweg in Notion |
| --- | --- | --- |
| 5.1a | 60 Zeilen, 30 offen, 8 gewonnen, 22 verloren | Anzahl unter der Tabelle bzw. je Board-Spalte |
| 5.1b | 6 gestockte Deals, zusammen 154.981 € | Erweiterter Filter: `Abschlussdatum` vor 01.12.2026 **oder** `Letzter Kontakt` vor 01.11.2026, dazu `Phase` ist nicht Gewonnen und nicht Verloren |
| 5.1c | Kanzleien 50,0 %, Mittelstand-Büro 23,1 %, Coworking 11,1 %, gesamt 26,7 % | Filter `Segment` ist Coworking und Flexible Office, `Phase` ist Gewonnen oder Verloren → 9 Einträge, davon 1 gewonnen |
| 5.1d | Preis 12 von 22; RaumPilot bei 13 verlorenen Deals | Filter `Phase` ist Verloren und `Wettbewerber` ist RaumPilot → 13 Einträge |
| 5.1e | 3 von 8 gewonnenen Kunden | Filter `Phase` ist Gewonnen und `Produkte` enthält „Basic“ oder „kein Care“ → 3 Einträge |

Alle Werte stammen aus [`notion/deals-muster-erklaerung.md`](notion/deals-muster-erklaerung.md).
