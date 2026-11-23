# Kursüberblick: KI im Vertrieb – Effizienz, Leadgenerierung und Automatisierung

## Die Entwicklung von KI im Vertrieb

- Vertriebsleute verkaufen im Schnitt nur 40 % ihrer Woche ([1.1](m01-ai-sales-basics/l01-big-picture.md)).
- Seit Ende 2022 schreiben KI-Assistenten Mails, Recherchen und Zusammenfassungen in Sekunden.
- 57 % der Unternehmen in Deutschland nutzen KI, im Vertrieb noch mehr ([1.1](m01-ai-sales-basics/l01-big-picture.md)).
- Workflow-Werkzeuge wie n8n verbinden KI mit CRM, Formularen und Zeitplänen – ohne Programmierung.

## Was ist KI im Vertrieb?

- **Machine Learning:** lernt Muster aus Daten, z. B. Abschlusswahrscheinlichkeit aus gewonnenen und verlorenen Deals.
- **Sprachmodell:** erzeugt Text; sagt die plausibelste Fortsetzung voraus, nicht die geprüfte Wahrheit.
- **Workflow:** Auslöser → Schritte → Ergebnis, läuft von selbst, z. B. bei jeder neuen Anfrage.
- **Verantwortung:** entscheiden und freigeben bleibt beim Menschen.

Details: [1.1 KI im Vertrieb: das große Bild](m01-ai-sales-basics/l01-big-picture.md)

## Warum KI im Vertrieb?

| Aufgabe | Ohne KI | Mit KI und Workflow |
| --- | --- | --- |
| Potenzielle Kunden finden | Stunden Suchen und Lesen | Lead-Liste mit Quellen in Minuten, Mensch prüft |
| Leads bewerten | Bauchgefühl, je Person anders | gleiche Bewertungsmatrix für alle, mit Begründung |
| Neue Anfrage beantworten | oft erst Tage später | bewertet, angereichert und Antwortentwurf in Minuten |
| Pipeline-Überblick | Listen von Hand | Briefing jeden Morgen, Zahlen in Notion geprüft |

## Leitmotiv: The Nextise Agentic Way

> **KI nutzen, um KI zu bauen:** Problem verstehen → Lösung konzipieren → Lösung bauen. Der Mensch entscheidet in jedem Schritt.

Details: [The Nextise Agentic Way](00-nextise-agentic-way.md)

## Ziel und Ergebnis

- KI-Assistenten sicher und nach Datenregeln für Vertriebsaufgaben nutzen.
- Leads finden, mit einer Bewertungsmatrix bewerten und rechtssicher ansprechen.
- CRM-Daten auswerten, Prognosen erstellen und Zahlen gegenprüfen.
- Drei Workflows in n8n: Lead-Eingang, Gesprächsnotiz mit Follow-up, Pipeline-Briefing.
- Einen Business Case mit Workflow-Konzept und Pilotplan für die eigene Firma.

## Szenario Nordwind Workspace

- Fiktiver B2B-Anbieter für Besprechungsräume: Raumdisplay, Kamera-Set, Buchungs-Software, Service.
- Mittelstand in Deutschland, Österreich, der Schweiz und den Niederlanden.
- Übungs-CRM in Notion mit den Datenbanken `Leads` und `Deals`; Stichtag der Übungsdaten: 01.12.2026.
- Alle Daten erfunden, deshalb in jedes Werkzeug eingebbar.

Details: [`material/nordwind-unternehmen.md`](material/nordwind-unternehmen.md)

## Ablauf der drei Kurstage

### Tag 1 – KI verstehen, Leads finden und bewerten, CRM aufbauen

| Zeit | Inhalt |
| --- | --- |
| 09:00 | Auftakt, The Nextise Agentic Way |
| 09:30 | **Modul 1** KI-Grundlagen, Grenzen, Datenregeln |
| 10:30 | Pause |
| 10:45 | **Modul 2** Prompting für Vertriebsaufgaben |
| 11:45 | **Modul 3** Leadgenerierung (Mittag 12:15–13:15) |
| 14:45 | Pause |
| 15:00 | **Modul 4** Notion als Übungs-CRM |
| 16:15 | Tagesabschluss |

### Tag 2 – CRM-Daten auswerten, Prognosen, automatisierte Lead-Qualifizierung

| Zeit | Inhalt |
| --- | --- |
| 09:00 | Tageseinstieg |
| 09:15 | **Modul 5** Vertriebsdaten analysieren und prognostizieren |
| 10:30 | Pause |
| 10:45 | **Modul 6** Workflow-Automatisierung mit n8n |
| 12:15 | Mittagspause |
| 13:15 | **Modul 7** Lead-Qualifizierung mit KI |
| 14:45 | Pause |
| 15:00 | **Modul 8** Leads anreichern, Antworten vorbereiten |
| 16:15 | Tagesabschluss |

### Tag 3 – Prozesse automatisieren, Recht und Ethik, eigener Business Case

| Zeit | Inhalt |
| --- | --- |
| 09:00 | Tageseinstieg |
| 09:15 | **Modul 9** Vertriebsaufgaben automatisieren (Pause 10:30) |
| 11:10 | **Modul 10** Customer Journey, Kampagnen, Tool-Landschaft |
| 12:15 | Mittagspause |
| 13:15 | **Modul 11** Rechtliche und ethische Aspekte |
| 14:15 | **Modul 12** Strategie und Business Case (Pause 14:45) |
| 16:15 | Kursabschluss |

Alle Labs mit Zeiten: [`README.md`](README.md#tag-1--ki-verstehen-leads-finden-crm-aufbauen)

## Arbeitsweise

- Jedes Lab: Leitfragen → Kern mit Bild → Übung im Werkzeug → Musterergebnis → Merksatz.
- Rund 70 % der Zeit wird im Werkzeug gearbeitet.
- Jeder Workflow liegt als Muster zum Import bereit, falls der eigene Bau hängt.

## Voraussetzungen

- Laptop mit aktuellem Chrome oder Edge; nichts zu installieren.
- Konten: ein KI-Assistent, Notion, n8n Cloud (Testphase) – Anleitung: [00-setup.md](00-setup.md).
- Keine Programmier- oder Automatisierungskenntnisse.
