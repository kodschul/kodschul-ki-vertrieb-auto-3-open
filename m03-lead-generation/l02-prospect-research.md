# Lab 3.2: Potenzielle Kunden recherchieren

**Leitfragen:**

<details>
<summary>Woran wird heute erkannt, dass eine Firma gerade Bedarf haben könnte?</summary>

An Veränderungen: Umzug, Neubau, neue Etage, Wachstum, neue Arbeitsmodelle, Stellenanzeigen. Wer sich gerade verändert, kauft eher als jemand, bei dem alles läuft.

</details>

<details>
<summary>Welche öffentlichen Ereignisse sind ein guter Anlass für eine Kontaktaufnahme?</summary>

Pressemitteilungen zu Umzug oder neuem Standort, Meldungen über Übernahmen, Karriereseiten mit Stellen im Facility Management, Berichte über hybrides Arbeiten. Sie liefern zugleich den ersten Satz der Nachricht (Lab 3.4).

</details>

<details>
<summary>Wo endet sinnvolle Recherche und beginnt Ausspähen?</summary>

Sinnvoll ist, was eine Firma selbst oder die Presse über das Geschäft veröffentlicht. Persönliches über einzelne Menschen zusammenzutragen (Privatleben, private Profile) ist Ausspähen und datenschutzrechtlich heikel.

</details>

- Die Websuche des KI-Assistenten findet in wenigen Minuten Firmen nach dem Zielkundenprofil aus Lab 3.1, jeweils mit Kaufsignal und Quelle; geprüft wird trotzdem selbst.
- Ergebnis ist eine Lead-Liste als CSV-Datei, die sich später in das Übungs-CRM Notion laden lässt.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| Prospect | Firma, die zum Zielkundenprofil passt und noch keinen Kontakt hatte; im Kurs heißt sie auch vor dem Kontakt schon Lead (Lab 1.1) |
| Kaufsignal | öffentlicher Hinweis, dass eine Firma gerade Bedarf haben könnte, z. B. ein angekündigter Umzug |
| Ansprechrolle | Funktion statt Name („Leitung Facility Management“); der Name kommt erst aus dem Gespräch |
| CSV (Comma-Separated Values) | reine Textdatei für Tabellen: eine Zeile je Datensatz, Spalten durch Kommas getrennt; jedes Tabellenprogramm und Notion können sie lesen |

## Kaufsignale für Nordwind

| Kaufsignal | wo es steht | Beispiel (fiktiv) | warum relevant |
| --- | --- | --- | --- |
| Umzug, Neubau, neue Etage | Pressemitteilung, Website „Aktuelles“ | „Zentrale zieht im April 2027 in die HafenCity, 18 Besprechungsräume geplant“ | Räume werden neu ausgestattet |
| hybrides Arbeiten, Desk-Sharing | Karriereseite, Interview der Geschäftsführung | „Einführung von Desk-Sharing angekündigt“ | mehr Videokonferenzen, Räume knapper |
| Stellenanzeige Facility oder Office Management | Karriereseite, Jobportale | „Office Manager (m/w/d) für Raum- und Terminorganisation“ | jemand wird für Räume zuständig |
| Wachstum, Übernahme, neuer Standort | Pressemitteilung, Wirtschaftspresse | „Übernahme einer Kanzlei in Winterthur“ | Standorte müssen zusammenarbeiten |

Vertriebswerkzeuge melden solche Ereignisse automatisch. LinkedIn Sales Navigator zum Beispiel zeigt Hinweise, wenn eine gespeicherte Firma in den Nachrichten erwähnt wird oder eine Person befördert wurde:

![Produktbild LinkedIn Sales Navigator, Bereich „Alerts“: drei Meldungen – Mitarbeitende einer Firma recherchieren das eigene Unternehmen, eine Firma wurde in den Nachrichten erwähnt („View article“), eine Person wurde befördert („Message“)](https://delivery-p143253-e1476319.adobeaemcloud.com/adobe/assets/urn:aaid:aem:2597dde7-ecac-4ea8-a1a7-1572141a4f3e/as/alerts-2x-v2.png?width=1199)
_Quelle: LinkedIn, „Sales Navigator“ (https://business.linkedin.com/sales-solutions/sales-navigator), Produktbild © LinkedIn, abgerufen am 22.11.2026._

## Recherche mit Websuche

```text
Zielkundenprofil (3.1) + Region
   → KI sucht im Web:  Firmenliste → je Firma ein Kaufsignal → Quelle mit Link
   → Mensch prüft zwei Einträge an der Quelle
   → KI gibt die Tabelle als CSV aus → leads.csv
```

| Assistent | Websuche sicherstellen (Stand: 22.11.2026, Bezeichnung je nach Version) |
| --- | --- |
| ChatGPT, Claude, Microsoft 365 Copilot | Satz „Suche im Web“ in den Prompt schreiben oder die Websuche im Menü einschalten (Lab 1.2) |
| Perplexity | sucht immer im Web |

Kostenlose Konten haben Tageslimits für die Websuche. Zehn Firmen in einer Anfrage sind deshalb besser als zehn einzelne Anfragen.

## Quellen der Recherche prüfen

Auch mit Websuche kann der Assistent eine Aussage der falschen Quelle zuordnen oder eine alte Meldung als aktuell darstellen (Lab 1.2). Darum werden mindestens zwei Einträge an der Quelle geprüft:

- **Link öffnen:** Steht das Kaufsignal dort wirklich, mit derselben Zahl?
- **Datum ansehen:** Stammt die Meldung aus den letzten zwölf Monaten, gerechnet ab heute?
- **Absender ansehen:** Firma selbst, Geschäftsbericht oder seriöse Presse, kein anonymes Forum.

ChatGPT zeigt beim Klick auf eine Quellenangabe Absender, Titel und Datum der Seite:

![ChatGPT-Antwort mit einer Quellenmarke unter einem Satz; darunter eine aufgeklappte Karte mit Absender „University of Maryland Extension“, Seitentitel und Datum „April 9, 2024“ samt Textauszug](https://images.ctfassets.net/j22is2dtoxu1/intercom-img-ee55c065a6a39252834b7646/1078515a708268061d94f87e8ec86391/AD_4nXfkiwzPjm0hemvaZQ19JGTxrrE3YZujQ7Ayj_8CRgQujp9Nt1N4mVNBIou5J9bl-FXOiXVtWmBgb_JMtbdgP38dyNbRvIFyobbzw4gCim-DCjacXCwyYO-leU8P)
_Quelle: OpenAI Help Center, „ChatGPT search“ (https://help.openai.com/en/articles/9237897-chatgpt-search), Screenshot © OpenAI, abgerufen am 22.11.2026._

## Grenzen der Recherche: nur öffentliche Firmendaten

- Recherchiert wird über Firmen, nicht über Menschen. Öffentliche Firmendaten sind nach der Datenampel aus Lab 1.3 grün.
- Ansprechrollen statt Namen: In der Lead-Liste steht „Leitung Facility Management“, kein Personenname.
- Keine Profile von Privatpersonen, keine privaten Social-Media-Inhalte, kein Privatleben.
- Namen und Kontaktdaten kommen erst aus dem Gespräch oder aus einer Anfrage und gehören ins CRM, nicht in den KI-Chat.

## Lead-Liste als CSV-Datei

Notion, Excel und später n8n lesen Tabellen am zuverlässigsten als CSV. Eine CSV-Datei ist reiner Text: Die erste Zeile enthält die Spaltennamen, jede weitere Zeile einen Datensatz, die Spalten trennt ein Komma.

![Beispiel einer CSV-Datei in Schreibmaschinenschrift: erste Zeile „company,surname,forename“, darunter drei Zeilen mit Firmenname, Nachname und Vorname, jeweils durch Kommas getrennt](https://upload.wikimedia.org/wikipedia/commons/thumb/0/0b/Example_CSV_file.png/960px-Example_CSV_file.png)
_Quelle: Wikimedia Commons, „Example CSV file.png“ (https://commons.wikimedia.org/wiki/File:Example_CSV_file.png), Belbury, CC BY-SA 4.0, abgerufen am 22.11.2026._

Die Lead-Liste im Kurs hat genau diese acht Spalten (wie [`leads-recherche-muster.csv`](../material/leads-recherche-muster.csv)):

```text
Firma,Website,Branche,Mitarbeitende,Räume,Region,Kaufsignal,Quelle-URL
```

| Regel | Grund |
| --- | --- |
| Spaltennamen exakt so schreiben | Notion ordnet Spalten beim Import über den Namen zu (Lab 4.1) |
| Text mit Komma in Anführungszeichen: `"Umzug im April, 18 Räume"` | sonst zerfällt die Zeile in zu viele Spalten |
| `Mitarbeitende` nur als Zahl (`260`, nicht „ca. 260 MA“) | Notion und die Bewertung (Lab 3.3) rechnen damit |
| `Räume` = Besprechungsräume, nur wenn öffentlich genannt (Pressemitteilung zum Neubau, Stellenanzeige, Standortseite), sonst leer | eine geratene Zahl verfälscht die Bewertung; leer = unbekannt; die Matrix schätzt dann vorsichtig (höchstens 10 Punkte, Lab 3.3) |
| `Region` nur aus der Liste DE-Nord, DE-West, DE-Süd, DE-Ost, AT, CH, NL, Sonstige | dieselben Werte nutzt das CRM ab Lab 4.1 |

Regionen nach Bundesland: DE-Nord = HH, HB, SH, NI, MV · DE-West = NW, HE, RP, SL · DE-Süd = BY, BW · DE-Ost = BE, BB, SN, ST, TH.

So wird aus der Chat-Antwort eine Datei: CSV-Block im Chat kopieren (Kopier-Symbol am Codeblock), im Texteditor eine neue Datei anlegen, einfügen und als `leads.csv` speichern (Dateityp „Alle Dateien“ bzw. reiner Text, Kodierung UTF-8).

## Übung: Zehn Firmen nach dem Zielkundenprofil finden

**Material:** eigene `zielkundenprofil.md` aus Lab 3.1, Rückfallebene [`leads-recherche-muster.csv`](../material/leads-recherche-muster.csv) · **Werkzeug:** KI-Assistent mit Websuche, Texteditor

**Ausgangslage:** Nordwind will in einer Region zehn Firmen finden, die zum Zielkundenprofil passen und gerade einen Anlass haben. Das Ergebnis soll als `leads.csv` direkt weiterverwendbar sein: in Lab 3.3 für die Bewertung, danach im CRM.

1. Wähle eine Region (z. B. Großraum Köln, Hamburg, München, Wien, Zürich oder Utrecht), öffne einen neuen Chat, füge Prompt-Karte 3.2a mit dem Profil aus `zielkundenprofil.md` ein und sende ab.
2. Öffne bei zwei Firmen den Quell-Link und prüfe Kaufsignal, Datum und Absender; lass falsche oder veraltete Einträge im Chat ersetzen.
3. Sende Prompt-Karte 3.2b für die CSV-Ausgabe.
4. Kopiere den CSV-Block in eine neue Datei im Texteditor und speichere sie als `leads.csv`.
5. Kopiere Prompt-Karte 3.2a als „Lead-Recherche (v1)“ in `meine-prompts.md`.

**Prompt-Karte 3.2a – Lead-Recherche nach Profil**

```text
Rolle: Du bist Research-Assistenz im B2B-Vertrieb von Nordwind Workspace (Raumdisplays, Konferenzkamera-Sets, Raumbuchungs-Software, Service für Besprechungsräume).

Aufgabe: Suche im Web zehn Unternehmen in der Region [Region], die zu unserem Zielkundenprofil passen und in den letzten zwölf Monaten (ab heute gerechnet) ein Kaufsignal zeigen.

Kontext – unser Zielkundenprofil:
[Profil aus zielkundenprofil.md einfügen]
Kaufsignale: Umzug, Neubau, neue Etage oder neuer Standort; Einführung von hybridem Arbeiten oder Desk-Sharing; Stellenanzeigen Facility oder Office Management; Wachstum oder Übernahme.

Format: Tabelle mit den Spalten Firma | Website | Branche | Mitarbeitende | Räume | Region | Kaufsignal | Quelle-URL. Mitarbeitende als Zahl (Schätzung mit "ca." nur in der Antwort, nicht in der Tabelle). Räume = Anzahl Besprechungsräume, nur wenn öffentlich genannt, sonst leer lassen. Region nur als DE-Nord, DE-West, DE-Süd, DE-Ost, AT, CH, NL oder Sonstige.

Rahmenbedingungen: Nur öffentliche Quellen über Unternehmen. Keine Namen von Personen, keine Profile von Privatpersonen. Jede Zeile braucht eine Quelle mit Link. Findest du kein Kaufsignal, schreibe "kein Anlass gefunden" statt eines erfundenen.
```

**Prompt-Karte 3.2b – Tabelle als CSV**

```text
Gib die Tabelle jetzt als CSV in einem einzigen Codeblock aus:
- erste Zeile exakt: Firma,Website,Branche,Mitarbeitende,Räume,Region,Kaufsignal,Quelle-URL
- Komma als Trennzeichen, Texte mit Komma in doppelten Anführungszeichen
- Mitarbeitende und Räume nur als Zahl, unbekannte Räume als leeres Feld, keine Leerzeilen, kein Text vor oder nach dem Codeblock
```

**Checkpoint:** `leads.csv` hat eine Kopfzeile und zehn Datenzeilen mit acht Spalten; jede Zeile enthält eine Quelle-URL, keine Zeile einen Personennamen; zwei Kaufsignale sind an der Quelle geprüft.

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Das Muster zeigt fiktive Firmen mit `.example`-Adressen, damit im Handout keine veralteten Aussagen über echte Firmen stehen. Eine echte Recherche mit Websuche liefert echte Firmen und Quellen, die sich öffnen lassen. Das Muster verteilt die zehn Firmen bewusst auf mehrere Regionen, damit die Bewertung in Lab 3.3 alle Regionspunkte zeigt; eine eigene Recherche bleibt in einer Region. Vollständige Datei: [`leads-recherche-muster.csv`](../material/leads-recherche-muster.csv).

**1. Tabelle im Chat (Auszug)**

| Firma | Branche | Mitarbeitende | Räume | Region | Kaufsignal |
| --- | --- | --- | --- | --- | --- |
| Hafenkontor Logistik GmbH | Logistik | 260 | 18 | DE-Nord | Umzug der Zentrale in die HafenCity im April 2027, 18 Besprechungsräume geplant |
| Brenner & Voss Rechtsanwälte PartG mbB | Rechtsberatung | 65 | 9 | DE-West | zusätzliche Etage mit vier Mandanten-Besprechungsräumen, Bezug Februar 2027 (dann 9 Räume) |
| Vogelsang Medizintechnik GmbH | Medizintechnik | 340 | (leer) | DE-Süd | Einführung von hybridem Arbeiten mit Desk-Sharing angekündigt, ohne Termin |
| Lechfeld Stahlhandel GmbH | Stahlhandel | 180 | 3 | DE-Süd | Stellenanzeige Facility Manager (m/w/d) |

**2. Prüfung an der Quelle**

| Firma | geprüft | Ergebnis |
| --- | --- | --- |
| Hafenkontor Logistik | Pressemitteilung „Umzug HafenCity 2027“ | ✓ Umzug und 18 Räume stehen so in der Meldung, Absender ist die Firma selbst |
| Lechfeld Stahlhandel | Stellenanzeige Facility Manager | ✓ Anzeige online, nennt drei Besprechungsräume |

**3.–4. `leads.csv` (erste drei Zeilen)**

```text
Firma,Website,Branche,Mitarbeitende,Räume,Region,Kaufsignal,Quelle-URL
Hafenkontor Logistik GmbH,https://www.hafenkontor-logistik.example,Logistik,260,18,DE-Nord,"Umzug der Zentrale in die HafenCity im April 2027, 18 Besprechungsräume geplant",https://www.hafenkontor-logistik.example/presse/umzug-hafencity-2027
Brenner & Voss Rechtsanwälte PartG mbB,https://www.brenner-voss.example,Rechtsberatung,65,9,DE-West,"Zusätzliche Etage mit vier Mandanten-Besprechungsräumen, Bezug Februar 2027 (dann 9 Räume)",https://www.brenner-voss.example/aktuelles/neue-etage-2027
```

Warum gut: Jede Zeile hat eine Quelle, unbekannte Raumzahlen bleiben leer statt geraten, und es gibt keinen einzigen Personennamen.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Liste enthält Namen von Geschäftsführern | Rahmenbedingung zu Personen überlesen | „Entferne alle Personennamen, nur Rollen“ nachschieben |
| Kaufsignal steht nicht in der Quelle oder ist drei Jahre alt | KI hat falsch zugeordnet | Eintrag ersetzen lassen, „letzte zwölf Monate“ im Prompt behalten |
| Notion zeigt später verschobene Spalten | Komma im Text ohne Anführungszeichen | Prompt-Karte 3.2b erneut senden, Zeilen mit Komma prüfen |
| Datei heißt `leads.csv.txt` oder ist formatiert | Editor speichert als `.txt` bzw. Rich Text | Dateityp „Alle Dateien“ bzw. „In reinen Text umwandeln“ (Lab 2.1) |
| Websuche liefert nichts | Tageslimit des kostenlosen Kontos erreicht | Perplexity nutzen oder mit `leads-recherche-muster.csv` weiterarbeiten |

## Fazit

- Kaufsignale machen aus einer Firmenliste eine Lead-Liste mit Anlass.
- Jede Zeile braucht eine Quelle; recherchiert wird über Firmen, Rollen statt Namen.

> **Merksatz:** Keine Zeile ohne Quelle, kein Name ohne Gespräch.
