# Lab 2.1: Die fünf Bausteine eines guten Prompts

**Leitfragen:**

<details>
<summary>Was braucht eine neue Kollegin, um eine Kundenanfrage ohne Rückfrage richtig zu beantworten?</summary>

Wer anfragt und warum, die eigenen Produktunterlagen, wie die Antwort aussehen soll und was auf keinen Fall drinstehen darf. Ohne diese Angaben rät sie – genau wie ein Sprachmodell.

</details>

<details>
<summary>Was passiert, wenn niemand sagt, wie lang und in welchem Ton?</summary>

Es entsteht ein Durchschnittstext: mittellang, höflich, voller Floskeln. Nicht falsch, aber selten direkt verwendbar.

</details>

<details>
<summary>Lohnt es sich, eine Minute länger am Auftrag zu schreiben?</summary>

Ja. Die Minute spart meist mehrere Runden Nachbessern, und der fertige Auftrag lässt sich für die nächste Anfrage wiederverwenden.

</details>

- Ein Prompt ist eine Arbeitsanweisung an jemanden, der weder Kunden noch Hausregeln kennt.
- Fünf Bausteine machen sie vollständig: Rolle, Aufgabe, Kontext, Format, Rahmenbedingungen.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| Kontext | Material, das die KI für die Aufgabe kennen muss: Anfrage, Produktblatt, Notiz – wie die Unterlagen, die einer neuen Kollegin auf den Tisch gelegt werden |
| Rahmenbedingungen | Regeln für das Ergebnis: Länge, Ton, Sprache und was nicht vorkommen darf |
| Texteditor | einfaches Programm für reinen Text ohne Formatierung: unter Windows „Editor“, unter macOS „TextEdit“ |
| `meine-prompts.md` | eigene Notizdatei im Texteditor, in der jeder getestete Prompt landet; `.md` steht für Markdown, reinen Text mit einfachen Zeichen wie `#` für Überschriften |

## Auftrag an eine neue Kollegin

Eine neue Kollegin im Nordwind-Innendienst bekommt am ersten Tag den Zettel _„Beantworte bitte diese Anfrage.“_ Der Auftrag ist nicht falsch, sondern unvollständig; ein Sprachmodell scheitert an derselben Stelle, nur ohne nachzufragen.

| Was sie liefert | Was das Team erwartet hätte |
| --- | --- |
| allgemeiner Dank, „unsere innovativen Lösungen“ | eine Antwort auf genau die vier gestellten Fragen |
| Preise aus dem Gedächtnis, „Lieferung nächste Woche“ | keine Preise ohne Angebot, Lieferzeit nur laut Produktblatt |
| eine Seite Fließtext | kurz, eine Zeile je Frage, ein klarer nächster Schritt |

## Fünf Bausteine eines Prompts

| Baustein | Frage | Beispiel Antwort auf eine Kundenanfrage |
| --- | --- | --- |
| **Rolle** | Aus wessen Sicht wird geschrieben? | „Du bist Vertriebsmitarbeiterin im Innendienst bei Nordwind Workspace.“ |
| **Aufgabe** | Was genau soll entstehen? | „Beantworte die Anfrage von Frau Lindqvist unten.“ |
| **Kontext** | Was muss bekannt sein? | Anfrage, Produktblatt als Datei oder Text; Ziel: kurzes Telefonat vereinbaren |
| **Format** | Wie sieht das Ergebnis aus? | Betreff, Anrede, je Frage ein bis zwei Sätze, ein nächster Schritt |
| **Rahmenbedingungen** | Was gilt sonst: Länge, Ton, Sprache, was nicht vorkommen darf? | höchstens 180 Wörter, Sie-Form, keine Preise, Angaben nur aus dem Produktblatt |

Microsoft beschreibt für Copilot ein ähnliches Schema mit vier Teilen: Ziel, Kontext, Erwartungen, Quelle. Die Namen unterscheiden sich, die Idee ist dieselbe:

![Schema „Goal + Context + Expectations + Source“ von Microsoft: vier Kästen mit Leitfrage und Beispielsatz, etwa „I want a list of 3-5 bullet points to prepare me“ für Goal und „Respond with a tone that is friendly but authoritative“ für Expectations](https://support.microsoft.com/en-us/microsoft-365-copilot/media/prompt-framework.png)
_Quelle: Microsoft Support, „Get started writing prompts in Microsoft 365 Copilot“ (https://support.microsoft.com/en-us/microsoft-365-copilot/get-started-writing-prompts-in-microsoft-365-copilot), © Microsoft, abgerufen am 22.11.2026._

Auch Anthropic empfiehlt, zu sagen, wie „fertig“ aussieht, und den eigenen Hausstil mitzugeben:

![Grafik „Prompting habits for Opus 5.5“ mit sieben Kacheln, darunter Connect your files and systems, Say what done looks like, Share charts and screenshots und Share your house style](https://assets.claude.com/d61fa79e1e1a38bd6ad4547ddb66c993ef569705.png)
_Quelle: Anthropic, „Using Claude Opus 5.5 as your daily driver for knowledge work“, 12.11.2026 (https://claude.com/resources/articles/using-claude-opus-5-5-as-your-daily-driver-for-knowledge-work), © Anthropic, abgerufen am 22.11.2026._

Fehlt das Format, antworten KI-Assistenten mit langem Fließtext. Beispiel aus Le Chat (Mistral) auf einen kurzen Prompt:

![Le Chat von Mistral: auf den kurzen Prompt „Describe Wikipedia in a thoughtful way“ antwortet das Modell mit mehreren langen Absätzen Fließtext](https://upload.wikimedia.org/wikipedia/commons/thumb/8/81/Le_Chat_chatbot_example_screenshot.webp/500px-Le_Chat_chatbot_example_screenshot.webp)
_Quelle: Wikimedia Commons, „Le Chat chatbot example screenshot.webp“ (https://commons.wikimedia.org/wiki/File:Le_Chat_chatbot_example_screenshot.webp), Screenshot VulcanSphere, Software Mistral AI, gemeinfrei, abgerufen am 22.11.2026._

## Notizdatei `meine-prompts.md` ab Lab 2.1

Ein guter Prompt, der nur im Chatverlauf steht, ist nach einer Woche verschwunden (und jede neue Antwort fällt anders aus, Lab 1.2). Darum wandert jeder getestete Prompt in eine eigene Textdatei:

- Aufbau je Eintrag: Überschrift `## <Name> (v1)`, Zeilen „Werkzeug:“ und „Platzhalter:“, darunter der Prompt; vollständiges Beispiel im Musterergebnis.
- `#` und `##` markieren Überschriften, sonst ist alles reiner Text; Kundennamen werden durch Platzhalter ersetzt (Lab 1.3).

## Übung: Vom Einzeiler zum vollständigen Prompt

**Material:** [`produktblatt.docx`](../material/produktblatt.docx) (Textfassung [`produktblatt.md`](../material/produktblatt.md)), Kundenanfrage unten · **Werkzeug:** KI-Assistent, Texteditor

**Ausgangslage:** Bei Nordwind ist eine Anfrage einer Kanzlei eingegangen (erfunden). Die Antwort soll heute raus. Erst der Einzeiler, dann der Prompt mit fünf Bausteinen.

**Kundenanfrage zum Kopieren**
```text
Betreff: Anfrage Besprechungsräume
Guten Tag,
wir sind eine Kanzlei mit 35 Mitarbeitenden und 5 Besprechungsräumen in Bremen. Mandantengespräche laufen zunehmend per Video, der Ton über die Laptops ist schlecht. Außerdem werden Räume oft doppelt gebucht.
Meine Fragen:
1. Funktioniert Ihre Kamera mit Microsoft Teams?
2. Wo liegen die Buchungsdaten?
3. Wie schnell könnten Sie liefern und installieren?
4. Was kostet das ungefähr für 5 Räume?
Viele Grüße
Jana Lindqvist, Büroleitung, Lindqvist & Haas Rechtsanwälte
```

1. Öffne einen neuen Chat und sende Prompt-Karte 2.1a mit der Anfrage darunter.
2. Öffne einen neuen Chat, lade `produktblatt.docx` hoch (oder füge den Text aus `produktblatt.md` ein), sende Prompt-Karte 2.1b mit der Anfrage darunter.
3. Vergleiche beide Antworten: beantwortete Fragen, erfundene Angaben, Preis, Länge, nächster Schritt.
4. Öffne den Texteditor, lege eine neue Datei an und speichere sie als `meine-prompts.md` (macOS: vorher „Format“ → „In reinen Text umwandeln“; Windows: Dateityp „Alle Dateien“).
5. Kopiere Prompt-Karte 2.1b als Eintrag „Antwort auf eine Kundenanfrage (v1)“ in die Datei, ersetze darin Frau Lindqvist und die Anfrage durch `[Ansprechperson]` und `[Anfrage]` und speichere.

**Prompt-Karte 2.1a – Der Einzeiler**
```text
Beantworte diese Anfrage:

[Anfrage einfügen]
```

**Prompt-Karte 2.1b – Fünf Bausteine**
```text
Rolle: Du bist Vertriebsmitarbeiterin im Innendienst bei Nordwind Workspace, einem Anbieter von Lösungen für Besprechungsräume.
Aufgabe: Beantworte die Kundenanfrage von Frau Lindqvist unten.
Kontext: Das Produktblatt ist angehängt. Ziel der Antwort ist ein kurzes Telefonat, um den Bedarf zu klären.
Format: Betreffzeile, Anrede, je Frage ein bis zwei Sätze in der Reihenfolge der Anfrage, ein nächster Schritt mit zwei Terminvorschlägen, Gruß mit dem Namen Lena Hoffmann.
Rahmenbedingungen: Deutsch, Sie-Form, höchstens 180 Wörter. Keine Preise und keine Rabatte nennen; zum Preis ein Angebot nach dem Telefonat anbieten. Produkteigenschaften und Lieferzeiten nur aus dem Produktblatt.

Anfrage:
[Anfrage einfügen]
```

**Checkpoint:** Die zweite Antwort beantwortet alle vier Fragen mit Angaben aus dem Produktblatt (Teams, Frankfurt am Main, zwei Wochen) und nennt keinen Preis; `meine-prompts.md` enthält den Eintrag mit zwei Platzhaltern.

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Beispiel aus ChatGPT, gekürzt – KI-Antworten fallen jedes Mal etwas anders aus.

**1. Antwort auf den Einzeiler**
> Sehr geehrte Frau Lindqvist,
> vielen Dank für Ihr Interesse an unseren innovativen Lösungen! Unsere Kameras sind mit allen gängigen Plattformen kompatibel. Die Daten werden sicher in der Cloud gespeichert. Die Lieferung erfolgt in der Regel innerhalb weniger Tage. Für fünf Räume liegen die Kosten erfahrungsgemäß zwischen 5.000 und 15.000 Euro …

**2. Antwort auf Prompt-Karte 2.1b**
> Betreff: Ihre Anfrage – Videokonferenzen und Raumbuchung für 5 Räume
>
> Guten Tag Frau Lindqvist,
>
> vielen Dank für Ihre Anfrage. Zu Ihren Fragen:
> 1. Ja, Nordwind Vista arbeitet mit Microsoft Teams, Zoom und Google Meet und wird mit einem USB-C-Kabel an den Laptop angeschlossen.
> 2. Die Buchungsdaten von Nordwind Book liegen in einem Rechenzentrum in Frankfurt am Main (EU).
> 3. Lieferung und Installation erfolgen in der Regel innerhalb von zwei Wochen nach Auftrag, je Raum rechnen wir mit etwa zwei Stunden.
> 4. Den Preis stellen wir Ihnen gern in einem Angebot zusammen, sobald wir Raumgrößen und Ausstattung kurz besprochen haben.
>
> Passt Ihnen ein 15-minütiges Telefonat am Dienstag um 10 Uhr oder am Donnerstag um 14 Uhr?
>
> Viele Grüße
> Lena Hoffmann, Nordwind Workspace

**3. Vergleich**

| | Einzeiler | Fünf Bausteine |
| --- | --- | --- |
| beantwortete Fragen | allgemein | alle vier, in Reihenfolge |
| erfundene Angaben | „alle Plattformen“, „Cloud“, „wenige Tage“ | keine, alles aus dem Produktblatt |
| Preis | geschätzte Spanne | kein Preis, Angebot angekündigt |
| nächster Schritt | fehlt | Telefonat mit zwei Terminen |

**4.–5. Eintrag in `meine-prompts.md`**
```markdown
# Meine Prompts

## Antwort auf eine Kundenanfrage (v1)

Werkzeug: KI-Assistent, Produktblatt als Datei oder Text
Platzhalter: [Ansprechperson], [Anfrage]

Rolle: Du bist Vertriebsmitarbeiterin im Innendienst bei Nordwind Workspace, einem Anbieter von Lösungen für Besprechungsräume.
Aufgabe: Beantworte die Kundenanfrage von [Ansprechperson] unten.
Kontext: Das Produktblatt ist angehängt. Ziel der Antwort ist ein kurzes Telefonat, um den Bedarf zu klären.
Format: Betreffzeile, Anrede, je Frage ein bis zwei Sätze in der Reihenfolge der Anfrage, ein nächster Schritt mit zwei Terminvorschlägen, Gruß mit dem Namen Lena Hoffmann.
Rahmenbedingungen: Deutsch, Sie-Form, höchstens 180 Wörter. Keine Preise und keine Rabatte nennen; zum Preis ein Angebot nach dem Telefonat anbieten. Produkteigenschaften und Lieferzeiten nur aus dem Produktblatt.

Anfrage:
[Anfrage]
```

Warum gut: Jede Aussage der zweiten Antwort lässt sich auf das Produktblatt zurückführen, und der Eintrag passt durch die Platzhalter auf die nächste Anfrage.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Antwort nennt Eigenschaften, die nicht im Produktblatt stehen | Datei nicht angehängt oder Rahmenbedingung fehlt | Datei-Symbol über dem Eingabefeld prüfen, sonst Text aus `produktblatt.md` einfügen |
| Upload schlägt fehl | Nutzungslimit des kostenlosen Kontos | Text aus `produktblatt.md` in den Chat kopieren |
| Datei heißt `meine-prompts.md.txt` | Editor hängt `.txt` an | beim Speichern Dateityp „Alle Dateien“ wählen bzw. in TextEdit reinen Text einstellen |

## Fazit

- Rolle, Aufgabe, Kontext, Format und Rahmenbedingungen machen aus einem Einzeiler eine vollständige Anweisung.
- Eigene Unterlagen als Kontext verhindern erfundene Angaben.
- Jeder getestete Prompt wandert mit Platzhaltern in `meine-prompts.md`.

> **Merksatz:** Was im Prompt fehlt, entscheidet das Modell.
