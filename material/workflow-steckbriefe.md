# Steckbriefe der Nordwind-Workflows

Fiktives Unternehmen, alle Angaben erfunden.

Kurzbeschreibungen der drei Workflows aus dem Kurs für die Prüfung in [Lab 11.2](../m11-legal-ethics/l02-ai-act.md): je Workflow Auslöser, Daten, KI-Schritte, Empfänger der Daten, Freigabe und Speicherort. Der gesamte Text ist zum Einfügen in einen KI-Chat gedacht und enthält keine echten Personen- oder Kundendaten. Wer eigene Workflows prüft, beschreibt sie im selben Raster.

Stand der Dienste und Speicherorte: 22.11.2026, Quellen in [Lab 11.1](../m11-legal-ethics/l01-data-protection.md), Tabelle „Dienstleister im Lead-Eingang und ihr Speicherort“; vor dem Einsatz prüfen.

## Gemeinsame Plattform

| Baustein | Dienst | Speicherort laut Anbieter |
| --- | --- | --- |
| Automatisierung | n8n Cloud (Auftragsverarbeiter mit AVV) | Microsoft Azure in der EU |
| KI-Modell | über n8n Gateway credits, Modell gpt-5-mini (OpenAI); OpenAI ist Unterauftragsverarbeiter von n8n | USA |
| CRM | Notion, Arbeitsbereich „Nordwind CRM“ mit den Datenbanken `Leads` und `Deals` | USA (Standard), EU nur im Enterprise-Tarif |
| Ausführungsprotokolle | n8n speichert Eingaben und Ausgaben jedes Knotens je Ausführung | n8n Cloud, aufbewahrt je Tarif 7 Tage (Starter) oder 30 Tage (Pro), Enterprise unbegrenzt |

Kein Workflow versendet Mails. Entwürfe landen in Notion und werden von einem Menschen geprüft.

## Workflow 1: Lead-Eingang (Lab 6.2–8.2, datensparsam seit Lab 11.1)

| Punkt | Beschreibung |
| --- | --- |
| Zweck | Website-Anfragen zusammenfassen, nach der Bewertungsmatrix bewerten, Antwortentwurf vorbereiten, Lead im CRM anlegen |
| Auslöser | Formular „Lead-Anfrage“ auf einer n8n-Formularseite |
| Daten im Eingang | Firma, Website, Name, Rolle, E-Mail, Mitarbeitende, Anzahl Räume, Region, Nachricht (Freitext) |
| Personenbezug | Name, Rolle, E-Mail der Ansprechperson; die Nachricht kann Namen und weitere Angaben enthalten |
| Rechtsgrundlage (Annahme) | Anfrage der Person (Art. 6 Abs. 1 b DSGVO) |
| Web-Abruf | „Firmenprofil abrufen“ lädt die Seite unter der angegebenen Website (im Kurs: fiktive Profile auf GitHub) |
| KI-Schritt 1 | „Firmenprofil zusammenfassen“ (Basic LLM Chain): bekommt Website-Adresse und Seiteninhalt → fünf Stichpunkte |
| KI-Schritt 2 | „Anfrage zusammenfassen“ (Basic LLM Chain): bekommt Firma, Mitarbeitende, Anzahl Räume, Region, Nachricht → ein Satz |
| KI-Schritt 3 | „Lead bewerten“ (Information Extractor): bekommt Firma, Website, Mitarbeitende, Anzahl Räume, Region, Nachricht, Firmenprofil → Score, Stufe, Begründung, Nächster Schritt, Segment, Branche |
| KI-Schritt 4 | „Antwortentwurf schreiben“ (Basic LLM Chain): bekommt Firma, Nachricht, Bewertung → Entwurf ohne Anrede |
| Nicht an die KI | Name, E-Mail (seit Lab 7.2), Rolle (bis Lab 11.1 ging sie an „Lead bewerten“ und „Antwortentwurf schreiben“) |
| Regeln ohne KI | Region „Sonstige“ → Status „Prüfen“; Score ab 70, „Anzahl Räume“ leer oder mindestens 2 und Segment nicht „Kein Fit“ → „Heiß“, sonst „Später pflegen“ |
| Empfänger der Daten | n8n Cloud; KI-Anbieter (Firmendaten, Nachricht); Notion (alle Felder) |
| Freigabe | Antwortentwurf mit „Freigabe offen“; ein Mensch prüft, versendet von Hand, setzt „Gesendet“ |
| Kennzeichnung | Kontrollkästchen `KI-gestützt` |
| Speicherort Ergebnis | Notion, Datenbank `Leads`, eine Seite je Anfrage |
| Information der Person | offen: Formular enthält bisher nur den Übungshinweis |
| Speicherdauer | offen: keine Löschfrist für Leads festgelegt |
| Verantwortlich | Vertriebsinnendienst (Annahme) |

## Workflow 2: Gesprächsnotiz → CRM-Update und Follow-up-Entwurf (Lab 9.1)

| Punkt | Beschreibung |
| --- | --- |
| Zweck | Notiz nach einem Kundengespräch auswerten, Lead im CRM aktualisieren, Follow-up-Mail vorbereiten |
| Auslöser | Formular „Gesprächsnotiz“ mit den Feldern Firma und Notiz |
| Daten im Eingang | Firmenname, Rohnotiz als Freitext (Teilnehmende mit Namen und Funktion, Bedarf, Einwände, Rabattwunsch, Telefonnummer und Mailadresse der Ansprechperson) |
| Personenbezug | Namen, Funktionen, Telefonnummer, Mailadresse, Aussagen von Personen |
| Rechtsgrundlage (Annahme) | vorvertragliche Maßnahme auf Wunsch des Interessenten (Art. 6 Abs. 1 b DSGVO) |
| Suche ohne KI | „Lead in Notion finden“ sucht den Lead mit genau diesem Firmennamen |
| KI-Schritt | „Notiz auswerten“ (Information Extractor): bekommt Firma und die ganze Notiz → Bedarf, Budget, Entscheider (Name und Funktion), Zeitrahmen, Nächster Schritt, Follow-up-Entwurf; Regel: keine Telefonnummern und Mailadressen in die Felder |
| Nicht an die KI | nichts; die Notiz geht vollständig an die KI |
| Empfänger der Daten | n8n Cloud; KI-Anbieter (ganze Notiz); Notion (Ergebnisfelder) |
| Freigabe | Follow-up-Entwurf mit „Freigabe offen“, Status „Gespräch geführt“ |
| Kennzeichnung | offen: `KI-gestützt` wird nicht gesetzt |
| Speicherort Ergebnis | Notion, Datenbank `Leads`, bestehende Seite des Leads |
| Speicherdauer | offen |
| Verantwortlich | jeweilige Vertriebsperson (Annahme) |

## Workflow 3: Pipeline-Briefing am Morgen (Lab 9.2)

| Punkt | Beschreibung |
| --- | --- |
| Zweck | Überblick über offene Deals jeden Werktag um 08:00 |
| Auslöser | Zeitplan, werktags 08:00 |
| Daten im Eingang | alle Deals außer Gewonnen und Verloren: Deal, Firma, Phase, Wert, Wahrscheinlichkeit, Abschlussdatum, Letzter Kontakt, Verantwortlich |
| Personenbezug | Namen der verantwortlichen Vertriebsmitarbeitenden; Firmennamen der Kunden; keine Kontaktdaten von Kunden |
| Daten des Unternehmens | Dealwerte und Phasen (intern, Datenampel gelb) |
| KI-Schritt | „Briefing schreiben“ (Basic LLM Chain): bekommt die gebündelten Deals → Markdown-Briefing mit Lage, gestockten Deals, Abschlüssen bald, drei Aufgaben |
| Regeln ohne KI | Summen rechnet Notion, nicht die KI |
| Empfänger der Daten | n8n Cloud; KI-Anbieter (Deal-Liste); Notion (Briefing-Seite) |
| Freigabe | keine nötig, das Briefing bleibt intern |
| Kennzeichnung | offen |
| Speicherort Ergebnis | Notion, neue Seite „Briefing <Datum>“ unter „Nordwind CRM“ |
| Speicherdauer | offen: jeden Werktag eine neue Seite |
| Verantwortlich | Vertriebsleitung (Annahme) |

## Raster für eigene Workflows

```text
Workflow: <Name>
Zweck:
Auslöser:
Daten im Eingang:
Personenbezug:
Rechtsgrundlage (Annahme):
KI-Schritte (Knoten → bekommt → liefert):
Nicht an die KI:
Empfänger der Daten (Dienst, Speicherort):
Freigabe (wer, welcher Status):
Kennzeichnung:
Speicherort Ergebnis:
Speicherdauer:
Verantwortlich:
```
