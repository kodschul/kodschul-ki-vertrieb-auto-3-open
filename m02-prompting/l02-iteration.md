# Lab 2.2: Im Dialog nachschärfen

**Leitfragen:**

<details>
<summary>Wie geht ein Gespräch weiter, wenn die erste Antwort nicht ganz passt?</summary>

Es wird gesagt, was fehlt oder stört, statt von vorn anzufangen. Im KI-Chat genauso: Der bisherige Verlauf bleibt erhalten, die Nachbesserung baut darauf auf.

</details>

<details>
<summary>Was ist schneller: neu anfangen oder gezielt nachbessern?</summary>

Meist gezielt nachbessern. Neu anfangen lohnt sich nur, wenn die Richtung grundsätzlich falsch ist oder sich im Verlauf Widersprüche angesammelt haben.

</details>

<details>
<summary>Wann ist ein Entwurf gut genug?</summary>

Wenn jede Aussage stimmt (Produktblatt, keine Erfindungen), nichts zugesagt wird, was niemand zugesagt hat, und der Text ohne weiteren Umbau verschickt werden könnte.

</details>

- Ein Prompt ist selten beim ersten Mal fertig; das Nachschärfen im Dialog gehört zur Methode.
- Jede Nachbesserung nennt genau, was sich ändern soll: kürzer, anderer Ton, Beispiel, Tabelle.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| Nachschärfen | im selben Chat eine gezielte Änderung verlangen, statt den ganzen Auftrag neu zu schreiben – wie eine Korrekturanmerkung am Rand |
| Beispiel mitgeben | ein vorhandenes gutes Ergebnis anhängen, an dem sich Aufbau und Ton orientieren sollen – „so klingt das bei uns“ |
| Rückfragen zulassen | die KI auffordern, vor dem Schreiben Fragen zu stellen, statt zu raten |
| Tabellenausgabe | Antwort in Zeilen und Spalten statt Fließtext; lässt sich prüfen, kopieren und in andere Werkzeuge übernehmen |

## Vier Arten, einen Entwurf nachzuschärfen

| Weg | Beispiel im Vertrieb | wann |
| --- | --- | --- |
| eingrenzen | „Kürze auf höchstens 120 Wörter, Inhalt bleibt.“ | zu lang, zu ausführlich |
| Ton anpassen | „Weniger werblich: ohne ‚Wir freuen uns sehr‘, direkter, aber höflich.“ | Floskeln, falsche Tonlage |
| Beispiel mitgeben | „So klingt eine gute Antwort bei uns: … Übernimm Aufbau und Ton, nicht den Inhalt.“ | Hausstil fehlt |
| Rückfragen zulassen | „Stelle mir zuerst drei Fragen, bevor du schreibst.“ | Auftrag ist noch unscharf |

„Rückfragen zulassen“ bauen manche Werkzeuge schon ein. Der Recherche-Assistent „Researcher“ in Microsoft 365 Copilot stellt nach der ersten Frage Rückfragen (Schritt 3 „Clarify“) und beginnt erst danach mit der Arbeit:

![Ablauf von Researcher in Microsoft 365 Copilot in sechs Schritten: Researcher öffnen, Frage stellen, Rückfragen beantworten (Clarify), arbeiten lassen, Bericht erhalten, weiterarbeiten](https://learn.microsoft.com/en-us/copilot/media/researcher-agent/researcher-agent-workflow.png)
_Quelle: Microsoft Learn, „What is Researcher Agent in Microsoft Copilot?“ (https://learn.microsoft.com/en-us/copilot/manage/researcher-agent), © Microsoft, abgerufen am 22.11.2026._

## Ablauf vom ersten Entwurf zur fertigen Antwort

```text
Prompt ──► Entwurf ──► prüfen ──► Änderung ──► neuer Entwurf ──► …
                                                         │
                          gut genug? ──► Prompt mit allen Änderungen als v2 in meine-prompts.md
```

- Wenige, klar benannte Änderungen pro Runde: So bleibt sichtbar, was gewirkt hat.
- Am Ende wandern die Änderungen in den Prompt selbst, damit das nächste Mal eine Runde reicht.
- Neu anfangen, wenn nach drei Runden noch Fakten fehlen (Information nachliefern) oder jede Korrektur einen neuen Fehler erzeugt (Verlauf widersprüchlich).

## Ausgabe als Tabelle anfordern

Fließtext ist für Menschen, Tabellen sind zum Prüfen und Weiterverarbeiten: Jede Zeile ist ein Datensatz, jede Spalte ein Feld. Das wird ab Lab 3.2 wichtig, wenn Lead-Listen aus dem Chat ins Übungs-CRM Notion wandern.

| Regel | Beispiel |
| --- | --- |
| Spalten genau benennen und in der gewünschten Reihenfolge | „Spalten: Kundenfrage \| Antwort \| Quelle im Produktblatt“ |
| eine Zeile je Datensatz | „eine Zeile je Frage der Anfrage“ |
| leere Felder sichtbar machen statt raten | „Steht etwas nicht im Produktblatt, schreibe ‚nicht im Produktblatt‘.“ |
| nur die Tabelle ausgeben | „Gib nur die Tabelle aus, ohne Einleitung.“ |

Die Spalte „Quelle“ macht die Prüfung schnell: Jede Antwort lässt sich mit einem Blick ins Produktblatt bestätigen. So sieht eine Tabellenausgabe im Chat aus (hier Le Chat von Mistral); über der Tabelle stehen Schaltflächen zum Kopieren und Herunterladen:

![Le Chat von Mistral: Eine lange Beschreibung in Fließtext wird als Tabelle mit den Spalten „Category“ und „Highlights“ zusammengefasst; rechts über der Tabelle Symbole zum Kopieren und Herunterladen](https://upload.wikimedia.org/wikipedia/commons/thumb/a/a9/Le_Chat_chatbot_memories_screenshot.webp/500px-Le_Chat_chatbot_memories_screenshot.webp)
_Quelle: Wikimedia Commons, „Le Chat chatbot memories screenshot.webp“ (https://commons.wikimedia.org/wiki/File:Le_Chat_chatbot_memories_screenshot.webp), Screenshot VulcanSphere, Software Mistral AI, gemeinfrei, abgerufen am 22.11.2026._

## Übung: Antwort nachschärfen und als Tabelle ausgeben

**Material:** Chat aus Lab 2.1, eigene `meine-prompts.md`, Beispielmail unten · **Werkzeug:** KI-Assistent, Texteditor

**Ausgangslage:** Die Antwort an die Kanzlei aus Lab 2.1 ist inhaltlich richtig, aber noch nicht im Nordwind-Stil. Für die interne Prüfung soll zusätzlich jede Antwort mit ihrer Quelle im Produktblatt in einer Tabelle stehen.

**Beispielmail zum Kopieren**

```text
Betreff: Ihre Anfrage – Raumdisplays für 8 Räume
Guten Tag Herr Mühlbach,
danke für Ihre Anfrage. Kurz zu Ihren Punkten:
- Nordwind Panel 10 zeigt an jeder Tür, ob der Raum frei ist.
- Gebucht wird weiter über Outlook, ohne neues Programm.
Nächster Schritt: ein Telefonat von 15 Minuten. Passt Ihnen Mittwoch um 9 Uhr?
Viele Grüße
Lena Hoffmann
```

1. Öffne den Chat aus Lab 2.1 mit der Antwort auf Prompt-Karte 2.1b (fehlt er, sende 2.1b mit Produktblatt und Anfrage in einem neuen Chat) und sende Prompt-Karte 2.2a.
2. Sende Prompt-Karte 2.2b und füge die Beispielmail darunter ein.
3. Sende Prompt-Karte 2.2c und prüfe zwei Zeilen der Tabelle im Produktblatt.
4. Sende Prompt-Karte 2.2d und kopiere den neuen Prompt als „Antwort auf eine Kundenanfrage (v2)“ in `meine-prompts.md`; speichere die Datei.

**Prompt-Karte 2.2a – Kürzer und sachlicher**

```text
Kürze die Antwort auf höchstens 120 Wörter. Alle vier Fragen bleiben beantwortet, der nächste Schritt bleibt gleich. Der Ton ist noch zu werblich: Streiche Floskeln wie „Wir freuen uns sehr" und „innovativ", schreibe direkt und höflich, Anrede „Guten Tag Frau Lindqvist".
```

**Prompt-Karte 2.2b – Beispiel mitgeben**

```text
So klingt eine gute Antwort bei uns. Übernimm Aufbau und Ton dieses Beispiels, nicht seinen Inhalt:

[Beispielmail einfügen]
```

**Prompt-Karte 2.2c – Tabelle**

```text
Erstelle für die interne Prüfung eine Tabelle mit den Spalten: Kundenfrage | Antwort | Quelle im Produktblatt. Eine Zeile je Frage der Anfrage. Steht etwas nicht im Produktblatt, schreibe „nicht im Produktblatt". Gib nur die Tabelle aus.
```

**Prompt-Karte 2.2d – Verbesserter Prompt**

```text
Schreibe meinen ersten Prompt aus diesem Chat (Rolle, Aufgabe, Kontext, Format, Rahmenbedingungen) so um, dass alle Änderungswünsche aus diesem Chat schon darin stehen. Ergänze, dass eine Beispielmail für Aufbau und Ton angehängt wird. Ersetze die Kundin durch [Ansprechperson] und die Anfrage durch [Anfrage]. Gib nur den Prompt in einem Textblock aus.
```

**Checkpoint:** Der Chat zeigt eine Antwort mit höchstens 120 Wörtern im Aufbau der Beispielmail und eine Tabelle mit vier Zeilen und drei Spalten; `meine-prompts.md` enthält den Prompt als v2 mit Platzhaltern.

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Beispiel aus ChatGPT, gekürzt – KI-Antworten fallen jedes Mal etwas anders aus.

**1.–2. Antwort nach zwei Nachbesserungen** (rund 95 Wörter)

> Betreff: Ihre Anfrage – Videokonferenzen und Raumbuchung für 5 Räume
>
> Guten Tag Frau Lindqvist,
>
> danke für Ihre Anfrage. Kurz zu Ihren Punkten:
> - Nordwind Vista funktioniert mit Microsoft Teams, angeschlossen per USB-C am Laptop.
> - Die Buchungsdaten liegen in Frankfurt am Main (EU).
> - Lieferung und Installation in der Regel innerhalb von zwei Wochen nach Auftrag.
> - Den Preis stellen wir in einem Angebot zusammen, sobald Raumgrößen und Ausstattung geklärt sind.
>
> Nächster Schritt: ein Telefonat von 15 Minuten. Passt Ihnen Dienstag um 10 Uhr oder Donnerstag um 14 Uhr?
>
> Viele Grüße
> Lena Hoffmann

**3. Tabelle**

| Kundenfrage | Antwort | Quelle im Produktblatt |
| --- | --- | --- |
| Funktioniert die Kamera mit Microsoft Teams? | Ja, Vista und Vista Plus arbeiten mit Teams, Zoom und Google Meet. | Abschnitt „Nordwind Vista und Vista Plus“, Zeile „Kompatibel mit“ |
| Wo liegen die Buchungsdaten? | In einem Rechenzentrum in Frankfurt am Main (EU). | Abschnitt „Nordwind Book“ |
| Wie schnell Lieferung und Installation? | In der Regel innerhalb von zwei Wochen nach Auftrag, ca. zwei Stunden pro Raum. | Abschnitt „Installation“ |
| Was kostet das für 5 Räume? | Angebot nach dem Telefonat. | nicht im Produktblatt |

Geprüft: Zeilen 2 und 3 stimmen wörtlich mit dem Produktblatt überein.

**4. Prompt v2 für `meine-prompts.md`**

```text
Rolle: Du bist Vertriebsmitarbeiterin im Innendienst bei Nordwind Workspace, einem Anbieter von Lösungen für Besprechungsräume.
Aufgabe: Beantworte die Kundenanfrage von [Ansprechperson] unten.
Kontext: Produktblatt und eine Beispielmail sind angehängt. Ziel der Antwort ist ein Telefonat von 15 Minuten, um den Bedarf zu klären.
Format: Betreff mit Inhalt, Anrede „Guten Tag …", ein Satz Dank, je Frage ein Stichpunkt in der Reihenfolge der Anfrage, genau ein nächster Schritt mit zwei Terminvorschlägen, Gruß mit Lena Hoffmann.
Rahmenbedingungen: Deutsch, Sie-Form, höchstens 120 Wörter. Aufbau und Ton wie die Beispielmail, deren Inhalt nicht übernehmen. Keine Floskeln wie „Wir freuen uns sehr" oder „innovativ". Keine Preise und keine Rabatte; zum Preis ein Angebot nach dem Telefonat anbieten. Angaben nur aus dem Produktblatt.

Anfrage:
[Anfrage]
```

Warum gut: Beide Nachbesserungen stecken jetzt im Prompt; bei der nächsten Anfrage reicht eine Runde. Die Tabelle zeigt auf einen Blick, welche Aussage woher stammt.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Antwort übernimmt Inhalte der Beispielmail (Herr Mühlbach, 8 Räume) | Hinweis „nicht den Inhalt“ fehlt | Prompt-Karte 2.2b vollständig senden |
| Tabelle erfindet eine Quelle für den Preis | Regel für fehlende Angaben fehlt | „Steht etwas nicht im Produktblatt …“ nachschicken |
| jede Runde wird schlechter | viele Änderungen auf einmal verlangt | höchstens ein bis zwei klar benannte Änderungen pro Nachricht |

## Fazit

- Nachschärfen ist schneller als neu anfangen, solange die Richtung stimmt.
- Ein mitgegebenes Beispiel ersetzt viele Sätze Stilbeschreibung.
- Eine Tabelle mit festen Spalten und Quellenspalte macht Ergebnisse prüfbar und weiterverwendbar.

> **Merksatz:** Nicht „mach es besser“, sondern „ändere genau das“.
