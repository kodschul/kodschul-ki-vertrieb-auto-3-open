# Business Case und Pilotplan auf einer Seite – Vorlage

Fiktives Unternehmen im Beispiel, alle Angaben erfunden.

Ausgabeformat des Workflow-Architekten (Assistent 2 in [`assistenten-prompts.md`](assistenten-prompts.md)) für [Lab 12.2](../m12-strategy-business-case/l02-solution-design.md). Die Vorlage passt auf eine Seite und beantwortet die Fragen einer Geschäftsführung: Was bringt es, was kostet es, was kann schiefgehen, wie wird es getestet, wann wird entschieden?

In den Chat gehören nur Schätzwerte und Rollen, keine roten Daten (Lab 1.3). Jede Zahl, die nicht gemessen ist, steht als „Annahme“ da.

## Rechenweg für den Nutzen

```text
Nutzen pro Jahr = Zeitersparnis je Vorgang (Stunden) × Vorgänge pro Jahr × Kostensatz (€ pro Stunde)
```

| Baustein | Woher | Hinweis |
| --- | --- | --- |
| Zeitersparnis je Vorgang | Ist-Zeit aus dem Canvas minus Soll-Zeit (Prüfen und Freigeben bleibt) | in Stunden umrechnen: 15 min = 0,25 h |
| Vorgänge pro Jahr | Häufigkeit aus dem Canvas, z. B. pro Monat × 12 | Urlaub und Saison grob berücksichtigen |
| Kostensatz | Vollkosten einer Stunde Vertriebszeit (Gehalt, Nebenkosten, Arbeitsplatz) | beim Controlling erfragen; sonst als Annahme markieren |
| weiterer Nutzen | schnellere Reaktion, weniger vergessene Follow-ups, höhere Abschlussquote | beschreiben; beziffern nur als getrenntes Szenario |

Eine Zeile wird immer von Hand nachgerechnet, bevor der Business Case weitergegeben wird. Sprachmodelle verrechnen sich bei Zahlen (Lab 1.2).

## Vorlage zum Kopieren

```text
# Business Case: <Use Case>

## 1 Problem und Lösung
Problem (2 Sätze):
Lösung (1 Satz): Workflow <Auslöser> → <Schritte> → <Ergebnis im CRM>, ein Mensch gibt frei.

## 2 Nutzen pro Jahr
| Baustein | Wert | Quelle |
| Zeitersparnis je Vorgang | ... h | Ist ... min − Soll ... min (Annahme/gemessen) |
| Vorgänge pro Jahr | ... | ... pro Monat × 12 |
| Kostensatz | ... € | Controlling / Annahme |
| Nutzen | ... € | Rechnung: ... × ... × ... |
Weiterer Nutzen (nicht beziffert):

## 3 Kosten
| Posten | Jahr 1 | ab Jahr 2 |
| Lizenzen Automatisierung | | |
| KI-Nutzung | | |
| CRM (falls zusätzlich) | | |
| Einrichtung (... h × ... €) | | – |
| Pflege (... h pro Monat × 12 × ... €) | | |
| Summe | | |

## 4 Ergebnis
Nutzen minus Kosten Jahr 1:      ab Jahr 2:
Einrichtung amortisiert nach etwa ... Monaten

## 5 Risiken und Compliance
| Risiko | Gegenmaßnahme |
| Datenschutz (Rechtsgrundlage, AVV, Datenminimierung, Drittland) | |
| Werberecht (Werbe-Mail nur mit Einwilligung) | |
| automatisierte Entscheidung über Personen | |
| Fehlerfolgen beim Kunden (falsche Zusage, falscher Ton) | |
| Transparenz (AI Act Art. 50, Hinweis an Kunden) | |

## 6 Pilotplan
Umfang (ein Team, ein Prozess):
Dauer: ... Wochen (6–8), Start ..., Ende ...
Verantwortlich:
Woche 1: bauen und mit Testfällen prüfen · Woche 2–...: Betrieb mit Freigabe · letzte Woche: auswerten und entscheiden

## 7 Kennzahlen
| Kennzahl | Ausgangswert | Zielwert | Messung |

## 8 Erfolgskriterien
-

## 9 Entscheidung nach dem Pilot
Ausrollen, wenn ... · Anpassen, wenn ... · Stoppen, wenn ...
Entscheidet: ... am ...
```

## Beispiel Nordwind: Angebote werden nicht nachgefasst

Ausgangsdaten aus [`notion/deals-muster-erklaerung.md`](notion/deals-muster-erklaerung.md), Stichtag der Übungsdaten 01.12.2026. Lösung: Musterworkflow [`m12-showcase-workflow.json`](workflows/m12-showcase-workflow.json).

### 1 Problem und Lösung

Angebote in der Phase „Angebot versendet“ werden unregelmäßig nachgefasst: Von 6 offenen Angeboten sind 3 seit mehr als 30 Tagen ohne Kontakt (Rheinfels Logistik 75 Tage, Kanaalhuis Coworking 60, Inntal Versicherungsmakler 34). Nach einem Angebot gewinnt Nordwind tatsächlich nur 33,3 % statt der angenommenen 50 %; 12 von 22 verlorenen Deals gingen in dieser Phase verloren.

Lösung: Werktags um 9 Uhr holt ein Workflow alle Deals in „Angebot versendet“ ohne Kontakt seit 7 Tagen aus Notion, die KI schreibt je Deal einen Nachfass-Entwurf, der als Seite „Nachfassen: <Deal>“ mit „Freigabe offen“ in Notion liegt; die verantwortliche Person prüft und sendet.

### 2 Nutzen pro Jahr

| Baustein | Wert | Quelle |
| --- | --- | --- |
| Zeitersparnis je Vorgang | 0,25 h | heute 20 min (Deal öffnen, Angebot lesen, Mail schreiben), künftig 5 min (prüfen, senden); Annahme |
| Vorgänge pro Jahr | 60 | rund 30 Angebote pro Jahr (24 abgeschlossene Deals erreichten die Phase, 6 offen) × 2 Nachfass-Mails; Annahme |
| Kostensatz | 60 € | Annahme |
| **Nutzen** | **900 €** | 0,25 × 60 × 60 |

Weiterer Nutzen, getrennt als Szenario: Ein offenes Angebot ist im Schnitt 30.710 € wert (184.260 € ÷ 6, erstes Vertragsjahr). Bringt konsequentes Nachfassen nur einen zusätzlichen Abschluss pro Jahr, ist das ein Vielfaches der Kosten. Dieser Wert ist Umsatz, kein Gewinn, und nicht belegt; deshalb steht er nicht in der Rechnung.

### 3 Kosten

| Posten | Jahr 1 | ab Jahr 2 |
| --- | --- | --- |
| Lizenz n8n | 0 € (für den Lead-Eingang schon vorhanden; neu: Starter 20 € pro Monat bei jährlicher Zahlung, Stand 22.11.2026, prüfen) | 0 € |
| KI-Nutzung (rund 6 Entwürfe pro Werktag) | 60 € (Annahme 5 € pro Monat) | 60 € |
| CRM Notion | 0 € (vorhanden) | 0 € |
| Einrichtung 6 h × 60 € | 360 € | – |
| Pflege 1 h pro Monat × 12 × 60 € | 720 € | 720 € |
| **Summe** | **1.140 €** | **780 €** |

### 4 Ergebnis

Allein über die Zeitersparnis: Jahr 1 −240 €, ab Jahr 2 +120 €. Der Business Case trägt nur über die Abschlussquote; deshalb ist sie die wichtigste Kennzahl im Pilot.

### 5 Risiken und Compliance

| Risiko | Gegenmaßnahme |
| --- | --- |
| Datenschutz: Firmenname, Produkte, Wert und Name der verantwortlichen Person gehen an die KI | keine Kontaktdaten von Kunden im Prompt; AVV mit n8n; Speicherorte laut Lab 11.1 |
| Werberecht | Nachfassen zu einem angeforderten Angebot, keine Kaltwerbung; mit Rechtsabteilung bestätigen (keine Rechtsberatung) |
| Druck oder falsche Zusagen im Entwurf | Systemanweisung: keine künstliche Dringlichkeit, keine Rabatte, Preise oder Liefertermine (Lab 11.3) |
| täglich neue Entwürfe für denselben Deal | nach dem Senden `Letzter Kontakt` in Notion aktualisieren; im Pilot täglich prüfen |
| automatisierte Entscheidung | keine: der Workflow schreibt nur Entwürfe, ein Mensch sendet |

### 6 Pilotplan

Umfang: Phase „Angebot versendet“, alle vier Vertriebsmitarbeitenden. Dauer: 8 Wochen. Verantwortlich: Vertriebsleitung.
Woche 1: Workflow importieren, Datum im Filter relativ zu heute setzen, fünf Testfälle (Normalfall, Deal ohne Produkte, Deal mit Kontakt gestern, Notion nicht erreichbar, Anweisung im Deal-Namen). Woche 2–7: Betrieb mit Freigabe. Woche 8: Auswertung und Entscheidung.

### 7 Kennzahlen

| Kennzahl | Ausgangswert | Zielwert | Messung |
| --- | --- | --- | --- |
| Tage seit letztem Kontakt, offene Angebote (Median) | 26 Tage (12, 15, 18, 34, 60, 75) | höchstens 7 Tage | Notion-Filter, wöchentlich |
| Angebote länger als 30 Tage ohne Kontakt | 3 von 6 | 0 | Notion-Filter, wöchentlich |
| Zeit je Nachfass-Mail | 20 min (Annahme) | 5 min | Selbstauskunft im Pilot |
| tatsächliche Quote nach Angebot | 33,3 % | 40 % | nach 6 Monaten, Pilot zeigt nur den Trend |

### 8 Erfolgskriterien

- Kein offenes Angebot länger als 14 Tage ohne Kontakt.
- Mindestens 80 % der Entwürfe werden mit kleinen Änderungen gesendet.
- Kein Entwurf mit Preis, Rabatt oder Termin-Zusage; keine Beschwerde eines Kunden.

### 9 Entscheidung nach dem Pilot

Ausrollen, wenn alle drei Erfolgskriterien erfüllt sind · Anpassen, wenn Entwürfe oft umgeschrieben werden (Systemanweisung mit Assistent 3 verbessern) · Stoppen, wenn das Team die Entwürfe nicht nutzt. Entscheidet: Vertriebsleitung in Woche 8.
