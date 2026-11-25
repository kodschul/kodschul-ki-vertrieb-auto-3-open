# Lab 5.3: Leads und Kunden priorisieren

**Leitfragen:**

<details>
<summary>Wie wird heute entschieden, womit der Montag beginnt?</summary>

Oft mit dem, was zuletzt laut war: die neueste Mail, der Kunde, der angerufen hat. Eine Wochenliste mit Begründung setzt stattdessen die Deals nach oben, bei denen am meisten Umsatz am schnellsten entschieden wird.

</details>

<details>
<summary>Was ist wertvoller: ein großer kalter oder ein kleiner heißer Lead?</summary>

Kommt auf das Produkt aus Chance, Wert und Dringlichkeit an. Ein großer kalter Lead hat hohen Wert, aber kaum Chance; ein kleiner heißer Lead schließt schnell, bringt aber wenig. Die Formel macht den Vergleich sichtbar.

</details>

<details>
<summary>Welcher Kunde bekommt zu viel Aufmerksamkeit, gemessen am Umsatz?</summary>

Häufig der sympathische oder fordernde Kunde mit kleinem Auftrag. Bei Nordwind gewinnt das Segment Coworking nur jeden neunten Deal (11,1 %, Lab 5.1), hat aber acht offene Deals in der Pipeline.

</details>

- Priorität = Chance × Wert × Dringlichkeit; aus Punkten je Faktor entsteht eine nachvollziehbare Reihenfolge.
- Die KI rechnet die Liste aus `Leads` und `Deals` vor, der Mensch prüft sie und setzt in Notion „Diese Woche“.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| Priorität | Rang einer Aufgabe in der Reihenfolge der Woche; hier das Produkt aus drei Punktwerten |
| Chance | wie wahrscheinlich ein Abschluss ist, abgeleitet aus Phase bzw. Stufe |
| Dringlichkeit | wie bald eine Entscheidung fällt oder ein Deal ohne Handeln verloren geht |
| Vier-Felder-Matrix | Raster aus zwei Achsen (hier Chance und Wert) mit vier Feldern, die je eine Handlung vorgeben |
| Kontrollkästchen (Checkbox) | Notion-Eigenschaft mit Häkchen an oder aus, z. B. „Diese Woche“ |

## Prioritätsformel Chance × Wert × Dringlichkeit

Jeder Faktor bekommt 0 bis 3 Punkte; multipliziert ergibt sich 0 bis 27. Multiplizieren statt Addieren sorgt dafür, dass ein Faktor mit 0 die Priorität auf 0 setzt: Ein Lead ohne Passung wird nicht wichtig, nur weil er groß ist.

| Punkte | Chance | Wert | Dringlichkeit |
| --- | --- | --- | --- |
| 3 | Deal in Verhandlung | ab 50.000 € | Entscheidung bis 31.12.2026, Termin überschritten oder gestockt (Lab 5.1) |
| 2 | Deal in Demo oder Angebot versendet | 20.000–49.999 € | Entscheidung bis 31.03.2027 |
| 1 | Deal in Qualifiziert oder Bedarfsgespräch; Lead heiß oder warm | unter 20.000 € | später oder kein Termin |
| 0 | Lead kalt oder Segment „Kein Fit“ | – | – |

Leads haben noch keinen Wert im CRM. Geschätzt wird er über die Räume: Räume × 1.900 €, dem Durchschnitt je Raum der offenen Nordwind-Deals (915.942 € ÷ 483 Räume ≈ 1.896 €).

Die Punktgrenzen sind eine Setzung für Nordwind; die tatsächlichen Quoten aus Lab 5.2 stützen sie (Verhandlung 60 %, ab Demo etwa 30 %).

## Matrix „schnell gewinnen / pflegen / beobachten / loslassen“

```text
                  Wert niedrig (1)                Wert hoch (2–3)
               ┌────────────────────────────────┬────────────────────────────────┐
Chance hoch    │ BEOBACHTEN                     │ SCHNELL GEWINNEN               │
(2–3)          │ wenig Aufwand, nachhalten      │ diese Woche vorantreiben       │
               ├────────────────────────────────┼────────────────────────────────┤
Chance niedrig │ LOSLASSEN                      │ PFLEGEN                        │
(0–1)          │ freundlich abschließen         │ Beziehung aufbauen, Anlass     │
               └────────────────────────────────┴────────────────────────────────┘
Dringlichkeit entscheidet die Reihenfolge innerhalb eines Feldes.
```

| Feld | Beispiele aus den Nordwind-Daten |
| --- | --- |
| schnell gewinnen | Polderland Verzekeringen (Verhandlung, 91.478 €), Rheinfels Logistik (Angebot, 54.394 €, gestockt) |
| pflegen | Hafenkontor Logistik (Lead heiß, 18 Räume, Umzug April 2027), Mainhattan Flex Office (Bedarfsgespräch, 31.037 €) |
| beobachten | Sternwarte Coworking (Verhandlung, 17.901 €), Inntal Versicherungsmakler (Angebot, 16.420 €) |
| loslassen | Elster Backwaren (Kein Fit), Weserbogen Physiotherapie (Kein Fit, 1 Raum) |

## Wochenliste „Diese Woche“ in Notion

Die Top 5 bekommen in Notion ein Häkchen in der Eigenschaft „Diese Woche“; eine gefilterte Ansicht zeigt nur diese Einträge. In `Leads` gibt es die Spalte seit dem Import aus Lab 4.1 (Typ auf Kontrollkästchen stellen, falls noch Text, siehe [`notion-import-anleitung.md`](../material/notion/notion-import-anleitung.md)); in `Deals` wird sie neu angelegt.

![Notion-Filterfenster „Filters for Mary's High Priority Tasks“: Filterzeilen nach dem Muster „Where – Eigenschaft – Is – Wert“, z. B. „Where Engineers Contains Mary Cassatt“, darunter mit „And“ und „Or“ verknüpfte Filtergruppen (Type is Task oder Bug; Priority is P1) und jeweils „+ Add a filter“](https://images.ctfassets.net/spoqsaf9291f/Z8Ab1rCZgvHAPn8MWRhal/ddb5b31d145492ebe218b7e3079e19e2/nested-filters.png)
_Quelle: Notion Help Center, „Using advanced database filters“ (https://www.notion.com/help/guides/using-advanced-database-filters), © Notion Labs, abgerufen am 23.11.2026._

Für die Wochenliste genügt eine einzige Filterzeile: `Diese Woche` → **ist angehakt** (Checked).

Jede Ansicht hat eigene Filter und Sortierungen; dieselben Daten erscheinen so einmal vollständig („Pipeline“) und einmal als Wochenliste („Diese Woche“). Neue Eigenschaften entstehen über **Eigenschaften** → **Neue Eigenschaft** (Bezeichnung je nach Version):

![Notion-Bereich „Properties for Tasks“ mit Eigenschaften wie Projects, Priority, Sprint, Status, je mit Schalter für die Sichtbarkeit, unten „+ Add a property“](https://images.ctfassets.net/spoqsaf9291f/2C9kI0iZiHR4iAHoV6AIRP/030a34f9a7ae10d7ea78274319a5a18d/Database_properties_-_hero.png)
_Quelle: Notion Help Center, „Database properties“ (https://www.notion.com/help/database-properties), © Notion Labs, abgerufen am 23.11.2026._

## Übung: Wochenliste mit fünf Einträgen

**Material:** CSV von `Deals` aus Lab 5.1 oder [`nordwind-deals.csv`](../material/notion/nordwind-deals.csv), [`leads-start.csv`](../material/notion/leads-start.csv) (oder Export von `Leads`) · **Werkzeug:** KI-Assistent, Notion

**Ausgangslage:** Dienstag, 01.12.2026. Das Nordwind-Team will die fünf wichtigsten Einträge der Woche aus Deals und Leads kennen, mit Grund und nächstem Schritt, sichtbar in Notion.

1. Öffne einen neuen Chat, lade beide CSV-Dateien hoch (oder füge den Inhalt ein) und sende Prompt-Karte 5.3a.
2. Rechne einen Eintrag selbst nach, z. B. Rheinfels Logistik: Chance, Wert und Dringlichkeit aus der Punktetabelle bestimmen und multiplizieren.
3. Lege in `Deals` die Eigenschaft `Diese Woche` vom Typ **Kontrollkästchen** (Checkbox) an und setze das Häkchen bei den Top 5; steht ein Lead in den Top 5, setze es dort in `Leads`.
4. Lege in `Deals` eine neue Tabellenansicht `Diese Woche` an: **Filter** → `Diese Woche` → **ist angehakt** (Checked), **Sortieren** → `Abschlussdatum` aufsteigend.

**Prompt-Karte 5.3a – Top 5 der Woche**
```text
Stichtag der Übungsdaten ist der 01.12.2026.
Im Anhang stehen zwei CSV-Dateien unseres CRM: „Deals“ (Verkaufschancen) und „Leads“ (Interessenten ohne Angebot). Bestimme die Top 5 der Woche aus den offenen Deals (Phase nicht Gewonnen und nicht Verloren) und allen Leads.

Priorität = Chance × Wert × Dringlichkeit, je 0 bis 3 Punkte:
- Chance: 3 = Phase Verhandlung; 2 = Demo oder Angebot versendet; 1 = Qualifiziert, Bedarfsgespräch oder Lead mit Stufe heiß oder warm; 0 = Lead mit Stufe kalt oder Segment „Kein Fit“.
- Wert: 3 = ab 50.000 €; 2 = 20.000 bis 49.999 €; 1 = unter 20.000 €. Für Leads: Räume × 1.900 €; Räume leer = 1 Punkt.
- Dringlichkeit: 3 = Abschlussdatum bis 31.12.2026 oder bereits überschritten, letzter Kontakt vor dem 01.11.2026 oder ein Termin bis Jahresende in Kaufsignal oder Begründung; 2 = Abschlussdatum oder Termin bis 31.03.2027; 1 = später oder kein Termin.
Bei Gleichstand zuerst das frühere Abschlussdatum, dann der höhere Wert.

Ausgabe als Tabelle: Platz | Name | Datenbank | Chance | Wert | Dringlichkeit | Priorität | Begründung (ein Satz mit Zahlen aus den Daten) | nächster Schritt diese Woche.
Zeige für jeden Eintrag die Punkte-Rechnung. Nenne danach die Plätze 6 bis 8 in einer Zeile. Erfinde keine Daten.
```

**Checkpoint:** Die Ansicht `Diese Woche` in `Deals` zeigt fünf Einträge, nach Abschlussdatum sortiert oben Rheinfels Logistik; Platz 1 der KI-Liste ist Polderland Verzekeringen. Die eigene Nachrechnung stimmt mit der KI überein.

**Erweiterung:** Prompt nachschieben: „Ordne alle offenen Deals und Leads den vier Feldern schnell gewinnen, pflegen, beobachten, loslassen zu (Chance 2–3 = hoch, Wert 2–3 = hoch).“

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Berechnet mit den Regeln der Prompt-Karte aus [`nordwind-deals.csv`](../material/notion/nordwind-deals.csv) und [`leads-start.csv`](../material/notion/leads-start.csv); Stichtag 01.12.2026.

| Platz | Name | Datenbank | Chance | Wert | Dringl. | Priorität | Begründung | nächster Schritt |
| --- | --- | --- | --- | --- | --- | --- | --- | --- |
| 1 | Polderland Verzekeringen – 40 Räume | Deals | 3 | 3 | 3 | 27 | Verhandlung, 91.478 €, Abschluss 18.12.2026; größter Einzelposten der Pipeline, MeetSpace Pro im Wettbewerb | Termin mit dem Entscheider für die Vertragsfreigabe vereinbaren (Sander de Vries) |
| 2 | Rheinfels Logistik – 24 Räume | Deals | 2 | 3 | 3 | 18 | Angebot über 54.394 €, Abschlussdatum 30.10.2026 überschritten, seit 75 Tagen kein Kontakt, RaumPilot im Wettbewerb | anrufen, Entscheidungsstand klären, neues Abschlussdatum eintragen (Jonas Brink) |
| 3 | Weber & Kollegen Wirtschaftsprüfung – 10 Räume | Deals | 3 | 2 | 3 | 18 | Verhandlung, 28.212 €, Abschlussdatum 27.11.2026 überschritten | offene Vertragspunkte klären, Abschlussdatum aktualisieren (Jonas Brink) |
| 4 | Kranich Elektrotechnik – 14 Räume | Deals | 3 | 2 | 3 | 18 | Verhandlung, 31.713 €, Abschluss 22.12.2026, RaumPilot im Wettbewerb | Argument „Hardware, Software und Service aus einer Hand“ ins Gespräch bringen (Lena Hoffmann) |
| 5 | Aare Versicherungsdienst – 26 Räume | Deals | 3 | 3 | 2 | 18 | Verhandlung, 56.605 €, Abschluss 15.01.2027, kein Wettbewerber | Vertragsentwurf vor den Feiertagen senden (Aylin Demir) |

Plätze 6 bis 8 (je 12 Punkte): Lindgrün Energie (Angebot, 63.049 €, 29.01.2027), Brandt Maschinenbau (Demo, 52.184 €, 26.02.2027), Marquardt & Lenz Rechtsanwälte (Demo, 23.865 €, seit 50 Tagen kein Kontakt).

Bester Lead: Rheinpark Versicherungsmakler mit 1 × 2 × 2 = 4 (heiß, 12 Räume ≈ 22.800 €, neue Räume ab Februar 2027). Deals in Verhandlung liegen vorn, weil dort Chance und Wert schon belegt sind; der heiße Lead gehört trotzdem in die Woche, wenn Zeit bleibt.

Nachrechnung Rheinfels Logistik: Chance 2 (Angebot versendet) × Wert 3 (54.394 € ≥ 50.000 €) × Dringlichkeit 3 (Abschlussdatum überschritten) = 18.

**Notion:** `Deals` → Eigenschaft `Diese Woche` (Kontrollkästchen), Häkchen bei den fünf Deals oben; Ansicht `Diese Woche` mit Filter „Diese Woche ist angehakt“ zeigt in der Reihenfolge nach Abschlussdatum: Rheinfels Logistik (30.10.2026), Weber & Kollegen (27.11.2026), Polderland (18.12.2026), Kranich (22.12.2026), Aare (15.01.2027).

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Gewonnene Deals in den Top 5 | „offen“ nicht beachtet | im Prompt „Phase nicht Gewonnen und nicht Verloren“ prüfen |
| Rheinfels fehlt in der Liste | KI erkennt „überschritten“ nicht, weil sie mit heute rechnet | Stichtag 01.12.2026 nennen |
| Filter bietet „ist angehakt“ nicht an | `Diese Woche` ist noch Text | Typ auf Kontrollkästchen ändern |
| Ansicht `Pipeline` zeigt nur noch fünf Karten | Filter in der falschen Ansicht gesetzt | Filter dort entfernen, neue Ansicht anlegen |

## Fazit

- Chance × Wert × Dringlichkeit macht Prioritäten begründbar und vergleichbar.
- Die Vier-Felder-Matrix ordnet jeden Eintrag einer Handlung zu: schnell gewinnen, pflegen, beobachten, loslassen.
- Die KI rechnet die Liste vor, der Mensch prüft eine Zeile nach und setzt in Notion die Wochenliste.

> **Merksatz:** Erst die Liste begründen, dann den Montag beginnen.
