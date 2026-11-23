# Lab 6.2: Der erste Workflow: Anfrage-Formular → Notion

**Leitfragen:**

<details>
<summary>Welche Angaben braucht der Vertrieb von einer neuen Anfrage mindestens?</summary>

Firma, eine Ansprechperson mit Rolle und Kontaktweg, Größe (Mitarbeitende, Räume), Region und das Anliegen in eigenen Worten. Genau diese Felder fragt das Formular ab; sie passen zu den Eigenschaften der Datenbank `Leads`.

</details>

<details>
<summary>Wie viele Minuten vergehen heute zwischen Anfrage und CRM-Eintrag?</summary>

Oft Stunden bis Tage, je nachdem, wann jemand die Mail liest und abtippt. Mit dem Workflow steht der Lead Sekunden nach dem Absenden in Notion, ohne Tippfehler beim Übertragen.

</details>

<details>
<summary>Was passiert, wenn jemand das Feld Firma leer lässt?</summary>

Ohne Firma entsteht ein Lead ohne Namen, den niemand zuordnen kann. Deshalb ist Firma im Formular ein Pflichtfeld: Das Formular lässt sich ohne Eintrag nicht absenden.

</details>

- Ein Formular-Auslöser in n8n nimmt Anfragen entgegen; ein Notion-Knoten legt daraus einen neuen Eintrag in `Leads` an.
- Die Verbindung zu Notion läuft über eine interne Integration (in Notion heute „Connection“) mit geheimem Schlüssel; Notion zeigt n8n nur Datenbanken, die mit dieser Integration geteilt sind.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| Formular-Auslöser (n8n Form Trigger) | Knoten, der eine Formular-Webseite erzeugt und den Workflow startet, sobald jemand sie absendet |
| Test-URL / Produktions-URL | zwei Adressen desselben Formulars: die Test-URL für Probeläufe im Editor, die Produktions-URL für den echten Betrieb nach dem Veröffentlichen |
| Startdatei | importierbarer Workflow, in dem ein Teil schon fertig ist (hier das Formular); das Lab baut den Rest |
| Integration (Connection, Verbindung) | in Notion angelegter Zugang für ein fremdes Programm wie n8n; gilt nur für einen Arbeitsbereich; neuere Notion-Versionen sagen „Connection“ |
| Developer Mode | Schalter in den Notion-Einstellungen, der die Werkzeuge zum Anlegen eigener Verbindungen einblendet |
| Integration Secret (API token) | geheimer Schlüssel der Integration; Notion nennt ihn heute „API token“, ältere Anleitungen „Internal Integration Token“, n8n fragt nach dem „Internal Integration Secret“: derselbe Schlüssel. Wer ihn hat, kann die geteilten Notion-Daten lesen und ändern |
| Credential | in n8n gespeicherte Zugangsdaten für einen Dienst, hier der Notion-Schlüssel; einmal angelegt, in jedem Notion-Knoten wählbar |
| Teilen mit der Integration | Freigabe einer Notion-Seite oder Datenbank für die Integration über das Menü **Verbindungen** (Connections) |
| Ausdruck | Platzhalter in doppelten geschweiften Klammern, z. B. `{{ $json.Firma }}`; n8n setzt beim Lauf den Wert aus dem vorherigen Knoten ein (Details in Lab 6.3) |

## Zielbild des Workflows

```text
Website-Besucher ──▶ [Lead-Anfrage]  ──▶ [Lead in Notion anlegen] ──▶ Notion: Leads
                     n8n Form Trigger     Notion: Database Page → Create   neuer Eintrag
                     9 Felder             Quelle „Website“, Status „Neu“
```

## Aufbau des Formular-Auslösers „Lead-Anfrage“

Formulartitel „Anfrage an Nordwind Workspace“, Beschreibung „Übungsformular mit fiktiven Daten: nur erfundene Angaben eintragen.“, Schaltfläche „Anfrage senden“.

| Feld (Field Label) | Typ (Element Type) | Pflicht | Notion-Eigenschaft in `Leads` |
| --- | --- | --- | --- |
| Firma | Text | ja | Firma (Titel) |
| Website | Text | nein | Website (URL), ab Lab 8.1 gebraucht |
| Name | Text | ja | Ansprechperson |
| Rolle | Text | nein | Rolle |
| E-Mail | Email | ja | E-Mail |
| Mitarbeitende | Number | nein | Mitarbeitende (Zahl) |
| Anzahl Räume | Number | nein | **Räume** (Zahl) |
| Region | Dropdown: DE-Nord, DE-West, DE-Süd, DE-Ost, AT, CH, NL, Sonstige | ja | Region (Auswahl) |
| Nachricht | Textarea | ja | Nachricht |
| – | fester Wert | – | Quelle = „Website“, Status = „Neu“ |

Zwei Felder heißen im Formular anders als in Notion: „Name“ wird zu `Ansprechperson`, „Anzahl Räume“ zu `Räume`. Das Formular spricht die Besucher an, Notion den Vertrieb.

Der Formular-Auslöser hat zwei Adressen. Während des Bauens wird mit der **Test URL** gearbeitet: **Execute workflow** öffnet das Formular, nach dem Absenden läuft der Workflow einmal und die Daten sind im Editor sichtbar. Die **Production URL** gilt erst, wenn der Workflow veröffentlicht ist (Stand: 22.11.2026, Bezeichnungen je nach Version).

![n8n-Knoten „n8n Form Trigger“, Bereich „Form URLs“ mit den Reitern „Test URL“ und „Production URL“ und darunter einer Test-Adresse, oben die Schaltfläche „Test Step“](https://raw.githubusercontent.com/n8n-io/n8n-docs/main/docs/integrations/.gitbook/assets/form-urls.png)
_Quelle: n8n Docs, „n8n Form Trigger node“ (https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.formtrigger), © n8n GmbH, abgerufen am 23.11.2026._

## Notion-Verbindung in drei Schritten

Stand: 23.11.2026, Bezeichnung je nach Version. Notion nennt Integrationen inzwischen „Connections“ (Verbindungen) und den Schlüssel „API token“; n8n fragt nach dem „Internal Integration Secret“. Gemeint ist derselbe Schlüssel.

| Schritt | Wo | Was |
| --- | --- | --- |
| 1 Verbindung anlegen | Notion: **Einstellungen** (Settings) → **Verbindungen** (Connections) | **Developer Mode** einschalten → **+ New connection** → Name „n8n Kurs“, unter **Associated workspace** den eigenen Kurs-Arbeitsbereich wählen → speichern; danach **•••** neben „n8n Kurs“ → API token kopieren (**Copy API token**) |
| 2 Credential anlegen | n8n, im Notion-Knoten | **Credential to connect with** → **Create new credential** → API token in **Internal Integration Secret** einfügen → **Save**; n8n meldet „Connection tested successfully“ |
| 3 Datenbank teilen | Notion, Datenbank `Leads` als ganze Seite | **•••** oben rechts (je nach Version unter **More**) → **Verbindungen** (Connections) → **Add connections** bzw. **Connect to** → „n8n Kurs“ wählen und bestätigen |

Die Verbindung braucht die Fähigkeiten (Capabilities) Inhalte lesen, aktualisieren und einfügen (Read, Update, Insert content). Sie werden beim Anlegen bzw. in den Einstellungen der Verbindung im Notion-Entwicklerportal (Developer portal) festgelegt.

Ältere Oberfläche, so beschreibt es die n8n-Dokumentation: [notion.so/my-integrations](https://www.notion.so/my-integrations) → **+ New integration** → Name → **Submit**; Reiter **Capabilities**: Read content, Update content, Insert content → **Save changes**; Reiter **Secrets** → **Internal Integration Token** kopieren. Der Link führt am 23.11.2026 in das Entwicklerportal mit der Liste der Verbindungen.

Nur Arbeitsbereichs-Inhaber dürfen in den Tarifen Free und Plus Verbindungen anlegen; im eigenen Kurs-Arbeitsbereich ist das die eigene Person.

![Notion-Entwicklerportal „Basic information“ einer Integration: Feld Name „Fig's Internal Integration“, Logo-Upload und „Associated workspace“ mit Auswahl des Arbeitsbereichs](https://images.ctfassets.net/spoqsaf9291f/2wD6nPwE9Jcm7zHxH00YOw/78187a345065a2920c388143f3251d56/Integration_info.png)
_Quelle: Notion Help Center, „Notion API connections“ (https://www.notion.com/help/create-integrations-with-the-notion-api), © Notion Labs, abgerufen am 23.11.2026._

![Notion-Datenbank „Marketing tasks“ mit geöffnetem •••-Menü; unter „Connections“ ist „Connect to“ gewählt, daneben eine Suchliste mit Verbindungen wie Make und Pipedream](https://images.ctfassets.net/spoqsaf9291f/7zzSpPbv4zLVJBfFFSW5dU/23b05f9414fd0aa964b36205cc3b55ec/add_connections_to_pages.png)
_Quelle: Notion Help Center, „Add and manage connections with the API“ (https://www.notion.com/help/add-and-manage-connections-with-the-api), © Notion Labs, abgerufen am 23.11.2026._

_Quellen der Schritte: Notion Help Center, „Notion API connections“ (https://www.notion.com/help/create-integrations-with-the-notion-api) und „Add and manage connections with the API“ (https://www.notion.com/help/add-and-manage-connections-with-the-api); Notion Developers, „Connections and tokens“ (https://developers.notion.com/guides/connections-and-tokens/overview); n8n Docs, „Notion credentials“ (https://docs.n8n.io/integrations/builtin/credentials/notion); abgerufen am 23.11.2026._

### Integration Secret als rote Angabe der Datenampel

Nach der Datenampel aus [Lab 1.3](../m01-ai-sales-basics/l03-data-rules.md) ist ein Zugangsschlüssel **rot, immer**: Er gehört nur in das Credential-Feld von n8n. Nie in einen KI-Chat, eine Mail, eine Notion-Seite oder einen Screenshot. Bei Problemen wird nur die Fehlermeldung ohne Schlüssel weitergegeben. Ist ein Schlüssel versehentlich herausgegeben, wird er im Notion-Entwicklerportal neu erzeugt.

## Notion-Knoten „Lead in Notion anlegen“

| Einstellung | Wert |
| --- | --- |
| Credential to connect with | Notion-Credential aus Schritt 2 |
| Resource | **Database Page** (neuere Versionen zeigen dazu „Data Source“) |
| Operation | **Create** |
| Data Source / Database | **From list** → `Leads` (erscheint nur, wenn `Leads` mit der Integration geteilt ist) |
| Title | `{{ $json.Firma }}` |
| Properties | je Zeile **Add property**, Eigenschaft aus der Liste wählen, Wert zuordnen (Tabelle unten) |

| Notion-Eigenschaft (Typ) | Wert | Hinweis |
| --- | --- | --- |
| Website (url) | `{{ $json.Website }}` | **Ignore If Empty** einschalten: leere Adresse wird übersprungen |
| Ansprechperson (rich_text) | `{{ $json.Name }}` | |
| Rolle (rich_text) | `{{ $json.Rolle }}` | |
| E-Mail (email) | `{{ $json['E-Mail'] }}` | eckige Klammern, weil der Name einen Bindestrich enthält |
| Mitarbeitende (number) | `{{ $json.Mitarbeitende }}` | |
| Räume (number) | `{{ $json['Anzahl Räume'] }}` | Formularfeld „Anzahl Räume“ → Eigenschaft `Räume` |
| Region (select) | `{{ $json.Region }}` | Optionen in Notion exakt wie im Dropdown |
| Nachricht (rich_text) | `{{ $json.Nachricht }}` | |
| Quelle (select) | `Website` | fester Wert |
| Status (select) | `Neu` | fester Wert |

**Felder per Ziehen zuordnen:** Detailansicht des Notion-Knotens öffnen, links unter INPUT das Feld (z. B. `Firma`) mit der Maus greifen und in das Wertfeld ziehen. n8n schreibt den Ausdruck selbst; Tippfehler im Feldnamen entfallen. Damit INPUT Felder zeigt, muss das Formular einmal abgeschickt worden sein.

## Übung: Anfrage-Formular, das Leads in Notion anlegt

**Material:** Startdatei [`m06-l02-start.json`](../material/workflows/m06-l02-start.json), [`testanfragen.md`](../material/testanfragen.md) (T1, T2), Rückfallebene [`m06-l02-formular-notion.json`](../material/workflows/m06-l02-formular-notion.json) · **Werkzeug:** n8n Cloud, Notion

**Ausgangslage:** Website-Anfragen an Nordwind sollen ohne Abtippen in `Leads` landen, mit Quelle „Website“ und Status „Neu“. Bewertung und Antwort folgen in Modul 7 und 8. Abkürzung für die Zeit: Das Formular „Lead-Anfrage“ kommt mit allen neun Feldern fertig aus der Startdatei; selbst gebaut wird der Notion-Teil. Das Formular von Hand anzulegen ist die Erweiterung.

1. Importiere [`m06-l02-start.json`](../material/workflows/m06-l02-start.json) in einen neuen Workflow (Anleitung: [`workflows/README.md`](../material/workflows/README.md)), benenne ihn „Lead-Eingang“ und speichere ihn.
2. Klicke **Execute workflow**, sende im geöffneten Formular T1 aus `testanfragen.md` ab (Website leer lassen) und prüfe, ob „Lead-Anfrage“ die neun Felder unter OUTPUT zeigt.
3. Lege in Notion die Verbindung „n8n Kurs“ an, teile die Datenbank `Leads` mit ihr und kopiere den API token direkt in das neue Notion-Credential eines Notion-Knotens hinter „Lead-Anfrage“.
4. Richte diesen Knoten nach der Tabelle „Notion-Knoten“ ein, benenne ihn `Lead in Notion anlegen` und ordne die Werte per Ziehen zu; speichere den Workflow.
5. Klicke erneut **Execute workflow**, sende T1 und danach (nach einem weiteren **Execute workflow**) T2 ab und prüfe beide Einträge in Notion `Leads`.

**Checkpoint nach 20 Minuten:** Die Verbindung steht: Das Credential meldet „Connection tested successfully“, und unter **Data Source** ist `Leads` aus der Liste wählbar. Am Ende stehen in `Leads` zwei neue Einträge mit Quelle „Website“ und Status „Neu“.

**Rückfallebene:** [`m06-l02-formular-notion.json`](../material/workflows/m06-l02-formular-notion.json) importieren, im Knoten „Lead in Notion anlegen“ das eigene Credential und unter **Data Source** die Datenbank `Leads` wählen.

**Erweiterung:** Formular selbst bauen: in einem neuen Workflow den Auslöser **On form submission** (n8n Form Trigger) hinzufügen, in `Lead-Anfrage` umbenennen und Titel, Beschreibung, neun Felder und Schaltfläche nach der Tabelle „Aufbau des Formular-Auslösers“ einrichten; unter **Options** zusätzlich einen Abschlusstext setzen, z. B. „Danke, wir melden uns innerhalb eines Werktags.“

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Stand: 23.11.2026, gebaut mit n8n 2.48.7.

**Workflow:** `Lead-Anfrage` (n8n Form Trigger, aus der Startdatei) → `Lead in Notion anlegen` (Notion, Database Page → Create), Einstellungen wie in den Tabellen oben; identisch mit [`m06-l02-formular-notion.json`](../material/workflows/m06-l02-formular-notion.json).

**Credential:** Typ „Notion API“, Feld „Internal Integration Secret“ gefüllt (Wert nie weitergeben), Test erfolgreich.

**Neue Einträge in Notion `Leads`**

| Firma | Ansprechperson | Rolle | E-Mail | Mitarbeitende | Räume | Region | Quelle | Status |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| Steuerkanzlei Lorenzen & Partner mbB | Johanna Weiß | Kanzleimanagerin | j.weiss@lorenzen-partner.example | 48 | 6 | DE-Süd | Website | Neu |
| Brückner Antriebstechnik GmbH | Stefan Okafor | Leitung Facility Management | s.okafor@brueckner-antriebstechnik.example | 420 | 40 | DE-West | Website | Neu |

`Nachricht` enthält den Text der Anfrage („Guten Tag, wir möchten unsere sechs Besprechungsräume …“ bzw. „Wir beziehen am 01.02.2027 …“). `Website`, `Score`, `Stufe` und `Begründung` bleiben leer; die Bewertung folgt in Lab 7.2.

**Ausführungen:** Im Reiter **Executions** stehen die Läufe mit Status „Success“; der erste Lauf aus Aufgabe 2 endete nach „Lead-Anfrage“, weil der Notion-Knoten noch fehlte.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| `Leads` fehlt in der Liste **Data Source** | Datenbank nicht mit der Integration geteilt | in Notion **•••** → **Verbindungen** → „n8n Kurs“ hinzufügen, Liste neu laden |
| Credential-Test schlägt fehl | Schlüssel unvollständig kopiert oder mit Leerzeichen | Schlüssel neu kopieren und einfügen |
| **+ New connection** fehlt in den Einstellungen | Developer Mode aus oder keine Inhaber-Rolle im Arbeitsbereich | Developer Mode einschalten; im eigenen Kurs-Arbeitsbereich arbeiten |
| Formular-Seite meldet „waiting“ bzw. nichts passiert | Test-URL nur nach **Execute workflow** aktiv, und nur für eine Anfrage | vor jeder Testanfrage **Execute workflow** klicken |
| Notion-Fehler bei `Website` | leere Adresse an eine URL-Eigenschaft gesendet | **Ignore If Empty** einschalten |
| Region bleibt leer oder neue Option „DE-Sued“ | Schreibweise im Dropdown weicht von Notion ab | Optionen exakt wie in Notion (mit ü) anlegen |
| Mehrere Einträge für dieselbe Anfrage | Formular mehrfach abgeschickt | doppelte Einträge in Notion löschen |

## Fazit

- Formular-Auslöser plus Notion-Knoten ersetzen das Abtippen von Anfragen; der Lead steht Sekunden nach dem Absenden in Notion.
- Die Notion-Verbindung braucht drei Dinge: Integration, Credential, geteilte Datenbank.
- Das Integration Secret ist rot: nur ins Credential-Feld, nie in einen Chat.

> **Merksatz:** Ohne Teilen keine Daten: Notion zeigt n8n nur, was mit der Integration verbunden ist.
