# Lab 7.1: Ein KI-Schritt im Workflow

**Leitfragen:**

<details>
<summary>Was müsste eine Kollegin wissen, um jede Anfrage gleich zusammenzufassen?</summary>

Für wen die Zusammenfassung ist, was hineingehört (Firma, Anliegen, Räume, Zeitrahmen), wie lang sie sein darf und was nicht passieren darf (nichts erfinden). Genau das steht später einmal fest in der Systemanweisung.

</details>

<details>
<summary>Ist ein Prompt im Workflow ein anderer Prompt als im Chat?</summary>

Er folgt denselben fünf Bausteinen aus Lab 2.1, wird aber zweigeteilt: Der feste Teil (Rolle, Aufgabe, Format, Regeln) steht einmal im Knoten, die wechselnden Angaben kommen bei jeder Anfrage als Felder aus dem Formular dazu. Nachfragen wie im Chat gibt es nicht, deshalb muss der feste Teil vollständig sein.

</details>

<details>
<summary>Wer bezahlt eigentlich die Rechenleistung hinter einer KI-Antwort?</summary>

Der Anbieter des Sprachmodells rechnet jede Anfrage nach Modell und Textmenge ab. Im Kurs zahlt n8n aus einem Guthaben (Gateway credits), im eigenen Betrieb meist das eigene Konto beim Anbieter über einen API-Schlüssel.

</details>

- Ein KI-Schritt in n8n besteht aus zwei Teilen: dem Knoten „Basic LLM Chain“, der den Auftrag enthält, und einem angehängten Modell-Knoten, der die Antwort erzeugt.
- Der Auftrag folgt den fünf Bausteinen aus Lab 2.1: Rolle, Aufgabe, Format und Regeln stehen fest in der Systemanweisung, die Angaben der Anfrage kommen als Felder dazu.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| Basic LLM Chain | n8n-Knoten für einen KI-Schritt, der freien Text erzeugt (Zusammenfassung, Entwurf); LLM steht für Large Language Model, also Sprachmodell |
| Unterknoten (Sub-node) | kleiner runder Knoten, der unter einem anderen Knoten hängt und ihm eine Fähigkeit liefert, z. B. das Sprachmodell – wie ein Motor, der in ein Fahrzeug eingesetzt wird |
| Chat-Modell-Knoten | Unterknoten, der festlegt, welches Sprachmodell antwortet (im Kurs „OpenAI Chat Model“ mit dem Modell `gpt-5-mini`) |
| Systemanweisung (System Message) | fester Teil des Prompts, der bei jeder Ausführung gleich bleibt: Rolle, Aufgabe, Format, Regeln |
| Nutzer-Prompt (Prompt (User Message)) | wechselnder Teil des Prompts: die Angaben der aktuellen Anfrage, eingesetzt über Ausdrücke aus Lab 6.3 |
| `$('Knotenname')` | Ausdruck für die Daten eines bestimmten früheren Knotens, z. B. `$('Lead-Anfrage').item.json.Firma` für die Firma aus dem Formular |
| API | Programmierschnittstelle: fester Zugang, über den ein Programm einem anderen einen Auftrag gibt, z. B. n8n dem Sprachmodell – wie ein Bestellschalter zwischen zwei Firmen |
| API-Schlüssel | geheime Zeichenfolge, an der ein KI-Anbieter erkennt, wer eine Anfrage schickt und wem er sie berechnet; nach der Datenampel aus Lab 1.3 immer rot |
| Gateway credits | Guthaben in n8n Cloud, mit dem KI-Schritte ohne eigenes Anbieterkonto und ohne API-Schlüssel laufen |

## Aufbau eines KI-Schritts in n8n

n8n nennt solche Gruppen „Cluster-Knoten“: ein Hauptknoten (Root node) mit dem Auftrag, darunter Unterknoten, die ihm Fähigkeiten geben. Das Bild aus der n8n-Dokumentation zeigt einen Agent-Knoten mit Modell und Gedächtnis; bei der Basic LLM Chain hängt nur das Modell darunter.

![n8n-Arbeitsfläche: Auslöser „On new manual Chat Message“ führt zum Hauptknoten „Agent“ (beschriftet als Root node); darunter über gestrichelte Linien die runden Unterknoten „OpenAI Chat Model“ und „Window Buffer Memory“ (beschriftet als Sub-nodes)](https://raw.githubusercontent.com/n8n-io/n8n-docs/main/docs/reusable-content/.gitbook/assets/root-sub-nodes.png)
_Quelle: n8n Docs, „Cluster nodes“ (https://docs.n8n.io/integrations/builtin/cluster-nodes), © n8n, abgerufen am 23.11.2026._

```text
Lead-Anfrage ──► Anfrage zusammenfassen (Basic LLM Chain) ──► … ──► Lead in Notion anlegen
                        ▲  Anschluss „Model“
                        │
                 KI-Modell Zusammenfassung (OpenAI Chat Model, gpt-5-mini)
```

| Teil | Wo in n8n | Inhalt im Lead-Workflow |
| --- | --- | --- |
| Systemanweisung | Basic LLM Chain → „Chat Messages“ → Nachricht vom Typ „System“ | Rolle, Aufgabe „ein Satz, höchstens 25 Wörter“, Regeln |
| Nutzer-Prompt | Basic LLM Chain → „Prompt (User Message)“ | Firma, Mitarbeitende, Anzahl Räume, Region, Nachricht aus dem Formular |
| Modell | Unterknoten am Anschluss „Model“ | OpenAI Chat Model, `gpt-5-mini` |
| Ergebnis | Ausgabe der Basic LLM Chain | Feld `text`, im nächsten Knoten `{{ $('Anfrage zusammenfassen').item.json.text }}` |

Bezeichnungen der Oberfläche Stand 22.11.2026, n8n 2.48 (Bezeichnung je nach Version). Quelle: [n8n Docs – Basic LLM Chain](https://docs.n8n.io/integrations/builtin/cluster-nodes/root-nodes/n8n-nodes-langchain.chainllm).

## Fünf Prompt-Bausteine in Systemanweisung und Nutzer-Prompt

| Baustein aus Lab 2.1 | Ort im Knoten | Text im Lab |
| --- | --- | --- |
| **Rolle** | Systemanweisung | „Du bist Assistenz im Vertriebsinnendienst von Nordwind Workspace GmbH …“ |
| **Aufgabe** | Systemanweisung | „Fasse eine Website-Anfrage in genau einem deutschen Satz mit höchstens 25 Wörtern zusammen.“ |
| **Kontext** | Nutzer-Prompt | Formularfelder, je Anfrage neu eingesetzt |
| **Format** | Systemanweisung | „Gib nur den Satz aus, ohne Einleitung und ohne Anführungszeichen.“ |
| **Rahmenbedingungen** | Systemanweisung | „Nur Angaben aus der Anfrage, nichts erfinden.“ |

Name und E-Mail stehen nicht im Nutzer-Prompt: Für eine Zusammenfassung des Anliegens braucht die KI sie nicht (Datenampel, Lab 1.3).

## Gateway credits und eigener API-Schlüssel

Jeder KI-Schritt ist ein bezahlter Aufruf beim Modellanbieter. n8n Cloud bietet dafür zwei Wege, die je Knoten im Feld „Credential“ gewählt werden.

![n8n-Knotenfenster: Feld „Credential“ ist aufgeklappt, ausgewählt ist „Gateway credits“ mit dem Hinweis „$1.99 remaining“, darunter „Create new credential“](https://raw.githubusercontent.com/n8n-io/n8n-docs/main/docs/changelog/.gitbook/assets/select%20credits.png)
_Quelle: n8n Docs, „Release notes“, n8n 2.44 (https://docs.n8n.io/changelog/release-notes), © n8n, abgerufen am 23.11.2026._

| | Gateway credits | Eigener API-Schlüssel |
| --- | --- | --- |
| Einrichtung | im Feld „Credential“ „Gateway credits“ bzw. „Use Gateway credits“ wählen (je nach Version) | Konto beim Anbieter, Schlüssel erzeugen, als Credential in n8n eintragen |
| Kosten je Aufruf | n8n zieht jeden Aufruf vom Guthaben ab; Preis je nach Modell und Textmenge laut Preisliste von n8n | Abrechnung direkt beim Anbieter zu dessen Preisen |
| Datenschutz | n8n leitet die Anfrage über ein eigenes Konto von n8n beim Anbieter weiter; der Anbieter erhält laut n8n den Inhalt des Prompts, aber nicht die Identität und die Kontodaten des n8n-Kontos | es gelten Vertrag und Datenschutzeinstellungen des eigenen Anbieterkontos |
| Grenzen | nur unterstützte Modelle (u. a. OpenAI, Anthropic, Google Gemini); Guthaben gilt für die ganze Instanz; bei null schlagen die Knoten fehl | alle Modelle, die n8n anbindet |
| Im Kurs | Standard: Testphase enthält Guthaben, Aufladen erst nach Upgrade | Rückfallebene, wenn das Guthaben aufgebraucht ist |

Stand: 22.11.2026, ab n8n 2.36.0, n8n Cloud Starter und Pro sowie Testphase; Quellen: [n8n Docs – Gateway credits](https://docs.n8n.io/deploy/use-n8n-cloud/gateway-credits), [n8n Docs – Use Gateway credits](https://docs.n8n.io/build/understand-workflows/use-gateway-credits). Die Menge des Guthabens in der Testphase nennt die Doku nicht (prüfen).

Auch mit Gateway credits gilt die Datenampel: Im Kurs sind alle Daten erfunden; echte Kundendaten gehören nur mit Firmenkonto, Vertrag und Freigabe in einen Workflow.

## Formularwerte nach dem KI-Schritt mit `$('Lead-Anfrage')`

Nach dem KI-Schritt enthält `$json` nur noch das Feld `text` der Basic LLM Chain. Ein Ausdruck wie `{{ $json.Firma }}` im nächsten Knoten bleibt deshalb leer.

| Ausdruck | liest | im Lead-Workflow |
| --- | --- | --- |
| `{{ $json.Firma }}` | Ausgabe des direkt vorherigen Knotens | nur vor dem KI-Schritt richtig |
| `{{ $('Lead-Anfrage').item.json.Firma }}` | Ausgabe des Knotens „Lead-Anfrage“, egal wie viele Knoten dazwischen liegen | ab jetzt in allen Knoten nach dem KI-Schritt |
| `{{ $('Anfrage zusammenfassen').item.json.text }}` | Ausgabe des KI-Schritts | Wert für die Notion-Eigenschaft `Zusammenfassung` |

Der Knotenname im Ausdruck muss genau so geschrieben sein wie auf der Arbeitsfläche.

## Übung: Zusammenfassung jeder Anfrage nach Notion schreiben

**Material:** Workflow aus Lab 6.3 (Rückfallebene: [`m06-l03-bedingung.json`](../material/workflows/m06-l03-bedingung.json)), [`material/testanfragen.md`](../material/testanfragen.md) (T1) · **Werkzeug:** n8n, Notion

**Ausgangslage:** Der Workflow aus Lab 6.3 trägt jede Anfrage mit Status „Neu“ oder „Prüfen“ in `Leads` ein. Ab jetzt steht in Notion zusätzlich ein Satz, der die Anfrage zusammenfasst, damit niemand die ganze Nachricht lesen muss.

1. Öffne den Workflow aus Lab 6.3, klicke auf das „+“ zwischen „Lead-Anfrage“ und „Region außerhalb DACH/NL?“, füge den Knoten „Basic LLM Chain“ ein und benenne ihn „Anfrage zusammenfassen“.
2. Stelle in „Anfrage zusammenfassen“ „Prompt (User Message)“ auf „Define below“, trage den Nutzer-Prompt aus der Tabelle unten ein, ergänze unter „Chat Messages“ eine Nachricht vom Typ „System“ mit Prompt-Karte 7.1a und hänge am Anschluss „Model“ den Unterknoten „OpenAI Chat Model“ an (Credential „Gateway credits“ bzw. „Use Gateway credits“, Modell `gpt-5-mini`, Name „KI-Modell Zusammenfassung“).
3. Stelle in „Region außerhalb DACH/NL?“ und in „Lead in Notion anlegen“ jeden Ausdruck von `$json.<Feld>` auf `$('Lead-Anfrage').item.json.<Feld>` um, außer `{{ $json.Status }}`; am einfachsten im Eingabebereich links den Knoten „Lead-Anfrage“ wählen und die Felder neu hineinziehen.
4. Ergänze in „Lead in Notion anlegen“ die Eigenschaft `Zusammenfassung` mit dem Wert `{{ $('Anfrage zusammenfassen').item.json.text }}` und speichere.
5. Führe den Workflow aus, sende T1 über das Testformular (alle Felder aus `testanfragen.md`, auch Website) und öffne den neuen Eintrag in Notion.

| Knoten | Einstellung | Wert |
| --- | --- | --- |
| Anfrage zusammenfassen | Prompt (User Message) | `Define below` |
| | Text des Nutzer-Prompts | `Firma: {{ $json.Firma }}` · `Mitarbeitende: {{ $json.Mitarbeitende }}` · `Anzahl Räume: {{ $json['Anzahl Räume'] }}` · `Region: {{ $json.Region }}` · `Nachricht: {{ $json.Nachricht }}` (je eine Zeile) |
| | Chat Messages → System | Prompt-Karte 7.1a |
| KI-Modell Zusammenfassung | Credential · Model | `Gateway credits` bzw. `Use Gateway credits` (je nach Version) · `gpt-5-mini` |
| Region außerhalb DACH/NL? | Wert links | `{{ $('Lead-Anfrage').item.json.Region }}` |
| Lead in Notion anlegen | Titel · übrige Formularfelder | `{{ $('Lead-Anfrage').item.json.Firma }}` usw. |
| | `Zusammenfassung` (Text) | `{{ $('Anfrage zusammenfassen').item.json.text }}` |

**Prompt-Karte 7.1a – Systemanweisung „Anfrage zusammenfassen“**

```text
Du bist Assistenz im Vertriebsinnendienst von Nordwind Workspace GmbH (Raumdisplays, Konferenzkamera-Sets und Raumbuchungs-Software für Besprechungsräume).

Aufgabe: Fasse eine Website-Anfrage in genau einem deutschen Satz mit höchstens 25 Wörtern zusammen.

Regeln:
- Nenne Firma, Anliegen und, falls angegeben, Anzahl der Räume und Zeitrahmen.
- Nur Angaben aus der Anfrage, nichts erfinden.
- Gib nur den Satz aus, ohne Einleitung und ohne Anführungszeichen.
```

**Checkpoint:** Der Eintrag „Steuerkanzlei Lorenzen & Partner mbB“ in Notion hat in `Zusammenfassung` genau einen Satz mit Firma, sechs Räumen und dem Anliegen Kamera-Sets; alle übrigen Felder sind wie in Lab 6.3 gefüllt.

**Erweiterung:** T2 senden und prüfen, ob der Satz den Termin 01.02.2027 nennt.

**Rückfallebene:** [`m07-l01-ki-zusammenfassung.json`](../material/workflows/m07-l01-ki-zusammenfassung.json) importieren, Notion-Verbindung, Datenbank `Leads` und „Use Gateway credits“ setzen ([Anleitung](../material/workflows/README.md)).

```text
Stand nach Lab 7.1
Lead-Anfrage → Anfrage zusammenfassen (+ KI-Modell) → Region außerhalb DACH/NL?
                                                        ├─ true  → Status Prüfen ─┐
                                                        └─ false → Status Neu ────┴→ Lead in Notion anlegen
```

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Beispiel – KI-Antworten fallen jedes Mal etwas anders aus.

**Ausgabe von „Anfrage zusammenfassen“ (Ansicht JSON im Ausgabebereich)**

```json
[
  {
    "text": "Steuerkanzlei Lorenzen & Partner mbB möchte sechs Besprechungsräume für Mandanten-Videokonferenzen ausstatten und bittet um Infos zu Kamera-Sets und Preisrahmen."
  }
]
```

`text` ist das einzige Feld; genau dieses wird nach Notion geschrieben.

**Eintrag in Notion, Datenbank `Leads`**

| Eigenschaft | Wert |
| --- | --- |
| Firma | Steuerkanzlei Lorenzen & Partner mbB |
| Website | https://raw.githubusercontent.com/kodschul/kodschul-ki-vertrieb-auto-3-open/main/material/firmenprofile/lorenzen-partner.md |
| Ansprechperson · Rolle | Johanna Weiß · Kanzleimanagerin |
| Mitarbeitende · Räume · Region | 48 · 6 · DE-Süd |
| Quelle · Status | Website · Neu |
| Zusammenfassung | Steuerkanzlei Lorenzen & Partner mbB möchte sechs Besprechungsräume für Mandanten-Videokonferenzen ausstatten und bittet um Infos zu Kamera-Sets und Preisrahmen. |

Warum gut: 19 Wörter, Firma, Räume und Anliegen sind drin, nichts ist erfunden (kein Termin, weil die Anfrage keinen nennt).

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Notion-Eintrag ohne Firma, Felder leer | Ausdrücke lesen noch `$json.Firma`; nach dem KI-Schritt hat `$json` nur `text` | Ausdrücke auf `$('Lead-Anfrage').item.json.…` umstellen (Aufgabe 3) |
| Basic LLM Chain meldet „No prompt specified“ | „Define below“ gewählt, aber Text leer | Nutzer-Prompt eintragen |
| Option „Gateway credits“ bzw. „Use Gateway credits“ fehlt | n8n-Version unter 2.36.0 oder Gateway credits auf der Instanz abgeschaltet | Version prüfen, sonst eigenen API-Schlüssel nutzen oder Musterworkflow im Paar ausführen |
| KI-Knoten schlägt plötzlich fehl, vorher lief er | Guthaben aufgebraucht | Credit-Stand im Knoten ansehen; Rückfallebene aus den Voraussetzungen (Paararbeit, eigener Schlüssel) |
| Satz beginnt mit „Hier ist die Zusammenfassung:“ | Format-Regel fehlt oder steht im Nutzer-Prompt statt in der Systemanweisung | Prompt-Karte 7.1a vollständig als System-Nachricht einfügen |

## Fazit

- Ein KI-Schritt in n8n ist ein Hauptknoten mit Auftrag plus ein Unterknoten mit dem Modell.
- Der feste Teil des Prompts steht in der Systemanweisung, die Anfrage kommt über Ausdrücke dazu.
- Nach einem KI-Schritt werden Formularwerte mit `$('Lead-Anfrage')` geholt.
- Gateway credits ersparen den eigenen API-Schlüssel; bezahlt wird trotzdem jeder Aufruf.

> **Merksatz:** Im Workflow fragt die KI nicht nach – die Systemanweisung muss vorher alles sagen.
