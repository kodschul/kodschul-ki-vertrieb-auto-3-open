# Lab 12.3: Präsentation eigener Lösungsvorschläge

**Leitfragen:**

<details>
<summary>Was muss in den ersten 30 Sekunden einer Präsentation klar sein?</summary>

Welches Problem gelöst wird, mit einer Zahl von heute, und welche Entscheidung am Ende erbeten wird. Wer das nach 30 Sekunden nicht weiß, hört dem Rest nur halb zu.

</details>

<details>
<summary>Welcher Einwand kommt von der Geschäftsführung garantiert?</summary>

„Was kostet das, und was bringt es?“, kurz danach „Was ist mit dem Datenschutz?“ und „Was, wenn die KI Fehler macht?“. Die Antworten stehen im Business Case aus Lab 12.2.

</details>

<details>
<summary>Was wäre ein guter erster Schritt am Montag?</summary>

Ein Schritt, der ohne Budget geht: Ausgangswert messen, mit Datenschutz und IT sprechen, Termin für die Entscheidung über den Pilot anfragen.

</details>

- Drei Minuten entlang der Kette: Problem, Konzept, Nutzen, nächster Schritt; die drei Folien aus Lab 12.2 tragen die Struktur.
- Rückmeldung nach drei festen Kriterien: Nutzen klar, machbar, Risiken bedacht.

## Aufbau einer 3-Minuten-Präsentation

| Zeit | Teil | Inhalt | Folie aus 12.2 |
| --- | --- | --- | --- |
| 0:00–0:30 | Problem | Problem in einem Satz, eine Zahl von heute, die erbetene Entscheidung | 1 |
| 0:30–1:30 | Konzept | Ablauf in 4–6 Schritten, Stelle der Freigabe; Prototyp zeigen, wenn vorhanden | 2 |
| 1:30–2:30 | Nutzen | Rechenweg, Kosten, wichtigstes Risiko mit Gegenmaßnahme, Pilot mit Kennzahl | 3 |
| 2:30–3:00 | nächster Schritt | Bitte um Entscheidung, erster Schritt am Montag | 3 |

Beispiel für die erste und die letzte Folie (fiktiver Fall aus Lab 12.1 und 12.2):

```text
Folie 1 – Neuanfragen warten zwei Tage auf Antwort
  120 Anfragen pro Monat, 15 Minuten Handarbeit je Anfrage
  Neuanfragen gehen zwischen Ersatzteil und Service unter
  ► 2 Werktage bis zur Antwort
  Sprechtext: „Ich bitte heute um Freigabe für einen sechswöchigen Pilot.“

Folie 3 – 6 Wochen Pilot, danach Entscheidung
  Nutzen 11.880 € pro Jahr (0,15 h × 1.440 × 55 €)
  Kosten Jahr 1: 3.060 €, Datenschutz vor Start geklärt
  Ziel: Antwort auf Neuanfragen in 4 Stunden
  ► Montag: Ausgangswert messen, Termin mit Datenschutz
```

## Einwände der Geschäftsführung

| Einwand | Antwort aus dem eigenen Material |
| --- | --- |
| „Was kostet das, was bringt es?“ | Business Case: Rechenweg, Kosten Jahr 1 und ab Jahr 2 |
| „Was ist mit dem Datenschutz?“ | Risiken: Rechtsgrundlage, AVV, keine Namen an die KI, Speicherorte (Lab 11.1) |
| „Was, wenn die KI Fehler macht?“ | Freigabe vor jedem Kundenkontakt, Testfälle, Gleichbehandlungstest (Lab 11.3) |
| „Haben wir dafür Zeit?“ | kleiner Pilot, ein Team, Enddatum, Entscheidung danach |
| „Machen das andere schon?“ | Zahl von Eurostat, Bild unten |

![Eurostat-Balkendiagramm „Type of AI technology used by enterprises in the EU, 2024 and 2025“: vorn Analyse geschriebener Sprache (2025 knapp 12 %), Erzeugen von Bildern und Audio (knapp 10 %), Erzeugen von Text oder Sprache (knapp 9 %); Automatisieren von Abläufen oder Unterstützung bei Entscheidungen bei gut 5 %](https://ec.europa.eu/eurostat/o/adaptive-media/image/22691503/Preview-1000x0/ai-tecnhologies-used-eu-enterprises-2024-2025.jpg)
_Quelle: Eurostat, „20% of EU enterprises use AI technologies“, 11.12.2025 (https://ec.europa.eu/eurostat/web/products-eurostat-news/w/ddn-20251211-2), © Europäische Union, Weiterverwendung mit Quellenangabe, abgerufen am 22.11.2026._

2025 nutzte jedes fünfte Unternehmen in der EU KI, aber nur gut 5 % automatisierten damit Abläufe: Wer jetzt einen Workflow-Pilot startet, ist früh dran.

## Rückmeldung nach drei Kriterien

| Kriterium | Frage | erkennbar an |
| --- | --- | --- |
| Nutzen klar | Ist nach der Präsentation klar, was besser wird und um wie viel? | Problem mit Ausgangswert, Rechenweg, eine Zielzahl |
| machbar | Lässt sich der Pilot mit vorhandenen Systemen und Leuten in 6–8 Wochen umsetzen? | höchstens 8 Knoten, verantwortliche Person, CRM-Anbindung geklärt |
| Risiken bedacht | Sind Datenschutz, Fehler und Akzeptanz mit Gegenmaßnahme genannt? | Freigabepunkt, keine Namen an die KI, Testfälle |

Jede Rückmeldung nennt je Kriterium einen Punkt, der überzeugt hat, oder eine Frage, die offen blieb.

## Übung: Business Case präsentieren

**Material:** Notion-Seite „Business Case – …“ aus Lab 12.1 und 12.2 · **Werkzeug:** Notion, Bildschirmfreigabe, optional n8n

**Ausgangslage:** Jede Person stellt ihren Business Case mit Workflow-Konzept in drei Minuten im Plenum vor; die Gruppe gibt Rückmeldung nach den drei Kriterien.

1. Öffne die Notion-Seite und ordne die drei Folientexte nach dem Aufbau oben; ergänze auf Folie 1 die erbetene Entscheidung und auf Folie 3 den ersten Schritt am Montag.
2. Präsentiere in drei Minuten und zeige, wenn vorhanden, den Prototyp in n8n.
3. Trage die Rückmeldungen der Gruppe in die Tabelle „Rückmeldung“ auf der Notion-Seite ein (Kriterium, Punkt, Änderung).

**Checkpoint:** Die Notion-Seite enthält drei Folientexte in der Reihenfolge Problem, Konzept, Nutzen und nächster Schritt sowie eine ausgefüllte Rückmeldungstabelle mit drei Zeilen.

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Fiktiver Fall aus Lab 12.1 und 12.2; Rückmeldungen als Beispiel.

| Kriterium | Punkt aus der Gruppe | Änderung |
| --- | --- | --- |
| Nutzen klar | Rechenweg auf Folie 3 sofort nachvollziehbar; offen: wie die 2 Werktage gemessen wurden | Ausgangswert ab Montag zwei Wochen im CRM messen |
| machbar | Formular und CRM vorhanden, fünf Knoten; offen: wer den Workflow im Urlaub betreut | Vertretung im Pilotplan eintragen |
| Risiken bedacht | Name und E-Mail gehen nicht an die KI, Freigabe durch Innendienst; offen: Hinweis für Kunden | Transparenzhinweis im Formular wie in Lab 11.2 |

Erster Schritt am Montag: Ausgangswert messen und Termin mit dem Datenschutz anfragen.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| nach drei Minuten erst bei der Technik | Konzept-Teil mit Knotendetails überladen | Ablauf in 4–6 Schritten, Knoten nur im Prototyp zeigen |
| Zuhörende fragen „Und was soll ich jetzt entscheiden?“ | keine erbetene Entscheidung genannt | Bitte auf Folie 1 und Folie 3 |
| Zahl wird angezweifelt | Rechenweg fehlt auf der Folie | Rechnung in einer Zeile zeigen, Annahmen benennen |

## Fazit

- In den ersten 30 Sekunden: Problem, Zahl, erbetene Entscheidung.
- Die Antworten auf die Einwände stehen schon im Business Case; die Präsentation zeigt sie nur in der richtigen Reihenfolge.
- Rückmeldung nach festen Kriterien macht Vorschläge vergleichbar und verbessert den nächsten Schritt.

> **Merksatz:** Ein Problem, eine Zahl, eine Bitte – und ein Schritt für Montag.
