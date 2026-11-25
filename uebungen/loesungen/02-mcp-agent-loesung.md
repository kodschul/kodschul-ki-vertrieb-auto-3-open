# Lösung 2: Notion mit dem KI-Assistenten verbinden und einen Agenten arbeiten lassen

Zurück zur [Übung 2](../02-mcp-agent.md). _Beispiel – KI-Antworten fallen jedes Mal etwas anders aus. Entscheidend ist, dass das Erfolgskriterium erfüllt ist._

## Schritt 1: Verbindung

Notion steht als verbunden: in Claude unter **Customize > Connectors**, in ChatGPT unter **Settings > Plugins**. Im Notion-Fenster wurde der Übungs-Arbeitsbereich mit der Seite „Nordwind CRM“ gewählt, kein Firmen-Arbeitsbereich.

## Schritt 2–3: Antwort auf Prompt-Karte 2a (nur lesen)

> In der Datenbank „Leads“ gibt es drei Leads mit Region „DE-Süd“:
>
> | Firma | Score | Stufe | Status | Rolle | Kaufsignal |
> | --- | --- | --- | --- | --- | --- |
> | Vogelsang Medizintechnik GmbH | 75 | heiß | Neu | Leitung Workplace Management | Einführung von hybridem Arbeiten mit Desk-Sharing angekündigt, ohne Termin |
> | Lechfeld Stahlhandel GmbH | 59 | warm | Neu | Leitung Facility Management | Stellenanzeige Facility Manager (m/w/d) |
> | Isarblick Steuerberatung GmbH | 55 | warm | Neu | Kanzleileitung | Stellenanzeige Office Manager (m/w/d) für Raum- und Terminorganisation |
>
> Leere Felder: Bei allen drei sind „Ansprechperson“, „E-Mail“ und „Nächster Schritt“ leer; bei Vogelsang und Isarblick fehlt außerdem die Anzahl der Räume.

Gegenprobe in Notion: Spalte `Region` zeigt genau diese drei Einträge mit „DE-Süd“; Score und Stufe stimmen.

Gut, weil zuerst nur gelesen und nachgeprüft wird. Erst wenn die Daten stimmen, darf der Agent schreiben.

## Schritt 4: Plan auf Prompt-Karte 2b

> Plan – ich ändere nur „Diese Woche“ und „Nächster Schritt“ bei diesen drei Leads:
>
> | Firma | Nächster Schritt |
> | --- | --- |
> | Vogelsang Medizintechnik GmbH | Leitung Workplace Management anrufen: Desk-Sharing ist angekündigt – Raumbuchung für hybrides Arbeiten anbieten. |
> | Lechfeld Stahlhandel GmbH | Leitung Facility Management anrufen: Stelle Facility Manager ist ausgeschrieben – Raumdisplays und Buchung als Entlastung vorschlagen. |
> | Isarblick Steuerberatung GmbH | Kanzleileitung anrufen: sucht Office Manager für Raum- und Terminorganisation – Raumbuchung als Entlastung zeigen. |
>
> Soll ich das so ausführen?

Antwort: „OK, bitte ausführen.“ Danach meldet der Assistent die drei aktualisierten Einträge; im Arbeitsverlauf bzw. in den Bestätigungskarten stehen die Aufrufe der Notion-Werkzeuge (z. B. Suchen, Abrufen, Seite aktualisieren).

Kann ChatGPT im eigenen Tarif nicht schreiben: Der Plan oben ist das Ergebnis des Agenten, die drei Einträge werden von Hand in Notion übernommen. Das Ergebnis in Notion ist dasselbe.

## Schritt 5: Ergebnis in Notion

| Firma | Diese Woche | Nächster Schritt |
| --- | --- | --- |
| Vogelsang Medizintechnik GmbH | ☑ | Leitung Workplace Management anrufen: … |
| Lechfeld Stahlhandel GmbH | ☑ | Leitung Facility Management anrufen: … |
| Isarblick Steuerberatung GmbH | ☑ | Kanzleileitung anrufen: … |
| alle anderen acht Leads | unverändert | unverändert |

Gut, weil der Assistent die Arbeit erledigt, der Mensch aber an zwei Stellen entscheidet: beim Plan und bei der Kontrolle in Notion.

## Noch einmal: andere Regionen

| Region | Lead | Nächster Schritt (Beispiel) |
| --- | --- | --- |
| CH | Limmat Treuhand AG (65, warm) | Leitung Administration anrufen: Übernahme einer Treuhandkanzlei in Winterthur – Raumbuchung für den gemeinsamen Standort anbieten. |
| NL | Grachtenwerk Coworking B.V. (66, warm) | Operations Management anrufen: Mitgliederzahl 2026 verdoppelt – Raumdisplays und Buchung für mehr Mitglieder vorschlagen. |

Nach Prompt-Karte 2c sind bei den DE-Süd-Leads `Diese Woche` wieder leer und `Nächster Schritt` ohne Text; Übung 2 kann von vorn beginnen.
