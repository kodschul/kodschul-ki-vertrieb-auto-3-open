# Lab 10.2: Tools und Plattformen – vom Übungs-CRM ins eigene System

**Leitfragen:**

<details>
<summary>Welche Systeme nutzt der eigene Vertrieb heute, und welche reden miteinander?</summary>

Typisch sind CRM, Mailprogramm, Kalender, ein Marketing-Werkzeug für Newsletter und Tabellen für Auswertungen. Oft tauschen nur CRM und Mail Daten aus; der Rest wird von Hand übertragen.

</details>

<details>
<summary>Was kostet es, wenn Daten zwischen zwei Systemen von Hand kopiert werden?</summary>

Zeit je Vorgang mal Häufigkeit mal Stundensatz, dazu Tippfehler und veraltete Daten. Fünf Minuten je Anfrage bei 200 Anfragen im Monat sind über 16 Stunden; diese Rechnung kommt in Lab 12.2 in den Business Case.

</details>

<details>
<summary>Welche Funktion des eigenen CRM wird bezahlt, aber nie genutzt?</summary>

Häufig gerade die KI-Funktionen: Zusammenfassungen, Mail-Entwürfe, Prognosen. Sie stecken in vielen Tarifen, sind aber nicht eingeschaltet oder niemand kennt sie. Ein Steckbrief macht sichtbar, was schon da ist.

</details>

- Für KI im Vertrieb gibt es drei Werkzeugklassen: CRM-Systeme, Marketing-Automatisierung und spezialisierte KI-Vertriebswerkzeuge; die großen CRM-Systeme haben eigene KI-Assistenten eingebaut.
- Der Weg ins eigene System ist kurz: Das Workflow-Muster aus Tag 2 und 3 bleibt gleich, nur der Notion-Knoten wird durch den Knoten des eigenen CRM ersetzt.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| CRM-System | Software für Kunden, Kontakte, Leads und Deals; das echte Gegenstück zum Übungs-CRM in Notion |
| KI-Vertriebswerkzeug | spezialisiertes Werkzeug für eine Vertriebsaufgabe mit KI, z. B. Firmendaten anreichern oder Gespräche auswerten |
| Gesprächsanalyse (Conversation Intelligence) | Software, die Anrufe und Videotermine aufzeichnet, verschriftlicht und auswertet, z. B. Redeanteile, Einwände, nächste Schritte |
| Datenstandort (EU-Hosting) | Land oder Region der Rechenzentren, in denen ein Anbieter die Daten speichert und verarbeitet |
| Anbieterabhängigkeit (Lock-in) | Wechsel zu einem anderen Anbieter wird teuer, weil Daten, Abläufe oder Verträge schwer mitzunehmen sind |
| Upsert | Kunstwort aus „update“ und „insert“: Eintrag aktualisieren, wenn er existiert, sonst neu anlegen – „suchen, dann aktualisieren“ in einem Schritt |

## Drei Werkzeugklassen für KI im Vertrieb

| Klasse | Wofür | Beispiele | Typische KI-Funktionen |
| --- | --- | --- | --- |
| CRM-System | Leads, Kontakte, Deals, Pipeline | HubSpot, Salesforce, Microsoft Dynamics 365 Sales, Pipedrive | Zusammenfassung eines Datensatzes, Mail-Entwurf, Abschlussprognose, Assistent im Seitenfenster |
| Marketing-Automatisierung | Kampagnen, Newsletter, Nurturing (Lab 10.1) | HubSpot Marketing Hub, Brevo, ActiveCampaign | Kampagne und Mails entwerfen, Inhalte je Kontakt anpassen |
| KI-Vertriebswerkzeug | eine Aufgabe besonders gut | Recherche und Anreicherung: Clay, Apollo, Leadfeeder; Gesprächsanalyse: Gong | Firmendaten zusammentragen, Kaufsignale erkennen, Gespräche auswerten |

## KI-Funktionen in CRM-Systemen

| CRM | KI-Funktionen laut Hersteller | Datenstandort | Testzugang |
| --- | --- | --- | --- |
| **HubSpot** | „Agent Hub“ mit Breeze Assistant: Berichte, Angebote und Seiten aus CRM-Daten; Agent für Interessenten-Recherche und Datenfragen; in Starter, Professional und Enterprise enthalten, viele Funktionen verbrauchen „HubSpot Credits“ | AWS-Rechenzentren u. a. in der EU (Deutschland); Zuordnung bei der Registrierung nach IP-Adresse, Wechsel nur mit bezahltem Tarif | CRM kostenlos ohne Ablaufdatum |
| **Salesforce** Sales Cloud | Agentforce: Zusammenfassungen für Accounts, Opportunities, Leads und Kontakte, automatische Pflege von Phase und nächstem Schritt, Prognosen („Predictive Scoring“) | Hyperforce-Regionen u. a. Deutschland | 30 Tage kostenlos |
| **Microsoft Dynamics 365 Sales** | Copilot: Zusammenfassung von Datensätzen, Vorbereitung von Terminen, Mail-Entwürfe, Nachrichten zu Kunden; Nachfolger ist der „Sales agent“ in Microsoft 365 Copilot | Verarbeitung in der EU Data Boundary; „Flex routing“ kann bei Last außerhalb verarbeiten, solange Admins es nicht abschalten | 30 Tage kostenlos |
| **Pipedrive** | AI Sales Assistant: Zusammenfassungen, Abschlusswahrscheinlichkeit mit nächster Aktion, Mail-Generator und Mail-Zusammenfassung | EU-Kunden in AWS-Regionen Frankfurt und Dublin; KI-Funktionen nutzen Unterauftragnehmer in verschiedenen Ländern | 14 Tage kostenlos |

Stand 22.11.2026, Angaben der Hersteller ohne Prüfung im eigenen Konto; vor einer Entscheidung prüfen. Quellen: HubSpot [Agent Hub](https://www.hubspot.com/products/artificial-intelligence), [Rechenzentren](https://knowledge.hubspot.com/account-security/hubspot-cloud-infrastructure-and-data-hosting-frequently-asked-questions), [Free CRM](https://www.hubspot.com/products/crm) · Salesforce [Sales AI](https://www.salesforce.com/sales/ai/), [Hyperforce](https://www.salesforce.com/platform/public-cloud-infrastructure/) · Microsoft [Copilot in Dynamics 365 Sales](https://learn.microsoft.com/en-us/dynamics365/sales/copilot-overview), [Geografische Verfügbarkeit](https://learn.microsoft.com/en-us/power-platform/admin/geographical-availability-copilot), [Testversion](https://www.microsoft.com/en-us/dynamics-365/free-trial) · Pipedrive [AI Sales Assistant](https://www.pipedrive.com/en/features/ai-sales-assistant), [Trust Center](https://trustcenter.pipedrive.com/).

![Microsoft Dynamics 365 Sales: Formular einer Verkaufschance mit rot markiertem Copilot-Widget „Summary“, das die wichtigsten Angaben der Verkaufschance in Stichpunkten zusammenfasst](https://learn.microsoft.com/en-us/dynamics365/sales/media/copilot-opportunity-summary-widget.png)
_Quelle: Microsoft Learn, „Summarize records with Copilot“ (https://learn.microsoft.com/en-us/dynamics365/sales/copilot-summarize-records), © Microsoft, abgerufen am 23.11.2026._

Die Zusammenfassung im Bild ist dasselbe wie die Zusammenfassung aus Lab 7.1, nur fest im CRM eingebaut.

![Pipedrive Sales Assistant als Chatfenster: Frage „What's our sales performance for the last quarter?“, Antwort mit Anzahl der Deals je Monat und den Reitern „Answer“ und „Sources“](https://kb-cms.pipedriveassets.com/questions%20about%20my%20data.png)
_Quelle: Pipedrive Knowledge Base, „Sales Assistant“ (https://support.pipedrive.com/en/article/sales-assistant), © Pipedrive, abgerufen am 23.11.2026._

## Marketing-Automatisierung mit KI

| Werkzeug | KI-Funktionen laut Hersteller | Datenstandort | Testzugang |
| --- | --- | --- | --- |
| **HubSpot Marketing Hub** | Content Agent (Blog, Social, Landingpages), Nurture Agent (schreibt jede Nurturing-Mail für den einzelnen Kontakt um), Campaign Agent (plant eine ganze Kampagne) | wie HubSpot CRM | 14 Tage; kostenlose Basiswerkzeuge |
| **Brevo** | „Aura“-Agenten: Inhalte erzeugen, Kontakte anreichern, Deals anlegen, Live-Chats zusammenfassen | Server in der EU | kostenloser Tarif bis 300 Mails pro Tag |
| **ActiveCampaign** | Active Intelligence: erkennt Anlässe und baut ganze Kampagnen, regelmäßige Auswertungen per Mail, Bilder erzeugen | keine Angabe zu EU-Rechenzentren gefunden (prüfen) | 14 Tage |

Stand 22.11.2026; Quellen: [HubSpot Marketing Hub](https://www.hubspot.com/products/marketing), [Brevo AI](https://www.brevo.com/ai/), [Brevo Datensicherheit](https://www.brevo.com/features/data-security/), [Brevo Preise](https://www.brevo.com/pricing/), [ActiveCampaign AI](https://www.activecampaign.com/ai).

![HubSpot Marketing Studio: links das Breeze-Fenster „Hi Maria, how can I help you?“ mit Vorschlägen; rechts Insights zu Kampagnen, ein Diagramm „Active campaigns pipeline“ und die Kampagnenliste mit 18 Kampagnen](https://www.hubspot.com/hubfs/MH_Studio_Overview_08212026%20%281%29.png)
_Quelle: HubSpot, „Marketing Hub“ (https://www.hubspot.com/products/marketing), Produktbild © HubSpot, abgerufen am 23.11.2026._

## KI-Vertriebswerkzeuge für einzelne Aufgaben

| Aufgabe | Beispiel | Was es laut Hersteller tut | Bezug im Kurs |
| --- | --- | --- | --- |
| Recherche und Anreicherung | [Clay](https://www.clay.com/) | Daten von über 200 Anbietern an einem Ort, Signale wie Jobwechsel verfolgen | Anreicherung mit Firmenprofil (Lab 8.1) |
| | [Apollo](https://www.apollo.io/) | Vertriebsplattform mit Kontaktdaten, Signalen und Ausführung | Recherche (Lab 3.2) |
| | [Leadfeeder](https://www.dealfront.com/) (früher Dealfront) | erkennt Firmen, die die eigene Website besuchen; „Hosted in the EU“ | Kaufsignale (Lab 3.2) |
| Gesprächsanalyse | [Gong](https://www.gong.io/) | lernt aus Anrufen, Mails und Terminen, Agenten unterstützen das Vertriebsteam | Gesprächsnotiz (Lab 4.3, 9.1) |
| Assistent im CRM | Copilot, Breeze, Agentforce, Pipedrive Sales Assistant | siehe Tabelle oben | Briefing (Lab 9.2) |

Stand 22.11.2026, Herstellerseiten. Kontaktdatenbanken und Gesprächsaufzeichnung berühren Datenschutz und Einwilligung besonders stark (vertieft in Modul 11).

## Auswahlkriterien für Werkzeuge

| Kriterium | Prüffrage | Warnzeichen |
| --- | --- | --- |
| Datenschutz und EU-Hosting | Wo liegen die Daten, auch bei KI-Funktionen? Gibt es einen Auftragsverarbeitungsvertrag? | Datenstandort nur „weltweit“, KI über unbenannte Drittanbieter |
| Integration | Gibt es einen n8n-Knoten oder eine offene Schnittstelle (API)? Lassen sich Leads lesen und schreiben? | Daten nur per Export-Datei, keine API im gewählten Tarif |
| Kosten | Lizenz je Person plus KI-Guthaben (Credits) plus Einrichtung und Pflege? | KI nur im teuersten Tarif, Verbrauch nicht planbar |
| Abhängigkeit vom Anbieter | Lassen sich alle Daten vollständig exportieren? Laufen Abläufe auch außerhalb? | Abläufe nur im Werkzeug selbst, Export unvollständig |

## Vom Notion-Knoten zum Knoten des eigenen CRM

Die Workflows aus Tag 2 und 3 bleiben gleich: Auslöser, KI-Schritt, Regeln, Freigabe. Nur der Knoten, der liest und schreibt, wird ausgetauscht.

```text
Lead-Anfrage → Lead bewerten → Score ab 70? → [ Notion: Lead in Notion anlegen ]
                                                   ↓ ersetzen durch
                                              [ HubSpot: Contact → Create/Update ]
                                              [ Salesforce: Lead → Create ]
                                              [ Pipedrive: Lead → Create ]
```

| Aufgabe im Kurs | Notion (Übung) | HubSpot | Salesforce | Pipedrive | Microsoft Dynamics CRM |
| --- | --- | --- | --- | --- | --- |
| Lead anlegen (Lab 6.2) | Database Page → Create | Contact → Create/Update | Lead → Create | Lead → Create | nur Account; mehr über HTTP Request (Lab 8.1) |
| Lead suchen und aktualisieren (Lab 9.1) | Get Many mit Filter → Update | Contact → Create/Update (Upsert über die Mailadresse) | Lead → Upsert oder Get All → Update | Lead → Get All → Update | Account → Get All → Update |
| Offene Deals lesen (Lab 9.2) | Database Page → Get Many | Deal → Get All | Opportunity → Get All | Deal → Get All | über HTTP Request |
| Ressourcen des Knotens | Database Page, Page, Block … | Contact, Company, Deal, Engagement, Form, Ticket … | Account, Contact, Lead, Opportunity, Task … | Activity, Deal, Lead, Note, Organization, Person … | Account |

Stand 22.11.2026, Operationen je nach Version anders benannt; Quellen: n8n Docs [HubSpot](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.hubspot), [Salesforce](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.salesforce), [Pipedrive](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.pipedrive), [Microsoft Dynamics CRM](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.microsoftdynamicscrm), Übersicht [n8n.io/integrations](https://n8n.io/integrations/). Die Verbindung zum Firmen-CRM richtet die IT ein (Zugangsdaten, Rechte); getestet wird in einer Testumgebung, nie im echten Kundenbestand.

## Übung: Steckbrief „Unser CRM und KI“ recherchieren

**Material:** Name des CRM der eigenen Firma oder eines der vier Beispiele · **Werkzeug:** KI-Assistent mit Websuche (ChatGPT, Claude, Perplexity oder Microsoft 365 Copilot), Texteditor

**Ausgangslage:** Für den Business Case in Modul 12 wird ein Baustein gebraucht: Was kann das eigene CRM schon mit KI, lässt es sich an n8n anbinden, und wo liegen die Daten? Interne Angaben (Verträge, Preise, Kundendaten) gehören nach der Datenampel aus Lab 1.3 nicht in den Chat.

1. Öffne einen neuen Chat mit eingeschalteter Websuche und sende Prompt-Karte 10.2a mit dem Namen des CRM.
2. Prüfe, ob jede Angabe einen Link auf eine Seite des Herstellers oder von n8n hat, und lass fehlende Quellen nachliefern oder die Angabe streichen.
3. Öffne für zwei Angaben die Quelle (eine davon die n8n-Anbindung auf `n8n.io/integrations`) und markiere jede als bestätigt oder korrigiert.
4. Speichere den Steckbrief als `crm-steckbrief.md` im Texteditor.

**Prompt-Karte 10.2a – CRM-Steckbrief recherchieren**

```text
Recherchiere im Web einen Steckbrief zum CRM-System [Name des CRM] für den Vertrieb eines mittelständischen Unternehmens in Deutschland.

Gliederung:
1. Kurzprofil in zwei Sätzen
2. Eingebaute KI-Funktionen: Name der Funktion, was sie tut, in welchem Tarif
3. Anbindung an n8n: eigener Knoten ja/nein, welche Ressourcen (z. B. Lead, Deal, Kontakt); sonst API
4. Datenstandort: EU-Rechenzentrum ja/nein, auch für die KI-Funktionen
5. Testzugang und Kostenmodell (ohne konkrete Vertragspreise)
6. Offene Punkte, die mit IT oder Datenschutz zu klären sind

Regeln: Nur Herstellerseiten, Hilfeseiten des Herstellers, docs.n8n.io und n8n.io als Quellen. Hinter jede Angabe den Link und das Datum. Was nicht belegt ist, als „nicht gefunden“ markieren statt zu raten. Antworte auf Deutsch als Tabelle.
```

**Checkpoint:** `crm-steckbrief.md` enthält sechs Abschnitte mit Quellenlinks; zwei Angaben sind an der Quelle geprüft und als bestätigt oder korrigiert markiert.

**Erweiterung:** Prüfe auf der n8n-Dokumentationsseite des Knotens, ob die Operation „Update“ für Leads vorhanden ist, und notiere, welcher Knoten im Workflow „Gesprächsnotiz → CRM“ ersetzt würde.

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Beispiel aus ChatGPT mit Websuche für Pipedrive, Stand 22.11.2026 – Recherche-Ergebnisse fallen jedes Mal etwas anders aus.

**Steckbrief „Unser CRM und KI“: Pipedrive**

| Abschnitt | Angabe | Quelle | Prüfung |
| --- | --- | --- | --- |
| Kurzprofil | Vertriebs-CRM mit Pipeline-Ansicht für kleine und mittlere Vertriebsteams | pipedrive.com | |
| KI-Funktionen | AI Sales Assistant: Zusammenfassungen und verknüpfte Deals, Abschlusswahrscheinlichkeit mit nächster Aktion, Mail-Generator, Mail-Zusammenfassung | [pipedrive.com/en/features/ai-sales-assistant](https://www.pipedrive.com/en/features/ai-sales-assistant) | |
| Anbindung an n8n | eigener Knoten „Pipedrive“ mit Activity, Deal, Lead, Note, Organization, Person, Product u. a.; Lead: Create, Get, Get All, Update | [docs.n8n.io – Pipedrive](https://docs.n8n.io/integrations/builtin/app-nodes/n8n-nodes-base.pipedrive), [n8n.io/integrations/pipedrive](https://n8n.io/integrations/pipedrive/) | ✓ bestätigt an der Quelle |
| Datenstandort | EU-Kunden in den AWS-Regionen Frankfurt und Dublin; KI-Funktionen nutzen Unterauftragnehmer in verschiedenen Ländern, Standardvertragsklauseln wo nötig | [trustcenter.pipedrive.com](https://trustcenter.pipedrive.com/) | ✓ bestätigt; korrigiert: Die erste Antwort nannte „alle Daten in der EU“, die KI-Verarbeitung ist ausgenommen |
| Testzugang | 14 Tage kostenlos, ohne Kreditkarte | pipedrive.com (Seite AI Sales Assistant) | |
| Offene Punkte | welche Unterauftragnehmer die KI nutzt; ob KI-Funktionen im eigenen Tarif enthalten sind; Auftragsverarbeitungsvertrag | – | mit IT und Datenschutz klären |

**Bezug zum Kurs:** Im Workflow „Gesprächsnotiz → CRM“ würden „Lead in Notion finden“ und „Lead in Notion aktualisieren“ durch Pipedrive-Knoten (Lead → Get All, Lead → Update) ersetzt; Formular, KI-Schritt und Freigabe bleiben gleich.

Warum gut: Jede Angabe hat eine Herstellerquelle, und die Prüfung hat eine zu glatte Aussage der KI zum Datenstandort korrigiert.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Steckbrief ohne Links oder mit Links auf Vergleichsportale | Websuche aus oder Quellenregel fehlt | Websuche einschalten, Regel „nur Herstellerseiten“ |
| Funktion existiert laut KI, auf der Herstellerseite aber nicht | veraltete Angabe oder Produktname verwechselt (KI-Marken werden oft umbenannt) | Angabe streichen oder mit Datum als „nicht gefunden“ markieren |
| „Daten liegen in der EU“ ohne Einschränkung | Datenstandort des CRM mit dem der KI-Funktionen verwechselt | gezielt nach KI-Verarbeitung und Unterauftragnehmern fragen |
| Vertragspreise oder Kundenzahlen der eigenen Firma im Chat | Datenampel nicht beachtet | nur öffentliche Angaben verwenden (Lab 1.3) |
| n8n-Knoten wird genannt, kann aber nicht, was gebraucht wird | nur der Name geprüft, nicht die Ressourcen | Dokumentationsseite des Knotens öffnen, sonst HTTP Request |

## Fazit

- CRM, Marketing-Automatisierung und KI-Vertriebswerkzeuge bringen eigene KI mit; ein Steckbrief zeigt, was im eigenen System schon vorhanden ist.
- Ausgewählt wird nach Datenschutz und Datenstandort, Integration, Kosten und Abhängigkeit vom Anbieter.
- Der Weg ins eigene CRM tauscht nur den Notion-Knoten; Auslöser, KI-Schritte und Freigabe bleiben.

> **Merksatz:** Erst prüfen, was das eigene CRM schon kann, dann ergänzen, was fehlt.
