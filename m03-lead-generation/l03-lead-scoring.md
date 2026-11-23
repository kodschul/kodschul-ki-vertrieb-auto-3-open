# Lab 3.3: Leads mit einer Bewertungsmatrix bewerten

**Leitfragen:**

<details>
<summary>Woran wird heute entschieden, welcher Lead zuerst angerufen wird?</summary>

Oft nach Bauchgefühl, Reihenfolge des Eingangs oder bekanntem Namen. Eine Bewertungsmatrix macht daraus eine Punktzahl mit Begründung, die jede Person im Team gleich anwendet.

</details>

<details>
<summary>Ist eine große Firma automatisch ein guter Lead?</summary>

Nein. Größe ist nur ein Kriterium von mehreren; ohne Anlass kauft auch ein Konzern nichts, und ein Filialbetrieb ohne Büro braucht keine Besprechungsräume.

</details>

<details>
<summary>Würden zwei Kollegen denselben Lead gleich einschätzen?</summary>

Selten, wenn jeder nach eigenem Gefühl urteilt. Mit festen Kriterien, Punkten und Schwellen kommen beide zum selben Ergebnis oder sehen genau, an welchem Kriterium sie sich unterscheiden.

</details>

- Lead-Scoring prüft zwei Fragen: Passt die Firma (Fit)? Will sie jetzt kaufen (Interesse)? Eine Bewertungsmatrix vergibt dafür Punkte je Kriterium.
- Jeder Score kommt mit Begründung, damit ihn ein Mensch nachrechnen kann. Diese Matrix wird an Tag 2 Teil des Workflows (Lab 7.2).

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| Lead-Qualifizierung | Prüfung, ob ein Lead weiterverfolgt wird und wie dringend |
| Fit | wie gut die Firma zum Zielkundenprofil passt: Branche, Größe, Räume, Region |
| Interesse | ob es einen Anlass gibt, jetzt zu kaufen: Kaufsignal und Zeitrahmen |
| Bewertungsmatrix | Tabelle mit Kriterien, Punkten je Ausprägung und Schwellen – wie ein Bewertungsbogen bei einer Ausschreibung |
| Gewichtung | wie viel ein Kriterium höchstens zählt; hier steckt sie in der Höchstpunktzahl |
| Stufe | Einordnung nach Score: heiß, warm, kalt |

## Aufbau der Nordwind-Bewertungsmatrix

Fit ändert sich selten (eine Kanzlei bleibt eine Kanzlei), Interesse schnell (der Umzug ist in sechs Monaten vorbei); deshalb trennt die Matrix beide Gruppen. Kurzfassung von [`bewertungsmatrix-muster.md`](../material/bewertungsmatrix-muster.md), dort stehen alle Teilpunkte und Sonderregeln.

| Gruppe | Kriterium | Höchstpunkte | volle Punkte, wenn … |
| --- | --- | --- | --- |
| Fit | Branche und Segment | 20 | Firma passt klar zu einem der drei Segmente |
| Fit | Größe | 10 | 50–500 Mitarbeitende |
| Fit | Besprechungsräume | 15 | 10 und mehr Räume |
| Fit | Region | 15 | DE-Nord, DE-West oder NL |
| Interesse | Anlass | 25 | konkreter Anlass mit Bezug zu Räumen (Umzug, neue Etage, Desk-Sharing) |
| Interesse | Dringlichkeit | 15 | Termin innerhalb von 3 Monaten nach Stichtag (Musterdaten: Stichtag 01.12.2026, also bis 28.02.2027; eigene Leads: heutiges Datum) |

| Stufe | Score | Bedeutung |
| --- | --- | --- |
| heiß | 70–100 | passt und hat einen Anlass: heute anrufen |
| warm | 40–69 | passt teilweise oder Anlass fehlt: pflegen und nachfassen |
| kalt | 0–39 | passt kaum oder kein Interesse: beobachten oder aussortieren |

Sonderregeln: Räume unbekannt → Mitarbeitende ÷ 10 schätzen, höchstens 10 Punkte (nie 15) und „geschätzt“ vermerken; sonst gibt, was nicht belegt ist, 0 Punkte; Name, Sprachstil und Rechtschreibung zählen nie.

Rechenbeispiel Hafenkontor Logistik (aus Lab 3.2): Büro-Unternehmen 20 + 260 Mitarbeitende 10 + 18 Räume 15 + DE-Nord 15 = **Fit 60**; Umzug 25 + Bezug April 2027 (3–12 Monate) 8 = **Interesse 33**; **Score 93 → heiß**.

## Drei Wege zum Lead-Score

| Weg | so funktioniert es | braucht | Stärke | Schwäche |
| --- | --- | --- | --- | --- |
| Feste Regeln | Wenn-dann-Punkte je Merkmal, im CRM eingestellt | durchdachte Kriterien, gepflegte Felder | durchschaubar, für alle gleich | liest keinen Freitext, veraltet still |
| Machine Learning im CRM | Modell lernt aus gewonnenen und verlorenen Leads, welche Merkmale zählen (Lab 1.1) | viele abgeschlossene Leads, z. B. mindestens 40 qualifizierte und 40 verworfene in Dynamics 365 | findet Muster, die niemand aufgeschrieben hat | braucht Historie; Gründe nur so gut wie die Daten |
| Sprachmodell mit Matrix | Assistent liest Kaufsignal und Anfrage als Text und wendet die Matrix an | Matrix im Prompt, menschliche Prüfung | versteht Freitext, sofort startklar | kann sich verrechnen, Antworten schwanken (Lab 1.2) |

Feste Regeln sehen im CRM so aus: In HubSpot bekommt jede Ausprägung einer Eigenschaft Punkte, hier je nach Region 10, 5 oder 8 Punkte:

![HubSpot Lead Scoring, Bereich „Properties“: Bedingung „Country/Region is equal to any of Northeast, Midwest, Southeast“, darunter je Region ein Feld „Add … points“ mit 10, 5 und 8 Punkten, rechts die Option „Scoring individually“](https://knowledge.hubspot.com/hubfs/Knowledge_Base_2023-24-25/KB-Lead-scoring/property-criteria-scoring-individually.png)
_Quelle: HubSpot Knowledge Base, „Build lead scores“ (https://knowledge.hubspot.com/scoring/build-lead-scores), Screenshot © HubSpot, abgerufen am 22.11.2026._

Machine Learning im CRM liefert dagegen eine Zahl, einen Trend und eine Note, berechnet aus der eigenen Verkaufshistorie:

![Microsoft Dynamics 365 Sales, Ansicht „My Open Leads Scored“: Liste von Leads mit den nummerierten Spalten Score (z. B. 89, 64, 84), Score trend (Improving, Declining) und Grade (Grade A, Grade B)](https://learn.microsoft.com/en-us/dynamics365/sales/media/my-open-lead-score-view.png)
_Quelle: Microsoft Learn, „Prioritize leads through scores“ (https://learn.microsoft.com/en-us/dynamics365/sales/work-predictive-lead-scoring), Screenshot © Microsoft, abgerufen am 22.11.2026._

Im Kurs wird der dritte Weg genutzt: Nordwind hat zu wenige abgeschlossene Leads für Machine Learning, und Kaufsignale stehen als Freitext da. Die Begründung macht jedes Ergebnis nachprüfbar.

## Übung: Matrix erstellen und zehn Leads bewerten

**Material:** eigene `leads.csv` aus Lab 3.2 (Rückfallebene [`leads-recherche-muster.csv`](../material/leads-recherche-muster.csv)), `zielkundenprofil.md` aus Lab 3.1, [`kundensegmente.md`](../material/kundensegmente.md), Referenz und Rückfallebene [`bewertungsmatrix-muster.md`](../material/bewertungsmatrix-muster.md) · **Werkzeug:** KI-Assistent, Texteditor

**Ausgangslage:** Zehn Firmen stehen in `leads.csv`, aber nicht jede ist gleich viel wert. Der Vertrieb braucht eine Matrix, nach der jede Person im Team gleich bewertet, und eine Liste mit Score, Stufe und Begründung je Firma.

1. Öffne einen neuen Chat, lade `kundensegmente.md` und `zielkundenprofil.md` hoch (oder füge den Text ein) und sende Prompt-Karte 3.3a; beantworte die vier Fragen mit der Antworthilfe und speichere die fertige Matrix als `bewertungsmatrix.md` im Texteditor.
2. Sende im selben Chat Prompt-Karte 3.3b mit dem Inhalt von `leads.csv` (Datei hochladen oder Text einfügen).
3. Kopiere den CSV-Block in `leads.csv` (alten Inhalt ersetzen) und speichere.
4. Rechne zwei Bewertungen mit der Matrix selbst nach, z. B. den höchsten Score und einen Lead ohne bekannte Raumzahl.
5. Passe eine Gewichtung mit Prompt-Karte 3.3c an und vergleiche, welche Stufen sich ändern; übernimm die Änderung nur, wenn sie überzeugt.

**Prompt-Karte 3.3a – Interview für die Bewertungsmatrix**

```text
Du bist ein erfahrener Vertriebsberater für B2B-Lead-Qualifizierung. Du hilfst mir, eine Bewertungsmatrix für Leads von Nordwind Workspace zu erstellen. Zielkundenprofil und Kundensegmente sind angehängt.

Gehe so vor:
1. Stelle mir nacheinander genau vier Fragen (Ziel, Nutzer der Bewertung, Beispiele für gute und schlechte Leads, Grenzen), immer nur eine pro Nachricht.
2. Fasse meine Antworten in drei Sätzen zusammen und frage, ob das stimmt.
3. Erstelle dann die Matrix: höchstens sechs Kriterien in den Gruppen Fit und Interesse, je Kriterium Höchstpunkte sowie volle Punkte, Teilpunkte und 0 Punkte mit klaren Bedingungen; Summe 0–100; Stufen heiß, warm, kalt mit Schwellen; Sonderregeln; Format der Begründung.

Regeln: Nutze nur Angaben aus den Dateien und meinen Antworten. Gib die Matrix als Markdown-Tabellen aus.
```

**Antworthilfe für die vier Fragen**

| Frage | Antwort zum Kopieren |
| --- | --- |
| Ziel | Jeden Lead mit 0–100 Punkten bewerten, Stufe heiß (ab 70), warm (40–69) oder kalt (unter 40), mit nachrechenbarer Begründung. |
| Nutzer | Der Vertriebsinnendienst entscheidet damit, wen er zuerst anruft. Später bewertet ein Workflow mit derselben Matrix. |
| Beispiele | Gut: Logistikfirma mit 260 Mitarbeitenden, Umzug mit 18 neuen Räumen. Mittel: Steuerberatung mit 38 Mitarbeitenden, nur eine Stellenanzeige. Schlecht: Physiotherapie-Praxis mit einem Raum. |
| Grenzen | Sechs Kriterien: Fit (zusammen 60) = Branche und Segment 20, Größe 10, Räume 15, Region 15; Interesse (40) = Anlass 25, Dringlichkeit 15. Stichtag 01.12.2026 bei Musterdaten, sonst heutiges Datum. Räume unbekannt: Mitarbeitende ÷ 10 schätzen, höchstens 10 Punkte. Nicht belegte Angaben 0 Punkte. Name, Sprachstil und Rechtschreibung zählen nie. |

**Prompt-Karte 3.3b – Leads bewerten**

```text
Bewerte jede Zeile der folgenden Lead-Liste mit unserer Bewertungsmatrix aus diesem Chat. Stichtag für alle Zeitangaben: [Stichtag: 01.12.2026 bei Musterdaten, sonst heutiges Datum].

Gib die Liste als CSV in einem einzigen Codeblock zurück: alle bisherigen Spalten unverändert, dazu am Ende die Spalten Score,Stufe,Begründung.
- Score als Zahl 0–100, Stufe nur heiß, warm oder kalt
- Begründung im Format: "Fit <Summe>/60: <Kriterium> (<Punkte>), … Interesse <Summe>/40: <Anlass> (<Punkte>), <Zeitrahmen> (<Punkte>)."
- unbekannte Räume: Mitarbeitende ÷ 10 schätzen, höchstens 10 Punkte, mit "geschätzt" kennzeichnen; sonst zählen nur belegte Angaben
- Texte mit Komma in doppelten Anführungszeichen

[Inhalt von leads.csv]
```

**Prompt-Karte 3.3c – Gewichtung anpassen**

```text
Ändere in der Matrix: [Änderung, z. B. "Region: AT und CH bekommen 15 statt 10 Punkte"]. Bewerte alle Leads neu und zeige nur die Leads, deren Score sich ändert, als Tabelle: Firma | Score alt | Score neu | Stufe alt | Stufe neu.
```

**Checkpoint:** `bewertungsmatrix.md` enthält sechs Kriterien mit zusammen 100 Punkten und drei Stufen; `leads.csv` hat drei neue Spalten Score, Stufe und Begründung; zwei Scores sind von Hand nachgerechnet.

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Beispiel mit [`leads-recherche-muster.csv`](../material/leads-recherche-muster.csv) und der Mustermatrix; KI-Antworten fallen jedes Mal etwas anders aus.

**1. `bewertungsmatrix.md`:** sechs Kriterien und Stufen wie in [`bewertungsmatrix-muster.md`](../material/bewertungsmatrix-muster.md).

**2.–3. Bewertete Lead-Liste**

| Firma | Fit | Interesse | Score | Stufe | Hinweis |
| --- | --- | --- | --- | --- | --- |
| Brenner & Voss Rechtsanwälte PartG mbB | 55 | 40 | 95 | heiß | 9 Räume, Bezug Februar 2027 |
| Hafenkontor Logistik GmbH | 60 | 33 | 93 | heiß | Rechenbeispiel oben |
| Vogelsang Medizintechnik GmbH | 50 | 25 | 75 | heiß | Räume geschätzt 34, daher höchstens 10 Punkte |
| Grachtenwerk Coworking B.V. | 51 | 15 | 66 | warm | 8 Räume, Wachstum ohne Termin |
| Limmat Treuhand AG | 50 | 15 | 65 | warm | 8 Räume, Übernahme als Wachstumssignal |
| Lechfeld Stahlhandel GmbH | 44 | 15 | 59 | warm | nur 3 Räume |
| Isarblick Steuerberatung GmbH | 40 | 15 | 55 | warm | Räume geschätzt 4 |
| Donautal Kommunikation GmbH | 36 | 0 | 36 | kalt | kein Anlass |
| Weserbogen Physiotherapie | 25 | 0 | 25 | kalt | 1 Raum, 14 Mitarbeitende |
| Elster Backwaren GmbH | 20 | 0 | 20 | kalt | Filialbetrieb: Segment Kein Fit |

```text
Firma,Website,Branche,Mitarbeitende,Räume,Region,Kaufsignal,Quelle-URL,Score,Stufe,Begründung
Hafenkontor Logistik GmbH,https://www.hafenkontor-logistik.example,Logistik,260,18,DE-Nord,"Umzug der Zentrale in die HafenCity im April 2027, 18 Besprechungsräume geplant",https://www.hafenkontor-logistik.example/presse/umzug-hafencity-2027,93,heiß,"Fit 60/60: Büro-Unternehmen (20), 260 MA (10), 18 Räume (15), DE-Nord (15). Interesse 33/40: Umzug mit 18 neuen Räumen (25), Bezug April 2027 in 4–5 Monaten (8)."
```

**4. Nachgerechnet**

- Hafenkontor: 20 + 10 + 15 + 15 + 25 + 8 = 93 ✓
- Vogelsang (Räume leer): Büro-Unternehmen 20 + 340 Mitarbeitende 10 + geschätzt 34 Räume, als Schätzung höchstens 10 + DE-Süd 10 + Desk-Sharing 25 + kein Termin 0 = 75 ✓

**5. Gewichtung angepasst:** „Region: AT und CH bekommen 15 statt 10 Punkte“

| Firma | Score alt | Score neu | Stufe alt | Stufe neu |
| --- | --- | --- | --- | --- |
| Limmat Treuhand AG | 65 | 70 | warm | heiß |
| Donautal Kommunikation GmbH | 36 | 41 | kalt | warm |

Entscheidung: nicht übernommen. Nordwind hat Büros in Hamburg, Köln und Utrecht, Termine in AT und CH sind aufwendiger; die Mustermatrix bleibt.

Warum gut: Jede Zahl lässt sich aus der Begründung nachrechnen, und das Nachrechnen zeigt, welches Kriterium den Ausschlag gibt.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Summe der Teilpunkte ergibt nicht den Score | Sprachmodell rechnet im Kopf | „Rechne die Summe Schritt für Schritt“ nachschieben; Notion-Formeln rechnen ab Lab 4.2 zuverlässig |
| Dringlichkeit falsch, z. B. „April 2027“ als dringend | Stichtag fehlt oder passt nicht zu den Daten | Platzhalter in Prompt-Karte 3.3b füllen: 01.12.2026 bei Musterdaten, heutiges Datum bei eigenen Leads |
| CSV hat nach der Bewertung andere Spaltennamen | KI übersetzt oder kürzt Spalten | „alle bisherigen Spalten unverändert“ wiederholen |

## Fazit

- Lead-Scoring trennt Fit (passt die Firma?) und Interesse (will sie jetzt?).
- Regeln, Machine Learning und Sprachmodell sind drei Wege; im Kurs bewertet das Sprachmodell nach einer festen Matrix.
- Ohne Begründung ist ein Score nicht prüfbar; geschätzte Angaben werden markiert.

> **Merksatz:** Ein Score ohne Begründung ist eine Meinung, ein Score mit Begründung ist eine Entscheidungsgrundlage.
