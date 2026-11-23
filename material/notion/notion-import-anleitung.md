# Übungs-CRM „Nordwind CRM“ in Notion einrichten

Fiktives Unternehmen, alle Angaben erfunden. Die Dateien enthalten keine echten Firmen- oder Personendaten.

**Stand: 22.11.2026, Bezeichnung je nach Version.** Menüs heißen hier wie in der deutschen Notion-Oberfläche, die englische Bezeichnung steht in Klammern. Notion ändert Menüs regelmäßig; wenn ein Eintrag anders heißt, hilft die Suche im Menü oder die Notion-Hilfe (Quellen am Ende).

Das Übungs-CRM besteht aus einer Seite mit zwei Datenbanken:

```text
Nordwind CRM (Seite)
├── Leads   ← leads-start.csv     (Lab 4.1)  Interessenten, die noch kein Angebot haben
└── Deals   ← nordwind-deals.csv  (Lab 4.2)  laufende und abgeschlossene Verkaufschancen
```

Begriffe: Eine **Datenbank** ist in Notion eine Tabelle, in der jede Zeile eine eigene Seite ist. Eine **Eigenschaft** (Property) ist eine Spalte mit festem Typ, zum Beispiel Zahl oder Datum. Eine **Ansicht** (View) zeigt dieselben Daten anders, etwa als Tabelle oder als Board.

## Seite „Nordwind CRM“ anlegen

1. Öffne Notion im Browser mit dem kostenlosen Übungskonto (kein Firmenkonto) und wähle den eigenen Arbeitsbereich.
2. Lege in der Seitenleiste eine neue Seite an: Mauszeiger auf „Privat“ (Private) oder den Arbeitsbereich → **+** → leere Seite.
3. Gib der Seite den Titel `Nordwind CRM`.

## Datenbank Leads aus leads-start.csv importieren

Datei: [`leads-start.csv`](leads-start.csv) (11 Leads, 30 Spalten; Spalten für spätere Labs sind noch leer).

1. Lade die Datei herunter (auf GitHub: Datei öffnen → **Download raw file**).
2. Klicke in der Seite „Nordwind CRM“ in eine leere Zeile, tippe `/csv` und wähle **CSV** unter „Importieren“ (Import). Alternativ: Seitenleiste → **Einstellungen** (Settings) → **Importieren** (Import) → **CSV**.
3. Wähle die Datei aus und bestätige, dass eine **neue Datenbank** entsteht.
4. Benenne die neue Datenbank in `Leads` um (auf den Titel `leads-start` klicken und überschreiben).
5. Prüfe: 11 Zeilen, erste Spalte `Firma` ist der Titel.

Landet der Import in „Privat“ statt in der Seite, die Datenbank in der Seitenleiste per Ziehen auf „Nordwind CRM“ verschieben.

### Eigenschaftstypen setzen

Nach dem Import sind die meisten Spalten Text. Den Typ einer Spalte ändern: auf den Spaltenkopf klicken → **Eigenschaft bearbeiten** (Edit property) → **Typ** (Type) → neuen Typ wählen. Für Lab 4.1 genügen die fett markierten Zeilen; die übrigen können auch später gesetzt werden.

| Eigenschaft | Typ | Hinweis |
| --- | --- | --- |
| `Firma` | Titel (Title) | automatisch |
| `Website` | URL | |
| `Branche` | Auswählen (Select) | |
| `Segment` | Auswählen (Select) | Optionen: Mittelstand-Büro, Kanzleien und Beratungen, Coworking und Flexible Office, Kein Fit |
| `Mitarbeitende` | Zahl (Number) | |
| `Räume` | Zahl (Number) | bei zwei Leads leer (unbekannt) |
| `Region` | Auswählen (Select) | Optionen siehe unten |
| `Kaufsignal` | Text | |
| `Quelle` | Auswählen (Select) | |
| `Ansprechperson`, `Rolle` | Text | |
| `E-Mail` | E-Mail | |
| `Nachricht` | Text | ab Lab 6.2 |
| **`Score`** | **Zahl (Number)** | 0–100 |
| **`Stufe`** | **Auswählen (Select)** | heiß, warm, kalt |
| `Begründung` | Text | |
| **`Status`** | **Auswählen (Select)** | Optionen siehe unten |
| `Nächster Schritt`, `Bedarf`, `Budget`, `Entscheider`, `Zeitrahmen` | Text | ab Lab 4.3 |
| `Zusammenfassung`, `Firmenprofil`, `Antwortentwurf`, `Follow-up-Entwurf` | Text | ab Tag 2 |
| `Freigabe` | Auswählen (Select) | Optionen siehe unten |
| `Diese Woche`, `KI-gestützt` | Kontrollkästchen (Checkbox) | |
| `Einwilligung Werbung` | Kontrollkästchen (Checkbox) | gefüllt ab Lab 10.1; im Übungs-CRM ohne dokumentiertes Opt-in leer |

Beim Wechsel von Text zu „Auswählen“ legt Notion aus den vorhandenen Werten automatisch Optionen an. Optionen, die in der Datei noch nicht vorkommen, fehlen dann. Ergänze die fehlenden Optionen in **Eigenschaft bearbeiten** (Edit property) unter den Optionen, Schreibweise exakt wie in der Tabelle, denn die Workflows ab Tag 2 schreiben genau diese Werte:

| Eigenschaft | Alle Optionen | Nach dem Import fehlen |
| --- | --- | --- |
| `Region` | DE-Nord, DE-West, DE-Süd, DE-Ost, AT, CH, NL, Sonstige | Sonstige |
| `Quelle` | Recherche, Website, Messe, Empfehlung | Website, Messe |
| `Status` | Neu, Prüfen, Heiß, Später pflegen, Gespräch geführt, Kein Fit | alle außer Neu |
| `Freigabe` | Freigabe offen, Freigegeben, Gesendet | alle |

### Ansicht nach Score sortieren

Klicke oben in der Datenbank auf **Sortieren** (Sort) → `Score` → **Absteigend** (Descending). Ganz oben stehen jetzt Rheinpark Versicherungsmakler (100), Brenner & Voss (95) und Hafenkontor Logistik (93).

## Datenbank Deals aus nordwind-deals.csv importieren

Datei: [`nordwind-deals.csv`](nordwind-deals.csv) (60 Deals, 13 Spalten). Aufbau und Muster: [`deals-muster-erklaerung.md`](deals-muster-erklaerung.md).

1. Importiere die Datei wie oben mit `/csv` in die Seite „Nordwind CRM“ als neue Datenbank.
2. Benenne die Datenbank in `Deals` um und prüfe: 60 Zeilen, erste Spalte `Deal` ist der Titel.
3. Setze die Typen nach der Tabelle.

| Eigenschaft | Typ | Hinweis |
| --- | --- | --- |
| `Deal` | Titel (Title) | automatisch |
| `Firma` | Text | |
| `Segment` | Auswählen (Select) | 3 Optionen |
| `Phase` | Auswählen (Select) | 7 Optionen, Reihenfolge siehe Board |
| `Höchste Phase` | Auswählen (Select) | |
| `Wert` | Zahl (Number) | Zahlenformat (Number format) **Euro** |
| `Wahrscheinlichkeit` | Zahl (Number) | 0–100, ohne Prozentformat lassen |
| `Abschlussdatum` | Datum (Date) | Werte wie `2026-12-15` |
| `Letzter Kontakt` | Datum (Date) | |
| `Wettbewerber` | Auswählen (Select) | |
| `Verlustgrund` | Text | nur bei Verloren gefüllt |
| `Produkte` | Text | nicht als Auswahl: Werte enthalten Kommas |
| `Verantwortlich` | Auswählen (Select) | 4 Personen, fiktiv |

`Wahrscheinlichkeit` bleibt eine einfache Zahl (z. B. 50). Mit dem Prozentformat würde Notion 50 als 5.000 % anzeigen, und die Formel unten müsste anders lauten.

### Formel „Gewichteter Wert“ ergänzen

Der gewichtete Wert ist der Teil des Deal-Werts, der nach der Phasen-Wahrscheinlichkeit zu erwarten ist: 54.394 € in „Angebot versendet“ (50 %) ergeben 27.197 €.

1. Klicke oben in der Datenbank auf das Schieberegler-Symbol → **Eigenschaften bearbeiten** (Edit properties) → **Neue Eigenschaft** (New property).
2. Wähle **Formel** (Formula) und gib den Namen `Gewichteter Wert` ein.
3. Wähle **Formel bearbeiten** (Edit formula) und trage ein:

```text
prop("Wert") * prop("Wahrscheinlichkeit") / 100
```

4. Bestätige mit **Fertig** (Done) und stelle das Zahlenformat auf **Euro**.

Prüfwert: Die Zeile „Rheinfels Logistik – 24 Räume“ zeigt 27.197 €.

### Board-Ansicht nach Phase

1. Klicke auf **+** neben dem Namen der aktuellen Ansicht und wähle **Board**.
2. Gruppiere nach `Phase`: Einstellungsmenü oben rechts in der Datenbank → **Gruppieren** (Group) → `Phase`.
3. Ziehe die Spalten in die Reihenfolge Qualifiziert → Bedarfsgespräch → Demo → Angebot versendet → Verhandlung → Gewonnen → Verloren.
4. Zeige die Summe je Spalte: auf die graue Zahl neben dem Spaltentitel klicken → `Gewichteter Wert` → **Summe** (Sum). Die graue Zahl zeigt sonst die Anzahl der Karten.
5. Nenne die Ansicht `Pipeline`.

Prüfwert: Die Summe der fünf offenen Spalten beträgt 376.922,70 € gewichtet bzw. 915.942 € ungewichtet (Spaltensumme `Wert`). In der Tabellenansicht zeigt die Berechnung unter einer Spalte dasselbe: auf die Spalte klicken → **Berechnen** (Calculate) → **Summe** (Sum); dort fließen aber auch Gewonnen und Verloren ein, solange kein Filter gesetzt ist.

### Filter für offene Deals

Für Auswertungen ohne abgeschlossene Deals: **Filter** → `Phase` → **ist nicht** (Is not) → Gewonnen und Verloren wählen. Bedingungen mit „oder“ (z. B. für gestockte Deals in Lab 5.1) entstehen über **Erweiterter Filter** (Advanced filter) mit Filtergruppen UND/ODER.

## Weitere Zeilen per „Mit CSV zusammenführen“

Eine bestehende Datenbank lässt sich um Zeilen aus einer CSV-Datei ergänzen, zum Beispiel um die eigene Lead-Liste aus Lab 3.3: Datenbank als ganze Seite öffnen → **•••** oben → **Mit CSV zusammenführen** (Merge with CSV) → Spalten den Eigenschaften zuordnen. Die Spaltennamen der CSV müssen exakt den Eigenschaftsnamen entsprechen. Zusammenführen fügt nur Zeilen hinzu; bestehende Zeilen werden nicht aktualisiert, doppelte Firmen also vorher löschen.

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Umlaute als Sonderzeichen (z. B. â€“) | Datei nicht als UTF-8 gespeichert, meist nach Öffnen und Speichern in Excel | Original-CSV aus dem Kursmaterial erneut herunterladen und ohne Umweg über Excel importieren |
| Spalte `Produkte` als Auswahl zeigt nur Bruchstücke | Werte mit Kommas werden in mehrere Optionen zerlegt | Typ auf Text zurückstellen |
| Datumsfelder nach dem Typwechsel leer | Datumserkennung je nach Version unterschiedlich (prüfen) | Typwechsel rückgängig machen (Strg+Z bzw. Cmd+Z), Werte als Text lassen; für die KI-Auswertung in Lab 5.1 genügt Text, nur die Notion-Filter „vor Datum“ brauchen den Typ Datum |
| Formel zeigt Fehler oder leer | `Wert` oder `Wahrscheinlichkeit` noch Text, oder Eigenschaftsname anders geschrieben | beide auf Zahl stellen; Namen in der Formel exakt wie die Spaltenköpfe |
| Board gruppiert nach `Segment` statt `Phase` | Notion wählt die erste Auswahl-Eigenschaft | **Gruppieren** (Group) → `Phase` |
| Datenbank fehlt in „Nordwind CRM“ | Import landet in „Privat“ | in der Seitenleiste auf die Seite ziehen |

## Quellen

- Notion-Hilfe „Daten in Notion importieren“, Abschnitt CSV und „Mit CSV zusammenführen“: <https://www.notion.com/de/help/import-data-into-notion> (englisch: <https://www.notion.com/help/import-data-into-notion>)
- Notion-Hilfe „Datenbankeigenschaften“: <https://www.notion.com/de/help/database-properties>
- Notion-Hilfe „Formeln“: <https://www.notion.com/de/help/formulas>
- Notion-Hilfe „Board-Ansicht“ (Gruppieren, Berechnungen): <https://www.notion.com/de/help/boards>
- Notion-Hilfe „Tabellen“ (Berechnen): <https://www.notion.com/de/help/tables>
- Notion-Hilfe „Ansichten, Filter und Sortierungen“ (Erweiterter Filter): <https://www.notion.com/de/help/views-filters-and-sorts>

Alle abgerufen am 22.11.2026.
