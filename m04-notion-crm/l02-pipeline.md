# Lab 4.2: Pipeline-Datenbank mit Phasen und Werten

**Leitfragen:**

<details>
<summary>Wie viel Umsatz steckt in einem Angebot, das zu 30 % gewonnen wird?</summary>

Rechnerisch 30 % des Angebotswerts: bei 50.000 € also 15.000 €. Im Einzelfall wird es 0 € oder 50.000 €; über viele Deals hinweg ergibt die Summe solcher gewichteten Werte aber eine brauchbare Prognose.

</details>

<details>
<summary>Woran wird heute gesehen, in welcher Phase ein Deal steht?</summary>

Oft gar nicht oder nur durch Nachfragen. Im CRM hat jeder Deal eine Eigenschaft „Phase“, und eine Board-Ansicht zeigt alle Deals als Karten in Spalten je Phase.

</details>

<details>
<summary>Was passiert mit einer Auswertung, wenn die Hälfte der Abschlussdaten fehlt?</summary>

Sie wird falsch oder unmöglich: Prognosen nach Monat, gestockte Deals oder Abschlussquoten lassen sich nicht berechnen. Ohne gepflegte Felder bringt auch die beste KI-Auswertung nichts.

</details>

- Jeder Deal hat Phase, Wert und Wahrscheinlichkeit; der gewichtete Wert = Wert × Wahrscheinlichkeit ÷ 100 ist der Teil, der nach der Phase zu erwarten ist.
- Die Formel rechnet in Notion, die Board-Ansicht zeigt die Pipeline, die Summe je Spalte dient als Prüfrechnung. Zur offenen Pipeline zählen nur Deals vor Gewonnen und Verloren.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| Wert | Umsatz des Deals, bei Nordwind das erste Vertragsjahr in Euro |
| Wahrscheinlichkeit | angenommene Chance, dass ein Deal in dieser Phase gewonnen wird, in Prozent |
| Gewichteter Wert | Wert × Wahrscheinlichkeit ÷ 100; Summe aller gewichteten Werte = gewichtete Pipeline, eine einfache Umsatzprognose |
| Offene Pipeline | alle Deals, die weder gewonnen noch verloren sind |
| Formel-Eigenschaft (Notion) | Eigenschaft, die ihren Wert aus anderen Eigenschaften derselben Zeile berechnet – wie eine Formel in einer Tabellenkalkulation |
| Board-Ansicht | Darstellung als Spalten mit Karten, gruppiert nach einer Auswahl-Eigenschaft (Kanban) |
| Berechnung | Wert unter einer Tabellenspalte bzw. neben einer Board-Spalte, z. B. Summe oder Anzahl |

## Eigenschaften eines Deals

| Eigenschaft | Bedeutung | Typ in Notion | Beispiel „Rheinfels Logistik – 24 Räume“ |
| --- | --- | --- | --- |
| `Deal` | Kurzname | Titel | Rheinfels Logistik – 24 Räume |
| `Phase` | aktuelle Station in der Pipeline | Auswählen | Angebot versendet |
| `Wert` | erstes Vertragsjahr | Zahl (Euro) | 54.394 € |
| `Wahrscheinlichkeit` | angenommene Chance der Phase | Zahl (ohne Prozentformat) | 50 |
| `Abschlussdatum` | geplanter oder tatsächlicher Abschluss | Datum | 30.10.2026 |
| `Letzter Kontakt` | letzter Kundenkontakt | Datum | 17.09.2026 |
| `Wettbewerber` | genannter Mitbewerber | Auswählen | RaumPilot |
| `Verantwortlich` | zuständige Person im Vertrieb (fiktiv) | Auswählen | Jonas Brink |

Weitere Spalten (`Firma`, `Segment`, `Höchste Phase`, `Verlustgrund`, `Produkte`) erklärt [`deals-muster-erklaerung.md`](../material/notion/deals-muster-erklaerung.md); sie werden an Tag 2 ausgewertet.

| Phase | Qualifiziert | Bedarfsgespräch | Demo | Angebot versendet | Verhandlung | Gewonnen | Verloren |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Wahrscheinlichkeit | 10 | 20 | 40 | 50 | 70 | 100 | 0 |

Die Wahrscheinlichkeiten sind Annahmen des Vertriebs, keine Messung. Ob sie stimmen, prüft die Auswertung in Modul 5.

## Gewichtete Pipeline als Board

Echte CRMs zeigen die Pipeline als Board: eine Spalte je Phase, darin die Deals als Karten, am Spaltenkopf die Summe der Werte und die Anzahl der Deals. In Pipedrive steht über der Spalte „Proposal Made“ (Angebot gemacht) zum Beispiel „$81,712.09 · 2 deals“:

![Pipedrive-Ansicht „Deals“ als Board mit den Phasen-Spalten Qualified, First call, Demo Scheduled, Proposal Made und Negotiations Started; je Spalte Summe und Anzahl der Deals, darunter Deal-Karten mit Firma, Kontakt und Betrag; oben die Schaltfläche „+ Deal“](https://kb-cms.pipedriveassets.com/pv2.1.png)
_Quelle: Pipedrive Knowledge Base, „Pipeline view: manage deals lifecycle“ (https://support.pipedrive.com/en/article/pipeline-view), Screenshot © Pipedrive, abgerufen am 23.11.2026._

Notion baut dasselbe aus drei Teilen: einer Board-Ansicht gruppiert nach `Phase`, einer Formel-Eigenschaft `Gewichteter Wert` und der Berechnung „Summe“ je Spalte. Die Board-Ansicht entsteht über das Layout-Menü der Datenbank:

![Notion-Datenbank „Engineering tasks“ mit geöffnetem Menü „Layout“: Kacheln Table, Board, Timeline, Calendar, List und Gallery, darunter Schalter wie „Show vertical lines“ und „Wrap all columns“](https://images.ctfassets.net/spoqsaf9291f/nfJxbTGWexijW7BSAEPZL/a39afeb87300553e7fb97fc7006d320d/layouts.png?w=1280)
_Quelle: Notion-Hilfe, „Views, filters, sorts & groups“ (https://www.notion.com/help/views-filters-and-sorts), Screenshot © Notion Labs, abgerufen am 22.11.2026._

## Formel „Gewichteter Wert“

```text
prop("Wert") * prop("Wahrscheinlichkeit") / 100
```

| Teil | Bedeutung |
| --- | --- |
| `prop("Wert")` | Wert der Eigenschaft `Wert` in derselben Zeile; der Name muss exakt wie der Spaltenkopf geschrieben sein |
| `*` und `/` | mal und geteilt |
| `/ 100` | macht aus 50 (Prozent) den Faktor 0,5 |

Rechenbeispiel Rheinfels Logistik: 54.394 € × 50 ÷ 100 = **27.197 €**. Diese Zeile ist der Prüfwert nach dem Anlegen der Formel.

Im Formel-Editor stehen links die Eigenschaften der Datenbank zur Auswahl; ein Klick setzt sie als Baustein in die Formel ein:

![Notion-Formel-Editor: oben das Eingabefeld „Your formula“ und die Schaltfläche „Save“, links die Liste „Properties“ (Status, Name, Created By …), rechts Beispiele zur Eigenschaft Status wie Status == "Done"](https://images.ctfassets.net/spoqsaf9291f/3mfjLubTiV8GZ4wROlrShU/3bbd7a20ce0641828282e4991a1afbf6/Image_from_Notion__5_.png?w=1280)
_Quelle: Notion-Hilfe, „Formulas“ (https://www.notion.com/help/formulas), Screenshot © Notion Labs, abgerufen am 22.11.2026._

## Offene Pipeline und Datenqualität

- Zur offenen Pipeline zählen nur die Phasen Qualifiziert bis Verhandlung. Gewonnene Deals sind schon Umsatz, verlorene sind weg.
- Ohne Filter summiert Notion alle 60 Deals; die gewonnenen gehen dann mit 100 % in den gewichteten Wert ein.
- Filter für offene Deals: „Filter“ → `Phase` → „ist nicht“ (Is not) → Gewonnen und Verloren.
- Zahlen rechnet die Formel in Notion. Eine KI kommentiert sie ab Modul 5, rechnet sie aber nicht verlässlich selbst nach ([Lab 3.3](../m03-lead-generation/l03-lead-scoring.md)).
- Jede Auswertung ist nur so gut wie die Felder: Fehlen Phase, Wert oder Datum, fehlt der Deal in der Prognose.

## Übung: Pipeline-Board mit gewichteter Summe

**Material:** [`nordwind-deals.csv`](../material/notion/nordwind-deals.csv) (60 Deals, 13 Spalten), Anleitung [`notion-import-anleitung.md`](../material/notion/notion-import-anleitung.md) · **Werkzeug:** Notion im Browser

**Ausgangslage:** Die Vertriebsleitung von Nordwind will wissen, wie viel Umsatz in der offenen Pipeline steckt und wie viel davon nach den Phasen zu erwarten ist. Die Deals liegen als CSV-Export vor und kommen als zweite Datenbank in das Übungs-CRM.

1. Lade `nordwind-deals.csv` herunter, importiere sie wie in Lab 4.1 mit `/csv` in die Seite „Nordwind CRM“ als neue Datenbank und benenne sie in `Deals` um (60 Zeilen).
2. Setze die Typen: `Wert` Zahl mit Zahlenformat Euro, `Wahrscheinlichkeit` Zahl ohne Prozentformat, `Phase` Auswählen, `Abschlussdatum` und `Letzter Kontakt` Datum; die übrigen laut Importanleitung.
3. Lege die Formel an: Schieberegler-Symbol oben in der Datenbank → „Eigenschaften bearbeiten“ (Edit properties) → „Neue Eigenschaft“ (New property) → „Formel“ (Formula), Name `Gewichteter Wert`, „Formel bearbeiten“ (Edit formula), Formel von oben einfügen, Zahlenformat Euro; prüfe Rheinfels Logistik.
4. Lege die Board-Ansicht an: „+“ neben dem Ansichtsnamen → „Board“, „Gruppieren“ (Group) nach `Phase`, Spalten in die Reihenfolge der Pipeline ziehen, Ansicht `Pipeline` nennen.
5. Klicke je Spalte auf die graue Zahl neben dem Spaltentitel → `Gewichteter Wert` → „Summe“ (Sum) und addiere die fünf offenen Spalten.

Bezeichnungen je nach Version. _Quellen: Notion-Hilfe „Formeln“ (https://www.notion.com/de/help/formulas), „Board-Ansicht“ (https://www.notion.com/de/help/boards), „Ansichten, Filter und Sortierungen“ (https://www.notion.com/de/help/views-filters-and-sorts), alle abgerufen am 22.11.2026; Stand: 22.11.2026._

**Checkpoint:** Die Zeile „Rheinfels Logistik – 24 Räume“ zeigt 27.197 € als gewichteten Wert; das Board `Pipeline` hat sieben Spalten in Pipeline-Reihenfolge; die fünf offenen Spalten ergeben zusammen 376.922,70 € gewichtet.

**Erweiterung:** Tabellenansicht duplizieren, Filter `Phase` ist nicht Gewonnen und Verloren setzen und unter `Wert` und `Gewichteter Wert` „Berechnen“ (Calculate) → „Summe“ (Sum) wählen: 915.942 € bzw. 376.922,70 €.

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Werte aus [`deals-muster-erklaerung.md`](../material/notion/deals-muster-erklaerung.md), exakt nachgerechnet.

**Board `Pipeline`, Summen je Spalte**

| Phase | Deals | Summe Wert | Wahrscheinlichkeit | Summe Gewichteter Wert |
| --- | --- | --- | --- | --- |
| Qualifiziert | 5 | 123.946 € | 10 % | 12.394,60 € |
| Bedarfsgespräch | 7 | 192.345 € | 20 % | 38.469,00 € |
| Demo | 7 | 189.482 € | 40 % | 75.792,80 € |
| Angebot versendet | 6 | 184.260 € | 50 % | 92.130,00 € |
| Verhandlung | 5 | 225.909 € | 70 % | 158.136,30 € |
| **Offene Pipeline** | **30** | **915.942 €** | | **376.922,70 €** |
| Gewonnen | 8 | 244.233 € | 100 % | 244.233,00 € |
| Verloren | 22 | 579.025 € | 0 % | 0,00 € |

**Prüfwerte**

- Rheinfels Logistik – 24 Räume: 54.394 € × 50 ÷ 100 = 27.197 € ✓
- Größter offener Einzelposten: Polderland Verzekeringen – 40 Räume, Verhandlung, 91.478 €, gewichtet 64.034,60 €.
- Summe über alle 60 Deals ohne Filter: 621.155,70 € gewichtet – zu hoch, weil die gewonnenen 244.233 € mitzählen.

Aussage für die Vertriebsleitung: In der offenen Pipeline stecken 915.942 €; nach den angenommenen Phasen-Wahrscheinlichkeiten sind davon 376.922,70 € zu erwarten. Ob diese Annahmen stimmen, zeigt Lab 5.2.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Formel zeigt Fehler oder bleibt leer | `Wert` oder `Wahrscheinlichkeit` noch Text, oder Name in der Formel anders geschrieben | beide auf Zahl stellen; Namen exakt wie der Spaltenkopf |
| Rheinfels zeigt 2.719.700 € | `/ 100` fehlt in der Formel | Formel vollständig einfügen |
| Wahrscheinlichkeit zeigt 5.000 % | Zahlenformat Prozent gewählt | Zahlenformat auf „Zahl“ zurückstellen |
| Board gruppiert nach `Segment` | Notion wählt die erste Auswahl-Eigenschaft | „Gruppieren“ (Group) → `Phase` |
| Gesamtsumme 621.155,70 € | Gewonnen und Verloren mitgezählt | nur die fünf offenen Spalten addieren bzw. Filter setzen |
| Datumsfelder nach dem Typwechsel leer | Datumserkennung je nach Version | rückgängig machen (Strg+Z bzw. Cmd+Z) und als Text lassen; siehe Importanleitung |

## Fazit

- Phase, Wert und Wahrscheinlichkeit machen aus einer Deal-Liste eine Pipeline.
- Die Formel rechnet den gewichteten Wert, die Summe je Spalte ist die Prüfrechnung.
- Offene Pipeline heißt: ohne Gewonnen und Verloren.

> **Merksatz:** Ein Deal ohne Phase, Wert und Datum zählt in keiner Prognose.
