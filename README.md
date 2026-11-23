<div align="center">

<img src="assets/kodschul-logo.png" alt="Kodschul" width="220" />

# KI im Vertrieb – Effizienz, Leadgenerierung und Automatisierung

3-Tage-Workshop · KI-Assistent, n8n und Notion im B2B-Vertrieb · Deutsch

**Leads mit KI finden und bewerten, CRM-Daten auswerten, Vertriebsaufgaben als Workflow automatisieren**

</div>

---

[Worum es geht](#worum-es-geht) · [Start](#start) · [Tag 1](#tag-1--ki-verstehen-leads-finden-crm-aufbauen) · [Tag 2](#tag-2--crm-daten-prognosen-lead-qualifizierung) · [Tag 3](#tag-3--automatisieren-recht-business-case) · [Hilfe](#hilfe)

## Worum es geht

- Viel Vertriebszeit geht in Recherche, Pflege und Schreibarbeit statt ins Kundengespräch.
- Tag 1: Leads mit dem KI-Assistenten finden, bewerten und ansprechen; ein Übungs-CRM in Notion aufbauen.
- Tag 2–3: CRM-Daten auswerten und die Aufgaben in n8n automatisieren, mit Freigabe durch den Menschen.
- Ergebnis: drei laufende Workflows und ein Business Case für die eigene Firma.

| | |
| --- | --- |
| **Für** | Vertrieb, Key Account, Sales Management, Marketing, Führungskräfte, Digitalisierungsverantwortliche |
| **Vorkenntnisse** | Grundkenntnisse in Vertrieb und Marketing; keine Programmierkenntnisse |
| **Werkzeuge** | KI-Assistent (ChatGPT, Claude, Perplexity oder Microsoft 365 Copilot), n8n Cloud, Notion |
| **Szenario** | Nordwind Workspace GmbH, fiktiver Anbieter für Besprechungsraum-Lösungen |
| **Leitmotiv** | [The Nextise Agentic Way](00-nextise-agentic-way.md): KI nutzen, um KI zu bauen |
| **Material** | [`material/`](material/): Unternehmensdaten, CRM-Daten, Testanfragen, Vorlagen, Musterworkflows |

## Start

1. Richte die drei Konten ein: [Vorbereitung](00-setup.md).
2. Lies den [Kursüberblick](00-ueberblick.md) und [The Nextise Agentic Way](00-nextise-agentic-way.md).
3. Öffne das Kursunternehmen [Nordwind Workspace](material/nordwind-unternehmen.md).
4. Beginne mit [Lab 1.1 KI im Vertrieb: das große Bild](m01-ai-sales-basics/l01-big-picture.md).

## Tag 1 – KI verstehen, Leads finden, CRM aufbauen

| Modul | Labs | Ergebnis |
| --- | --- | --- |
| 1 [KI-Grundlagen, Grenzen, Datenregeln](m01-ai-sales-basics/l01-big-picture.md) | [1.1 Das große Bild](m01-ai-sales-basics/l01-big-picture.md) · [1.2 Grenzen](m01-ai-sales-basics/l02-llm-limits.md) · [1.3 Datenregeln](m01-ai-sales-basics/l03-data-rules.md) | KI-Assistent startklar, Datenampel |
| 2 [Prompting für Vertriebsaufgaben](m02-prompting/l01-prompt-blocks.md) | [2.1 Fünf Bausteine](m02-prompting/l01-prompt-blocks.md) · [2.2 Nachschärfen](m02-prompting/l02-iteration.md) · [2.3 KI schreibt den Prompt](m02-prompting/l03-meta-prompt.md) | eigene Prompts in `meine-prompts.md` |
| 3 [KI-gestützte Leadgenerierung](m03-lead-generation/l01-ideal-customer.md) | [3.1 Zielkundenprofil](m03-lead-generation/l01-ideal-customer.md) · [3.2 Recherche](m03-lead-generation/l02-prospect-research.md) · [3.3 Lead-Scoring](m03-lead-generation/l03-lead-scoring.md) · [3.4 Erstansprache](m03-lead-generation/l04-first-contact.md) | bewertete Lead-Liste, Bewertungsmatrix |
| 4 [Notion als Übungs-CRM](m04-notion-crm/l01-crm-basics.md) | [4.1 CRM und Notion](m04-notion-crm/l01-crm-basics.md) · [4.2 Pipeline](m04-notion-crm/l02-pipeline.md) · [4.3 Gesprächsnotiz](m04-notion-crm/l03-call-notes.md) | Nordwind-CRM mit `Leads` und `Deals` |

## Tag 2 – CRM-Daten, Prognosen, Lead-Qualifizierung

| Modul | Labs | Ergebnis |
| --- | --- | --- |
| 5 [Vertriebsdaten analysieren und prognostizieren](m05-sales-analytics/l01-pipeline-analysis.md) | [5.1 Pipeline-Auswertung](m05-sales-analytics/l01-pipeline-analysis.md) · [5.2 Prognose](m05-sales-analytics/l02-forecast.md) · [5.3 Priorisieren](m05-sales-analytics/l03-prioritization.md) | geprüfte Auswertung, Quartalsprognose |
| 6 [Workflow-Automatisierung mit n8n](m06-n8n-basics/l01-automation-basics.md) | [6.1 Automatisierung](m06-n8n-basics/l01-automation-basics.md) · [6.2 Formular → Notion](m06-n8n-basics/l02-first-workflow.md) · [6.3 Daten und Fehler](m06-n8n-basics/l03-data-flow.md) | erster Workflow schreibt nach Notion |
| 7 [Lead-Qualifizierung mit KI](m07-ai-workflows/l01-ai-node.md) | [7.1 KI-Schritt](m07-ai-workflows/l01-ai-node.md) · [7.2 Lead-Scoring](m07-ai-workflows/l02-auto-scoring.md) · [7.3 Testfälle](m07-ai-workflows/l03-testing.md) | jede Anfrage kommt bewertet an |
| 8 [Leads anreichern, Antworten vorbereiten](m08-lead-enrichment/l01-enrichment.md) | [8.1 Anreicherung](m08-lead-enrichment/l01-enrichment.md) · [8.2 Antwortentwurf](m08-lead-enrichment/l02-reply-draft.md) | Workflow „Lead-Eingang“ komplett |

## Tag 3 – Automatisieren, Recht, Business Case

| Modul | Labs | Ergebnis |
| --- | --- | --- |
| 9 [Vertriebsaufgaben automatisieren](m09-sales-automation/l01-follow-up-flow.md) | [9.1 Follow-up](m09-sales-automation/l01-follow-up-flow.md) · [9.2 Pipeline-Briefing](m09-sales-automation/l02-daily-briefing.md) · [9.3 Betrieb](m09-sales-automation/l03-operations.md) | zwei weitere Workflows, alle exportiert |
| 10 [Customer Journey, Kampagnen, Tools](m10-journey-tools/l01-customer-journey.md) | [10.1 Customer Journey](m10-journey-tools/l01-customer-journey.md) · [10.2 Tool-Landschaft](m10-journey-tools/l02-tool-landscape.md) | Kampagnenplan, CRM-Steckbrief |
| 11 [Rechtliche und ethische Aspekte](m11-legal-ethics/l01-data-protection.md) | [11.1 Datenschutz](m11-legal-ethics/l01-data-protection.md) · [11.2 AI Act](m11-legal-ethics/l02-ai-act.md) · [11.3 Ethik](m11-legal-ethics/l03-ethics.md) | datensparsamer, geprüfter Workflow |
| 12 [Strategie und Business Case](m12-strategy-business-case/l01-use-case.md) | [12.1 Use Case](m12-strategy-business-case/l01-use-case.md) · [12.2 Konzept und Business Case](m12-strategy-business-case/l02-solution-design.md) · [12.3 Präsentation](m12-strategy-business-case/l03-presentation.md) | eigener Business Case mit Pilotplan |

Jedes Lab ist eine Seite mit Theorie, Übung und aufklappbarem Musterergebnis. Ablauf mit Uhrzeiten: [Kursüberblick](00-ueberblick.md#ablauf-der-drei-kurstage).

## Hilfe

- **Übungsdateien:** alle in [`material/`](material/); jede Übung nennt die Datei, mit der sie startet.
- **CRM-Daten:** Import-Anleitung und Erklärung der Übungsdaten in [`material/notion/`](material/notion/).
- **Workflow hängt:** Musterworkflow des Labs aus [`material/workflows/`](material/workflows/) importieren.
- **Prompts kopieren:** alle Prompt-Karten in [`material/prompt-karten.md`](material/prompt-karten.md), die drei Assistenten in [`material/assistenten-prompts.md`](material/assistenten-prompts.md).
- **Nachschlagen:** [Glossar](00-glossar.md), [Spickzettel](00-spickzettel.md).

---

<div align="center">
<sub>© Nextise GmbH · <a href="https://www.kodschul.com">kodschul.com</a> · Kompetenz aufbauen – von der sicheren KI-Anwendung bis zur modernen IT-Basis</sub>
</div>
