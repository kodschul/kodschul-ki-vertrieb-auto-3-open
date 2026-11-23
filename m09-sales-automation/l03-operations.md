# Lab 9.3: Workflows betreiben und sichern

**Leitfragen:**

<details>
<summary>Wer merkt es heute, wenn ein Prozess im Vertrieb still ausfällt?</summary>

Meist niemand, bis ein Kunde nachfragt, warum keine Antwort kam. Ein Workflow, der nachts scheitert, meldet sich nicht von selbst; dafür braucht es eine Fehlermeldung an einer Stelle, die jemand täglich ansieht.

</details>

<details>
<summary>Was passiert mit dem Gebauten, wenn das Testkonto abläuft?</summary>

Nach 14 Tagen löscht n8n die Test-Instanz mit allen Workflows. Wer die Workflows vorher als Datei herunterlädt, kann sie in jede andere n8n-Instanz importieren.

</details>

<details>
<summary>Wer sollte im Team für eine Automatisierung zuständig sein?</summary>

Eine benannte Person je Workflow, mit Vertretung: Sie bekommt die Fehlermeldungen, prüft die Ergebnisse stichprobenartig und entscheidet über Änderungen. Ohne Zuständigkeit verwaist ein Workflow, sobald die Person geht, die ihn gebaut hat.

</details>

- Ein Workflow im Betrieb braucht drei Dinge: ein Protokoll, in dem jeder Lauf nachzulesen ist, eine Meldung bei Fehlern und eine verantwortliche Person.
- Gesichert wird ein Workflow als JSON-Datei; sie lässt sich in jede andere n8n-Instanz importieren.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| Ausführungsprotokoll (Executions) | Liste aller Läufe eines Workflows mit Zeit, Status (Success, Error) und den Daten jedes Knotens – wie das Fahrtenbuch eines Firmenwagens |
| Fehler-Workflow (Error Workflow) | eigener Workflow, den n8n startet, wenn ein anderer Workflow scheitert |
| Error Trigger | Auslöser des Fehler-Workflows; liefert Name des gescheiterten Workflows, letzten Knoten, Fehlermeldung und Link zur Ausführung |
| Export | Workflow als JSON-Datei herunterladen; JSON ist ein Textformat für strukturierte Daten |

## Ausführungsprotokoll in n8n

Jeder Workflow hat oben den Reiter „Executions“ (Lab 6.3); alle Läufe aller Workflows zeigt der gleichnamige Reiter in der Übersicht „Personal“. Ein Lauf lässt sich öffnen, um Ein- und Ausgaben jedes Knotens zu sehen, und nach Behebung der Ursache über „Retry“ wiederholen.

![n8n-Übersicht „Personal“ mit den Reitern Workflows, Agents, Credentials, Executions, Variables und Data tables; in der Liste der Workflow „weather log“ mit dem Hinweis „Published“](https://raw.githubusercontent.com/n8n-io/n8n-docs/main/docs/get-started/.gitbook/assets/build-your-first-workflow-optional-01-01.png)
_Quelle: n8n Docs, „Build your first workflow“ (https://docs.n8n.io/build-your-first-workflow), © n8n, abgerufen am 23.11.2026._

## Fehler-Workflow mit Meldung in Notion

```text
Gesprächsnotiz → CRM  ──✗ Fehler in „Lead in Notion aktualisieren“
        │  Workflow-Einstellung „Error Workflow“ = Fehler-Workflow
        ▼
Fehler-Workflow:  Bei Fehler (Error Trigger) ──► Fehler in Notion melden
                                                 (neue Seite „Fehler <Workflow> <Zeit>“ unter „Nordwind CRM“)
```

| Feld des Error Trigger | Inhalt | Verwendet im Seitentext |
| --- | --- | --- |
| `workflow.name` | Name des gescheiterten Workflows | Titel und „Workflow:“ |
| `execution.lastNodeExecuted` | Knoten, bei dem der Fehler auftrat | „Letzter Knoten:“ |
| `execution.error.message` | Fehlermeldung | „Fehlermeldung:“ |
| `execution.url` | Link zum Lauf im Ausführungsprotokoll | „Ausführung:“ |

Regeln aus der n8n-Dokumentation (Stand 22.11.2026, Quellen: [Error Trigger](https://docs.n8n.io/integrations/builtin/core-nodes/n8n-nodes-base.errortrigger), [Error handling](https://docs.n8n.io/build/flow-logic/handle-errors-gracefully)):

- Der Fehler-Workflow beginnt mit dem Error Trigger, wird veröffentlicht und in jedem überwachten Workflow unter ⋯ → Settings → „Error Workflow“ ausgewählt. Ein Fehler-Workflow kann viele Workflows überwachen.
- Er startet nur bei automatischen Läufen, nicht bei „Execute workflow“. Zum Testen läuft der überwachte Workflow deshalb veröffentlicht, ein Formular über die Production URL (die Test URL gilt nur während „Execute workflow“).
- Läufe des Fehler-Workflows zählen nicht als Ausführungen im Tarif.

![Ältere n8n-Oberfläche: Fenster „Workflow Executions“ mit zwei Läufen zur selben Sekunde: „Workflow with error“ mit Status Error und Modus trigger, darüber „Error Workflow“ mit Status Success und Modus error](https://storage.ghost.io/c/0d/78/0d78b34c-0c5f-4975-900e-61d00ccb1c2d/content/images/2021/03/executions.png)
_Quelle: n8n Blog, „Creating error workflows in n8n“ (https://blog.n8n.io/creating-error-workflows-in-n8n/), Oberfläche von 2020, Prinzip unverändert, © n8n, abgerufen am 23.11.2026._

## Workflows sichern und umziehen

- **Download:** im geöffneten Workflow das Workflow-Menü ⋯ oben rechts → „Download“; n8n speichert eine JSON-Datei.
- **Import:** in jeder anderen n8n-Instanz ⋯ → „Import from File“ (Anleitung: [`workflows/README.md`](../material/workflows/README.md)). Verbindungen (Credentials) reisen nicht mit und werden neu gewählt.
- **Inhalt der Datei:** alle Knoten, Einstellungen und Prompts, dazu Namen und IDs der verwendeten Verbindungen, aber keine Schlüssel. Vor dem Weitergeben Verbindungsnamen prüfen.
- **Nach der Testphase:** n8n löscht die Instanz; Workflows lassen sich noch 90 Tage in der Cloud-Konsole unter „Export“ herunterladen, danach sind sie endgültig gelöscht.

Stand 22.11.2026, Quellen: [n8n Docs – Export and import](https://docs.n8n.io/build/manage-workflows/export-and-import), [Download workflows](https://docs.n8n.io/deploy/use-n8n-cloud/download-workflows). Tarife, Kosten und Zuständigkeiten je Workflow stehen unter [Vertiefung](#vertiefung).

## Übung: Fehler-Workflow einrichten und alle Workflows sichern

**Material:** Workflows aus Lab 8.2, 9.1 und 9.2, [`gespraechsnotiz-roh.md`](../material/gespraechsnotiz-roh.md), [`m09-l03-fehler-workflow.json`](../material/workflows/m09-l03-fehler-workflow.json) · **Werkzeug:** n8n, Notion, Dateiablage des Laptops

**Ausgangslage:** Drei Workflows laufen; jeder Fehler soll als Seite in Notion auftauchen, und vor dem Ende der Testphase liegt alles als Datei vor.

> **Standardstart:** Den Fehler-Workflow aus `m09-l03-fehler-workflow.json` importieren ([Anleitung](../material/workflows/README.md)) und in Schritt 2 nur Notion-Verbindung und Link zu „Nordwind CRM“ einstellen. Vorrang hat Schritt 5 (die Testphase läuft ab); was nicht fertig wird, folgt im 5-Minuten-Flex-Puffer am Ende von Modul 9.

1. Öffne im Workflow „Pipeline-Briefing“ den Reiter „Executions“, öffne den Lauf aus Lab 9.2 und klicke auf „Briefing schreiben“, um Eingabe und Ausgabe zu sehen.
2. Lege den Workflow „Fehler-Workflow“ an (oder importiere ihn): Auslöser „Error Trigger“ (Name „Bei Fehler“) → Notion-Knoten „Fehler in Notion melden“ nach der Tabelle unten; klicke auf „Publish“.
3. Öffne „Gesprächsnotiz → CRM“, wähle ⋯ → Settings → Error Workflow „Fehler-Workflow“, speichere, klicke auf „Publish“ und kopiere im Knoten „Gesprächsnotiz“ die Production URL.
4. Benenne in Notion in `Leads` die Eigenschaft `Status` vorübergehend in `Status alt` um, sende über die Production URL die Rheinpark-Notiz ab, prüfe „Executions“ (Fehler „Status is not a property that exists“, Wortlaut je nach Version) und die neue Seite „Fehler …“ unter „Nordwind CRM“ und benenne `Status alt` danach wieder in `Status` um.
5. Lade „Lead-Eingang“, „Gesprächsnotiz → CRM“, „Pipeline-Briefing“ und „Fehler-Workflow“ je über ⋯ → „Download“ herunter und speichere die vier Dateien in einem Ordner `n8n-sicherung`.

| Knoten | Einstellung | Wert |
| --- | --- | --- |
| Fehler in Notion melden (Notion) | Resource · Operation | `Page` · `Create` |
| | Parent Page | Link zur Seite „Nordwind CRM“ |
| | Title | `Fehler {{ $json.workflow.name }} {{ $now.toFormat('dd.MM.yyyy HH:mm') }}` |
| | Inhalt (Markdown) | `**Workflow:** {{ $json.workflow.name }}`, `**Letzter Knoten:** {{ $json.execution.lastNodeExecuted }}`, `**Fehlermeldung:** {{ $json.execution.error.message }}`, `**Ausführung:** {{ $json.execution.url }}`, je eine Zeile, dazu der Satz „Die verantwortliche Person prüft den Fehler, behebt die Ursache und startet die Ausführung erneut.“ |

Bezeichnungen Stand 22.11.2026, n8n 2.48 (Bezeichnung je nach Version).

**Variante für Schritt 4:** Statt umzubenennen lässt sich bei `Leads` die Verbindung zur Integration trennen (⋯ → Verbindungen), sofern Notion das bei der Datenbank anbietet. Meist erbt `Leads` die Verbindung von der Seite „Nordwind CRM“; dann fehlt „Trennen“, und die Umbenennung ist der sichere Weg.

![Notion-Datenbank „Marketing tasks“ mit geöffnetem ⋯-Menü; unten der Abschnitt „Connections“ mit „Connect to“ und der Liste verfügbarer Verbindungen sowie „Manage connections“](https://images.ctfassets.net/spoqsaf9291f/7zzSpPbv4zLVJBfFFSW5dU/23b05f9414fd0aa964b36205cc3b55ec/add_connections_to_pages.png?w=1280)
_Quelle: Notion Help Center, „Add & manage connections in Notion“ (https://www.notion.com/help/add-and-manage-connections-with-the-api), © Notion Labs, abgerufen am 23.11.2026._

**Checkpoint:** Unter „Nordwind CRM“ steht eine Seite „Fehler Gesprächsnotiz → CRM <Datum Uhrzeit>“ mit Fehlermeldung und Link; die Eigenschaft in `Leads` heißt wieder `Status`; im Ordner `n8n-sicherung` liegen vier JSON-Dateien.

**Erweiterung:** Trage den Fehler-Workflow auch in „Lead-Eingang“ und „Pipeline-Briefing“ als Error Workflow ein.

**Rückfallebene:** [`m09-l03-fehler-workflow.json`](../material/workflows/m09-l03-fehler-workflow.json) importieren und einstellen ([Anleitung](../material/workflows/README.md)).

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Beispiel, Stand 22.11.2026; Datum, Uhrzeit und IDs je Lauf anders.

**Executions von „Gesprächsnotiz → CRM“ und „Fehler-Workflow“**

| Workflow | Status | Modus (sinngemäß, Bezeichnung je nach Version) | Gestartet |
| --- | --- | --- | --- |
| Fehler-Workflow | Success | Fehler-Workflow | 10:52:07 |
| Gesprächsnotiz → CRM | Error | Produktion (Formular) | 10:52:06 |
| Gesprächsnotiz → CRM | Success | Manuell | 09:31:40 (Test aus Lab 9.1) |

**Seite „Fehler Gesprächsnotiz → CRM 03.12.2026 10:52“ unter „Nordwind CRM“**

> **Workflow:** Gesprächsnotiz → CRM
>
> **Letzter Knoten:** Lead in Notion aktualisieren
>
> **Fehlermeldung:** Status is not a property that exists. (Wortlaut je nach Version)
>
> **Ausführung:** https://<eigene-instanz>.app.n8n.cloud/workflow/…/executions/…
>
> Die verantwortliche Person prüft den Fehler, behebt die Ursache und startet die Ausführung erneut.

Nach dem Zurückbenennen von `Status alt` in `Status` läuft der Lauf über „Retry“ im Ausführungsprotokoll erfolgreich durch.

**Ordner `n8n-sicherung`**

```text
n8n-sicherung/
├── Fehler-Workflow.json
├── Gesprächsnotiz → CRM.json
├── Lead-Eingang.json
└── Pipeline-Briefing.json
```

Dateinamen je nach Browser leicht anders. Jede Datei beginnt mit `{"name": "…", "nodes": [ …` und enthält keine Schlüssel.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Keine Seite „Fehler …“, obwohl der Lauf scheiterte | Lauf mit „Execute workflow“ gestartet; der Fehler-Workflow reagiert nur auf automatische Läufe | Workflow veröffentlichen, über die Production URL absenden |
| Keine Seite „Fehler …“, Lauf über Production URL | Fehler-Workflow nicht veröffentlicht oder in den Settings nicht ausgewählt | „Publish“ im Fehler-Workflow; ⋯ → Settings → Error Workflow prüfen |
| Lauf über Production URL endet mit Success, kein Fehler | Eigenschaft in `Deals` statt in `Leads` umbenannt | in `Deals` zurückbenennen, in `Leads` `Status` → `Status alt` |
| Fehler-Workflow scheitert selbst | Seite „Nordwind CRM“ nicht mit der Integration verbunden (z. B. nach der Variante „Trennen“) | „Nordwind CRM“ verbinden (⋯ → Verbindungen) |
| Nach dem Test scheitert jeder weitere Lauf mit „… is not a property that exists“ | `Status alt` nicht zurückbenannt | in `Leads` wieder `Status` nennen, Lauf über „Retry“ wiederholen |
| Notion bietet bei `Leads` kein „Trennen“ an | Verbindung wird von der Seite „Nordwind CRM“ geerbt (je nach Version) | Hauptweg nehmen: `Status` umbenennen |
| Production URL zeigt eine Fehlerseite statt des Formulars | Workflow nicht veröffentlicht | „Publish“, dann Seite neu laden |
| Heruntergeladene Datei lässt sich nicht importieren | Datei in Word oder Excel geöffnet und gespeichert | Original-Download verwenden, nur im Texteditor öffnen |
| Testphase abgelaufen, keine Sicherung | Download vergessen | innerhalb von 90 Tagen in der Cloud-Konsole unter „Export“ herunterladen |

## Fazit

- Das Ausführungsprotokoll zeigt jeden Lauf mit den Daten jedes Knotens; dort beginnt jede Fehlersuche.
- Ein Fehler-Workflow meldet automatische Läufe, die scheitern, als Notion-Seite; eine benannte Person kümmert sich darum.
- Vor dem Ende der Testphase liegen alle Workflows als JSON-Dateien lokal vor.

> **Merksatz:** Ein Workflow ohne Fehlermeldung und ohne Verantwortliche fällt still aus.

## Vertiefung

### Ausführungsprotokoll im Detail

| Angabe im Protokoll | Bedeutung | Nutzen im Betrieb |
| --- | --- | --- |
| Status | Success, Error, Running, Waiting | gescheiterte Läufe per Filter „Failed“ finden |
| Gestartet · Dauer | Zeitpunkt und Laufzeit | lief das Briefing heute um 08:00? |
| Lauf öffnen | Arbeitsfläche mit den Ein- und Ausgaben jedes Knotens | sehen, welcher Knoten mit welchen Daten scheiterte |
| Retry | gescheiterten Lauf erneut starten | nach Behebung der Ursache nachholen |

Gespeichert werden nach den Workflow-Einstellungen gescheiterte und erfolgreiche Produktionsläufe sowie manuelle Läufe (Workflow-Menü ⋯ → Settings, je „Save …“). Stand 22.11.2026, Quellen: [n8n Docs – Executions](https://docs.n8n.io/build/understand-workflows/understand-executions), [Workflow-level executions list](https://docs.n8n.io/build/understand-workflows/understand-executions/view-executions-for-a-single-workflow).

### Grenzen und Kosten von n8n Cloud

| Angebot | Preis (jährliche Zahlung) | Ausführungen pro Monat | Hinweis |
| --- | --- | --- | --- |
| Testphase | kostenlos, 14 Tage | 1000 insgesamt | Funktionen des Pro-Tarifs; danach wird die Instanz gelöscht |
| Starter | 20 € pro Monat | 2.500 | 5 gleichzeitige Ausführungen |
| Pro | 50 € pro Monat | 10.000 | bis 50 gleichzeitige Ausführungen, Workflow-Historie |
| Business | 667 € pro Monat | 40.000 | nur selbst betrieben (eigener Server), SSO |
| Enterprise | auf Anfrage | nach Vertrag | Hosting bei n8n oder selbst betrieben |
| Community Edition | kostenlos | unbegrenzt | selbst betrieben, Betrieb und Updates in eigener Verantwortung |

- Es zählt jeder Lauf eines Zeitplans und jede Formular-Einsendung über die Production URL; manuelle Läufe im Editor und Läufe des Fehler-Workflows zählen nicht.
- KI-Kosten kommen dazu: Gateway credits werden je Anfrage nach Modell abgerechnet; in der Testphase enthalten, Aufladen erst nach dem Wechsel in einen bezahlten Tarif (Lab 7.1).
- Stand 22.11.2026, Preise ohne Gewähr, vor einer Entscheidung prüfen. Quellen: [n8n.io/pricing](https://n8n.io/pricing/), [n8n Docs – Executions (Quotas)](https://docs.n8n.io/build/understand-workflows/understand-executions), [Start your free trial](https://docs.n8n.io/deploy/use-n8n-cloud/start-your-free-trial), [Gateway credits](https://docs.n8n.io/deploy/use-n8n-cloud/gateway-credits).

### Verantwortung je Workflow

| Workflow | Auslöser | Verantwortlich · Vertretung | Fehlermeldung an | Stichprobe |
| --- | --- | --- | --- | --- |
| Lead-Eingang | Formular auf der Website | Vertriebsinnendienst · Vertriebsleitung | Notion-Seite „Fehler …“ | wöchentlich 5 Bewertungen gegen die Matrix prüfen |
| Gesprächsnotiz → CRM | Formular nach dem Termin | Außendienst · Vertriebsinnendienst | Notion-Seite „Fehler …“ | jeder Follow-up-Entwurf vor der Freigabe |
| Pipeline-Briefing | werktags 08:00 | Vertriebsleitung · Key Account | Notion-Seite „Fehler …“ | morgens: Briefing da? Zahlen plausibel? |

Die Rollen sind ein Vorschlag für Nordwind; im eigenen Team gehören Namen hinein.
