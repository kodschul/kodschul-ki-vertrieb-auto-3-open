# Lab 6.3: Daten im Workflow verstehen und Fehler lesen

**Leitfragen:**

<details>
<summary>Wie wird einer Kollegin erklärt, welche Angabe aus einem Formular in welches CRM-Feld gehört?</summary>

Mit einer Zuordnung Feld für Feld: „Anzahl Räume“ aus dem Formular kommt in `Räume` in Notion. In n8n ist genau diese Zuordnung ein Ausdruck je Notion-Eigenschaft, der per Ziehen entsteht.

</details>

<details>
<summary>Was soll mit Anfragen passieren, die nicht ins Zielkundenprofil passen?</summary>

Sie sollen nicht verschwinden, aber auch nicht wie ein normaler Lead behandelt werden. Eine Regel im Workflow markiert sie, z. B. Region außerhalb von DACH und den Niederlanden → Status „Prüfen“.

</details>

<details>
<summary>Woran wäre zu erkennen, dass eine Automatisierung seit Tagen nichts mehr einträgt?</summary>

Am Ausführungsprotokoll: Dort steht jeder Lauf mit Erfolg oder Fehler. Rote Einträge oder gar keine neuen Läufe sind das Warnsignal; eine automatische Benachrichtigung folgt in Lab 9.3.

</details>

- Daten fließen als Felder von Knoten zu Knoten; Ausdrücke wie `{{ $json.Firma }}` holen ein Feld aus dem vorherigen Knoten.
- Fehler stehen im Klartext am roten Knoten und im Ausführungsprotokoll; die meisten sind falsche Namen, fehlende Freigaben oder falsche Datentypen.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| Item (Datensatz) | ein Paket Daten, das durch den Workflow wandert, z. B. eine Formular-Anfrage; „1 item“ auf einer Verbindung heißt: ein Datensatz |
| Feld | ein Name mit Wert innerhalb eines Items, z. B. `Region: DE-Süd` |
| JSON | Textformat für Daten: Feldname in Anführungszeichen, Doppelpunkt, Wert; n8n speichert jedes Item so |
| `$json` | im Ausdruck die Daten des Items, das gerade aus dem vorherigen Knoten hereinkommt |
| Felder bearbeiten (Edit Fields, Set) | Knoten, der Felder hinzufügt oder ändert, z. B. `Status = Prüfen` |
| Wenn (If) | Knoten mit Bedingung und zwei Ausgängen: `true` (erfüllt) und `false` (nicht erfüllt) |
| Testdaten festhalten (Pin data) | Ausgabe eines Knotens speichern und bei jedem Testlauf wiederverwenden, statt das Formular neu auszufüllen |
| Ausführungsprotokoll | Liste aller Läufe im Reiter **Executions**, je mit Status, Zeit und den Daten jedes Knotens |

## Eine Formular-Anfrage als Daten

Jede abgeschickte Anfrage wird zu einem Item. Die Detailansicht zeigt es auf drei Arten (Stand: 22.11.2026, Bezeichnungen je nach Version):

| Ansicht | Zeigt | Gut für |
| --- | --- | --- |
| **Schema** | Feldnamen mit Typ-Symbol und Beispielwert | Felder zum Ziehen finden |
| **Table** | Felder als Spalten, Items als Zeilen | mehrere Items vergleichen |
| **JSON** | die Rohdaten | genaue Werte, Leerzeichen, Zahl oder Text |

T1 aus [`testanfragen.md`](../material/testanfragen.md) in der Ansicht **JSON** des Knotens „Lead-Anfrage“ (Zeitstempel beispielhaft):

```json
[
  {
    "Firma": "Steuerkanzlei Lorenzen & Partner mbB",
    "Website": "",
    "Name": "Johanna Weiß",
    "Rolle": "Kanzleimanagerin",
    "E-Mail": "j.weiss@lorenzen-partner.example",
    "Mitarbeitende": 48,
    "Anzahl Räume": 6,
    "Region": "DE-Süd",
    "Nachricht": "Guten Tag, wir möchten unsere sechs Besprechungsräume für Videokonferenzen mit Mandanten ausstatten. …",
    "submittedAt": "2026-12-01T09:14:32.000+01:00",
    "formMode": "test"
  }
]
```

| Teil | Bedeutung |
| --- | --- |
| `[ … ]` | Liste der Items; hier genau eines |
| `"Firma": "Steuerkanzlei …"` | Feld mit Text in Anführungszeichen; Name = Feldbeschriftung im Formular |
| `"Mitarbeitende": 48` | Zahl ohne Anführungszeichen; passt zu einer Notion-Eigenschaft vom Typ Zahl |
| `"Website": ""` | leeres Feld; deshalb „Ignore If Empty“ im Notion-Knoten (Lab 6.2) |
| `submittedAt`, `formMode` | von n8n ergänzt (Zeitpunkt, Test- oder Produktionsmodus); für jetzt unwichtig |

In der Ansicht **Table** erscheinen dieselben Felder als Spalten. Verschachtelte Werte stehen eingerückt und lassen sich ebenfalls ziehen:

![n8n-Ausgabe als Tabelle mit den Spalten „name“ und „nested“ für zwei Items; ein Hinweis erklärt, dass example-number-field und example-string-field per Ziehen einem Parameter zugeordnet werden können](https://raw.githubusercontent.com/n8n-io/n8n-docs/main/docs/build/.gitbook/assets/nested-data.png)
_Quelle: n8n Docs, „Understand n8n's data structure“ (https://docs.n8n.io/build/work-with-data/understand-n8ns-data-structure), © n8n GmbH, abgerufen am 23.11.2026._

## Ausdrücke per Drag-and-drop einfügen

Ein Ausdruck steht in doppelten geschweiften Klammern. n8n ersetzt ihn beim Lauf durch den Wert des Feldes.

| Ausdruck | Ergebnis bei T1 | Wann so geschrieben |
| --- | --- | --- |
| `{{ $json.Firma }}` | Steuerkanzlei Lorenzen & Partner mbB | Feldname ohne Leerzeichen und Sonderzeichen |
| `{{ $json['Anzahl Räume'] }}` | 6 | Feldname mit Leerzeichen oder Bindestrich (auch `E-Mail`) |
| `{{ $json.Region }}` | DE-Süd | |

Wird ein Feld aus INPUT in ein Wertfeld gezogen, schreibt n8n den passenden Ausdruck und zeigt darunter das Ergebnis für das aktuelle Item. Tippfehler entfallen:

![n8n-Detailansicht „Edit Fields“: links INPUT mit Feldern city, date, temp_c; in der Mitte das Feld „report“ mit dem Ausdruck „The temperature in {{ $json.city }}“ und darunter das Ergebnis „The temperature in berlin“](https://raw.githubusercontent.com/n8n-io/n8n-docs/main/docs/get-started/.gitbook/assets/build-your-first-workflow-optional-04-03.png)
_Quelle: n8n Docs, „Build your first workflow“ (https://docs.n8n.io/build-your-first-workflow), © n8n GmbH, abgerufen am 23.11.2026._

## Bedingung mit „Wenn“ und „Felder bearbeiten“

Anfragen von außerhalb DACH und den Niederlanden (Region „Sonstige“) bekommen Status „Prüfen“, alle anderen Status „Neu“. Der Wenn-Knoten teilt, zwei Edit-Fields-Knoten setzen das Feld `Status`, der Notion-Knoten übernimmt es.

```text
[Lead-Anfrage] ──▶ [Region außerhalb DACH/NL?] ──true──▶  [Status Prüfen] ──┐
                    Region ist gleich „Sonstige“                               ├──▶ [Lead in Notion anlegen]
                                                 ──false─▶ [Status Neu]    ──┘     Status = {{ $json.Status }}
```

| Knoten | Einstellung |
| --- | --- |
| Region außerhalb DACH/NL? (If) | Bedingung: `{{ $json.Region }}` · **String** → **is equal to** · `Sonstige` |
| Status Prüfen (Edit Fields) | Feld `Status`, Typ String, Wert `Prüfen`; **Include Other Input Fields** an |
| Status Neu (Edit Fields) | Feld `Status`, Typ String, Wert `Neu`; **Include Other Input Fields** an |
| Lead in Notion anlegen | Eigenschaft `Status` (select): `{{ $json.Status }}` statt fest „Neu“; alles andere wie in Lab 6.2 |

**Include Other Input Fields** lässt alle Formularfelder durch den Edit-Fields-Knoten weiterlaufen. Ist es aus, kommt nur `Status` beim Notion-Knoten an, und Firma, Region und Nachricht bleiben leer.

![n8n-Workflow: Start → Set → IF; vom Ausgang true geht eine Linie zu „True Path“, vom Ausgang false zu „False Path“; beide laufen in einen Merge-Knoten, auf den Verbindungen steht jeweils „1 item“](https://raw.githubusercontent.com/n8n-io/n8n-docs/main/docs/reusable-content/.gitbook/assets/if-merge-node.png)
_Quelle: n8n Docs, „If node“ (https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.if), © n8n GmbH, abgerufen am 23.11.2026._

Im Kurs laufen beide Zweige ohne Merge-Knoten direkt in denselben Notion-Knoten; jedes Item kommt nur über einen Zweig.

## Testdaten festhalten und Ausführungen lesen

| Werkzeug | So geht es | Wofür |
| --- | --- | --- |
| **Pin data** | Knoten ausführen, im Bereich OUTPUT auf das Stecknadel-Symbol klicken; es erscheint „This data is pinned“ | weitere Testläufe ohne neues Formular; gepinnte Daten gelten nur im Editor, nie im echten Betrieb |
| **Executions** | Reiter oben auf der Arbeitsfläche; Liste mit Status (Success, Error), Filter nach Status | sehen, ob und wann der Workflow lief, und Fehler finden |
| **Debug in editor** | fehlgeschlagene Ausführung öffnen → **Debug in editor** | Daten des Fehlerlaufs in den Editor holen, korrigieren, erneut ausführen |

_Quellen: n8n Docs, „Pinning and mocking data“ (https://docs.n8n.io/build/work-with-data/pin-and-mock-data), „Workflow-level executions list“ (https://docs.n8n.io/build/understand-workflows/understand-executions/view-executions-for-a-single-workflow), „Debug and re-run past executions“ (https://docs.n8n.io/build/understand-workflows/understand-executions/debug-executions); abgerufen am 23.11.2026._

## Häufige Fehler im Notion-Knoten

Ein Fehler färbt den Knoten rot; ein Klick darauf zeigt die Meldung von Notion. Wortlaut je nach Version, prüfen:

| Fehler | Typische Meldung | Ursache | Lösung |
| --- | --- | --- | --- |
| Eigenschaftsname falsch | „Anzahl Räume is not a property that exists.“ | Formular-Feldname statt Notion-Eigenschaft verwendet | Eigenschaft aus der Liste wählen (`Räume`) |
| Datenbank nicht geteilt | „Could not find database with ID: … Make sure the relevant pages and databases are shared with your integration.“ (mit der neueren Data-Source-Schnittstelle ggf. „data source“ statt „database“; Wortlaut je nach Version) | Integration hat keinen Zugriff | in Notion **•••** → **Verbindungen** → Integration hinzufügen |
| falscher Datentyp | Meldung, dass für die Eigenschaft eine Zahl erwartet wird (z. B. „… should be a number …“) | Text in eine Zahl-Eigenschaft geschrieben, z. B. „ca. 120“ oder ein falsch zugeordnetes Textfeld | richtiges Feld zuordnen; Formularfeld als Number anlegen, in Notion Typ Zahl |
| Auswahl-Option falsch geschrieben | keine Meldung, aber neue Option in Notion (z. B. „Pruefen“) | Wert weicht von der Notion-Option ab | Schreibweise exakt wie in Notion |

## Übung: Bedingung einbauen und einen Fehler beheben

**Material:** Workflow „Lead-Eingang“ aus Lab 6.2, [`testanfragen.md`](../material/testanfragen.md) (T1, T3, T4), Rückfallebene [`m06-l03-bedingung.json`](../material/workflows/m06-l03-bedingung.json), Erweiterung [`m06-fehler.json`](../material/workflows/m06-fehler.json) · **Werkzeug:** n8n Cloud, Notion

**Ausgangslage:** Anfragen aus Regionen außerhalb von DACH und NL sollen mit Status „Prüfen“ in Notion landen. Danach wird im selben Workflow ein Fehler absichtlich eingebaut, gelesen und behoben.

1. Füge im Workflow „Lead-Eingang“ zwischen „Lead-Anfrage“ und „Lead in Notion anlegen“ einen **If**-Knoten `Region außerhalb DACH/NL?` ein: `Region` per Ziehen ins linke Feld, **String** → **is equal to**, rechts `Sonstige`.
2. Hänge an `true` den Edit-Fields-Knoten `Status Prüfen` und an `false` den Knoten `Status Neu` (Einstellungen aus der Tabelle oben), verbinde beide mit „Lead in Notion anlegen“ und setze dort `Status` auf `{{ $json.Status }}`.
3. Führe den Workflow zweimal aus, sende T4 (Region Sonstige) und T3 (Region DE-Nord) und prüfe in Notion: Rankfix Online-Marketing hat Status „Prüfen“, Texterei Lindqvist Status „Neu“.
4. Baue absichtlich einen Fehler ein: Ziehe im Knoten „Lead in Notion anlegen“ bei der Eigenschaft `Räume` das Feld `Firma` statt `Anzahl Räume` in das Wertfeld, führe aus, sende T1 und lies die Fehlermeldung am roten Knoten.
5. Ordne `Räume` wieder `{{ $json['Anzahl Räume'] }}` zu (per Ziehen), führe erneut aus, sende T1 und prüfe im Reiter **Executions** einen Lauf „Error“ und einen Lauf „Success“.

**Checkpoint:** `Leads` enthält Rankfix mit Status „Prüfen“ und Texterei Lindqvist mit Status „Neu“; nach der Korrektur trägt „Lead-Eingang“ T1 mit `Räume` = 6 ein, und **Executions** zeigt den Fehlerlauf davor.

**Rückfallebene:** [`m06-l03-bedingung.json`](../material/workflows/m06-l03-bedingung.json) importieren, Credential und Data Source `Leads` wählen.

**Erweiterung:** Zweites Fehlerbild: [`m06-fehler.json`](../material/workflows/m06-fehler.json) in einen neuen Workflow importieren, Credential und **Data Source** `Leads` wählen, T1 senden, die Meldung am roten Knoten lesen und die Zeile `Anzahl Räume` durch die Eigenschaft `Räume` aus der Liste ersetzen. Oder: In „Lead-Anfrage“ die Ausgabe von T3 pinnen, in der JSON-Ansicht `Region` auf `Sonstige` ändern und ohne Formular erneut ausführen; danach die Pin-Daten entfernen.

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Stand: 23.11.2026, gebaut mit n8n 2.48.7.

**Workflow „Lead-Eingang“ nach Lab 6.3** (entspricht [`m06-l03-bedingung.json`](../material/workflows/m06-l03-bedingung.json)):

`Lead-Anfrage` → `Region außerhalb DACH/NL?` → `true`: `Status Prüfen` / `false`: `Status Neu` → `Lead in Notion anlegen`

| Knoten | Einstellung |
| --- | --- |
| Region außerhalb DACH/NL? | `{{ $json.Region }}` is equal to `Sonstige` (String) |
| Status Prüfen | `Status` = `Prüfen`, Include Other Input Fields an |
| Status Neu | `Status` = `Neu`, Include Other Input Fields an |
| Lead in Notion anlegen | wie Lab 6.2, nur `Status` = `{{ $json.Status }}` |

**Neue Einträge in `Leads`**

| Firma | Region | Räume | Quelle | Status |
| --- | --- | --- | --- | --- |
| Rankfix Online-Marketing | Sonstige | 0 | Website | Prüfen |
| Texterei Lindqvist | DE-Nord | 1 | Website | Neu |

Bei T4 zeigt die Verbindung von `true` „1 item“, `false` bleibt leer; bei T3 umgekehrt.

**Absichtlicher Fehler (Aufgabe 4–5):** Mit `{{ $json.Firma }}` in `Räume` wird „Lead in Notion anlegen“ rot; die Meldung sagt sinngemäß, dass für `Räume` eine Zahl erwartet wird, statt „Steuerkanzlei Lorenzen & Partner mbB“ (Wortlaut je nach Version). Nach der Korrektur steht Steuerkanzlei Lorenzen & Partner mbB mit `Räume` = 6 und Status „Neu“ in Notion (ein zweiter Eintrag neben dem aus Lab 6.2, darf gelöscht werden), und **Executions** zeigt einen Lauf „Error“ und einen Lauf „Success“.

**Erweiterung `m06-fehler.json`:** Der Knoten „Lead in Notion anlegen“ wird rot mit der Meldung „Anzahl Räume is not a property that exists.“ (Wortlaut je nach Version). Ursache: Die Eigenschaft heißt in Notion `Räume`; „Anzahl Räume“ ist nur die Beschriftung im Formular.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Lead in Notion ohne Firma und Nachricht, nur Status gesetzt | **Include Other Input Fields** im Edit-Fields-Knoten aus | Schalter einschalten, erneut testen |
| Rankfix landet mit Status „Neu“ | Vergleichswert mit Tippfehler oder Leerzeichen („Sonstige “) | Wert exakt `Sonstige`; Ergebnis-Vorschau unter dem Feld prüfen |
| Formular öffnet sich nicht mehr beim Testen | Ausgabe von „Lead-Anfrage“ ist gepinnt | Pin entfernen (Stecknadel erneut klicken) |
| Ausdruck zeigt `[undefined]` | Feldname falsch geschrieben oder Leerzeichen ohne eckige Klammern | Feld per Ziehen neu zuordnen |
| Importierter Workflow meldet sofort einen Fehler zur Datenbank | Platzhalter `HIER-DATENBANK-AUSWAEHLEN` noch gesetzt | unter **Data Source** `Leads` aus der Liste wählen |

## Fazit

- Ein Item ist ein Datensatz aus Feldern; Schema, Table und JSON zeigen dasselbe unterschiedlich.
- Ausdrücke per Ziehen verbinden Formularfelder mit Notion-Eigenschaften; Namen mit Leerzeichen stehen in eckigen Klammern.
- Wenn-Knoten und Edit Fields bilden Regeln ab; Fehlermeldungen und das Ausführungsprotokoll zeigen, wo es hakt.

> **Merksatz:** Erst die Fehlermeldung lesen, dann klicken.
