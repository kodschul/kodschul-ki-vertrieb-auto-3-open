# Lab 5.2: Umsatzprognose und Abschlusswahrscheinlichkeit

**Leitfragen:**

<details>
<summary>Wie entsteht heute die Umsatzprognose im eigenen Team?</summary>

Meist durch Nachfragen: Jede Person meldet, was sie im Quartal sicher abschließt, die Leitung summiert. Das ist schnell, hängt aber an Optimismus und Erfahrung der Einzelnen.

</details>

<details>
<summary>Ist ein Deal in der Phase „Angebot“ bei jedem Kunden gleich wahrscheinlich?</summary>

Nein. In den Nordwind-Daten gewinnen Kanzleien jeden zweiten Deal, Coworking-Betreiber jeden neunten (Lab 5.1). Eine feste Prozentzahl je Phase ignoriert Segment, Wettbewerber und Kontakthäufigkeit.

</details>

<details>
<summary>Welcher Zahl würde die Geschäftsführung mehr trauen: Bauchgefühl oder Durchschnitt der letzten zwei Jahre?</summary>

Dem Durchschnitt, weil er nachrechenbar ist, solange genug abgeschlossene Deals dahinterstehen. Am stärksten ist die Kombination: Zahlen aus der Vergangenheit plus Einschätzung der Person, die den Kunden kennt.

</details>

- Eine Umsatzprognose entsteht auf drei Wegen: Einschätzung der Vertriebler, gewichtete Pipeline, Abschlusswahrscheinlichkeit aus historischen Daten.
- Die Notion-Formel rechnet die Summen exakt; der KI-Assistent vergleicht, erklärt und schreibt den Kommentar.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| Umsatzprognose (Forecast) | Schätzung, wie viel Umsatz in einem Zeitraum abgeschlossen wird, z. B. im nächsten Quartal |
| Commit | Betrag, den eine Vertriebsperson für den Zeitraum fest zusagt; daneben oft „Best Case“ für das, was zusätzlich möglich ist |
| angenommene Wahrscheinlichkeit | feste Prozentzahl je Phase im CRM, z. B. „Angebot versendet = 50 %“; meist einmal festgelegt und selten überprüft |
| tatsächliche Abschlussquote je Phase | Anteil gewonnener Deals unter allen abgeschlossenen Deals, die diese Phase erreicht haben – gemessen statt angenommen |
| Höchste Phase | Spalte in `Deals`: letzte offene Phase, die ein abgeschlossener Deal vor Gewonnen oder Verloren erreicht hat |
| Szenario | eine von mehreren Rechnungen mit unterschiedlichen Annahmen: bester, wahrscheinlicher, schlechtester Fall |

## Drei Wege zur Umsatzprognose

| Weg | So wird gerechnet | Stärke | Schwäche |
| --- | --- | --- | --- |
| **Einschätzung (Commit)** | jede Person meldet ihre sicheren Abschlüsse, die Leitung summiert | nutzt Wissen über den Kunden, das in keinem Feld steht | Optimismus, Vorsicht und Tagesform verzerren |
| **Gewichtete Pipeline** | Wert × Wahrscheinlichkeit der Phase, summiert (Formel „Gewichteter Wert“ aus [Lab 4.2](../m04-notion-crm/l02-pipeline.md)) | einfach, für jeden Deal gleich, sofort in Notion | Wahrscheinlichkeiten sind Annahmen; stimmen sie nicht, stimmt die Summe nicht |
| **Historische Daten bzw. Machine Learning** | Quote aus gewonnenen und verlorenen Deals; im CRM lernt ein Modell zusätzlich aus Segment, Aktivitäten, Wettbewerber | gemessen statt geschätzt, je Deal unterschiedlich | braucht viele abgeschlossene Deals mit gepflegten Feldern |

```text
Commit (Bauchgefühl) ──┐
Gewichtete Pipeline ───┼──▶ Szenarien (bester / wahrscheinlicher / schlechtester Fall) ──▶ Kommentar
Historische Quoten ────┘         Formel rechnet                                         KI erklärt
```

## Prognose mit Machine Learning in CRM-Systemen

Große CRM-Systeme bieten Prognosen, die aus den eigenen gewonnenen und verlorenen Deals lernen (Stand: 22.11.2026, Funktionsumfang je Tarif, prüfen):

| CRM | Funktion | Was sie nutzt | Voraussetzung |
| --- | --- | --- | --- |
| Microsoft Dynamics 365 Sales | Predictive forecasting, Spalte „Prediction“ im Forecast | historische Daten und offene Pipeline, KI-Modell | Premium-Forecasting-Lizenz; bei zu wenig Daten bleibt die Spalte leer |
| HubSpot Sales Hub | KI-Prognose mit Breeze | gewonnene Deals der letzten drei Monate; Ergebnis als Spanne mit „Most likely“ | Sales Hub bzw. Service Hub Professional oder Enterprise |
| Salesforce Sales Cloud | Einstein Forecasting (seit 2017) | historische CRM-Daten, Saisonalität, frühere Leistung | eigene Lizenz bzw. höhere Edition |

_Quellen: Microsoft Learn, „Analyze revenue outcome by using predictive forecasting“ (https://learn.microsoft.com/en-us/dynamics365/sales/analyze-revenue-outcome-using-predictive-forecasting, Stand 06.05.2026); HubSpot Knowledge Base, „Improve forecasting with AI projections“ (https://knowledge.hubspot.com/forecast/improve-forecasting-with-ai-projections, Stand 29.05.2026); Salesforce, Pressemitteilung „Salesforce Introduces Sales Cloud Einstein Forecasting“, 19.09.2017 (https://www.salesforce.com/news/press-releases/2017/09/19/salesforce-introduces-sales-cloud-einstein-forecasting-celebrates-one-year-of-salesforce-einstein/); alle abgerufen am 23.11.2026._

In Dynamics 365 stehen die drei Wege nebeneinander: Commit („Committed“, „Best case“), Pipeline und die KI-Prognose („Prediction“):

![Dynamics 365 Sales, Forecast-Tabelle mit den Spalten Quota, Forecast, Won, Committed, Best case, Pipeline, Prediction (rot umrandet), Lost; für Kenny Smith Prediction 499.013,25 $](https://learn.microsoft.com/en-us/dynamics365/sales/media/predictive-forecasting-prediction-column.png)
_Quelle: Microsoft Learn, „Analyze revenue outcome by using predictive forecasting“ (https://learn.microsoft.com/en-us/dynamics365/sales/analyze-revenue-outcome-using-predictive-forecasting), © Microsoft, abgerufen am 23.11.2026._

Die Prognose zerlegt sich in bereits Gewonnenes und den erwarteten Anteil der offenen Deals, mit den wichtigsten Einflussfaktoren:

![Dynamics 365 Sales, Bereich „Prediction details“: Balken Closed won 377,50 K $, Predicted from open 121,51 K $, Predicted from new 0 $, Total prediction 499,01 K $; darunter „Top factors that influence prediction“](https://learn.microsoft.com/en-us/dynamics365/sales/media/predictive-forecasting-prediction-details.png)
_Quelle: Microsoft Learn, „Analyze revenue outcome by using predictive forecasting“ (https://learn.microsoft.com/en-us/dynamics365/sales/analyze-revenue-outcome-using-predictive-forecasting), © Microsoft, abgerufen am 23.11.2026._

Im Kurs wird das Prinzip von Hand nachgebaut: tatsächliche Quote je Phase aus 30 abgeschlossenen Deals (für ein echtes Modell zu wenige).

## Szenarien für das nächste Quartal

| Szenario | Regel im Kurs | Aussage |
| --- | --- | --- |
| bester Fall | offene Deals des Quartals × angenommene Wahrscheinlichkeit | „wenn die CRM-Annahmen stimmen“ |
| wahrscheinlicher Fall | offene Deals des Quartals × tatsächliche Quote ihrer Phase | „wenn es so läuft wie bisher“ |
| schlechtester Fall | nur Deals ab „Angebot versendet“ × tatsächliche Quote; frühere Phasen zählen 0 € | „wenn nur reife Deals im Quartal schließen“ |

Die Spanne zwischen schlechtestem und bestem Fall ist ehrlicher als eine einzelne Zahl; die Gegenprobe mit der Board-Summe aus Lab 4.2 zeigt, ob die Rechnung stimmt.

## Übung: Quartalsprognose mit Prüfrechnung

**Material:** CSV-Export von `Deals` aus Lab 5.1 oder [`nordwind-deals.csv`](../material/notion/nordwind-deals.csv), Board-Ansicht `Pipeline` aus Lab 4.2 · **Werkzeug:** KI-Assistent, Notion

**Ausgangslage:** Die Vertriebsleitung braucht für das 1. Quartal 2027 eine Prognose mit Spanne und einen kurzen Kommentar. Die Wahrscheinlichkeiten im CRM wurden nie überprüft.

1. Sende im Chat aus Lab 5.1 (oder in einem neuen Chat mit CSV und Prompt-Karte 5.1a) die Prompt-Karte 5.2a und vergleiche die tatsächlichen Quoten mit den angenommenen Wahrscheinlichkeiten.
2. Sende Prompt-Karte 5.2b für die gewichtete Pipeline mit beiden Quoten, aufgeteilt nach Abschlusszeitraum.
3. Prüfe die gewichtete Summe mit angenommenen Wahrscheinlichkeiten gegen Notion: In der Board-Ansicht `Pipeline` die Summen von `Gewichteter Wert` der fünf offenen Spalten addieren; Sollwert 376.922,70 €.
4. Sende Prompt-Karte 5.2c für die drei Szenarien des 1. Quartals 2027.
5. Sende Prompt-Karte 5.2d, prüfe jede Zahl im Kommentar gegen die Tabellen und lege den Kommentar als Notion-Seite „Prognose Q1 2027“ unter „Nordwind CRM“ ab.

**Prompt-Karte 5.2a – Tatsächliche Abschlussquote je Phase**
```text
Stichtag der Übungsdaten ist der 01.12.2026.

Berechne aus den 30 abgeschlossenen Deals (Phase Gewonnen oder Verloren) die tatsächliche Abschlussquote je Phase. Nutze die Spalte „Höchste Phase“: Sie nennt die letzte offene Phase, die ein abgeschlossener Deal erreicht hat. Ein Deal hat eine Phase erreicht, wenn seine Höchste Phase gleich oder später ist. Reihenfolge: Qualifiziert, Bedarfsgespräch, Demo, Angebot versendet, Verhandlung.

Tabelle: Phase erreicht | abgeschlossene Deals | davon gewonnen | tatsächliche Quote | angenommene Wahrscheinlichkeit (Qualifiziert 10, Bedarfsgespräch 20, Demo 40, Angebot versendet 50, Verhandlung 70).
Zeige den Rechenweg je Zeile und nenne die Phase mit der größten Abweichung.
```

**Prompt-Karte 5.2b – Gewichtete Pipeline mit beiden Quoten**
```text
Stichtag der Übungsdaten ist der 01.12.2026.

Berechne für die 30 offenen Deals die gewichtete Pipeline zweimal:
A) Wert × Wahrscheinlichkeit aus der Spalte „Wahrscheinlichkeit“ ÷ 100,
B) Wert × tatsächliche Quote der Phase aus deiner letzten Tabelle.

Tabelle nach Abschlussdatum mit den Zeilen: überfällig (vor 01.12.2026), Dezember 2026, 1. Quartal 2027 (01.01.–31.03.2027), ab April 2027, Summe. Spalten: Deals | Summe Wert | gewichtet A | gewichtet B.
Runde auf zwei Nachkommastellen und zeige die Rechnung je Phase. Nenne die Deals im Dezember 2026 einzeln.
```

**Prompt-Karte 5.2c – Drei Szenarien für das 1. Quartal 2027**
```text
Erstelle die Umsatzprognose für das 1. Quartal 2027 (offene Deals mit Abschlussdatum 01.01.–31.03.2027) in drei Szenarien:
- bester Fall: gewichtet mit den angenommenen Wahrscheinlichkeiten,
- wahrscheinlicher Fall: gewichtet mit den tatsächlichen Quoten je Phase,
- schlechtester Fall: nur Deals ab „Angebot versendet“, gewichtet mit den tatsächlichen Quoten; frühere Phasen zählen 0 €.
Tabelle: Szenario | Regel | Betrag. Zeige die Rechnung je Phase und nenne, wie viele Deals je Phase im Quartal liegen.
```

**Prompt-Karte 5.2d – Prognosekommentar für die Vertriebsleitung**
```text
Schreibe einen Prognosekommentar für die Vertriebsleitung in genau fünf Sätzen:
1. Prognose für das 1. Quartal 2027 als Spanne der drei Szenarien, wahrscheinlicher Fall zuerst.
2. Warum die gewichtete Pipeline im CRM zu hoch ist, mit beiden Summen.
3. Welche Phase am stärksten überschätzt wird.
4. Welche Deals im Dezember 2026 entscheiden und wie viel überfällig ist.
5. Eine Empfehlung.
Nutze nur Zahlen aus diesem Chat, runde auf volle Tausend Euro, erfinde nichts. Klare Sprache ohne Fachjargon.
```

**Checkpoint:** Der Chat zeigt 339.221,17 € (tatsächliche Quoten) gegenüber 376.922,70 € (angenommen); die Notion-Board-Summe bestätigt 376.922,70 €; die Seite „Prognose Q1 2027“ enthält Szenarien und Kommentar.

**Erweiterung:** Prompt-Karte 5.2a getrennt nach Segment senden und prüfen, ob „Angebot versendet“ bei Kanzleien anders ausfällt als bei Coworking.

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Exakte Werte aus [`deals-muster-erklaerung.md`](../material/notion/deals-muster-erklaerung.md).

**5.2a – Tatsächlich gegenüber angenommen**

| Phase erreicht | abgeschlossen | gewonnen | tatsächliche Quote | angenommen |
| --- | --- | --- | --- | --- |
| Qualifiziert | 30 | 8 | 8 ÷ 30 = 26,7 % | 10 % |
| Bedarfsgespräch | 29 | 8 | 8 ÷ 29 = 27,6 % | 20 % |
| Demo | 27 | 8 | 8 ÷ 27 = 29,6 % | 40 % |
| **Angebot versendet** | **24** | **8** | **8 ÷ 24 = 33,3 %** | **50 %** |
| Verhandlung | 10 | 6 | 6 ÷ 10 = 60,0 % | 70 % |

Größte Abweichung: „Angebot versendet“ – angenommen ist jedes zweite Angebot, gewonnen wird jedes dritte. 16 der 22 Verluste kamen erst nach dem Angebot (12 in „Angebot versendet“, 4 in „Verhandlung“). Qualifiziert und Bedarfsgespräch sind dagegen zu vorsichtig angesetzt.

**5.2b – Prognosebasis nach Abschlusszeitraum**

| Abschlussdatum | Deals | Summe Wert | gewichtet A (angenommen) | gewichtet B (tatsächlich) |
| --- | --- | --- | --- | --- |
| überfällig (vor 01.12.2026) | 3 | 99.026 € | 55.155,40 € | 40.531,87 € |
| Dezember 2026 | 3 | 141.092 € | 98.764,40 € | 84.655,20 € |
| 1. Quartal 2027 | 19 | 551.878 € | 210.608,30 € | 180.981,84 € |
| ab April 2027 | 5 | 123.946 € | 12.394,60 € | 33.052,27 € |
| **Summe** | **30** | **915.942 €** | **376.922,70 €** | **339.221,17 €** |

Mit tatsächlichen Quoten sinkt die gewichtete Pipeline um 10 %. Dezember 2026: Polderland Verzekeringen (91.478 €), Kranich Elektrotechnik (31.713 €), Sternwarte Coworking (17.901 €), alle in „Verhandlung“. Überfällig: Rheinfels Logistik, Weber & Kollegen, Inntal Versicherungsmakler.

**Prüfrechnung Notion:** Board `Pipeline`, Summen `Gewichteter Wert`: 12.394,60 € + 38.469,00 € + 75.792,80 € + 92.130,00 € + 158.136,30 € = 376.922,70 €.

**5.2c – 1. Quartal 2027 (19 Deals: 7 Bedarfsgespräch, 7 Demo, 4 Angebot versendet, 1 Verhandlung)**

| Szenario | Regel | Betrag |
| --- | --- | --- |
| bester Fall | angenommene Wahrscheinlichkeiten | 210.608,30 € |
| wahrscheinlicher Fall | tatsächliche Quoten je Phase | 180.981,84 € |
| schlechtester Fall | nur Angebot versendet (113.446 € × 33,3 % = 37.815,33 €) und Verhandlung (Aare Versicherungsdienst, 56.605 € × 60 % = 33.963,00 €) | 71.778,33 € |

**5.2d – Prognosekommentar**
> Für das 1. Quartal 2027 rechnen wir mit rund 181.000 € Umsatz, in einer Spanne von 72.000 € bis 211.000 €. Die gewichtete Pipeline im CRM zeigt 377.000 €, mit den tatsächlichen Abschlussquoten der abgeschlossenen Deals sind es nur 339.000 €. Am stärksten überschätzt ist die Phase „Angebot versendet“: angenommen ist jedes zweite Angebot, gewonnen wird nur jedes dritte. Im Dezember entscheiden drei Deals in Verhandlung mit zusammen 141.000 €, vor allem Polderland Verzekeringen mit 91.000 €, und drei Deals mit 99.000 € sind bereits überfällig. Wir empfehlen, die Wahrscheinlichkeiten im CRM an die tatsächlichen Quoten anzupassen und die überfälligen Deals noch diese Woche nachzufassen.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Quote „Angebot versendet“ = 2 ÷ 14 o. Ä. | KI zählt nur Deals, deren Höchste Phase genau diese Phase ist | im Prompt „gleich oder später“ betonen, Rechenweg je Zeile anfordern |
| Summe A weicht von 376.922,70 € ab | Gewonnen oder Verloren mitgerechnet, oder Kopfrechenfehler | „nur offene Deals“ verlangen; Notion-Summe gilt |
| Board zeigt Anzahl statt Summe | Berechnung je Spalte nicht umgestellt | graue Zahl am Spaltenkopf → `Gewichteter Wert` → Summe (Lab 4.2) |
| Kommentar nennt Zahlen, die in keiner Tabelle stehen | KI ergänzt plausible Werte | „nur Zahlen aus diesem Chat“ im Prompt, jede Zahl abhaken |

## Fazit

- Drei Wege, eine Spanne: Commit, gewichtete Pipeline und historische Quoten ergänzen sich.
- Angenommene Wahrscheinlichkeiten gehören regelmäßig gegen die tatsächlichen Quoten geprüft; bei Nordwind ist die Pipeline um 10 % zu hoch.
- Notion rechnet die Summe, die KI vergleicht und formuliert den Kommentar.

> **Merksatz:** Die Formel rechnet, die KI erklärt.
