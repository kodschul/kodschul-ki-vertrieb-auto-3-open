# Glossar: KI im Vertrieb

| Begriff | Bedeutung | Lab |
| --- | --- | --- |
| Abschlussquote (Win Rate) | gewonnene ÷ alle abgeschlossenen Deals | [5.1](m05-sales-analytics/l01-pipeline-analysis.md) |
| Aggregate | n8n-Knoten, der viele Items zu einem bündelt | [9.2](m09-sales-automation/l02-daily-briefing.md) |
| AI Act | KI-Verordnung der EU (2024/1689), gilt direkt in allen EU-Staaten | [11.2](m11-legal-ethics/l02-ai-act.md) |
| Anonymisieren | Angaben ersetzen oder weglassen, bis niemand mehr erkennbar ist | [1.3](m01-ai-sales-basics/l03-data-rules.md) |
| Anreicherung (Enrichment) | fehlende Lead-Angaben automatisch aus anderen Quellen ergänzen | [8.1](m08-lead-enrichment/l01-enrichment.md) |
| API-Schlüssel | geheime Zeichenfolge, über die ein KI-Anbieter Aufrufe zuordnet und abrechnet | [7.1](m07-ai-workflows/l01-ai-node.md) |
| Auftragsverarbeitung | Dienstleister verarbeitet Daten im Auftrag, geregelt im AV-Vertrag | [11.1](m11-legal-ethics/l01-data-protection.md) |
| Auslöser (Trigger) | erster Schritt, der einen Workflow startet | [6.1](m06-n8n-basics/l01-automation-basics.md) |
| Ausführung (Execution) | ein protokollierter Durchlauf eines Workflows | [6.1](m06-n8n-basics/l01-automation-basics.md) |
| Ausdruck | Platzhalter `{{ $json.Firma }}`, den n8n beim Lauf füllt | [6.2](m06-n8n-basics/l02-first-workflow.md) |
| Basic LLM Chain | n8n-Knoten für einen KI-Schritt mit freiem Text | [7.1](m07-ai-workflows/l01-ai-node.md) |
| Bewertungsmatrix | Kriterien mit Punkten und Schwellen für Lead-Scoring | [3.3](m03-lead-generation/l03-lead-scoring.md) |
| Business Case | Nutzen, Kosten, Risiken und Entscheidung auf einer Seite | [12.2](m12-strategy-business-case/l02-solution-design.md) |
| Buyer Persona | realistische Beschreibung einer mitentscheidenden Rolle | [3.1](m03-lead-generation/l01-ideal-customer.md) |
| CRM | Software für Kunden, Kontakte, Leads und Deals | [4.1](m04-notion-crm/l01-crm-basics.md) |
| CSV | Textdatei für Tabellen, Spalten durch Kommas getrennt | [3.2](m03-lead-generation/l02-prospect-research.md) |
| Credential | in n8n gespeicherte Zugangsdaten für einen Dienst | [6.2](m06-n8n-basics/l02-first-workflow.md) |
| Customer Journey | Weg eines Kunden vom ersten Kontakt bis zum Wiederkauf | [10.1](m10-journey-tools/l01-customer-journey.md) |
| Datenampel | grün öffentlich, gelb intern, rot personenbezogen und vertraulich | [1.3](m01-ai-sales-basics/l03-data-rules.md) |
| Datenbank (Notion) | Tabelle, in der jede Zeile eine eigene Seite ist | [4.1](m04-notion-crm/l01-crm-basics.md) |
| Datenminimierung | nur die Daten verarbeiten, die der Zweck braucht | [11.1](m11-legal-ethics/l01-data-protection.md) |
| Deal | konkretes Geschäft mit Wert, Phase und Abschlussdatum | [4.1](m04-notion-crm/l01-crm-basics.md) |
| DSGVO | Datenschutz-Grundverordnung der EU | [1.3](m01-ai-sales-basics/l03-data-rules.md) |
| Eigenschaft (Property) | Spalte einer Notion-Datenbank mit festem Typ | [4.1](m04-notion-crm/l01-crm-basics.md) |
| Einwilligung (Opt-in) | vorherige, ausdrückliche Zustimmung, z. B. zu Werbe-Mails | [3.4](m03-lead-generation/l04-first-contact.md) |
| Fehler-Workflow | Workflow, den n8n startet, wenn ein anderer scheitert | [9.3](m09-sales-automation/l03-operations.md) |
| Fit / Interesse | passt die Firma? / will sie jetzt kaufen? | [3.3](m03-lead-generation/l03-lead-scoring.md) |
| Formel-Eigenschaft | Notion-Spalte, die aus anderen Spalten rechnet | [4.2](m04-notion-crm/l02-pipeline.md) |
| Formular-Auslöser | n8n-Knoten, der ein Formular erzeugt und den Workflow startet | [6.2](m06-n8n-basics/l02-first-workflow.md) |
| Freigabe-Matrix | KI allein / nur mit Freigabe / nie | [11.3](m11-legal-ethics/l03-ethics.md) |
| Gateway credits | Guthaben in n8n Cloud für KI-Schritte ohne eigenen Schlüssel | [7.1](m07-ai-workflows/l01-ai-node.md) |
| Gestockter Deal | offener Deal ohne Bewegung: Termin überschritten oder lange kein Kontakt | [5.1](m05-sales-analytics/l01-pipeline-analysis.md) |
| Gewichteter Wert | Wert × Wahrscheinlichkeit ÷ 100 | [4.2](m04-notion-crm/l02-pipeline.md) |
| Halluzination | überzeugend klingende, aber erfundene Aussage | [1.2](m01-ai-sales-basics/l02-llm-limits.md) |
| HTTP Request | n8n-Knoten, der eine Seite abruft | [8.1](m08-lead-enrichment/l01-enrichment.md) |
| Human-in-the-Loop | Mensch prüft und entscheidet an einer festen Stelle | [8.2](m08-lead-enrichment/l02-reply-draft.md) |
| Information Extractor | n8n-Knoten für einen KI-Schritt mit festen Feldern | [7.2](m07-ai-workflows/l02-auto-scoring.md) |
| Integration Secret | geheimer Schlüssel der Notion-Verbindung; Datenampel rot | [6.2](m06-n8n-basics/l02-first-workflow.md) |
| Interview-Prompt | die KI fragt zuerst und schreibt danach den Prompt | [2.3](m02-prompting/l03-meta-prompt.md) |
| Item | ein Datensatz, der durch den Workflow wandert | [6.3](m06-n8n-basics/l03-data-flow.md) |
| Kaltakquise | Erstkontakt zu einer Firma, die nicht angefragt hat | [3.4](m03-lead-generation/l04-first-contact.md) |
| Kaufsignal | öffentlicher Hinweis auf möglichen Bedarf, z. B. Umzug | [3.2](m03-lead-generation/l02-prospect-research.md) |
| Knoten (Node) | ein Schritt auf der n8n-Arbeitsfläche | [6.1](m06-n8n-basics/l01-automation-basics.md) |
| Lead | Interessent, der noch kein Kunde ist | [1.1](m01-ai-sales-basics/l01-big-picture.md) |
| Lead-Scoring | Punktzahl für Passung und Kaufwahrscheinlichkeit | [3.3](m03-lead-generation/l03-lead-scoring.md) |
| Machine Learning | lernt Muster aus Beispieldaten statt festen Regeln | [1.1](m01-ai-sales-basics/l01-big-picture.md) |
| Nextise Agentic Way | Problem verstehen → konzipieren → bauen; der Mensch entscheidet | [00-nextise-agentic-way.md](00-nextise-agentic-way.md) |
| Nurturing | Lead-Pflege über Wochen, bis ein Gespräch sinnvoll ist | [10.1](m10-journey-tools/l01-customer-journey.md) |
| Pilot | befristeter Testlauf mit Kennzahlen und Entscheidung danach | [12.1](m12-strategy-business-case/l01-use-case.md) |
| Pipeline | offene Deals, geordnet nach Phasen | [4.1](m04-notion-crm/l01-crm-basics.md) |
| Prompt | Eingabe an den KI-Assistenten | [1.1](m01-ai-sales-basics/l01-big-picture.md) |
| Prompt-Injection | versteckte Anweisung in einem Eingabetext, die das Modell umlenken soll | [7.3](m07-ai-workflows/l03-testing.md) |
| Sprachmodell (LLM) | Machine Learning für Sprache; erzeugt Text | [1.1](m01-ai-sales-basics/l01-big-picture.md) |
| Stichtag | festes Bezugsdatum der Übungsdaten: 01.12.2026 | [5.1](m05-sales-analytics/l01-pipeline-analysis.md) |
| Systemanweisung | fester Teil des Prompts im KI-Schritt: Rolle, Regeln, Format | [7.1](m07-ai-workflows/l01-ai-node.md) |
| Umsatzprognose (Forecast) | Schätzung des Umsatzes in einem Zeitraum | [5.2](m05-sales-analytics/l02-forecast.md) |
| Use-Case-Canvas | eine Seite, die einen Use Case vollständig beschreibt | [12.1](m12-strategy-business-case/l01-use-case.md) |
| UWG § 7 | regelt, wann Werbung als unzumutbare Belästigung verboten ist | [3.4](m03-lead-generation/l04-first-contact.md) |
| Veröffentlichen (Publish) | schaltet einen n8n-Workflow scharf | [9.2](m09-sales-automation/l02-daily-briefing.md) |
| Verzerrung (Bias) | ein Merkmal, das nicht zählen soll, verschiebt das Ergebnis | [11.3](m11-legal-ethics/l03-ethics.md) |
| Websuche | Assistent sucht im Internet und nennt Quellen | [1.2](m01-ai-sales-basics/l02-llm-limits.md) |
| Workflow | Auslöser und Schritte, die Daten weiterreichen | [6.1](m06-n8n-basics/l01-automation-basics.md) |
| Zeitplan-Auslöser | startet einen Workflow zu festen Zeiten | [9.2](m09-sales-automation/l02-daily-briefing.md) |
| Zielkundenprofil (ICP) | Beschreibung der Firma, die am besten passt | [3.1](m03-lead-generation/l01-ideal-customer.md) |
