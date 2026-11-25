# Lab 4.1: Was ein CRM leistet – Notion als Übungs-CRM

**Leitfragen:**

<details>
<summary>Wo stehen heute die Infos zu einem Kunden, wenn die zuständige Kollegin im Urlaub ist?</summary>

Oft in ihrem Postfach, ihrem Notizbuch oder ihrem Kopf. Ein CRM legt sie an eine Stelle, die das ganze Team sieht: Firma, Ansprechperson, letzter Kontakt, nächster Schritt.

</details>

<details>
<summary>Was ist der Unterschied zwischen einem Interessenten und einem laufenden Angebot?</summary>

Ein Interessent (Lead) ist eine Firma, die vielleicht kauft. Ein laufendes Angebot (Deal) ist ein konkretes Geschäft mit Wert, Phase und Abschlussdatum. Aus einem Lead wird ein Deal, sobald ein echter Bedarf geklärt ist.

</details>

<details>
<summary>Welche Angabe zu einem Kunden wird am häufigsten gesucht?</summary>

Meist: Wer ist die Ansprechperson, was wurde zuletzt besprochen, was ist der nächste Schritt? Genau diese Felder müssen im CRM gepflegt sein, sonst wird wieder nachgefragt.

</details>

- Ein CRM ist das gemeinsame Gedächtnis des Vertriebs: Firmen, Kontakte, Leads, Deals und Aktivitäten an einer Stelle.
- Im Kurs dient Notion als Übungs-CRM: kostenlos, im Browser und ab Tag 2 mit n8n verbindbar. Die erste Datenbank `Leads` entsteht per CSV-Import.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| CRM (Customer Relationship Management) | Software, in der der Vertrieb Kunden, Kontakte, Leads und Deals gemeinsam pflegt – wie eine Kundenkartei, die alle gleichzeitig sehen |
| Deal (Verkaufschance, Opportunity) | konkretes Geschäft mit Wert, Phase und erwartetem Abschlussdatum |
| Aktivität | protokollierter Kontakt: Anruf, Mail, Termin, Notiz |
| Pipeline | alle offenen Deals, geordnet nach Phasen vom ersten Gespräch bis zum Abschluss; wie ein Trichter: oben viele Gespräche, unten wenige Abschlüsse |
| Phase | Station in der Pipeline, z. B. „Demo“ oder „Angebot versendet“ |
| Seite (Notion) | ein Dokument in Notion; kann Text, Tabellen und Datenbanken enthalten |
| Datenbank (Notion) | Tabelle, in der jede Zeile eine eigene Seite ist |
| Eigenschaft (Property) | Spalte einer Datenbank mit festem Typ, z. B. Zahl, Datum oder Auswahl |
| Ansicht (View) | Darstellung derselben Daten, z. B. als Tabelle oder Board, mit eigener Sortierung und eigenem Filter |

## Die fünf Objekte eines CRM

| Objekt | was es ist | Beispiel Nordwind (fiktiv) | im Übungs-CRM |
| --- | --- | --- | --- |
| Firma (Account) | ein Unternehmen | Rheinpark Versicherungsmakler GmbH, Köln | Eigenschaft `Firma` |
| Kontakt | eine Person in der Firma | Melike Yilmaz, Office Management | Eigenschaften `Ansprechperson`, `Rolle`, `E-Mail` |
| Lead | Interessent ohne Angebot | Hafenkontor Logistik, Umzug 2027 | Datenbank `Leads` (dieses Lab) |
| Deal | Geschäft mit Wert und Phase | „Rheinfels Logistik – 24 Räume“, 54.394 € | Datenbank `Deals` (Lab 4.2) |
| Aktivität | Anruf, Mail, Termin, Notiz | Bedarfsgespräch bei Rheinpark | Eigenschaften wie `Nächster Schritt` (Lab 4.3) |

In echten CRMs hängen diese Objekte zusammen. Wird ein Lead in Microsoft Dynamics 365 Sales qualifiziert, entstehen daraus automatisch eine Firma (Account), ein Kontakt und eine Verkaufschance (Opportunity):

![Microsoft Dynamics 365 Sales, Bereich „Lead qualified“: verknüpfte Datensätze Account „Northwind Traders“, Contact und Opportunity, darunter eine KI-Zusammenfassung „Lead qualification details“ mit Stichpunkten zum Lead](https://learn.microsoft.com/en-us/dynamics365/sales/media/lead-qualify-finish-page.png)
_Quelle: Microsoft Learn, „Qualify a lead and convert it to an opportunity“ (https://learn.microsoft.com/en-us/dynamics365/sales/qualify-lead-convert-opportunity-sales), Screenshot © Microsoft, abgerufen am 22.11.2026._

## Pipeline mit Phasen

Nordwind führt Deals durch sieben Phasen ([`nordwind-unternehmen.md`](../material/nordwind-unternehmen.md)):

```text
Qualifiziert → Bedarfsgespräch → Demo → Angebot versendet → Verhandlung → Gewonnen
                                                                       ↘ Verloren
```

CRMs zeigen die Pipeline meist als Board: eine Spalte je Phase, eine Karte je Deal, Summe und Anzahl über jeder Spalte. So sieht das in Pipedrive aus:

![Produktbild Pipedrive, Bereich „Deals“: Board-Ansicht mit den Spalten „Qualified“ (10 000 $ · 4 deals) und „Contact Made“ (5 350 $ · 3 deals), darin Deal-Karten mit Firma und Betrag, oben die Schaltfläche „+ Deal“](https://www-cms.pipedriveassets.com/brand-half-page-illustrations/Deal-Pipeline-zoom-in-complete.jpg)
_Quelle: Pipedrive, „Pipeline management“ (https://www.pipedrive.com/en/features/pipeline-management), Produktbild © Pipedrive, abgerufen am 22.11.2026._

HubSpot, Salesforce und Microsoft Dynamics 365 bieten dieselben Bausteine; die Board-Ansicht von HubSpot folgt in Lab 4.2.

## Notion als Übungs-CRM

| | echtes CRM (HubSpot, Salesforce, Pipedrive, Dynamics 365) | Notion im Kurs |
| --- | --- | --- |
| Kosten | Lizenz je Nutzer | kostenloses Konto genügt |
| Objekte | Firma, Kontakt, Lead, Deal, Aktivität fest eingebaut | zwei selbst angelegte Datenbanken `Leads` und `Deals` |
| Aktivitäten | Mails und Anrufe werden automatisch protokolliert | Felder von Hand oder per Workflow (ab Tag 2) |
| Anbindung an n8n | ja | ja, über eine Notion-Integration (Lab 6.2) |
| Zweck | Tagesgeschäft im Unternehmen | üben ohne echte Kundendaten |

Die Arbeitsweise lässt sich auf jedes CRM übertragen; die Anbindung an ein echtes Firmen-CRM ist im Kurs nur Ausblick.

## Notion-Grundbegriffe am Beispiel

Eine Notion-Datenbank sieht aus wie eine Tabelle. Jede Spalte ist eine Eigenschaft mit Typ (Symbol im Spaltenkopf), jede Zeile lässt sich als eigene Seite öffnen, und über dem Tabellenkopf stehen die Ansichten:

![Notion-Datenbank „Projects“ in der Ansicht „Table“: Spalten Name, Start date, Due date und Effort level mit farbigen Auswahl-Werten Small, Medium, Large; oben rechts Symbole für Filter, Sortieren und Suche sowie die Schaltfläche „New“](https://images.ctfassets.net/spoqsaf9291f/6oTqf15bW6h16i8Bbgs9Zs/8fb0e4b4cbdb675174ad63d045dea45e/Reference_Visuals_Group_153.png?w=1280)
_Quelle: Notion-Hilfe, „What is a database?“ (https://www.notion.com/help/what-is-a-database), Screenshot © Notion Labs, abgerufen am 22.11.2026._

Das Übungs-CRM besteht aus einer Seite mit zwei Datenbanken:

```text
Nordwind CRM (Seite)
├── Leads   ← leads-start.csv     (dieses Lab)  Interessenten ohne Angebot
└── Deals   ← nordwind-deals.csv  (Lab 4.2)     laufende und abgeschlossene Deals
```

Importiert wird über die Notion-Einstellungen oder den Befehl `/csv` auf einer Seite; Notion macht aus jeder CSV-Zeile eine Seite und aus jeder Spalte eine Eigenschaft:

![Notion-Einstellungen, Bereich „Import“: Feld „Import your content to Notion“ zum Ablegen von Dateien, darunter „File-based imports“ mit den Kacheln CSV, PDF, Text & Markdown, HTML und Word](https://images.ctfassets.net/spoqsaf9291f/5UVDNOLoLTCBPecdPQHh6n/041b15ecabdad74d00c5b5a80b4f45ae/import_image__1_.png?w=1280)
_Quelle: Notion-Hilfe, „Import data into Notion“ (https://www.notion.com/help/import-data-into-notion, deutsch: https://www.notion.com/de/help/import-data-into-notion), Screenshot © Notion Labs, abgerufen am 22.11.2026._

## Übung: Datenbank Leads importieren und sortieren

**Material:** [`leads-start.csv`](../material/notion/leads-start.csv) (11 Leads, 30 Spalten), Anleitung [`notion-import-anleitung.md`](../material/notion/notion-import-anleitung.md) · **Werkzeug:** Notion im Browser

**Ausgangslage:** Die bewerteten Leads aus Modul 3 sollen dort stehen, wo das ganze Team sie findet. Die Startdatei enthält die zehn Muster-Leads mit Score, Stufe und Begründung sowie den Lead Rheinpark aus einer Empfehlung; Spalten für spätere Labs sind noch leer. Alle arbeiten ab hier mit derselben Startdatei, damit Auswertungen, Workflows und Musterergebnisse an Tag 2 und 3 für alle dieselben Leads und Zahlen zeigen; die eigene `leads.csv` aus Lab 3.3 kommt über die Erweiterung dazu.

1. Lade `leads-start.csv` herunter (auf GitHub: Datei öffnen → „Download raw file“) und öffne in Notion die Seite „Nordwind CRM“ aus der Einrichtung (sonst neu anlegen).
2. Tippe in der Seite `/csv`, wähle „CSV“ unter „Importieren“ (Import) bzw. öffne „Einstellungen“ (Settings) → „Importieren“ (Import) → „CSV“, wähle die Datei und lass eine neue Datenbank anlegen; benenne sie in `Leads` um.
3. Setze die Typen der Eigenschaften nach der Tabelle unten (Spaltenkopf → „Eigenschaft bearbeiten“ (Edit property) → „Typ“ (Type)) und ergänze bei `Status` die fehlenden Optionen.
4. Sortiere die Tabelle: „Sortieren“ (Sort) → `Score` → „Absteigend“ (Descending).
5. Öffne den Eintrag „Rheinpark Versicherungsmakler GmbH“ als Seite und prüfe Score, Stufe, Begründung und Status.

Bezeichnungen je nach Version; die vollständige Typtabelle mit allen 30 Eigenschaften steht in der [Importanleitung](../material/notion/notion-import-anleitung.md). Für dieses Lab genügen:

| Eigenschaft | Typ | Optionen bzw. Hinweis |
| --- | --- | --- |
| `Firma` | Titel (Title) | automatisch die erste Spalte |
| `Score`, `Mitarbeitende`, `Räume` | Zahl (Number) | Score 0–100 |
| `Stufe` | Auswählen (Select) | heiß, warm, kalt |
| `Status` | Auswählen (Select) | Neu, Prüfen, Heiß, Später pflegen, Gespräch geführt, Kein Fit; nach dem Import existiert nur „Neu“, die übrigen fünf von Hand ergänzen |
| `Segment`, `Region`, `Quelle` | Auswählen (Select) | Optionen laut Importanleitung (z. B. „Sonstige“ bei Region ergänzen) |
| `Diese Woche`, `KI-gestützt`, `Einwilligung Werbung` | Kontrollkästchen (Checkbox) | bleiben vorerst leer; Bedeutung folgt in den Labs, die sie nutzen |

Die Schreibweise der Optionen muss exakt stimmen: Die Workflows ab Tag 2 schreiben genau diese Werte.

**Checkpoint:** Die Datenbank `Leads` liegt in der Seite „Nordwind CRM“, hat 11 Zeilen, `Score` ist eine Zahl, und die Tabelle beginnt mit Rheinpark (100), Brenner & Voss (95) und Hafenkontor (93); `Status` bietet sechs Optionen.

**Erweiterung:** Die eigene `leads.csv` aus Lab 3.3 ergänzen: Datenbank als ganze Seite öffnen → „•••“ → „Mit CSV zusammenführen“ (Merge with CSV), Spalten gleichen Namens zuordnen (auch `Räume`, `Score`, `Stufe`, `Begründung`), `Quelle-URL` überspringen, danach `Quelle` auf „Recherche“ setzen. Sinnvoll nur mit eigener Recherche; die Musterdatei erzeugt Dubletten.

_Quellen: Notion-Hilfe „Daten in Notion importieren“ (https://www.notion.com/de/help/import-data-into-notion), „Datenbankeigenschaften“ (https://www.notion.com/de/help/database-properties), „Ansichten, Filter und Sortierungen“ (https://www.notion.com/de/help/views-filters-and-sorts), alle abgerufen am 22.11.2026. Stand: 22.11.2026, Bezeichnungen je nach Version._

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Datenbank `Leads` in „Nordwind CRM“, Ansicht „Tabelle“ (Table), sortiert nach `Score` absteigend (Auszug der wichtigsten Spalten):

| Firma | Segment | Region | Score | Stufe | Status |
| --- | --- | --- | --- | --- | --- |
| Rheinpark Versicherungsmakler GmbH | Mittelstand-Büro | DE-West | 100 | heiß | Neu |
| Brenner & Voss Rechtsanwälte PartG mbB | Kanzleien und Beratungen | DE-West | 95 | heiß | Neu |
| Hafenkontor Logistik GmbH | Mittelstand-Büro | DE-Nord | 93 | heiß | Neu |
| Vogelsang Medizintechnik GmbH | Mittelstand-Büro | DE-Süd | 75 | heiß | Neu |
| Grachtenwerk Coworking B.V. | Coworking und Flexible Office | NL | 66 | warm | Neu |
| Limmat Treuhand AG | Kanzleien und Beratungen | CH | 65 | warm | Neu |
| Lechfeld Stahlhandel GmbH | Mittelstand-Büro | DE-Süd | 59 | warm | Neu |
| Isarblick Steuerberatung GmbH | Kanzleien und Beratungen | DE-Süd | 55 | warm | Neu |
| Donautal Kommunikation GmbH | Mittelstand-Büro | AT | 36 | kalt | Neu |
| Weserbogen Physiotherapie | Kein Fit | DE-Nord | 25 | kalt | Neu |
| Elster Backwaren GmbH | Kein Fit | DE-Ost | 20 | kalt | Neu |

**Eintrag Rheinpark als Seite (Auszug der Eigenschaften):**

| Eigenschaft | Wert |
| --- | --- |
| Ansprechperson / Rolle | Melike Yilmaz / Office Management |
| E-Mail | m.yilmaz@rheinpark-makler.example |
| Quelle | Empfehlung |
| Score / Stufe | 100 / heiß |
| Begründung | Fit 60/60: Büro-Unternehmen (20), 120 MA (10), 12 Räume (15), DE-West (15). Interesse 40/40: laut Empfehlung drei neue Räume und Doppelbuchungen (25), neue Räume ab Februar 2027 innerhalb von 3 Monaten (15). |
| Status | Neu |
| Nächster Schritt, Bedarf, Budget, Entscheider, Zeitrahmen | leer (folgt in Lab 4.3) |

Die zehn recherchierten Leads haben keine Ansprechperson und keine E-Mail (Rollen statt Namen, Lab 3.2); nur Rheinpark kam über eine Empfehlung mit Kontakt. Die Scores der zehn recherchierten Leads entsprechen dem Musterergebnis aus Lab 3.3.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Umlaute als Sonderzeichen (z. B. â€“) | Datei vorher in Excel geöffnet und gespeichert | Original-CSV erneut herunterladen und direkt importieren |
| Rheinpark (100) steht nach dem Sortieren ganz unten | `Score` ist noch Text und wird Zeichen für Zeichen sortiert | Typ auf Zahl stellen |
| Status „Gespräch geführt“ fehlt später in Lab 4.3 | Optionen nach dem Import nicht ergänzt | in „Eigenschaft bearbeiten“ (Edit property) alle sechs Optionen anlegen |
| Datenbank liegt unter „Privat“ statt in „Nordwind CRM“ | Import über die Einstellungen landet außerhalb der Seite | in der Seitenleiste auf „Nordwind CRM“ ziehen |

## Fazit

- Ein CRM bündelt Firmen, Kontakte, Leads, Deals und Aktivitäten an einer Stelle; die Pipeline zeigt die Deals nach Phasen.
- Notion bildet das im Kurs mit Seiten, Datenbanken, Eigenschaften und Ansichten nach.
- Eigenschaftstypen und Optionen exakt setzen: Davon hängen Sortierung, Formeln und später die Workflows ab.

> **Merksatz:** Was nicht im CRM steht, ist für das Team nicht passiert.
