# Musterworkflows für n8n

Jede Datei ist der fertige Stand eines Labs als n8n-Workflow im JSON-Format. Wenn der eigene Aufbau hängt, den passenden Musterworkflow importieren und dort weiterarbeiten.

Die Dateien enthalten keine Zugangsdaten: keine Notion-Verbindung, keinen API-Schlüssel, keine echten Datenbank-IDs. Diese Angaben werden nach dem Import im eigenen n8n-Konto gesetzt. Alle Daten im Kurs sind fiktiv.

## Musterworkflows je Lab

| Datei | Stand nach Lab | Was nach dem Import einzustellen ist |
| --- | --- | --- |
| [`m06-hallo-workflow.json`](m06-hallo-workflow.json) | [6.1](../../m06-n8n-basics/l01-automation-basics.md): Klick-Auslöser → Beispiel-Lead → Bedingung „Mindestens 5 Räume?“ | nichts, sofort ausführbar |
| [`m06-l02-formular-notion.json`](m06-l02-formular-notion.json) | [6.2](../../m06-n8n-basics/l02-first-workflow.md): Formular „Lead-Anfrage“ → neuer Lead in Notion (Quelle „Website“, Status „Neu“) | Notion-Verbindung, Datenbank `Leads` |
| [`m06-l02-start.json`](m06-l02-start.json) | [6.2](../../m06-n8n-basics/l02-first-workflow.md), Startdatei: nur das fertige Formular „Lead-Anfrage“ mit allen neun Feldern; der Notion-Teil wird im Lab gebaut | nichts, sofort ausführbar; danach Notion-Knoten im Lab ergänzen |
| [`m06-fehler.json`](m06-fehler.json) | [6.3](../../m06-n8n-basics/l03-data-flow.md): Übungsdatei mit absichtlichem Fehler (falscher Eigenschaftsname) | Notion-Verbindung, Datenbank `Leads`; danach Fehler suchen |
| [`m06-l03-bedingung.json`](m06-l03-bedingung.json) | [6.3](../../m06-n8n-basics/l03-data-flow.md): Region „Sonstige“ → Status „Prüfen“, sonst „Neu“ | Notion-Verbindung, Datenbank `Leads` |
| [`m07-l01-ki-zusammenfassung.json`](m07-l01-ki-zusammenfassung.json) | [7.1](../../m07-ai-workflows/l01-ai-node.md): KI fasst die Nachricht in einem Satz zusammen → Feld „Zusammenfassung“ | Notion-Verbindung, Datenbank `Leads`, KI-Modell (Gateway credits oder eigener Schlüssel) |
| [`m07-l02-lead-scoring.json`](m07-l02-lead-scoring.json) | [7.2](../../m07-ai-workflows/l02-auto-scoring.md): Bewertung mit der Matrix (Score, Stufe, Begründung, Nächster Schritt, Segment, Branche); Score ab 70 → „Heiß“, sonst „Später pflegen“ | wie 7.1; Systemanweisung in „Lead bewerten“ durch die eigene ersetzen |
| [`m07-l03-getestet.json`](m07-l03-getestet.json) | [7.3](../../m07-ai-workflows/l03-testing.md): Systemanweisung gegen Spam und Manipulation, Plausibilitätsregel im Wenn-Knoten | wie 7.1 |
| [`m08-l01-anreicherung.json`](m08-l01-anreicherung.json) | [8.1](../../m08-lead-enrichment/l01-enrichment.md): Firmenseite abrufen → Firmenprofil in fünf Stichpunkten → Feld „Firmenprofil“ und Kontext fürs Scoring; ist die Seite nicht erreichbar, läuft der Workflow weiter (On Error: Continue) | wie 7.1 |
| [`m08-l02-lead-eingang.json`](m08-l02-lead-eingang.json) | [8.2](../../m08-lead-enrichment/l02-reply-draft.md): kompletter Workflow „Lead-Eingang“ mit Antwortentwurf und Freigabe „Freigabe offen“ | wie 7.1 |
| [`m09-l01-gespraechsnotiz.json`](m09-l01-gespraechsnotiz.json) | [9.1](../../m09-sales-automation/l01-follow-up-flow.md): Formular „Gesprächsnotiz“ → Lead finden → Felder und Follow-up-Entwurf → Lead aktualisieren | Notion-Verbindung in beiden Notion-Knoten, Datenbank `Leads` im Knoten „Lead in Notion finden“, KI-Modell |
| [`m09-l02-briefing.json`](m09-l02-briefing.json) | [9.2](../../m09-sales-automation/l02-daily-briefing.md): werktags 08:00 offene Deals → Briefing → Seite „Briefing <Datum>“ | Notion-Verbindung, Datenbank `Deals`, Link zur Seite „Nordwind CRM“, KI-Modell; danach veröffentlichen („Publish“, ältere Versionen: „Active“) |
| [`m09-l03-fehler-workflow.json`](m09-l03-fehler-workflow.json) | [9.3](../../m09-sales-automation/l03-operations.md): bei einem Fehler Seite „Fehler <Workflow> <Zeit>“ in Notion | Notion-Verbindung, Link zur Seite „Nordwind CRM“; in den überwachten Workflows als Fehler-Workflow eintragen |
| [`m11-l01-datensparsam.json`](m11-l01-datensparsam.json) | [11.1](../../m11-legal-ethics/l01-data-protection.md): Lead-Eingang ohne Rolle in den KI-Schritten (Name und E-Mail fehlen dort seit 7.2), Anrede mit Namen im Notion-Knoten, Feld „KI-gestützt“ angehakt | wie 7.1 |
| [`m12-showcase-workflow.json`](m12-showcase-workflow.json) | [12.2](../../m12-strategy-business-case/l02-solution-design.md): Showcase „Angebote nachfassen“: Deals in Phase „Angebot versendet“ ohne Kontakt seit 7 Tagen → Nachfass-Entwurf → Seite mit „Freigabe offen“ | Notion-Verbindung, Datenbank `Deals`, Link zur Seite „Nordwind CRM“, KI-Modell |

Jeder Workflow enthält einen Hinweiszettel (Sticky Note) mit denselben Schritten.

## Import in n8n

Stand: 22.11.2026, Quelle: [n8n Docs – Export and import workflows](https://docs.n8n.io/workflows/export-import/). Bezeichnungen je nach Version.

**Weg 1: Datei importieren**

1. Die JSON-Datei herunterladen: auf GitHub die Datei öffnen und „Download raw file“ wählen.
2. In n8n einen neuen, leeren Workflow öffnen.
3. Im Kopfbereich der Arbeitsfläche das Workflow-Menü (drei Punkte) öffnen und „Import from File“ wählen.
4. Die Datei auswählen; die Knoten erscheinen auf der Arbeitsfläche.
5. Den Workflow speichern.

**Weg 2: Einfügen auf der Arbeitsfläche**

1. Auf GitHub die Datei öffnen und mit „Copy raw file“ den ganzen Inhalt kopieren (oder „Raw“ öffnen, alles markieren, kopieren).
2. In n8n einen neuen, leeren Workflow öffnen und einmal auf die Arbeitsfläche klicken.
3. Mit Strg + V (Mac: Cmd + V) einfügen und den Workflow speichern.

## Einstellungen nach dem Import

Stand: 22.11.2026, Bezeichnungen je nach Version.

- **Notion-Verbindung:** im Notion-Knoten unter „Credential“ die eigene Notion-Verbindung aus Lab 6.2 wählen. Gibt es nur eine, setzt n8n sie oft automatisch.
- **Datenbank:** im Feld „Data Source“ statt `HIER-DATENBANK-AUSWAEHLEN` die Datenbank `Leads` bzw. `Deals` aus der Liste wählen. Erscheint sie nicht, ist sie in Notion noch nicht mit der Integration geteilt (⋯ → Verbindungen bzw. Connections).
- **Seite „Nordwind CRM“:** im Feld „Parent Page“ statt `HIER-LINK-ZUR-SEITE-NORDWIND-CRM-EINFUEGEN` den Link der Notion-Seite einfügen (in Notion: ⋯ → Link kopieren).
- **KI-Modell:** in jedem Knoten „KI-Modell …“ im Feld für die Verbindung „Use Gateway credits“ wählen oder eine eigene Verbindung mit API-Schlüssel. Voreingestellt ist das Modell `gpt-5-mini`; jedes andere Chat-Modell aus der Liste funktioniert ebenso.
- **Eigenschaften in Notion:** die Musterworkflows nutzen genau die Eigenschaftsnamen und Typen aus [`../notion/notion-import-anleitung.md`](../notion/notion-import-anleitung.md) (z. B. Website als URL, Räume als Zahl, Status als Auswahl mit allen Optionen). Weicht ein Name oder Typ ab, meldet der Notion-Knoten einen Fehler. Briefing und Showcase brauchen in `Deals` die Typen Datum für `Abschlussdatum` und `Letzter Kontakt`; als Text funktioniert der Datumsfilter im Showcase nicht.

## Hinweise zu den Inhalten

- Formularfelder heißen wie im Kurs: Firma, Website, Name, Rolle, E-Mail, Mitarbeitende, Anzahl Räume, Region, Nachricht. Ausdrücke wie `{{ $('Lead-Anfrage').item.json.Firma }}` holen den Wert aus dem Formular, auch wenn dazwischen KI-Schritte liegen.
- Die Systemanweisung in „Lead bewerten“ enthält die Mustermatrix aus [`../bewertungsmatrix-muster.md`](../bewertungsmatrix-muster.md) in Kurzform mit denselben Punkten und Sonderfällen; die erwarteten Ergebnisse je Testanfrage stehen in [`../testanfragen.md`](../testanfragen.md). Im Kurs wird sie durch die Anweisung ersetzt, die Assistent 3 aus der eigenen Matrix erzeugt.
- Testanfragen mit Region „Sonstige“ (z. B. T4) landen über die Bedingung „Region außerhalb DACH/NL?“ immer mit Status „Prüfen“ in Notion, unabhängig vom Score.
- Briefing, Gesprächsnotiz und Showcase rechnen mit dem Stichtag der Übungsdaten 01.12.2026. Der Showcase filtert deshalb auf „Letzter Kontakt vor dem 24.11.2026“; im echten Einsatz steht dort ein Datum relativ zu heute.
- Kein Workflow versendet Mails. Entwürfe landen in Notion mit Freigabe „Freigabe offen“ und werden dort von einem Menschen geprüft.
- Ein importierter Formular-Workflow bekommt eine eigene Formular-Adresse. Wird derselbe Workflow mehrfach importiert, nur eine Kopie veröffentlichen (Publish).
