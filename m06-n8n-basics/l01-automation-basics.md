# Lab 6.1: Automatisierung im Vertrieb: das große Bild

**Leitfragen:**

<details>
<summary>Welche Aufgabe von gestern lief genau so ab wie letzte Woche?</summary>

Typisch: eine Anfrage ins CRM übertragen, einen Bericht zusammenstellen, nach einem Termin nachfassen. Immer gleiche Schritte mit festem Ergebnis sind Kandidaten für einen Workflow.

</details>

<details>
<summary>Was passiert heute mit einer Website-Anfrage am Freitagabend?</summary>

Meist nichts bis Montag: Die Mail liegt im Postfach, niemand trägt sie ein, niemand bewertet sie. Ein Workflow startet in der Minute, in der die Anfrage eingeht, auch am Wochenende.

</details>

<details>
<summary>Was darf nie automatisch passieren, ohne dass ein Mensch draufschaut?</summary>

Alles, was den Kunden erreicht oder bindet: Mails, Angebote, Preise, Zusagen, Absagen. Ein Workflow bereitet vor und trägt ein; freigegeben wird von einem Menschen.

</details>

- Ein Workflow erledigt wiederkehrende Schritte selbstständig: Ein Auslöser startet ihn, Schritte verarbeiten Daten, am Ende steht ein Ergebnis, z. B. ein Eintrag in Notion.
- Tag 1 hat Vertriebsaufgaben von Hand im Chat verstanden; ab jetzt werden die wiederkehrenden davon in n8n gebaut.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| Automatisierung | Ablauf, der ohne Handgriff läuft, sobald ein Ereignis eintritt – wie ein Dauerauftrag bei der Bank |
| Workflow | eine Kette aus Auslöser und Schritten, die Daten von links nach rechts weiterreicht, wie ein Fließband |
| Auslöser (Trigger) | erster Schritt, der den Workflow startet: Klick, abgeschicktes Formular, Uhrzeit |
| Knoten (Node) | ein Kästchen auf der Arbeitsfläche, das genau eine Sache tut: Formular empfangen, Feld setzen, Notion beschreiben |
| Arbeitsfläche (Canvas) | gepunktete Fläche in n8n, auf der Knoten angeordnet und mit Linien verbunden werden |
| Ausführung (Execution) | ein Durchlauf des Workflows mit konkreten Daten; jede Ausführung wird mit Ergebnis protokolliert |
| regelbasierter Schritt | Schritt mit fester Regel: „wenn Region = Sonstige, dann Status Prüfen“; gleiche Eingabe, gleiches Ergebnis |
| KI-Schritt | Schritt, in dem ein Sprachmodell liest, bewertet oder schreibt; flexibel, aber nicht jedes Mal gleich |
| n8n Cloud | n8n als Website des Herstellers, ohne Installation; im Kurs die kostenlose Testphase ([`00-setup.md`](../00-setup.md)) |

## Wiederkehrende Aufgaben im Vertrieb

| Aufgabe | Auslöser | Schritte | Ergebnis |
| --- | --- | --- | --- |
| Website-Anfrage eintragen | Formular abgeschickt | Felder übernehmen, bewerten, Status setzen | neuer Lead in Notion (Lab 6.2–8.2) |
| nach einem Gespräch nachfassen | Gesprächsnotiz eingegeben | Lead finden, Felder herausziehen, Entwurf schreiben | gepflegter Lead, Follow-up-Entwurf (Lab 9.1) |
| Pipeline-Bericht | jeden Werktag 08:00 | offene Deals abrufen, zusammenfassen | Briefing-Seite in Notion (Lab 9.2) |
| Daten übertragen | neuer Eintrag in System A | Felder umbenennen, prüfen | Eintrag in System B |

## Aufbau eines Workflows: Auslöser → Schritte → Ergebnis

```text
AUSLÖSER              SCHRITTE                                          ERGEBNIS
Formular  ──▶  Felder übernehmen ──▶ Wenn-Dann-Regel ──▶ KI bewertet ──▶  Eintrag in Notion
(Anfrage)       regelbasiert          regelbasiert        KI-Schritt       (Status, Score)
```

Wie an einem Fließband reicht jeder Knoten sein Ergebnis an den nächsten weiter. Jeder Knoten sieht, was hereinkommt (Eingabe), und gibt weiter, was er daraus macht (Ausgabe).

| | Regelbasierter Schritt | KI-Schritt |
| --- | --- | --- |
| Beispiel | Region „Sonstige“ → Status „Prüfen“ | Nachricht lesen → Score und Begründung |
| Ergebnis | bei gleicher Eingabe immer gleich | bei gleicher Eingabe leicht verschieden |
| Stärke | exakt, kostenlos, prüfbar | versteht Freitext, schreibt Texte |
| Grenze | versteht keinen Freitext | kann irren, kostet je Aufruf |
| im Kurs ab | Lab 6.3 | Lab 7.1 |

## Automatisierungsplattformen im Vergleich

Stand: 22.11.2026, Preise und Tarife ändern sich, vor einer Entscheidung prüfen.

| Plattform | Kosten zum Einstieg | Hosting, EU | KI-Schritte | Lernkurve |
| --- | --- | --- | --- | --- |
| **Zapier** | Free: 100 Tasks pro Monat; Professional ab 19,99 $ pro Monat | Daten auf AWS-Servern in den USA; EU-only-Speicherung nicht angeboten | ja | flach: einfache Ketten („Zaps“) |
| **Make** | Free: 1.000 Credits pro Monat | Datenzone EU1/EU2 oder US1/US2 wählbar | ja | mittel: visuelle „Szenarien“ |
| **n8n** | Cloud Starter 20 € pro Monat (jährlich, 2.500 Ausführungen), Testphase 14 Tage; selbst betrieben ohne Lizenzkosten | Cloud bei Microsoft Azure in der EU; selbst betrieben auf eigenem Server | ja, KI-Knoten mit vielen Modellen | mittel: viele Knoten, Daten in jedem Schritt sichtbar |
| **Microsoft Power Automate** | Premium 15 $ pro Person und Monat (jährlich), Testphase 30 Tage | Microsoft-Cloud des Unternehmens | ja (Copilot, Umfang je Lizenz prüfen) | flach für Microsoft-365-Umgebungen |
| **Automatisierung im CRM** (z. B. HubSpot-Workflows) | im CRM-Tarif enthalten, je nach Stufe | wo das CRM gehostet ist | je nach CRM | flach, wirkt aber nur innerhalb des CRM |

_Quellen: Zapier Pricing (https://zapier.com/pricing) und Data Privacy Overview (https://zapier.com/legal/data-privacy); Make Pricing (https://www.make.com/en/pricing) und Help Center „AI providers and data zones in Make“ (https://help.make.com/ai-providers-and-data-zones-in-make); n8n Pricing (https://n8n.io/pricing/), Security (https://n8n.io/legal/security/) und Docs „Try free then choose a plan“ (Testphase 14 Tage mit Pro-Funktionen, https://docs.n8n.io/deploy/use-n8n-cloud/start-your-free-trial/); Microsoft Power Automate Pricing (https://www.microsoft.com/en-us/power-platform/products/power-automate/pricing); alle abgerufen am 23.11.2026._

Kriterien für die Wahl im eigenen Unternehmen: Was kostet es bei der erwarteten Zahl von Durchläufen? Wo liegen die Daten? Lassen sich KI-Schritte einbauen? Wer im Team kann es pflegen? Im Kurs fällt die Wahl auf n8n: kostenlos testbar, EU-Hosting, Notion- und KI-Knoten eingebaut, jeder Zwischenschritt sichtbar.

## n8n: Herkunft und Lizenz

| | |
| --- | --- |
| Gründung | 2019 in Berlin durch Jan Oberhauser |
| Name | „n8n“ (gesprochen „n eight n“) kürzt „nodemation“ ab: Knoten (nodes) plus Automatisierung |
| Lizenz | fair-code („Sustainable Use License“): Quellcode öffentlich auf GitHub; Nutzung für eigene interne Geschäftszwecke frei, Weiterverkauf als Dienst nur mit Vertrag |
| Verbreitung | Finanzierung zusammen 240 Mio. $, Bewertung 5,2 Mrd. $ nach einer Investition von SAP (Mai 2026) |

_Quellen: n8n Press (https://n8n.io/press/), n8n Docs „Community license“ (https://docs.n8n.io/sustainable-use-license/); abgerufen am 23.11.2026._

## Oberfläche von n8n: Arbeitsfläche, Knoten, Ausführungen

Ein Workflow besteht aus Knoten auf der Arbeitsfläche. Oben wechseln die Reiter zwischen **Editor** (bauen) und **Executions** (Ausführungen ansehen). Nach einem Durchlauf zeigt jede Verbindung, wie viele Datensätze („1 item“) weitergegeben wurden, und jeder erfolgreiche Knoten bekommt einen grünen Haken. Bezeichnungen je nach Version, die Oberfläche ist englisch.

![n8n-Arbeitsfläche nach einer Ausführung: vier verbundene Knoten „Every day at 8 AM“, „Get Berlin weather“, „Add weather report“, „Save weather log“, jeweils mit grünem Haken und „1 item“ auf den Verbindungen; oben die Reiter Editor, Executions, Evaluations, unten die Schaltfläche Execute](https://raw.githubusercontent.com/n8n-io/n8n-docs/main/docs/get-started/.gitbook/assets/build-your-first-workflow-optional-06-01.png)
_Quelle: n8n Docs, „Build your first workflow“ (https://docs.n8n.io/build-your-first-workflow), © n8n GmbH, abgerufen am 23.11.2026._

Jeder Workflow beginnt mit einem Auslöser. Beim ersten Knoten fragt n8n „What triggers this workflow?“ und bietet u. a. Start per Klick, nach Zeitplan oder bei einem abgeschickten Formular an:

![n8n, leere Arbeitsfläche mit „Add first step…“, rechts die Liste „What triggers this workflow?“ mit Trigger manually, On app event, On a schedule, On webhook call, On form submission](https://raw.githubusercontent.com/n8n-io/n8n-docs/main/docs/get-started/.gitbook/assets/build-your-first-workflow-optional-02-01.png)
_Quelle: n8n Docs, „Build your first workflow“ (https://docs.n8n.io/build-your-first-workflow), © n8n GmbH, abgerufen am 23.11.2026._

Ein Doppelklick auf einen Knoten öffnet seine Detailansicht: links **INPUT** (was hereinkommt), in der Mitte die Einstellungen (**Parameters**), rechts **OUTPUT** (was herausgeht). Die Daten lassen sich als **Schema**, **Table** oder **JSON** anzeigen; Lab 6.3 erklärt die Ansichten.

![n8n-Detailansicht des Knotens „HTTP Request“: links INPUT mit Feldern wie timestamp und Day of week, Mitte Parameters mit Method GET und URL, rechts OUTPUT als Tabelle mit feels_like_c, humidity_pct, wind_kmh, condition](https://raw.githubusercontent.com/n8n-io/n8n-docs/main/docs/get-started/.gitbook/assets/build-your-first-workflow-optional-03-03.png)
_Quelle: n8n Docs, „Build your first workflow“ (https://docs.n8n.io/build-your-first-workflow), © n8n GmbH, abgerufen am 23.11.2026._

## Wann Chat, wann Workflow

| | Chat mit dem KI-Assistenten | Workflow in n8n |
| --- | --- | --- |
| Häufigkeit | einmalig oder selten | wiederkehrend, oft täglich |
| Aufgabe | neu, noch unklar | bekannt, gleiche Schritte |
| Ergebnis | wird sofort gelesen und geprüft | festes Format, landet in Notion |
| Start | der Mensch tippt | Auslöser von außen: Anfrage, Uhrzeit |
| Beispiel | Pipeline einmal auswerten (Lab 5.1) | jede Website-Anfrage eintragen (Lab 6.2) |

## Der Weg vom Problem zum Workflow

Workflows entstehen im Kurs nach dem [Nextise Agentic Way](../00-nextise-agentic-way.md): erst das Problem verstehen, dann die Lösung konzipieren, dann bauen. Der Mensch entscheidet in jedem Schritt.

```text
Tag 1  PROBLEM VERSTEHEN   Leads finden, bewerten, ansprechen, CRM pflegen – von Hand im Chat   ✔ erledigt
Tag 2  KONZIPIEREN + BAUEN Workflow „Lead-Eingang“ in n8n; Assistent 3 schreibt die KI-Anweisung (Lab 7.2)
Tag 3  KONZIPIEREN + BAUEN Assistent 2 entwirft den Workflow (Lab 9.2), dann die ganze Kette am eigenen Fall
```

Die Bewertungsmatrix aus Lab 3.3 und die Gesprächsnotiz aus Lab 4.3 sind schon verstanden und geprüft; genau diese Aufgaben werden jetzt automatisiert.

## Übung: Erster Workflow importieren und ausführen

**Material:** [`m06-hallo-workflow.json`](../material/workflows/m06-hallo-workflow.json), Import-Anleitung in [`workflows/README.md`](../material/workflows/README.md) · **Werkzeug:** n8n Cloud

**Ausgangslage:** Der Musterworkflow startet per Klick, legt einen fiktiven Lead an und prüft, ob er mindestens 5 Räume hat. Er braucht keine Verbindung und keine KI.

1. Öffne die eigene n8n-Adresse (`<name>.app.n8n.cloud`) und lege einen neuen, leeren Workflow an (**Create workflow** bzw. **+**, Bezeichnung je nach Version).
2. Öffne `m06-hallo-workflow.json` auf GitHub, kopiere den Inhalt mit **Copy raw file**, klicke einmal auf die Arbeitsfläche und füge mit Strg + V (Mac: Cmd + V) ein; speichere den Workflow.
3. Klicke unten auf **Execute workflow** und prüfe, ob alle drei Knoten einen grünen Haken haben.
4. Öffne per Doppelklick nacheinander „Beispiel-Lead“ und „Mindestens 5 Räume?“ und vergleiche jeweils INPUT und OUTPUT in der Ansicht **Table**.
5. Ändere in „Beispiel-Lead“ den Wert von `Anzahl Räume` auf 3, führe erneut aus und beobachte, an welchem Ausgang von „Mindestens 5 Räume?“ der Lead jetzt herauskommt.

**Checkpoint:** Die Ausführung ist im Reiter **Executions** als erfolgreich gelistet; „Mindestens 5 Räume?“ gibt den Lead bei 12 Räumen am Ausgang `true`, bei 3 Räumen am Ausgang `false` aus.

**Erweiterung:** Den gelben Hinweiszettel lesen und per Rechtsklick auf die Arbeitsfläche einen eigenen Zettel ergänzen (**Add sticky note**, Bezeichnung je nach Version).

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Stand: 23.11.2026, gebaut mit n8n 2.48.7.

**Workflow auf der Arbeitsfläche:** `Workflow starten` → `Beispiel-Lead` → `Mindestens 5 Räume?`, dazu ein gelber Hinweiszettel.

| Knoten | Art | INPUT | OUTPUT |
| --- | --- | --- | --- |
| Workflow starten | Auslöser per Klick (Manual Trigger) | – | 1 leerer Datensatz, der den Lauf startet |
| Beispiel-Lead | Felder setzen (Edit Fields) | leerer Datensatz | 1 Datensatz mit 6 Feldern (Tabelle unten) |
| Mindestens 5 Räume? | Wenn-Dann-Prüfung (If): `Anzahl Räume` ≥ 5 | Datensatz aus „Beispiel-Lead“ | Ausgang `true`: 1 item; Ausgang `false`: leer |

**OUTPUT von „Beispiel-Lead“ (Ansicht Table)**

| Firma | Website | Region | Mitarbeitende | Anzahl Räume | Nachricht |
| --- | --- | --- | --- | --- | --- |
| Rheinpark Versicherungsmakler GmbH | https://rheinpark-makler.example | DE-West | 120 | 12 | Bei uns gibt es ständig Doppelbuchungen in den Besprechungsräumen. Wir suchen eine Lösung mit Raumdisplays. |

**Aufgabe 5:** Mit `Anzahl Räume` = 3 kommt derselbe Datensatz am Ausgang `false` heraus; `true` bleibt leer. Im Reiter **Executions** stehen danach zwei erfolgreiche Ausführungen.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Einfügen bewirkt nichts | Fokus liegt nicht auf der Arbeitsfläche | einmal in die leere Fläche klicken, erneut einfügen |
| Knoten erscheinen, aber ohne Linien | nur ein Teil der Datei kopiert | **Copy raw file** verwenden statt markieren |
| OUTPUT zeigt „No output data“ | Knoten noch nicht ausgeführt | **Execute workflow** klicken, dann Knoten öffnen |
| Änderung an „Anzahl Räume“ wirkt nicht | Workflow nicht neu ausgeführt | nach jeder Änderung erneut ausführen |

## Fazit

- Workflow = Auslöser → Schritte → Ergebnis; jeder Knoten zeigt Eingabe und Ausgabe.
- Regelbasierte Schritte sind exakt, KI-Schritte verstehen Freitext; beide kommen im Lead-Workflow vor.
- Chat für Neues und Einmaliges, Workflow für Wiederkehrendes mit festem Format.

> **Merksatz:** Erst von Hand verstehen, dann automatisieren.
