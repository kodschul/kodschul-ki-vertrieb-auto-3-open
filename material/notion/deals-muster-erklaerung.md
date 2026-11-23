# Deals-Datensatz Nordwind: Aufbau und richtige Antworten

Fiktives Unternehmen, alle Firmen, Personen und Zahlen erfunden. Ähnlichkeiten mit echten Firmen sind nicht beabsichtigt.

Diese Datei beschreibt [`nordwind-deals.csv`](nordwind-deals.csv), die Datenbank `Deals` im Übungs-CRM (Import in Lab 4.2). Die Zahlen unten sind exakt nachgerechnet und dienen als Prüfmaßstab: Was ein KI-Assistent in Lab 5.1, 5.2, 5.3 und 9.2 aus den Daten liest, wird mit diesen Werten verglichen.

**Stichtag der Übungsdaten: 01.12.2026.** Alle Aussagen wie „überfällig“ oder „seit 30 Tagen kein Kontakt“ beziehen sich auf dieses Datum, nicht auf das heutige.

## Spalten der Datei

| Spalte | Inhalt | Typ in Notion |
| --- | --- | --- |
| `Deal` | Kurzname der Firma und Anzahl Räume, z. B. „Brandt Maschinenbau – 22 Räume“ | Titel |
| `Firma` | vollständiger Firmenname | Text |
| `Segment` | Mittelstand-Büro, Kanzleien und Beratungen, Coworking und Flexible Office | Auswahl |
| `Phase` | Qualifiziert, Bedarfsgespräch, Demo, Angebot versendet, Verhandlung, Gewonnen, Verloren | Auswahl |
| `Höchste Phase` | bei offenen Deals gleich `Phase`; bei abgeschlossenen Deals die letzte offene Phase vor Gewonnen oder Verloren | Auswahl |
| `Wert` | Wert des ersten Vertragsjahres in Euro | Zahl (Euro) |
| `Wahrscheinlichkeit` | angenommene Abschlusswahrscheinlichkeit der Phase in Prozent | Zahl |
| `Abschlussdatum` | geplantes (offen) oder tatsächliches (abgeschlossen) Abschlussdatum | Datum |
| `Letzter Kontakt` | Datum des letzten Kundenkontakts | Datum |
| `Wettbewerber` | RaumPilot, MeetSpace Pro, Konferenzwerk oder „keiner“ | Auswahl |
| `Verlustgrund` | nur bei Verloren: Kategorie, Gedankenstrich, Erläuterung | Text |
| `Produkte` | angebotene oder gekaufte Produkte; fehlende Bausteine stehen nach dem Semikolon | Text |
| `Verantwortlich` | Lena Hoffmann, Jonas Brink, Aylin Demir, Sander de Vries | Auswahl |

Nach dem Import kommt die Formel `Gewichteter Wert` = `prop("Wert") * prop("Wahrscheinlichkeit") / 100` dazu (Anleitung: [`notion-import-anleitung.md`](notion-import-anleitung.md)).

### Herkunft der Werte

`Wert` folgt der [`preisliste.md`](../preisliste.md) und deckt das erste Vertragsjahr ab: Hardware + Installation (290 € pro Raum) + 12 Monate Nordwind Book (Basic 9 €, Pro 14 € pro Raum und Monat, Staffelrabatt 8 % ab 20 Räumen) + ein Jahr Nordwind Care (12 % des Hardwarewerts), falls enthalten.

Beispiel „Elbtal Steuerberatung – 5 Räume“: 4 × Vista (7.560 €) + 1 × Vista Plus (2.990 €) + Installation (1.450 €) + Book Basic (5 × 9 € × 12 = 540 €) = **12.540 €**.

### Angenommene Wahrscheinlichkeit je Phase

| Phase | Qualifiziert | Bedarfsgespräch | Demo | Angebot versendet | Verhandlung | Gewonnen | Verloren |
| --- | --- | --- | --- | --- | --- | --- | --- |
| Wahrscheinlichkeit | 10 | 20 | 40 | 50 | 70 | 100 | 0 |

## Inhalt in Zahlen

- **60 Deals:** 30 offen, 30 abgeschlossen (8 gewonnen, 22 verloren).
- **Offene Deals je Segment:** Mittelstand-Büro 14 (585.425 €), Kanzleien und Beratungen 8 (164.382 €), Coworking und Flexible Office 8 (166.135 €).
- **Abgeschlossene Deals:** Abschlussdaten zwischen 12.12.2025 und 13.11.2026; gewonnener Umsatz zusammen 244.233 €, verlorener Wert zusammen 579.025 €.

## Offene Pipeline und gewichtete Pipeline

Offene Deals sind alle Deals mit einer Phase vor Gewonnen oder Verloren.

| Phase | Deals | Summe Wert | Wahrscheinlichkeit | Summe Gewichteter Wert |
| --- | --- | --- | --- | --- |
| Qualifiziert | 5 | 123.946 € | 10 % | 12.394,60 € |
| Bedarfsgespräch | 7 | 192.345 € | 20 % | 38.469,00 € |
| Demo | 7 | 189.482 € | 40 % | 75.792,80 € |
| Angebot versendet | 6 | 184.260 € | 50 % | 92.130,00 € |
| Verhandlung | 5 | 225.909 € | 70 % | 158.136,30 € |
| **Offene Pipeline** | **30** | **915.942 €** | | **376.922,70 €** |

Prüfweg in Notion: Board-Ansicht nach `Phase`, je Spalte die Berechnung „Summe“ für `Wert` bzw. `Gewichteter Wert`; die Spalten Gewonnen und Verloren gehören nicht zur offenen Pipeline.

Größter Einzelposten: „Polderland Verzekeringen – 40 Räume“ (Verhandlung, 91.478 €, gewichtet 64.034,60 €).

## Gestockte Deals

Regel: Ein offener Deal gilt als gestockt, wenn das `Abschlussdatum` vor dem Stichtag 01.12.2026 liegt **oder** der `Letzte Kontakt` mehr als 30 Tage zurückliegt (vor dem 01.11.2026). Genau **6 Deals** erfüllen eine der Bedingungen:

| Deal | Phase | Wert | Grund | Verantwortlich |
| --- | --- | --- | --- | --- |
| Rheinfels Logistik – 24 Räume | Angebot versendet | 54.394 € | Abschlussdatum 30.10.2026 überschritten; letzter Kontakt 17.09.2026 (75 Tage) | Jonas Brink |
| Weber & Kollegen Wirtschaftsprüfung – 10 Räume | Verhandlung | 28.212 € | Abschlussdatum 27.11.2026 überschritten | Jonas Brink |
| Marquardt & Lenz Rechtsanwälte – 9 Räume | Demo | 23.865 € | letzter Kontakt 12.10.2026 (50 Tage) | Lena Hoffmann |
| Murtal Bau – 8 Räume | Demo | 17.418 € | letzter Kontakt 25.08.2026 (98 Tage) | Aylin Demir |
| Inntal Versicherungsmakler – 9 Räume | Angebot versendet | 16.420 € | Abschlussdatum 20.11.2026 überschritten; letzter Kontakt 28.10.2026 (34 Tage) | Aylin Demir |
| Kanaalhuis Coworking – 14 Räume | Angebot versendet | 14.672 € | letzter Kontakt 02.10.2026 (60 Tage) | Sander de Vries |

Zusammen 154.981 € Wert, gewichtet 79.004,60 €. Drei der sechs Deals stehen in „Angebot versendet“. Alle anderen 24 offenen Deals haben einen Kontakt ab dem 09.11.2026 und ein Abschlussdatum ab dem 15.12.2026; es gibt keine Grenzfälle.

Prüfweg in Notion: Filter `Abschlussdatum` ist vor 01.12.2026 **oder** `Letzter Kontakt` ist vor 01.11.2026, dazu `Phase` ist nicht Gewonnen und nicht Verloren.

## Abschlussquote je Segment

Basis: die 30 abgeschlossenen Deals. Abschlussquote = gewonnen ÷ abgeschlossen.

| Segment | Abgeschlossen | Gewonnen | Verloren | Abschlussquote |
| --- | --- | --- | --- | --- |
| Kanzleien und Beratungen | 8 | 4 | 4 | **50,0 %** |
| Mittelstand-Büro | 13 | 3 | 10 | 23,1 % |
| Coworking und Flexible Office | 9 | 1 | 8 | **11,1 %** |
| **Gesamt** | **30** | **8** | **22** | **26,7 %** |

Muster: Kanzleien und Beratungen gewinnen viermal so oft wie Coworking-Betreiber. Sechs der acht verlorenen Coworking-Deals scheitern am Preis (Einwand aus [`kundensegmente.md`](../kundensegmente.md): „Zu teuer pro Raum.“).

## Tatsächliche Abschlussquote je Phase

Frage: Von den abgeschlossenen Deals, die eine Phase mindestens erreicht haben (`Höchste Phase` gleich oder später), wie viele wurden gewonnen?

| Phase erreicht | Abgeschlossene Deals | Davon gewonnen | Tatsächliche Quote | Angenommene Wahrscheinlichkeit |
| --- | --- | --- | --- | --- |
| Qualifiziert | 30 | 8 | 26,7 % | 10 % |
| Bedarfsgespräch | 29 | 8 | 27,6 % | 20 % |
| Demo | 27 | 8 | 29,6 % | 40 % |
| **Angebot versendet** | **24** | **8** | **33,3 %** | **50 %** |
| Verhandlung | 10 | 6 | 60,0 % | 70 % |

Muster: Ab „Angebot versendet“ wird nur jedes dritte Angebot gewonnen, angenommen ist jedes zweite. Demo, Angebot und Verhandlung sind zu optimistisch angesetzt; deshalb ist die gewichtete Pipeline zu hoch. Von den 22 verlorenen Deals gingen 16 erst nach dem Angebot verloren (12 in „Angebot versendet“, 4 in „Verhandlung“).

Verteilung von `Höchste Phase` bei den abgeschlossenen Deals: Gewonnen 6 × Verhandlung, 2 × Angebot versendet; Verloren 1 × Qualifiziert, 2 × Bedarfsgespräch, 3 × Demo, 12 × Angebot versendet, 4 × Verhandlung.

## Prognose mit tatsächlichen Quoten

Wird jeder offene Deal mit der tatsächlichen Quote seiner Phase statt mit der angenommenen Wahrscheinlichkeit gewichtet, sinkt die gewichtete Pipeline von 376.922,70 € auf **339.221,17 €** (−10 %).

| Abschlussdatum | Deals | Summe Wert | Gewichtet (angenommen) | Gewichtet (tatsächliche Quote) |
| --- | --- | --- | --- | --- |
| überfällig (vor 01.12.2026) | 3 | 99.026 € | 55.155,40 € | 40.531,87 € |
| Dezember 2026 | 3 | 141.092 € | 98.764,40 € | 84.655,20 € |
| 1. Quartal 2027 (01.01.–31.03.2027) | 19 | 551.878 € | 210.608,30 € | 180.981,84 € |
| ab April 2027 | 5 | 123.946 € | 12.394,60 € | 33.052,27 € |
| **Summe** | **30** | **915.942 €** | **376.922,70 €** | **339.221,17 €** |

Die drei Deals im Dezember 2026 stehen alle in „Verhandlung“: Polderland Verzekeringen (91.478 €), Kranich Elektrotechnik (31.713 €), Sternwarte Coworking (17.901 €). Die überfälligen Deals sind Rheinfels Logistik, Weber & Kollegen und Inntal Versicherungsmakler (siehe gestockte Deals).

## Verlustgründe und Wettbewerber

Die Kategorie steht in `Verlustgrund` vor dem Gedankenstrich.

| Verlustgrund (Kategorie) | Anzahl |
| --- | --- |
| **Preis** | **12** |
| Projekt verschoben | 2 |
| Bestandslieferant | 2 |
| Service vor Ort | 2 |
| Kein Budget | 1 |
| Entscheider gewechselt | 1 |
| Produkt | 1 |
| Produktumfang | 1 |
| **Summe** | **22** |

| Wettbewerber bei verlorenen Deals | Anzahl |
| --- | --- |
| **RaumPilot** | **13** |
| keiner | 4 |
| MeetSpace Pro | 3 |
| Konferenzwerk | 2 |

Muster: **RaumPilot** steht bei 13 von 22 verlorenen Deals (59 %); alle 12 Preis-Verluste gingen an RaumPilot (6 Coworking, 5 Mittelstand-Büro, 1 Kanzlei). Verlorener Wert an RaumPilot: 303.112 €. Gegen RaumPilot hilft laut [`nordwind-wettbewerb.md`](../nordwind-wettbewerb.md) das Argument „Hardware, Software und Service aus einer Hand“; drei gewonnene Deals hatten RaumPilot ebenfalls als Wettbewerber (Brightdesk Coworking, Dornbusch & Kollegen, Teutoburger Möbelwerke). In den offenen Deals ist RaumPilot neunmal genannt.

## Gewonnene Kunden mit Ausbaupotenzial

Regel aus [`kundensegmente.md`](../kundensegmente.md): Ausbau von Book Basic auf Book Pro, weitere Räume oder Standorte, Nordwind Care nachkaufen. In `Produkte` steht nach dem Semikolon, was fehlt. Genau **3 der 8** gewonnenen Kunden haben Book Basic oder kein Care:

| Firma | Segment | Gekauft | Ausbauchance | Verantwortlich |
| --- | --- | --- | --- | --- |
| Steuerkanzlei Ahrens & Partner mbB | Kanzleien und Beratungen | 4 × Vista, 2 × Vista Plus, Book Basic (6 Räume), Installation; kein Panel 10, kein Care | Care, Book Pro, Panel 10 | Lena Hoffmann |
| Brightdesk Coworking B.V. | Coworking und Flexible Office | 35 × Panel 10, Book Pro (35 Räume), Installation; keine Kamera-Sets, kein Care | Care, Kamera-Sets | Sander de Vries |
| Seeblick Versicherungsmakler GmbH | Mittelstand-Büro | 14 × Panel 10, Book Basic (14 Räume), Care, Installation; keine Kamera-Sets | Book Pro, Kamera-Sets | Aylin Demir |

Die anderen fünf gewonnenen Kunden haben Panel 10, Kamera-Sets, Book Pro und Care: Dornbusch & Kollegen, Brandauer Steuerberatung, Kessler Revision, Baltica Schiffsausrüstung, Teutoburger Möbelwerke.

Prüfweg in Notion: Filter `Phase` ist Gewonnen und `Produkte` enthält „Basic“ oder „kein Care“.

## Typische Abweichungen bei der KI-Auswertung

| Beobachtung | Ursache | Prüfung |
| --- | --- | --- |
| Die KI nennt mehr oder weniger als 6 gestockte Deals | heutiges Datum statt Stichtag verwendet oder 30-Tage-Grenze anders gezählt | Stichtag 01.12.2026 im Prompt nennen, Notion-Filter aus dem Abschnitt oben |
| Pipeline-Summe enthält Gewonnen oder Verloren | „offen“ nicht definiert | im Prompt „nur Phasen vor Gewonnen und Verloren“ verlangen |
| Abschlussquote je Phase weicht ab | `Höchste Phase` ignoriert, nur `Phase` gezählt | Rechenweg anfordern, eine Zeile von Hand nachzählen |
| Summen leicht falsch | Sprachmodell rechnet im Kopf | Summe immer aus der Notion-Formel oder Spaltenberechnung nehmen |
