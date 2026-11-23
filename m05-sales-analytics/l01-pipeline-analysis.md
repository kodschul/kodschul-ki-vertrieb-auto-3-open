# Lab 5.1: Pipeline und Kundendaten mit KI auswerten

**Leitfragen:**

<details>
<summary>Woran wird heute erkannt, dass ein Deal einschläft?</summary>

Meist am Bauchgefühl oder zu spät: Der Kunde meldet sich nicht mehr, das geplante Abschlussdatum ist vorbei. Beides steht im CRM als Datum und lässt sich jeden Tag automatisch prüfen.

</details>

<details>
<summary>Warum wurde der letzte große Deal verloren – und steht das irgendwo?</summary>

Oft nur im Kopf der zuständigen Person. Steht der Grund als Feld im CRM (z. B. „Preis – RaumPilot günstiger“), wird aus Einzelfällen ein Muster, das sich zählen lässt.

</details>

<details>
<summary>Welche Bestandskunden könnten mehr kaufen, und woran wäre das zu sehen?</summary>

An dem, was im Auftrag fehlt: kleinere Software-Stufe, kein Service-Vertrag, nur ein Teil der Räume ausgestattet. Steht das Gekaufte im CRM, findet eine Auswertung die Lücken in Sekunden.

</details>

- Der KI-Assistent liest einen CRM-Export und beantwortet Fragen, für die sonst eine Tabellenkalkulation mit Filtern und Formeln nötig wäre.
- Eine KI-Zahl gilt erst, wenn sie an einer Stelle in Notion per Filter bestätigt ist.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| Export | Kopie der Daten aus einem Programm als Datei, z. B. die Datenbank `Deals` als CSV-Datei |
| CSV | Textdatei, in der jede Zeile ein Datensatz ist und Kommas die Spalten trennen; jedes Tabellenprogramm und jeder KI-Assistent kann sie lesen |
| gestockter Deal | offener Deal, bei dem sich nichts mehr bewegt: Abschlussdatum überschritten oder lange kein Kontakt |
| Abschlussquote | Anteil der gewonnenen an allen abgeschlossenen Deals (gewonnen ÷ gewonnen und verloren), englisch Win Rate |
| Stichtag | festes Datum, auf das sich „überfällig“ und „seit 30 Tagen“ beziehen; in den Übungsdaten der 01.12.2026 |
| Ausbaupotenzial | Chance, einem bestehenden Kunden mehr zu verkaufen: höhere Software-Stufe, Service, weitere Räume (Upselling, Cross-Selling) |

## Vier Auswertungsfragen an die Pipeline

| Frage | Woran erkennbar | Spalten in `Deals` | Nutzen |
| --- | --- | --- | --- |
| Welche Deals sind gestockt? | Abschlussdatum vor dem Stichtag oder letzter Kontakt älter als 30 Tage | `Phase`, `Abschlussdatum`, `Letzter Kontakt` | Liste zum Nachfassen, bevor der Deal verloren geht |
| Wie hoch ist die Abschlussquote je Segment? | gewonnen ÷ abgeschlossen, getrennt nach Segment | `Segment`, `Phase` | zeigt, wo sich Vertriebszeit lohnt |
| Warum gehen Deals verloren? | Kategorie im Verlustgrund, Wettbewerber | `Verlustgrund`, `Wettbewerber` | Argumente und Preise gezielt verbessern |
| Welche Kunden können mehr kaufen? | fehlende Bausteine nach dem Semikolon in `Produkte` | `Phase`, `Produkte` | Ausbau bei Kunden, die schon vertrauen |

## Weg vom Notion-Export zur geprüften Zahl

```text
Notion: Deals ──Export──▶ CSV-Datei ──Upload oder Text einfügen──▶ KI-Assistent
                                                                      │ 4 Auswertungs-Prompts
                                                                      ▼
Notion: Filter ◀── eine Zahl je Auswertung gegenprüfen ◀── Tabelle mit Rechenweg
```

| Schritt | Warum |
| --- | --- |
| Stichtag im Prompt nennen | die KI kennt das Datum der Übungsdaten nicht und rechnet sonst mit heute |
| Rechenweg verlangen | ein Sprachmodell rechnet „im Kopf“ und verzählt sich; der Rechenweg zeigt die Stelle |
| eine Zahl in Notion prüfen | Notion zählt exakt; stimmt eine Zahl nicht, ist die ganze Tabelle verdächtig |

Ein Export echter Kundendaten ist nach der Datenampel aus [Lab 1.3](../m01-ai-sales-basics/l03-data-rules.md) rot und gehört nicht in ein privates KI-Konto. Die Nordwind-Daten sind erfunden und dürfen in jedes Werkzeug.

## Datenbank aus Notion als CSV exportieren

Eine Datenbank, die als ganze Seite geöffnet ist, exportiert Notion als CSV-Datei, verpackt in einer ZIP-Datei. Weg (Stand: 22.11.2026, Bezeichnung je nach Version):

1. Datenbank `Deals` als ganze Seite öffnen (in der Seitenleiste anklicken).
2. Oben rechts **•••** → **Exportieren** (Export).
3. Format **Markdown & CSV** wählen → **Exportieren**.
4. ZIP-Datei entpacken; darin liegt die CSV-Datei der Datenbank (je nach Version zusätzlich eine Datei mit `_all` im Namen, die alle Zeilen unabhängig von Filtern enthält; diese verwenden, prüfen).

![Notion-Seite mit geöffnetem •••-Menü oben rechts; ein roter Pfeil zeigt auf den Eintrag „Export“ mit dem Untertitel „PDF, HTML, Markdown“](https://images.ctfassets.net/spoqsaf9291f/5kX5ljGEd2n5bRmHLPlhQh/23374b6f67d30f0a7abdd00493231da5/Export_menu.png)
_Quelle: Notion Help Center, „Export your content“ (https://www.notion.com/help/export-your-content), © Notion Labs, abgerufen am 23.11.2026._

![Notion-Dialog „Export format: Markdown & CSV“, „Include content: Everything“, Schalter „Include subpages“, Schaltflächen Cancel und Export](https://images.ctfassets.net/spoqsaf9291f/eFc5cC1PvvOh0vAjLDfoK/42de72bf965cff829da24d0904eaae30/Export_CSV_Markdown.png)
_Quelle: Notion Help Center, „Export your content“ (https://www.notion.com/help/export-your-content), © Notion Labs, abgerufen am 23.11.2026._

Klappt der Export nicht oder zeigt die CSV-Datei Datumswerte in einem ungewohnten Format: Die Datei [`nordwind-deals.csv`](../material/notion/nordwind-deals.csv) hat denselben Inhalt (ohne die Formel `Gewichteter Wert`) und funktioniert genauso.

## Übung: Pipeline-Auswertung mit Prüfrechnung

**Material:** Datenbank `Deals` aus [Lab 4.2](../m04-notion-crm/l02-pipeline.md), [`auswertungs-prompts.md`](../material/auswertungs-prompts.md), Ersatzdatei [`nordwind-deals.csv`](../material/notion/nordwind-deals.csv) · **Werkzeug:** Notion, KI-Assistent

**Ausgangslage:** Die Nordwind-Vertriebsleitung will vor dem Jahresende wissen, welche Deals hängen, wo Nordwind gewinnt, warum Deals verloren gehen und welche Kunden mehr kaufen könnten. Die Antworten kommen aus der Datenbank `Deals`, geprüft an je einer Zahl.

1. Exportiere die Datenbank `Deals` als **Markdown & CSV** und entpacke die ZIP-Datei.
2. Öffne einen neuen Chat, lade die CSV-Datei hoch (oder füge ihren Inhalt als Text ein) und sende Prompt-Karte 5.1a. Prüfe die vier Zahlen: 60, 30, 8, 22.
3. Sende im selben Chat nacheinander die Prompt-Karten 5.1b bis 5.1e aus [`auswertungs-prompts.md`](../material/auswertungs-prompts.md).
4. Prüfe zwei Zahlen in Notion: Lege in `Deals` eine neue Tabellenansicht „Prüfung“ an, setze nacheinander die Filter „gestockte Deals“ und „Verluste an RaumPilot“ aus der Tabelle „Prüfwege“ unten und vergleiche die Anzahl der Einträge mit der KI-Antwort.
5. Weicht eine Zahl ab, sende Prompt-Karte 5.1f und vergleiche erneut.

**Prompt-Karte 5.1a – Daten einlesen und zählen**
```text
Du bist Vertriebsanalyst. Im Anhang (oder unten als Text) steht die Datenbank „Deals“ aus unserem CRM als CSV. Jede Zeile ist ein Deal.
Wichtige Spalten: Phase (Qualifiziert, Bedarfsgespräch, Demo, Angebot versendet, Verhandlung, Gewonnen, Verloren), Höchste Phase, Wert (Euro, erstes Vertragsjahr), Wahrscheinlichkeit (Prozent), Abschlussdatum, Letzter Kontakt, Segment, Wettbewerber, Verlustgrund, Produkte, Verantwortlich.
Stichtag der Übungsdaten ist der 01.12.2026. Rechne nie mit dem heutigen Datum.

Lies die Daten ein und antworte nur mit vier Zahlen: Anzahl Zeilen, offene Deals (Phase vor Gewonnen und Verloren), gewonnene Deals, verlorene Deals. Zeige kurz, wie du gezählt hast. Rechne noch nichts weiter aus.
```

Prompt-Karten 5.1b (gestockte Deals), 5.1c (Abschlussquote je Segment), 5.1d (Verlustgründe) und 5.1e (Ausbaupotenzial) stehen vollständig in [`auswertungs-prompts.md`](../material/auswertungs-prompts.md).

**Prompt-Karte 5.1f – Abweichung klären**
```text
Notion zählt für diese Auswertung [Zahl aus Notion], du hast [Zahl der KI] genannt. Liste alle Zeilen einzeln auf, die du gezählt hast, mit den Werten der verwendeten Spalten. Prüfe dabei den Stichtag 01.12.2026 und nenne die Zeile, die den Unterschied erklärt.
```

**Prüfwege in Notion** (Filter in der Ansicht „Prüfung“)

| Auswertung | Filter | Erwartete Anzahl | Prüfung |
| --- | --- | --- | --- |
| gestockte Deals | `Abschlussdatum` vor 01.12.2026 **oder** `Letzter Kontakt` vor 01.11.2026; dazu `Phase` ist nicht Gewonnen und nicht Verloren | 6 | Pflicht |
| Verluste an RaumPilot | `Phase` ist Verloren; `Wettbewerber` ist RaumPilot | 13 | Pflicht |
| Abschlussquote Coworking | `Segment` ist Coworking und Flexible Office; `Phase` ist Gewonnen oder Verloren | 9, davon 1 gewonnen | Erweiterung |
| Ausbaupotenzial | `Phase` ist Gewonnen; `Produkte` enthält „Basic“ **oder** „kein Care“ | 3 | Erweiterung |

**Erweiterter Filter mit Oder-Gruppe** für „gestockte Deals“ (Stand: 23.11.2026, Bezeichnung je nach Version):

1. In der Ansicht „Prüfung“ das Einstellungsmenü oben an der Datenbank öffnen → **Filter** → **Erweiterten Filter hinzufügen** (Add advanced filter).
2. Regel 1: `Phase` → **ist nicht** (Is not) → Gewonnen; **+ Filter hinzufügen** (Add a filter) → `Phase` → ist nicht → Verloren; Verknüpfung **Und** (And).
3. **+ Filter hinzufügen** → **Filtergruppe hinzufügen** (Add a filter group); in der Gruppe `Abschlussdatum` → **ist vor** (Is before) → genaues Datum 01.12.2026 und `Letzter Kontakt` → ist vor → 01.11.2026; die Verknüpfung innerhalb der Gruppe von **Und** auf **Oder** (Or) umstellen.
4. Anzahl der Zeilen ablesen: 6.

_Quellen: Notion Help Center, „Views, filters, sorts & groups“, Abschnitt „Add an advanced filter“ (https://www.notion.com/help/views-filters-and-sorts), und „Using advanced database filters“ (https://www.notion.com/help/guides/using-advanced-database-filters); abgerufen am 23.11.2026._

**Checkpoint:** Der Chat enthält vier Auswertungen mit Rechenweg; die Ansicht „Prüfung“ bestätigt 6 gestockte Deals und 13 Verluste an RaumPilot.

**Erweiterung:** Die beiden übrigen Prüfwege (Coworking, Ausbaupotenzial) in Notion nachstellen; die Tabelle der gestockten Deals als Seite „Gestockte Deals 01.12.2026“ unter „Nordwind CRM“ ablegen.

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Exakte Werte aus [`deals-muster-erklaerung.md`](../material/notion/deals-muster-erklaerung.md); KI-Antworten formulieren anders, die Zahlen müssen gleich sein.

**5.1a** 60 Zeilen, 30 offen, 8 gewonnen, 22 verloren.

**5.1b – Gestockte Deals (Stichtag 01.12.2026)**

| Deal | Phase | Wert | Grund | Verantwortlich |
| --- | --- | --- | --- | --- |
| Rheinfels Logistik – 24 Räume | Angebot versendet | 54.394 € | Abschlussdatum 30.10.2026 überschritten; letzter Kontakt 17.09.2026 (75 Tage) | Jonas Brink |
| Weber & Kollegen Wirtschaftsprüfung – 10 Räume | Verhandlung | 28.212 € | Abschlussdatum 27.11.2026 überschritten | Jonas Brink |
| Marquardt & Lenz Rechtsanwälte – 9 Räume | Demo | 23.865 € | letzter Kontakt 12.10.2026 (50 Tage) | Lena Hoffmann |
| Murtal Bau – 8 Räume | Demo | 17.418 € | letzter Kontakt 25.08.2026 (98 Tage) | Aylin Demir |
| Inntal Versicherungsmakler – 9 Räume | Angebot versendet | 16.420 € | Abschlussdatum 20.11.2026 überschritten; letzter Kontakt 28.10.2026 (34 Tage) | Aylin Demir |
| Kanaalhuis Coworking – 14 Räume | Angebot versendet | 14.672 € | letzter Kontakt 02.10.2026 (60 Tage) | Sander de Vries |

6 Deals, zusammen 154.981 € (gewichtet 79.004,60 €); drei davon stehen in „Angebot versendet“.

**5.1c – Abschlussquote je Segment**

| Segment | abgeschlossen | gewonnen | verloren | Abschlussquote |
| --- | --- | --- | --- | --- |
| Kanzleien und Beratungen | 8 | 4 | 4 | 4 ÷ 8 = 50,0 % |
| Mittelstand-Büro | 13 | 3 | 10 | 3 ÷ 13 = 23,1 % |
| Coworking und Flexible Office | 9 | 1 | 8 | 1 ÷ 9 = 11,1 % |
| **Gesamt** | **30** | **8** | **22** | **8 ÷ 30 = 26,7 %** |

Muster: Kanzleien gewinnen Nordwind viermal so oft wie Coworking-Betreiber; sechs der acht verlorenen Coworking-Deals scheitern am Preis.

**5.1d – Verlustgründe**

| Verlustgrund | Anzahl |
| --- | --- |
| Preis | 12 |
| Projekt verschoben, Bestandslieferant, Service vor Ort | je 2 |
| Kein Budget, Entscheider gewechselt, Produkt, Produktumfang | je 1 |
| **Summe** | **22** |

| Wettbewerber | verlorene Deals | verlorener Wert |
| --- | --- | --- |
| RaumPilot | 13 | 303.112 € |
| MeetSpace Pro | 3 | 136.677 € |
| Konferenzwerk | 2 | 50.990 € |
| keiner | 4 | 88.246 € |
| **Summe** | **22** | **579.025 €** |

Alle 12 Preis-Verluste gingen an RaumPilot (6 Coworking, 5 Mittelstand-Büro, 1 Kanzlei). RaumPilot steht bei 13 von 22 Verlusten (59 %) und in 9 der 30 offenen Deals. Frage an den Vertrieb: Wird das Argument „Hardware, Software und Service aus einer Hand“ früh genug gebracht? Drei gewonnene Deals hatten RaumPilot ebenfalls im Wettbewerb.

**5.1e – Ausbaupotenzial (3 von 8 gewonnenen Kunden)**

| Firma | Segment | gekauft | Ausbauchance | Verantwortlich |
| --- | --- | --- | --- | --- |
| Steuerkanzlei Ahrens & Partner mbB | Kanzleien und Beratungen | 4 × Vista, 2 × Vista Plus, Book Basic (6 Räume), Installation | Care, Book Pro, Panel 10 | Lena Hoffmann |
| Brightdesk Coworking B.V. | Coworking und Flexible Office | 35 × Panel 10, Book Pro (35 Räume), Installation | Care, Kamera-Sets | Sander de Vries |
| Seeblick Versicherungsmakler GmbH | Mittelstand-Büro | 14 × Panel 10, Book Basic (14 Räume), Care, Installation | Book Pro, Kamera-Sets | Aylin Demir |

Die übrigen fünf Kunden haben Panel 10, Kamera-Sets, Book Pro und Care.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| KI nennt 8, 12 oder mehr gestockte Deals | Stichtag fehlt, KI rechnet mit dem heutigen Datum | Stichtag 01.12.2026 im Prompt nennen und Prompt erneut senden |
| Summen weichen um einige hundert Euro ab | Sprachmodell rechnet im Kopf | Rechenweg anfordern; Summen immer aus Notion (Spaltenberechnung) übernehmen |
| Upload scheitert („Limit erreicht“) | Tageslimit des kostenlosen Kontos | CSV-Datei im Texteditor öffnen, Inhalt in den Chat kopieren |
| Notion-Filter „vor Datum“ fehlt | `Abschlussdatum` oder `Letzter Kontakt` noch als Text | Typ in Notion auf Datum stellen (Lab 4.2) |
| Gewonnene Deals tauchen bei „gestockt“ auf | „offen“ nicht definiert | im Prompt „Phase nicht Gewonnen und nicht Verloren“ verlangen |

## Fazit

- Vier Fragen decken die Pipeline ab: gestockt, Abschlussquote, Verlustgründe, Ausbaupotenzial.
- Stichtag und Rechenweg im Prompt machen KI-Zahlen prüfbar.
- Notion zählt, die KI erklärt das Muster; eine Zahl je Auswertung wird gegengeprüft.

> **Merksatz:** Eine KI-Zahl ohne Gegenprobe ist eine Vermutung.
