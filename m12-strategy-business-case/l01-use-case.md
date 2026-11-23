# Lab 12.1: Problem verstehen: KI-Strategie und Use Case mit dem Use-Case-Coach

**Leitfragen:**

<details>
<summary>Welche Aufgabe aus diesen drei Tagen würde im eigenen Team am meisten Zeit sparen?</summary>

Meist eine, die oft vorkommt, immer gleich abläuft und heute von Hand erledigt wird: Anfragen sortieren, nach Gesprächen nachfassen, den Pipeline-Überblick erstellen. Häufigkeit mal Zeit je Vorgang zeigt, wo der größte Hebel liegt.

</details>

<details>
<summary>Was braucht ein Projekt, damit es nach dem Seminar nicht in der Schublade landet?</summary>

Ein klar beschriebenes Problem, eine verantwortliche Person, einen kleinen Pilot mit Enddatum und eine Zahl von heute, an der sich der Erfolg messen lässt.

</details>

<details>
<summary>Wer im eigenen Unternehmen müsste Ja sagen?</summary>

Die Person mit Budget (oft Vertriebs- oder Geschäftsleitung), dazu Datenschutz und IT für Werkzeuge und Daten, und das Team, das täglich damit arbeitet.

</details>

- Die ganze Kette des Nextise Agentic Way läuft jetzt am eigenen Fall: Problem verstehen (dieses Lab), konzipieren (12.2), präsentieren (12.3).
- Am Anfang steht ein Problem, nicht ein Werkzeug: Der Use-Case-Coach fragt so lange nach, bis Problem, Ablauf und Nutzen klar sind.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| KI-Strategie | Antwort auf vier Fragen: wofür KI, in welchen Aufgaben, mit welchen Daten und Systemen, mit welchen Menschen und Regeln |
| Use Case | eine konkrete, wiederkehrende Aufgabe, für die eine KI-Lösung geprüft wird |
| Use-Case-Canvas | eine Seite mit festen Feldern, die einen Use Case vollständig beschreibt, wie ein Formular für Ideen |
| Pilot | zeitlich begrenzter Testlauf mit einem Team und einem Prozess, an dessen Ende entschieden wird |
| Ausgangswert | Messwert von heute, z. B. „Antwort auf Anfragen nach 2 Werktagen“; ohne ihn ist kein Erfolg messbar |

## KI-Strategie im Vertrieb in vier Fragen

| Frage | Worum es geht | Beispiel Nordwind |
| --- | --- | --- |
| 1 Ziel | Welches Vertriebsziel soll KI unterstützen? | schneller auf Anfragen reagieren, mehr Angebote gewinnen |
| 2 Use Cases | Welche wiederkehrenden Aufgaben zahlen darauf ein? | Lead-Eingang, Follow-up nach Gesprächen, Pipeline-Briefing |
| 3 Daten und Systeme | Wo liegen die Daten, wie gut sind sie gepflegt, welche Werkzeuge sind verbunden? | Notion-CRM, n8n, Formular; Deals mit Phase und letztem Kontakt |
| 4 Menschen und Regeln | Wer verantwortet, wer gibt frei, welche Regeln gelten? | Datenampel, Freigabe-Matrix, KI-Kompetenz (Modul 11) |

Wo Unternehmen stehen: 2025 nutzte jedes fünfte Unternehmen in der EU mit mindestens zehn Beschäftigten KI-Technologien (20,0 %, 2024: 13,5 %); am häufigsten Textanalyse.

![Eurostat-Balkendiagramm „Enterprises using AI technologies, 2024 and 2025“: Anteil der Unternehmen je EU-Land, EU 2025 bei 20 %, Spitze Dänemark über 40 %, Deutschland und Österreich über dem EU-Wert, Rumänien am Ende bei rund 5 %](https://ec.europa.eu/eurostat/o/adaptive-media/image/22691519/Preview-1000x0/enterprises-using-ai-techonologies-2024-2025.jpg)
_Quelle: Eurostat, „20% of EU enterprises use AI technologies“, 11.12.2025 (https://ec.europa.eu/eurostat/web/products-eurostat-news/w/ddn-20251211-2), © Europäische Union, Weiterverwendung mit Quellenangabe, abgerufen am 22.11.2026._

## Warum KI-Projekte scheitern und was hilft

Die Forschungsorganisation RAND hat 2024 untersucht, warum KI-Projekte scheitern: Nach manchen Schätzungen scheitern über 80 % der KI-Projekte, doppelt so viele wie IT-Projekte ohne KI. Die fünf Hauptursachen und die Gegenmittel aus diesem Kurs:

| Ursache laut RAND | Gegenmittel im Kurs |
| --- | --- |
| Problem missverstanden oder falsch vermittelt | Problem zuerst: Use-Case-Coach, Canvas, Ist-Ablauf von Hand (Tag 1) |
| zu wenig geeignete Daten | Datenlage im Canvas bewerten; Daten im CRM pflegen, bevor automatisiert wird |
| Technik wichtiger als das Problem der Nutzer | Regel vor KI: Was eine feste Regel löst, ist kein KI-Schritt |
| fehlende Infrastruktur für Daten und Betrieb | Fehler-Workflow, Export, Verantwortliche (Lab 9.3) |
| Problem zu schwer für heutige KI | kleiner Pilot, Mensch gibt frei, Testfälle vor dem Einsatz |

_Quelle: Ryseff, De Bruhl, Newberry, „The Root Causes of Failure for Artificial Intelligence Projects and How They Can Succeed“, RAND, RR-A2680-1, 13.08.2024 (https://www.rand.org/pubs/research_reports/RRA2680-1.html), abgerufen am 22.11.2026._

Daraus folgen fünf Erfolgsfaktoren: klarer Prozess, gepflegte Daten, eine verantwortliche Person, kleiner Pilot mit Enddatum, messbare Ausgangslage.

## Use-Case-Canvas und Bewertung mit Assistent 1

Ein Canvas fasst ein Vorhaben auf einer Seite mit festen Feldern zusammen. Bekanntestes Vorbild ist das Business Model Canvas von Alexander Osterwalder (Buch „Business Model Generation“, 2010) mit neun Feldern für ein Geschäftsmodell:

![Vorlage „The Business Model Canvas“ mit neun Feldern: Key Partners, Key Activities, Key Resources, Value Propositions, Customer Relationships, Channels, Customer Segments, unten Cost Structure und Revenue Streams; je Feld Leitfragen in kleiner Schrift](https://upload.wikimedia.org/wikipedia/commons/thumb/1/10/Business_Model_Canvas.png/960px-Business_Model_Canvas.png)
_Quelle: Wikimedia Commons, „Business Model Canvas.png“ (https://commons.wikimedia.org/wiki/File:Business_Model_Canvas.png), Business Model Foundry AG (Strategyzer), CC BY-SA 1.0 laut Commons, abgerufen am 22.11.2026._

Der Use-Case-Canvas des Use-Case-Coachs ([`assistenten-prompts.md`](../material/assistenten-prompts.md), Assistent 1) ist kleiner und auf einen Vertriebsprozess zugeschnitten:

| Feld | Frage |
| --- | --- |
| 1 Problem | Welches konkrete, wiederkehrende Problem besteht heute? |
| 2 Zielgruppe | Welche Rollen sind betroffen, wie viele Personen? |
| 3 Ist-Ablauf | Welche 3 bis 5 Schritte heute, mit Zeit und Häufigkeit? |
| 4 Soll-Ablauf | Wie sieht es mit KI-Assistent oder Workflow aus, wo entscheidet der Mensch? |
| 5 Nutzen | Was wird messbar besser: Zeit, Reaktionszeit, vergessene Follow-ups, Abschlussquote? |
| 6 Daten und Systeme | Welche Systeme, wie gut gepflegt? |
| 7 Risiken | Datenschutz, Werberecht, Fehlerfolgen beim Kunden, Akzeptanz im Team |

Danach schlägt der Coach zwei bis drei Lösungsideen vor, ordnet sie Chat oder Workflow zu und bewertet jede mit 1 bis 5 Punkten:

| Kriterium | 5 Punkte bedeutet | Summe |
| --- | --- | --- |
| Nutzen | großer, messbarer Gewinn | höchstens 20; bei Gleichstand gewinnt die Idee mit besserer Datenlage und geringerem Risiko |
| Aufwand | einfach umzusetzen | |
| Datenlage | Daten vorhanden und gepflegt | |
| Risiko | geringes Risiko | |

```text
eigenes Problem ─► [1] Use-Case-Coach ─► Canvas + Bewertung + Top-1 ─► Mensch wählt ─► Übergabe-Block an [2] (Lab 12.2)
```

### Prüfung des Canvas vor der Wahl

| Prüfpunkt | Hinweis auf ein Problem |
| --- | --- |
| Problem ohne Lösungswort beschrieben | „Wir brauchen einen Chatbot“ ist eine Lösung, kein Problem |
| Ist-Ablauf mit Zeit und Häufigkeit | ohne Zahlen kein Business Case in 12.2 |
| Annahmen markiert | Zahlen, die niemand genannt hat, stehen als Fakt im Canvas |
| Risiken aus Modul 11 | Datenschutz, Werbe-Mails, Bewertung von Personen fehlen |
| Chat oder Workflow passend | einmalige Aufgabe als Workflow geplant oder umgekehrt |

## Übung: Use-Case-Canvas für ein Problem der eigenen Firma

**Material:** [`assistenten-prompts.md`](../material/assistenten-prompts.md) (Assistent 1), CRM-Steckbrief aus Lab 10.2, Anregungen: [`workflow-steckbriefe.md`](../material/workflow-steckbriefe.md) · **Werkzeug:** KI-Assistent, Notion

**Ausgangslage:** Ein wiederkehrendes Vertriebsproblem der eigenen Firma soll zum Pilot werden. In den Chat gehören nur Rollen, Abläufe und geschätzte Zahlen, keine roten Daten (Lab 1.3): keine Kundennamen, Kontaktdaten, Preise oder internen Umsätze. Wer kein eigenes Problem nutzen möchte, nimmt das Musterbeispiel aus dem Musterergebnis.

1. Öffne einen neuen Chat, füge den Rollen-Prompt von Assistent 1 ein und sende danach Prompt-Karte 12.1a mit der eigenen Schilderung.
2. Beantworte die Rückfragen des Coachs, bis Canvas, Bewertung und Top-1-Empfehlung vorliegen.
3. Prüfe den Canvas mit der Tabelle „Prüfung des Canvas vor der Wahl“ und lass Fehler mit Prompt-Karte 12.1b korrigieren.
4. Nimm die Top-1-Empfehlung an oder wähle begründet eine andere Idee mit Prompt-Karte 12.1c.
5. Lege in Notion eine Seite „Business Case – <Use Case>“ an und kopiere Canvas, Bewertung und den Übergabe-Block an den Workflow-Architekten hinein.

**Prompt-Karte 12.1a – Problem schildern**

```text
Mein Vertriebsproblem: [2–4 Sätze, was heute nervt oder Geld kostet]
Mein Team: [Rollen, Anzahl Personen]
So läuft es heute: [Schritte grob, Zeit je Vorgang, Vorgänge pro Woche oder Monat – geschätzt]
Systeme: [CRM, Mail, Formulare, Tabellen; aus dem CRM-Steckbrief]
Ich nenne keine Kundennamen und keine internen Zahlen außer Schätzungen.
```

**Prompt-Karte 12.1b – Canvas korrigieren**

```text
Im Canvas sind folgende Punkte falsch oder fehlen: [Punkt und richtige Angabe]. Markiere alle Zahlen, die ich nicht genannt habe, als Annahme. Passe Bewertung und Empfehlung nur an, wenn sich dadurch etwas ändert.
```

**Prompt-Karte 12.1c – Pilot wählen**

```text
Ich wähle Idee [Nummer] als Pilot, weil [Grund]. Erstelle dafür den Übergabe-Block an den Workflow-Architekten wie in deinem Ausgabeformat, Abschnitt 6.
```

**Checkpoint:** Die Notion-Seite enthält einen Canvas mit sieben Feldern, eine Bewertungstabelle mit Summen, den gewählten Pilot mit Erfolgskriterium (Ausgangswert, Zielwert, Zeitraum) und den Übergabe-Block.

**Erweiterung:** Ein zweites Problem durch den Coach laufen lassen und die beiden Top-1-Empfehlungen vergleichen.

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Fiktives Beispiel: Leiterin Vertriebsinnendienst eines mittelständischen Maschinenbauers (250 Mitarbeitende, Antriebe und Ersatzteile, Kunden in DACH). Keine echte Firma; KI-Antworten fallen jedes Mal etwas anders aus.

**1. Schilderung**

```text
Mein Vertriebsproblem: Anfragen über das Website-Formular bleiben oft zwei Tage liegen, weil der Innendienst jede von Hand liest, im CRM sucht, einordnet und beantwortet. Neue Interessenten für Maschinen gehen zwischen Ersatzteil- und Service-Anfragen unter.
Mein Team: Innendienst, 3 Personen; Außendienst 6 Personen bekommt heiße Anfragen.
So läuft es heute: Anfrage lesen, Firma im CRM suchen oder anlegen, Art und Dringlichkeit einschätzen, Antwort schreiben oder an den Außendienst geben; ca. 15 Minuten je Anfrage, ca. 120 Anfragen im Monat (geschätzt).
Systeme: HubSpot als CRM (laut CRM-Steckbrief mit n8n-Anbindung), Website-Formular, Outlook.
```

**2. Rückfragen des Coachs (Auszug):** Wie viele Anfragen sind Neuanfragen? Woran erkennt das Team heute eine dringende Anfrage? Wer darf Antworten freigeben? Antworten: etwa ein Drittel Neuanfragen; dringend = Termin oder Ausfall genannt; Freigabe durch den Innendienst.

**3. Use-Case-Canvas**

| Feld | Inhalt |
| --- | --- |
| Problem | Website-Anfragen warten im Schnitt 2 Werktage auf eine Antwort; Neuanfragen gehen unter |
| Zielgruppe | Innendienst (3), Außendienst (6) |
| Ist-Ablauf | lesen → im CRM suchen/anlegen → Art und Dringlichkeit einschätzen → Antwort oder Weitergabe; 15 min je Anfrage, 120 pro Monat (Annahme der Teilnehmerin) |
| Soll-Ablauf | Workflow ordnet jede Anfrage ein (Neuanfrage, Ersatzteil, Service), bewertet Neuanfragen, legt sie im CRM an und schreibt einen Antwortentwurf; der Innendienst prüft und sendet |
| Nutzen | Reaktionszeit von 2 Werktagen auf wenige Stunden, ca. 9 min weniger je Anfrage (Annahme), heiße Neuanfragen sofort beim Außendienst |
| Daten und Systeme | Formular-Felder vollständig; CRM-Firmendaten teilweise veraltet |
| Risiken | Personendaten in Anfragen (DSGVO, AVV mit n8n und KI-Anbieter); falsche Einordnung einer dringenden Service-Anfrage; Akzeptanz im Innendienst |

**4. Bewertung**

| Idee | Nutzen | Aufwand | Datenlage | Risiko | Summe | Begründung |
| --- | --- | --- | --- | --- | --- | --- |
| A Prompt-Vorlage im Chat für Antwortentwürfe (Chat) | 2 | 5 | 4 | 3 | 14 | schnell, spart aber nur Schreibzeit; Anfragen mit Personendaten im Chat |
| B Workflow „Anfrage-Eingang“ mit Einordnung, Bewertung, Entwurf und CRM-Eintrag (Workflow) | 5 | 3 | 4 | 4 | **16** | wiederkehrend, gleiche Schritte, Auslöser von außen; Freigabe bleibt beim Menschen |
| C eingebaute KI-Bewertung im CRM | 3 | 4 | 2 | 4 | 13 | laut Steckbrief nur in höherem Tarif, braucht viele gepflegte historische Daten |

**5. Top-1 und Erfolgskriterium:** Idee B. Messgröße: Reaktionszeit auf Neuanfragen, Ausgangswert 2 Werktage, Zielwert 4 Stunden, Zeitraum 6 Wochen Pilot. Voraussetzungen: AVV mit n8n und KI-Anbieter, Freigabe durch Datenschutz, eine verantwortliche Person im Innendienst.

**6. Übergabe-Block an den Workflow-Architekten**

```text
Problem: Website-Anfragen warten im Schnitt 2 Werktage auf eine Antwort, Neuanfragen gehen zwischen Ersatzteil- und Service-Anfragen unter.
Gewählter Use Case: Workflow „Anfrage-Eingang“: Anfrage einordnen (Neuanfrage, Ersatzteil, Service, Sonstiges), Neuanfragen bewerten, im CRM anlegen, Antwortentwurf zur Freigabe.
Ist-Ablauf: lesen → im CRM suchen oder anlegen → einschätzen → antworten oder weitergeben.
Daten und Systeme: Website-Formular (Firma, Name, E-Mail, Anliegen, Nachricht), HubSpot, Outlook; Innendienst gibt frei.
Risiken: Personendaten, Fehleinordnung dringender Service-Fälle, Akzeptanz.
Schätzwerte: 15 min je Anfrage heute, Ziel 6 min; 120 Anfragen pro Monat; ein Drittel Neuanfragen.
```

Warum gut: Das Problem ist ohne Werkzeug beschrieben, alle Zahlen sind als Schätzung markiert, und die gewählte Idee hat eine Messgröße mit Ausgangswert.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Coach schlägt sofort eine Lösung vor | Schilderung beginnt mit einer Lösung („Wir wollen einen Bot …“) | Problem und Ist-Ablauf schildern, Lösungswort weglassen |
| Canvas voller erfundener Zahlen | Schätzwerte fehlten | Prompt-Karte 12.1b, eigene Schätzungen nennen |
| alle Ideen haben 18–20 Punkte | Kriterien nicht ernst genommen | nach der Begründung je Punkt fragen, Aufwand und Risiko realistisch setzen |
| Chat fragt nach Kundennamen | Rollen-Prompt nicht vollständig eingefügt | neuen Chat öffnen, Assistent 1 vollständig einfügen |

## Fazit

- KI-Strategie im Vertrieb beantwortet vier Fragen: Ziel, Use Cases, Daten und Systeme, Menschen und Regeln.
- Die meisten KI-Projekte scheitern am Problemverständnis, nicht an der Technik; deshalb beginnt die Kette beim Canvas.
- Ein Pilot braucht eine verantwortliche Person, ein Enddatum und einen Ausgangswert.

> **Merksatz:** Erst das Problem auf eine Seite bringen, dann die Lösung bestellen.
