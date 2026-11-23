# Lab 1.2: Wie ein Sprachmodell antwortet und wo es irrt

**Leitfragen:**

<details>
<summary>Wie schlägt die Smartphone-Tastatur das nächste Wort vor?</summary>

Sie hat gelernt, welche Wörter oft aufeinander folgen, und zeigt die wahrscheinlichsten an. Ein Sprachmodell macht im Prinzip dasselbe, nur mit unvorstellbar viel mehr Text und über ganze Antworten hinweg.

</details>

<details>
<summary>Woher sollte ein Programm wissen, was ein Kunde gestern veröffentlicht hat?</summary>

Von selbst gar nicht: Das gelernte Wissen endet an einem Stichtag. Aktuelles kommt nur über eine Websuche oder über Text, den der Mensch mitgibt.

</details>

<details>
<summary>Wirkt eine selbstbewusst formulierte Antwort glaubwürdiger – zu Recht?</summary>

Sie wirkt glaubwürdiger, aber zu Unrecht. Ein Sprachmodell formuliert richtige und erfundene Aussagen im gleichen sicheren Ton.

</details>

- Ein Sprachmodell schreibt Wort für Wort die plausibelste Fortsetzung, nicht die geprüft richtige.
- Daraus folgen drei Grenzen: erfundene Fakten, Wissen mit Stichtag, jede Antwort etwas anders.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| Training | Lernphase vor der Nutzung: Das Modell liest riesige Textmengen und lernt, welche Wörter zusammenpassen |
| Wissensstichtag | Datum, bis zu dem die Trainingstexte reichen; danach weiß das Modell von selbst nichts mehr – wie ein Lexikon mit Druckdatum |
| Halluzination | überzeugend klingende, aber erfundene Aussage, z. B. ein Produkt, ein Preis oder eine Quelle, die es nicht gibt |
| Websuche | Funktion des KI-Assistenten: sucht vor der Antwort im Internet und nennt die Fundstellen als Quellen |

## Wie ein Sprachmodell Text erzeugt

Die Smartphone-Tastatur schlägt über den Tasten Wörter vor, die gut zum bisher Getippten passen:

![Smartphone mit Tastatur: im Textfeld der Satz „This is an example of T9 on an LG V60, August 2020. T9 is initiated“, darüber eine Vorschlagsleiste mit „initiated“, „initiates“ und „initialed“; Satzende und Vorschlagsleiste sind rot eingekreist](https://upload.wikimedia.org/wikipedia/commons/thumb/4/46/T9_on_an_LG_in_2020.png/330px-T9_on_an_LG_in_2020.png)
_Quelle: Wikimedia Commons, „T9 on an LG in 2020.png“ (https://commons.wikimedia.org/wiki/File:T9_on_an_LG_in_2020.png), TS6, CC BY-SA 4.0, abgerufen am 22.11.2026._

Ein Sprachmodell arbeitet nach demselben Prinzip, hängt den Vorschlag aber selbst an und macht weiter, bis eine ganze Antwort steht:

```text
Prompt: „Nordwind Panel 10 ist ein ..."
          │
          ▼
Modell wählt das plausibelste nächste Wort:  „Raumdisplay" → „," → „das" → „an" → „der" → „Tür" …
          │
          ▼
Antwort: „Nordwind Panel 10 ist ein Raumdisplay, das an der Tür zeigt, ob der Raum frei ist."
```

Ob die Antwort stimmt, prüft das Modell dabei nicht. Kennt es Nordwind nicht (weil kein Produktblatt im Chat liegt), schreibt es trotzdem etwas Plausibles.

## Drei Grenzen und ihre Folgen im Vertrieb

| Grenze | Warum | Beispiel im Vertrieb | Gegenmittel |
| --- | --- | --- | --- |
| erfundene Fakten (Halluzination) | das Modell wählt Plausibles, es schlägt nichts nach | erfundener Listenpreis, erfundene Referenz, falscher Firmensitz | eigene Unterlagen mitgeben, Fakten prüfen, Quellen verlangen |
| Wissen mit Stichtag | Training endet an einem Datum | „aktuelle“ Meldung eines Interessenten ist ein Jahr alt | Websuche einschalten oder anfordern |
| jede Antwort etwas anders | bei jedem Wort ist etwas Zufall im Spiel | dieselbe Mail zweimal angefragt, zwei Fassungen | gutes Ergebnis sofort sichern (ab Lab 2.1 in einer eigenen Notizdatei) |

Ein bekanntes Beispiel: ChatGPT bekommt 2023 nur den Link zu einem Zeitungsartikel, kann ihn ohne Websuche nicht öffnen und erfindet aus den Wörtern im Link eine flüssige Zusammenfassung.

![ChatGPT-Chat: Auf die Bitte, einen Artikel der New York Times anhand der Webadresse zusammenzufassen, liefert ChatGPT eine sachlich klingende Zusammenfassung eines Artikels, den es nie gelesen hat](https://upload.wikimedia.org/wikipedia/commons/thumb/3/3a/ChatGPT_hallucination.png/500px-ChatGPT_hallucination.png)
_Quelle: Wikimedia Commons, „ChatGPT hallucination.png“ (https://commons.wikimedia.org/wiki/File:ChatGPT_hallucination.png), gemeinfrei, Ansicht März 2023, abgerufen am 22.11.2026._

## Websuche mit Quellen gegen veraltetes Wissen

Mit Websuche sucht der Assistent vor der Antwort im Internet und hängt an Aussagen einen Quellenverweis. Das hilft bei allem, was aktuell sein muss: Meldungen eines Interessenten, neue Produkte eines Wettbewerbers, Zahlen aus einem Geschäftsbericht.

Perplexity sucht bei jeder Frage im Web und zeigt die Fundstellen über der Antwort; kleine Ziffern im Text verweisen auf die jeweilige Quelle:

![Perplexity-Antwort auf „What is Vilnius?“: oben ein Bereich „Sources“ mit drei Quellen-Kacheln (Wikipedia, Britannica, Simple English Wikipedia), darunter „Answer“ mit einer Faktentabelle und Fließtext mit kleinen Quellenziffern](https://upload.wikimedia.org/wikipedia/commons/thumb/6/6d/Screenshot_of_Perplexity_-_What_is_Vilnius_%282024%29.png/960px-Screenshot_of_Perplexity_-_What_is_Vilnius_%282024%29.png)
_Quelle: Wikimedia Commons, „Screenshot of Perplexity – What is Vilnius (2024).png“ (https://commons.wikimedia.org/wiki/File:Screenshot_of_Perplexity_-_What_is_Vilnius_(2024).png), gemeinfrei, Ansicht Juli 2024, abgerufen am 22.11.2026._

In ChatGPT steht die Websuche im Werkzeug-Menü am Eingabefeld, in der Ansicht 2025 als „Search – Find on the web“; „Auto“ bedeutet, dass ChatGPT selbst entscheidet, wann es sucht:

![ChatGPT-Menü am Eingabefeld: unter „Sources“ der Eintrag „Search – Find on the web“ mit dem Zusatz „Auto“, darunter unter „Tools“ Canvas, Create image und Deep research](https://images.ctfassets.net/j22is2dtoxu1/intercom-img-ca4f4e49315f4f902b229090/9ef22100e167e3155a2b88796257de87/Screenshot_2025-04-28_at_14_49_38.png)
_Quelle: OpenAI Help Center, „Searching the web with ChatGPT“ (https://help.openai.com/en/articles/9237897-chatgpt-search), © OpenAI, Ansicht April 2025, abgerufen am 22.11.2026._

| Assistent | Websuche steuern (Stand: 22.11.2026, Bezeichnung je nach Version) |
| --- | --- |
| ChatGPT | Werkzeug-Menü am Eingabefeld → „Search“ oder `/` im Eingabefeld; sucht sonst selbst, wenn es sinnvoll ist |
| Claude | „+“ → „Web search“; in der neuen Oberfläche sucht Claude selbst |
| Perplexity | sucht immer |
| Microsoft 365 Copilot | Websuche legt die Firma per Einstellung fest („Allow web search in Copilot“) |

- Der Satz „Suche im Web“ im Prompt stellt die Suche sicher, „Antworte ohne Websuche“ schließt sie aus (außer in Perplexity).
- Auch mit Quelle kann eine Aussage falsch wiedergegeben sein: wichtige Angaben an der Quelle selbst nachlesen. OpenAI schreibt dazu selbst, Suchergebnisse und Zitate können unvollständig, veraltet oder falsch sein.

_Quellen: OpenAI (Link oben); Anthropic, „Enabling and using web search“ (https://support.claude.com/en/articles/10684626-enabling-and-using-web-search); Microsoft Learn, „Microsoft 365 Copilot Chat overview“ (https://learn.microsoft.com/en-us/copilot/overview); abgerufen am 22.11.2026._

## Übung: Drei Grenzen sichtbar machen

**Material:** keines · **Werkzeug:** KI-Assistent

**Ausgangslage:** Bevor der KI-Assistent im Nordwind-Vertrieb Texte für Kunden schreibt, soll sichtbar werden, wo er irrt. Drei kurze Tests reichen dafür.

1. Öffne einen neuen Chat und sende Prompt-Karte 1.2a; öffne einen zweiten neuen Chat und sende dieselbe Karte noch einmal. Vergleiche beide Antworten.
2. Öffne einen neuen Chat und sende Prompt-Karte 1.2b (ohne Websuche). Mit Perplexity (sucht immer im Web): teste 1.2b und 1.2d in einem zweiten Assistenten ohne Websuche oder lies dazu das Musterergebnis.
3. Sende im selben Chat Prompt-Karte 1.2c (mit Websuche) und öffne eine der angezeigten Quellen.
4. Öffne einen neuen Chat und sende Prompt-Karte 1.2d. Das Produkt darin gibt es nicht (Stand: 22.11.2026).

**Prompt-Karte 1.2a – Dieselbe Frage zweimal**

```text
Erkläre in drei Sätzen, warum Unternehmen ein System zur Buchung von Besprechungsräumen einführen.
```

**Prompt-Karte 1.2b – Aktuelles ohne Websuche**

```text
Antworte ohne Websuche, nur aus deinem eigenen Wissen: Welche neuen Konferenzkameras für Besprechungsräume hat Logitech im Jahr 2026 vorgestellt? Nenne Produktnamen und Monat der Ankündigung.
```

**Prompt-Karte 1.2c – Aktuelles mit Websuche**

```text
Suche jetzt im Web und beantworte dieselbe Frage noch einmal. Nenne zu jeder Angabe die Quelle mit Link.
```

**Prompt-Karte 1.2d – Ein Produkt, das es nicht gibt**

```text
Antworte ohne Websuche: Was kann die Konferenzkamera „Logitech Rally Horizon 360"? Nenne die drei wichtigsten Funktionen und den Listenpreis in Euro.
```

**Checkpoint:** Zwei Chats zeigen zwei unterschiedlich formulierte Antworten auf 1.2a; die Antwort auf 1.2c enthält Links, die auf 1.2b nicht; zu 1.2d liegt eine Antwort vor, die entweder Nichtwissen zugibt oder Funktionen und Preis erfindet.

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Beispiel, gekürzt – KI-Antworten fallen jedes Mal etwas anders aus.

**1. Dieselbe Frage zweimal**

| Chat 1 | Chat 2 |
| --- | --- |
| „Unternehmen führen Raumbuchungssysteme ein, um Doppelbuchungen zu vermeiden. Mitarbeitende sehen auf einen Blick, welcher Raum frei ist. Außerdem zeigen die Daten, welche Räume kaum genutzt werden.“ | „Ohne System sind Räume oft doppelt belegt oder gebucht und dann leer. Ein Buchungssystem schafft Übersicht und spart Zeit bei der Suche. Viele Systeme liefern zudem Auswertungen zur Auslastung.“ |

Gleicher Kern, andere Worte: Ein gutes Ergebnis wird gesichert, nicht neu angefragt.

**2. Ohne Websuche**

> Mein Wissen reicht nur bis zu einem bestimmten Stichtag, deshalb kann ich Ankündigungen aus 2026 nicht sicher nennen. Bekannt sind mir Modelle der Rally-Reihe wie Rally Bar und Rally Bar Mini …

Ebenfalls möglich und kritischer: eine Liste „neuer“ Produkte ohne Quelle, die in Wahrheit älter oder erfunden sind.

**3. Mit Websuche**

> Im Januar 2026 hat Logitech die Rally AI Camera und die Rally AI Camera Pro angekündigt, mit automatischer Bildauswahl für Sprecher und Gruppen. [Quelle: Meldung vom 22.01.2026]

Die geöffnete Quelle bestätigt Datum und Produktnamen (Hardware Busters, „Logitech Unveils Rally AI Cameras for Large Meeting Spaces“, 22.01.2026, https://hwbusters.com/news/logitech-unveils-rally-ai-cameras-for-large-meeting-spaces/, abgerufen am 22.11.2026).

**4. Ein Produkt, das es nicht gibt**

| gutes Verhalten | Halluzination |
| --- | --- |
| „Eine Kamera mit dem Namen ‚Rally Horizon 360‘ ist mir nicht bekannt. Möglicherweise ist ein anderes Modell der Rally-Reihe gemeint …“ | „Die Logitech Rally Horizon 360 bietet 1. ein 360-Grad-Panorama, 2. KI-gestütztes Sprecher-Framing, 3. integrierte Mikrofone mit Geräuschunterdrückung. Listenpreis: 2.799 €.“ |

Warum wichtig: Beide Antworten klingen gleich sicher. Nur die Prüfung (Websuche, Herstellerseite) zeigt, welche stimmt.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Beide Antworten auf 1.2a sind identisch | zweite Frage im selben Chat gestellt | wirklich einen neuen Chat öffnen |
| 1.2b liefert trotzdem Quellen | Assistent hat selbst gesucht (Perplexity immer) | Satz „Antworte ohne Websuche“ am Anfang lassen; Websuche im Menü ausschalten |
| Quelle passt nicht zur Aussage | Aussage falsch wiedergegeben | Aussage nur übernehmen, wenn sie in der Quelle steht |

## Fazit

- Ein Sprachmodell setzt Text mit der plausibelsten Fortsetzung fort; Wahrheit prüft es nicht.
- Erfundene Fakten, Wissensstichtag und wechselnde Antworten folgen direkt daraus.
- Websuche und eigene Unterlagen sind die Gegenmittel; geprüft wird trotzdem.

> **Merksatz:** Plausibel ist nicht richtig.
