# Lab 2.3: Die KI schreibt den Prompt

**Leitfragen:**

<details>
<summary>Welche Fragen stellt eine gute Kollegin, bevor sie einen Auftrag annimmt?</summary>

Wofür ist das? Für wen? Gibt es ein Beispiel? Was darf auf keinen Fall passieren? Genau diese vier Fragen stellt die KI im Interview-Prompt.

</details>

<details>
<summary>Wer kennt eine Aufgabe besser: wer sie täglich macht oder die KI?</summary>

Wer sie täglich macht: Diese Person kennt Kunden, Ton und Stolperstellen. Die KI kennt dafür den Aufbau guter Prompts. Zusammen entsteht der beste Auftrag: der Mensch liefert das Wissen, die KI die Form.

</details>

<details>
<summary>Wer sollte einen Prompt prüfen, den eine KI geschrieben hat?</summary>

Die Person, die ihn nutzen wird. Sie führt ihn an einem echten Fall aus, prüft das Ergebnis und entscheidet erst dann, ob er in die Sammlung kommt.

</details>

- Statt selbst zu formulieren, lässt sich die KI interviewen und schreibt danach den Prompt mit den fünf Bausteinen aus Lab 2.1.
- Der Mensch liefert das Fachwissen, prüft den Entwurf und entscheidet, ob er ihn nutzt.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| Meta-Prompt | ein Prompt, dessen Ergebnis wieder ein Prompt ist – wie ein Formular, mit dem ein neues Formular entworfen wird |
| Interview-Prompt | Meta-Prompt, bei dem die KI zuerst Fragen stellt und erst danach schreibt – wie eine Kollegin, die vor dem Auftrag nachfragt |

## Erster Schritt des Nextise Agentic Way

Der Kurs folgt „Problem verstehen → Lösung konzipieren → Lösung bauen“ (Lab 1.1). Der häufigste Fehler mit KI: sofort eine Lösung bestellen („schreib mir einen Prompt für X“), bevor das Problem verstanden ist. Der Interview-Prompt dreht das um: Die KI wird geführt, fragt zuerst nach und schreibt erst dann. Dasselbe Muster nutzen später Zielkundenprofil (Lab 3.1), Bewertungsmatrix (Lab 3.3) und die drei Assistenten ab Tag 2.

| | Prompt selbst schreiben (Lab 2.1) | Interview-Prompt (Lab 2.3) |
| --- | --- | --- |
| Wer formuliert? | der Mensch | die KI |
| Wer liefert das Wissen? | der Mensch | der Mensch, als Antwort auf Fragen |
| Risiko | Bausteine fehlen unbemerkt | KI ergänzt Annahmen, die nicht stimmen |
| Gegenmittel | Checkliste der fünf Bausteine | Entwurf lesen und an einem echten Fall testen |

So läuft das Interview ab:

```text
Mensch nennt die Aufgabe
  → KI fragt nacheinander:  1 Ziel → 2 Zielgruppe → 3 Beispiele → 4 Grenzen
  → KI fasst die Antworten in drei Sätzen zusammen, Mensch bestätigt
  → KI schreibt den Prompt: Rolle · Aufgabe · Kontext · Format · Rahmenbedingungen
  → Mensch prüft, führt ihn an einem echten Fall aus und entscheidet
```

## Wohin die vier Antworten fließen

| Frage der KI | landet im Baustein | Beispiel Gesprächsvorbereitung |
| --- | --- | --- |
| **Ziel:** Was soll am Ende vorliegen? | Aufgabe, Format | „In fünf Minuten vorbereitet: Profil, Bedarf, Fragen“ |
| **Zielgruppe:** Wer liest das Ergebnis? | Rolle, Format | „nur ich selbst, nicht der Kunde“ |
| **Beispiele:** Was wird jedes Mal mitgegeben? | Kontext | „Produktblatt, Anfrage aus dem Website-Formular“ |
| **Grenzen:** Was darf nicht passieren? | Rahmenbedingungen | „keine Preise, nichts erfinden, höchstens eine Seite“ |

## Prompt-Generator in der Anthropic-Konsole

Anthropic, der Hersteller von Claude, bietet in seiner Entwicklerkonsole (Website zum Einbauen von Claude in eigene Software) einen Prompt-Generator: Aufgabe beschreiben, auf „Generate Prompt“ klicken, fertigen Prompt erhalten.

![Anthropic-Entwicklerkonsole mit dem Dialog „Your task“: Eingabefeld mit einer Aufgabenbeschreibung, darüber Beispiel-Schaltflächen wie „Write me an email“ und „Summarize a document“, unten die Schaltfläche „Generate Prompt“](https://assets.claude.com/44d2c58b7f523823519bc2058185551fe7938949.png)
_Quelle: Anthropic, „Evaluate prompts in the developer console“ (https://claude.com/resources/articles/evaluate-prompts), © Anthropic, abgerufen am 22.11.2026._

Das Ergebnis ist ein ausführlicher Prompt, der die Stellen, die sich von Fall zu Fall ändern, als Platzhalter markiert (hier `{{SMS_MESSAGE}}`) – dasselbe Prinzip wie `[Anfrage]` aus Lab 2.1. Im Vertrieb reicht dafür jeder KI-Assistent mit dem Interview-Prompt unten.

![Anthropic-Entwicklerkonsole: links ein vom Generator geschriebener Prompt mit dem Platzhalter {{SMS_MESSAGE}}, rechts das Feld „Variables“ mit einer eingesetzten Beispielnachricht und der Schaltfläche „Run“](https://assets.claude.com/0b0101ebd793461e21d61bf6e15543c22ffccb0b.png)
_Quelle: Anthropic, „Evaluate prompts in the developer console“ (https://claude.com/resources/articles/evaluate-prompts), © Anthropic, abgerufen am 22.11.2026._

## Woran ein guter KI-Prompt erkannt wird

- Alle fünf Bausteine sind vorhanden und mit Namen beschriftet.
- Veränderliche Angaben stehen als Platzhalter in eckigen Klammern (`[Firma]`), feste Angaben sind ausgeschrieben.
- Nichts über das eigene Unternehmen ist erfunden (z. B. kein „24/7-Support“, den es nicht gibt).
- Die Grenzen aus dem Interview stehen in den Rahmenbedingungen.

## Übung: Prompt für die Gesprächsvorbereitung

**Material:** [`produktblatt.md`](../material/produktblatt.md), Anfrage unten, eigene `meine-prompts.md` · **Werkzeug:** KI-Assistent, Texteditor

**Ausgangslage:** Bei Nordwind kommen jede Woche Anfragen über das Website-Formular. Vor jedem Erstgespräch soll eine Vorbereitung in fünf Minuten stehen. Die KI soll den Prompt dafür selbst schreiben; getestet wird er an einer echten Anfrage (erfunden, Kontaktdaten weggelassen).

**Anfrage zum Kopieren**
```text
Anfrage über das Kontaktformular der Website
Firma: Rheinpark Versicherungsmakler GmbH, Köln
Rolle: Office Management
Mitarbeitende: ca. 120
Nachricht: Wir haben 9 Besprechungsräume, ab Februar kommen 3 neue im 4. OG dazu. Räume werden ständig doppelt gebucht, vor allem unser großer Raum für 16 Personen. Wir buchen über Outlook (Microsoft 365). Einige Räume sollen videokonferenzfähig werden, der Ton über die Laptops ist schlecht. Können Sie uns ein Gespräch anbieten?
```

1. Öffne einen neuen Chat, kopiere Prompt-Karte 2.3a hinein und sende sie ab.
2. Beantworte die Rückfragen einzeln (die Antworthilfe unten darf direkt übernommen werden) und bestätige danach die Zusammenfassung.
3. Prüfe den erzeugten Prompt mit der Liste „Woran ein guter KI-Prompt erkannt wird“; fehlt etwas, bitte die KI in einem Satz um die Ergänzung.
4. Öffne einen neuen Chat, füge den erzeugten Prompt ein, setze die Rheinpark-Anfrage für die Platzhalter ein, lade `produktblatt.md` hoch (oder füge den Text ein) und sende ab.
5. Kopiere den geprüften Prompt als „Gesprächsvorbereitung Erstkontakt (v1)“ in `meine-prompts.md` und speichere.

**Prompt-Karte 2.3a – Interview-Prompt**
```text
Du bist ein erfahrener Prompt-Coach für den B2B-Vertrieb. Du hilfst mir, einen wiederverwendbaren Prompt für eine wiederkehrende Vertriebsaufgabe zu schreiben.

Gehe so vor:
1. Stelle mir nacheinander genau vier Fragen, immer nur eine Frage pro Nachricht, und warte auf meine Antwort:
   - Ziel: Was soll am Ende vorliegen, und woran erkenne ich ein gutes Ergebnis?
   - Zielgruppe: Wer liest oder nutzt das Ergebnis?
   - Beispiele: Welches Material gebe ich jedes Mal mit, und gibt es ein Beispiel für ein gutes Ergebnis?
   - Grenzen: Was darf nicht vorkommen? Welche Länge, Sprache und welcher Ton?
2. Fasse meine Antworten in drei Sätzen zusammen und frage, ob das stimmt.
3. Schreibe dann den Prompt mit den fünf Bausteinen Rolle, Aufgabe, Kontext, Format und Rahmenbedingungen. Beginne jeden Baustein mit seinem Namen und einem Doppelpunkt.
4. Setze alles, was sich von Fall zu Fall ändert, als Platzhalter in eckige Klammern, z. B. [Firma].
5. Gib den fertigen Prompt in einem einzigen Textblock aus und liste darunter die Platzhalter auf.

Regeln: Erfinde nichts über mein Unternehmen. Ist eine Antwort unklar, frage einmal nach.

Die Aufgabe: Gesprächsvorbereitung für einen Erstkontakt mit einem Interessenten von Nordwind Workspace (Lösungen für Besprechungsräume).
```

**Antworthilfe für die vier Fragen**

| Frage | Antwort zum Kopieren |
| --- | --- |
| Ziel | In fünf Minuten auf ein 30-minütiges Erstgespräch vorbereitet sein: Kurzprofil, vermuteter Bedarf mit passendem Nordwind-Produkt, fünf Fragen fürs Gespräch, mögliche Einwände, offene Punkte. |
| Zielgruppe | Nur ich selbst im Vertrieb; das Ergebnis geht nicht an den Kunden. |
| Beispiele | Ich gebe jedes Mal das Produktblatt mit und kopiere die Anfrage aus dem Website-Formular hinein. |
| Grenzen | Höchstens eine Seite, Stichpunkte, Deutsch. Keine Preise und keine Rabatte. Nichts erfinden, fehlende Angaben als offene Punkte aufführen. |

**Checkpoint:** Die KI hat vier einzelne Fragen gestellt; der erzeugte Prompt enthält die fünf beschrifteten Bausteine und Platzhalter in eckigen Klammern; die Vorbereitung für Rheinpark nennt Doppelbuchungen, Outlook und den großen Raum für 16 Personen.

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Beispiel aus ChatGPT, gekürzt – KI-Antworten fallen jedes Mal etwas anders aus.

**1.–2. Erste Rückfrage und Zusammenfassung der KI**
> Gern. Beginnen wir mit dem Ziel: Was soll nach der Vorbereitung konkret vorliegen, und woran merkst du, dass sie gut war?
>
> … (nach vier Antworten) Du willst dich in fünf Minuten auf ein 30-minütiges Erstgespräch vorbereiten, nur für dich selbst. Du gibst jedes Mal das Produktblatt und die Anfrage aus dem Website-Formular mit. Das Ergebnis ist höchstens eine Seite, auf Deutsch, ohne Preise und ohne erfundene Angaben. Stimmt das so?

**3. Erzeugter Prompt (v1, geprüft und in `meine-prompts.md` übernommen)**
```text
Rolle: Du bist eine erfahrene Vertriebsassistenz bei Nordwind Workspace, einem Anbieter von Lösungen für Besprechungsräume (Raumdisplay, Konferenzkamera-Sets, Raumbuchungs-Software, Service-Vertrag).

Aufgabe: Bereite mich auf ein 30-minütiges Erstgespräch mit einem Interessenten vor.

Kontext:
- Anfrage aus dem Website-Formular: [Anfrage]
- Unsere Produkte: siehe angehängtes Produktblatt

Format:
1. Kurzprofil des Interessenten (höchstens drei Sätze)
2. Vermuteter Bedarf und passendes Nordwind-Produkt als Tabelle: Bedarf | Produkt | Begründung
3. Fünf offene Fragen für das Gespräch
4. Zwei mögliche Einwände mit je einer kurzen Antwortidee
5. Fehlende Angaben, die im Gespräch zu klären sind

Rahmenbedingungen: Deutsch, Stichpunkte, höchstens eine Seite. Keine Preise, keine Rabatte. Erfinde nichts; was nicht in der Anfrage oder im Produktblatt steht, gehört unter Punkt 5.
```

**4. Ausgeführt mit der Rheinpark-Anfrage**
> **Kurzprofil:** Rheinpark Versicherungsmakler GmbH, Köln, ca. 120 Mitarbeitende, 9 Besprechungsräume, ab Februar 12. Ansprechrolle: Office Management.
>
> | Bedarf | Produkt | Begründung |
> | --- | --- | --- |
> | Doppelbuchungen | Panel 10 + Nordwind Book | Belegung an der Tür sichtbar, Buchung weiter über Outlook/Microsoft 365 |
> | Videokonferenz im großen Raum (16 Personen) | Vista Plus | Set für Räume bis 20 Personen |
> | Videokonferenz in kleineren Räumen | Vista | Set für Räume bis 12 Personen, Teams-kompatibel |
>
> **Fragen:** Welche Räume sollen videokonferenzfähig werden? Wer entscheidet über die Ausstattung? Ist die IT beim nächsten Termin dabei? Bis wann sollen die drei neuen Räume ausgestattet sein? Gibt es Anforderungen an den Datenschutz?
> **Einwände:** „Wir buchen doch schon über Outlook.“ → Book nutzt Outlook weiter und ergänzt Anzeige an der Tür und Freigabe von Geister-Buchungen. „Wo liegen die Daten?“ → Rechenzentrum in Frankfurt am Main.
> **Fehlende Angaben:** Raumgrößen der übrigen Räume, Budget, Entscheider, Zeitplan, IT-Ansprechperson.

Warum gut: Die vier Antworten stecken sichtbar in den Bausteinen, und die Regel „Erfinde nichts“ sorgt für eine Liste offener Punkte statt geratener Fakten.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| KI stellt alle Fragen auf einmal oder schreibt sofort | Regel „eine Frage pro Nachricht“ überlesen | „Bitte stelle die Fragen einzeln.“ nachschieben |
| Prompt enthält Leistungen, die Nordwind nicht anbietet | KI ergänzt plausible Annahmen | Stelle streichen lassen, Produktblatt als Kontext festlegen |
| Platzhalter beim Ausführen vergessen | eckige Klammern stehen noch im Text | vor dem Absenden nach `[` suchen |

## Fazit

- Der Interview-Prompt macht aus Fachwissen in vier Antworten einen vollständigen Prompt.
- Die KI liefert die Form, der Mensch das Wissen und die Entscheidung.
- Ein KI-Prompt ist erst ein Entwurf, bis er an einem echten Fall geklappt hat.

> **Merksatz:** Erst fragen lassen, dann schreiben lassen, dann selbst prüfen.
