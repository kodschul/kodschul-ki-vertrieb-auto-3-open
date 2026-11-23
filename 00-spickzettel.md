# Spickzettel: KI im Vertrieb

## Fünf Bausteine eines guten Prompts

| Baustein | Frage |
| --- | --- |
| **Rolle** | Aus wessen Sicht wird geschrieben? |
| **Aufgabe** | Was genau soll entstehen? |
| **Kontext** | Welches Material muss die KI kennen? |
| **Format** | Wie sieht das Ergebnis aus (Tabelle, Mail, CSV)? |
| **Rahmenbedingungen** | Länge, Ton, Sprache, was nicht vorkommen darf |

Gilt im Chat wie in der Systemanweisung eines KI-Schritts. Details: [2.1](m02-prompting/l01-prompt-blocks.md), [7.1](m07-ai-workflows/l01-ai-node.md)

## Datenampel

| Farbe | Art | Regel |
| --- | --- | --- |
| grün | öffentlich | in jedes KI-Werkzeug |
| gelb | intern (Preisliste, Produktunterlagen) | nur mit Firmenkonto und Freigabe |
| rot | personenbezogen, vertraulich | weglassen oder anonymisieren |
| rot, immer | Zugangsdaten, Integration Secret, API-Schlüssel | nie |

Details: [1.3](m01-ai-sales-basics/l03-data-rules.md)

## Bewertungsmatrix (Muster)

| Teil | Kriterien | Punkte |
| --- | --- | --- |
| **Fit** | Branche/Segment 20 · Größe 10 · Räume 15 · Region 15 | max. 60 |
| **Interesse** | Anlass 25 · Dringlichkeit 15 | max. 40 |
| **Stufe** | heiß ≥ 70 · warm 40–69 · kalt < 40 | 0–100 |

Nie bewertet: Name, Herkunft, Rechtschreibung, Sprachstil. Details: [3.3](m03-lead-generation/l03-lead-scoring.md), [`material/bewertungsmatrix-muster.md`](material/bewertungsmatrix-muster.md)

## Chat oder Workflow

| | Chat mit dem KI-Assistenten | Workflow in n8n |
| --- | --- | --- |
| Häufigkeit | einmalig oder selten | wiederkehrend |
| Aufgabe | neu, noch unklar | bekannt, gleiche Schritte |
| Start | der Mensch tippt | Formular, Uhrzeit |
| Ergebnis | sofort gelesen | festes Format in Notion |

Details: [6.1](m06-n8n-basics/l01-automation-basics.md)

## n8n-Knoten im Kurs

| Knoten | Wofür | Lab |
| --- | --- | --- |
| Form Trigger | Formular erzeugen, Workflow starten | [6.2](m06-n8n-basics/l02-first-workflow.md) |
| Notion | Seite anlegen, suchen, aktualisieren | [6.2](m06-n8n-basics/l02-first-workflow.md), [9.1](m09-sales-automation/l01-follow-up-flow.md) |
| Edit Fields / If | Feld setzen / nach Bedingung verzweigen | [6.3](m06-n8n-basics/l03-data-flow.md) |
| Basic LLM Chain | KI-Schritt mit freiem Text | [7.1](m07-ai-workflows/l01-ai-node.md) |
| Information Extractor | KI-Schritt mit festen Feldern | [7.2](m07-ai-workflows/l02-auto-scoring.md) |
| HTTP Request | Seite abrufen | [8.1](m08-lead-enrichment/l01-enrichment.md) |
| Schedule Trigger / Aggregate | zu festen Zeiten starten / Items bündeln | [9.2](m09-sales-automation/l02-daily-briefing.md) |
| Error Trigger | Fehler melden | [9.3](m09-sales-automation/l03-operations.md) |

## Drei-Assistenten-Kette

```text
Problem → [1] Use-Case-Coach → [2] Workflow-Architekt → [3] Systemanweisungs-Generator → n8n
```

Prompts: [`material/assistenten-prompts.md`](material/assistenten-prompts.md) · Details: [The Nextise Agentic Way](00-nextise-agentic-way.md)

## Prüfliste für einen KI-Workflow

| Prüfpunkt | Frage |
| --- | --- |
| Zweck und Rechtsgrundlage | Wofür, auf welcher Grundlage nach Art. 6 DSGVO? |
| Datenminimierung | Bekommt jeder KI-Schritt nur die Felder, die er braucht? |
| Auftragsverarbeitung, Drittland | AV-Vertrag mit jedem Dienst? Wo liegen die Daten? |
| Information, Kennzeichnung | Weiß die Person, dass KI beteiligt ist? Feld „KI-gestützt“? |
| Entscheidung, Werberecht | Entscheidet ein Mensch? Geht nichts ohne Einwilligung als Werbung raus? |

Details: [11.1](m11-legal-ethics/l01-data-protection.md)

## Freigabe-Matrix

| KI darf allein (intern) | nur mit Freigabe | nie |
| --- | --- | --- |
| zusammenfassen, Profil erstellen | Antwort- und Follow-up-Entwürfe | Mails automatisch an Kunden senden |
| Score als Vorschlag, Status setzen | Lead endgültig aussortieren | Preise, Rabatte, Termine zusagen |
| Pipeline-Briefing fürs Team | Kampagnen-Mail an eine Liste | Kundendaten löschen |

Details: [11.3](m11-legal-ethics/l03-ethics.md)

> **Merksatz:** Die Formel rechnet, die KI erklärt, der Mensch gibt frei.
