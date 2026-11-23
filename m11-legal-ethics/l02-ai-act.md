# Lab 11.2: EU AI Act und Transparenz

**Leitfragen:**

<details>
<summary>Sollte ein Kunde erfahren, dass seine Anfrage von einer KI vorsortiert wurde?</summary>

Ja, ein kurzer Hinweis schafft Vertrauen und erfüllt die Informationspflicht der DSGVO (Art. 13). Ein Chatbot muss sich nach dem AI Act ohnehin als KI zu erkennen geben.

</details>

<details>
<summary>Wer im Team weiß, welche KI-Werkzeuge im Vertrieb im Einsatz sind?</summary>

Oft niemand vollständig. Der AI Act verlangt Maßnahmen zur KI-Kompetenz der Mitarbeitenden (Art. 4); dafür braucht es zuerst eine Liste der Werkzeuge und Workflows mit Verantwortlichen.

</details>

<details>
<summary>Ist ein Werkzeug, das Leads bewertet, so riskant wie eines, das über Kredite entscheidet?</summary>

Nein. Die Kreditwürdigkeitsprüfung von Privatpersonen ist im AI Act Hochrisiko, Lead-Scoring von Firmen nicht. Die DSGVO-Regeln aus Lab 11.1 gelten trotzdem.

</details>

- Der EU AI Act regelt KI nach Risiko: je mehr eine KI über Menschen entscheidet, desto strenger die Pflichten.
- Für den Vertrieb zählen vor allem zwei Pflichten: KI-Kompetenz im Team (seit 02.02.2025) und Transparenz bei KI-Chats und KI-Inhalten (seit 02.08.2026).

Keine Rechtsberatung. Stand: 22.11.2026, vor Kursbeginn prüfen.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| EU AI Act | Verordnung (EU) 2024/1689, das KI-Gesetz der EU; seit 01.08.2024 in Kraft, gilt direkt in allen EU-Staaten |
| Anbieter | wer ein KI-System entwickelt und unter eigenem Namen anbietet, z. B. OpenAI für ChatGPT, Microsoft für Copilot |
| Betreiber | wer ein KI-System beruflich einsetzt, z. B. Nordwind mit dem Lead-Eingang |
| KI-Kompetenz | Wissen und Fähigkeiten, KI sachkundig und verantwortungsvoll einzusetzen (Art. 4) |
| Deepfake | KI-erzeugtes oder -verändertes Bild, Video oder Audio, das echte Personen, Orte oder Ereignisse zeigt und echt wirkt |
| Digital Omnibus zur KI | Änderungsverordnung (EU) 2026/1744, die Fristen des AI Act verschiebt und einzelne Pflichten vereinfacht |

## Vier Risikostufen des AI Act

![Risikopyramide des EU AI Act mit vier Stufen von oben nach unten: Unacceptable risk (rot), High risk (magenta), Limited risk – AI systems with specific transparency obligations (violett) und Minimal risk (türkis, breite Basis)](https://ec.europa.eu/information_society/newsroom/image/document/2021-17/pyramid_7F5843E5-9386-8052-931F5C4E98C6E5F2_75757.jpg)
_Quelle: Europäische Kommission, „AI Act“ (https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai), Seite Stand 19.10.2026, abgerufen am 22.11.2026._

| Stufe | Beispiele | Beispiele aus Vertrieb und Marketing | Folge |
| --- | --- | --- | --- |
| verboten | Social Scoring, manipulative Techniken, die Schwächen ausnutzen und erheblich schaden | KI, die gezielt Notlagen oder das Alter von Kunden ausnutzt, um zum Kauf zu drängen | darf nicht eingesetzt werden (Art. 5) |
| hohes Risiko | Bewerberauswahl, Kreditwürdigkeit von Privatpersonen (Anhang III) | Kreditprüfung im Ratenkauf für Verbraucher | strenge Pflichten; für Anhang III ab 02.12.2027 |
| Transparenz | Chatbots, KI-erzeugte Bilder, Videos, Stimmen | Chat auf der Website, KI-Produktfoto, KI-Stimme am Telefon | offenlegen und kennzeichnen (Art. 50) |
| minimal | Spamfilter, Textvorschläge | Lead-Scoring für Firmen, Antwortentwürfe mit Freigabe, Pipeline-Briefing | keine besonderen Pflichten aus dem AI Act; DSGVO gilt |

## KI-Kompetenz im Team nach Art. 4

- Gilt seit 02.02.2025 für alle Unternehmen, die KI beruflich einsetzen, auch für kleine.
- Seit 27.07.2026 durch die Verordnung (EU) 2026/1744 vereinfacht: Unternehmen ergreifen Maßnahmen zur KI-Kompetenz ihres Personals, passend zu Vorwissen und Einsatz; Kommission und Mitgliedstaaten fördern KI-Kompetenz stärker. Ein Zertifikat schreibt Art. 4 nicht vor.
- Praktisch im Vertrieb: Liste der KI-Werkzeuge und Workflows mit verantwortlicher Person (Vorlage: [`workflow-steckbriefe.md`](../material/workflow-steckbriefe.md)), Regeln wie Datenampel (Lab 1.3) und Freigabe, Schulung mit Nachweis.

## Transparenzpflichten nach Art. 50

Art. 50 gilt seit 02.08.2026 und wurde vom Omnibus nicht verschoben.

| Absatz | Pflicht | Wer | Seit |
| --- | --- | --- | --- |
| 50 Abs. 1 | Menschen erkennen, dass sie mit einer KI sprechen oder schreiben, außer es ist offensichtlich | Anbieter des Systems | 02.08.2026 |
| 50 Abs. 2 | KI-erzeugte Texte, Bilder, Audio, Video maschinenlesbar markieren | Anbieter generativer KI | 02.08.2026; Systeme, die schon vor dem 02.08.2026 am Markt waren: bis 02.12.2026 |
| 50 Abs. 3 | über Emotionserkennung informieren | Betreiber | 02.08.2026 |
| 50 Abs. 4 | Deepfakes offenlegen; KI-Texte, die die Öffentlichkeit über Themen von öffentlichem Interesse informieren, kennzeichnen, außer ein Mensch hat sie redaktionell geprüft und verantwortet | Betreiber | 02.08.2026 |

| Fall im Vertrieb | Was gilt | Empfehlung |
| --- | --- | --- |
| KI-Chat auf der eigenen Website | Art. 50 Abs. 1; wer den Chat unter eigenem Namen anbietet, kann selbst Anbieter sein | erste Nachricht: „Hier antwortet ein KI-Assistent“, Weg zu einem Menschen anbieten |
| KI-entworfene Mail an einen Kunden, vom Menschen geprüft | keine Kennzeichnungspflicht aus dem AI Act (kein Text für die Öffentlichkeit) | Verantwortung bleibt beim Absender; Datenschutzhinweis nennt KI-Dienste |
| KI-Bild, das wie ein echtes Foto wirkt (z. B. „Kunde im Besprechungsraum“) | Deepfake nach Abs. 4: offenlegen | Hinweis „KI-generiert“ am Bild, z. B. mit EU-Icon |
| KI-Grafik, Illustration, Symbolbild ohne Echtheitsanspruch | keine Täuschung, keine Offenlegungspflicht als Deepfake | Kennzeichnung trotzdem üblich |
| Anfrage im Formular KI-gestützt vorsortiert | AI Act: minimales Risiko; DSGVO Art. 13: informieren | Hinweis im Formular (Übung unten) |

Für die Kennzeichnung hat die EU-Kommission freiwillige Icons veröffentlicht; Pflicht ist die Kennzeichnung, nicht das Icon:

![EU-Icon zur Kennzeichnung KI-erzeugter Inhalte: schwarzes, abgerundetes Feld mit weißer Schrift „AI GENERATED“](https://upload.wikimedia.org/wikipedia/commons/thumb/e/ed/EU-LABEL_AI_GENERATED_black.svg/500px-EU-LABEL_AI_GENERATED_black.svg.png)
_Quelle: Wikimedia Commons, „EU-LABEL AI GENERATED black.svg“ (https://commons.wikimedia.org/wiki/File:EU-LABEL_AI_GENERATED_black.svg), Europäische Union, gemeinfrei; Original: Europäische Kommission, „EU icons for labelling AI-generated content“ (https://digital-strategy.ec.europa.eu/en/policies/eu-icons-labelling-ai-generated-content), Seite Stand 13.10.2026; abgerufen am 22.11.2026._

## Stand der AI-Act-Änderungen am 22.11.2026

| Status | Inhalt | Datum |
| --- | --- | --- |
| beschlossen, in Kraft | Digital Omnibus zur KI, Verordnung (EU) 2026/1744: Hochrisiko-Pflichten Anhang III auf 02.12.2027, Anhang I auf 02.08.2028 verschoben; Art. 4 vereinfacht; Übergangsfrist für Art. 50 Abs. 2 bis 02.12.2026; neues Verbot von „Nudify“-Apps ab Dezember 2026 | in Kraft seit 27.07.2026 |
| unverändert in Kraft | Transparenzpflichten Art. 50 | seit 02.08.2026 |
| veröffentlicht, freiwillig | Verhaltenskodex zur Kennzeichnung KI-erzeugter Inhalte (Anbieter: Markierung; Betreiber: Deepfakes und Texte), rund 190 Unterzeichner bis Ende Juli 2026 | final veröffentlicht 10.06.2026 |
| veröffentlicht | Leitlinien der Kommission zu den Transparenzpflichten | 20.07.2026 |
| nur vorgeschlagen | Digital Omnibus zu Daten mit Änderungen an der DSGVO (u. a. Art. 22) | Vorschlag 19.11.2025, Verfahren läuft |

_Quellen: Verordnung (EU) 2024/1689 (https://eur-lex.europa.eu/eli/reg/2024/1689/oj); Verordnung (EU) 2026/1744 (https://eur-lex.europa.eu/legal-content/DE/TXT/?uri=OJ:L_202601744); Europäische Kommission, „AI Act“, Stand 19.10.2026 (https://digital-strategy.ec.europa.eu/en/policies/regulatory-framework-ai); „AI Omnibus enters into force“, 27.07.2026 (https://digital-strategy.ec.europa.eu/en/news/ai-omnibus-enters-force); „Code of Practice on marking and labelling of AI-generated content“, Stand 19.10.2026 (https://digital-strategy.ec.europa.eu/en/policies/code-practice-ai-generated-content); Goodwin, „Not Delayed, Not Deferred: EU AI Act Transparency Obligations Are Now in Force“, 03.08.2026 (https://www.goodwinlaw.com/en/insights/publications/2026/08/alerts-technology-dpc-eu-ai-act-transparency-obligations-now-in-force); alle abgerufen am 22.11.2026._

## Übung: Workflows prüfen und Transparenzhinweis setzen

**Material:** [`workflow-steckbriefe.md`](../material/workflow-steckbriefe.md), Prüfliste aus [Lab 11.1](l01-data-protection.md) · **Werkzeug:** KI-Assistent, n8n

**Ausgangslage:** Nordwind betreibt drei Workflows: Lead-Eingang, Gesprächsnotiz und Pipeline-Briefing. Vor dem Einsatz mit echten Anfragen wird geprüft, wo Datenschutz- und Transparenzlücken bestehen; eine Maßnahme wird sofort umgesetzt. Feldnamen in n8n: Bezeichnung je nach Version.

1. Öffne einen neuen Chat und sende Prompt-Karte 11.2a; füge darunter den Inhalt von `workflow-steckbriefe.md` ein (oder Kurzbeschreibungen eigener Workflows ohne rote Daten).
2. Gleiche die Tabelle des Assistenten mit der Prüfliste aus Lab 11.1 und der Tabelle „Transparenzpflichten“ oben ab; streiche Punkte, die der Assistent ohne Beleg behauptet.
3. Sende Prompt-Karte 11.2b, um den Hinweistext für das Formular zu erhalten, und kürze ihn auf höchstens drei Sätze.
4. Öffne in n8n den Lead-Eingang, im Knoten „Lead-Anfrage“ das Feld „Form Description“, und füge den Hinweis unter dem vorhandenen Satz ein. Speichere den Workflow.
5. Öffne die Test-URL des Formulars und prüfe, dass der Hinweis unter dem Titel „Anfrage an Nordwind Workspace“ steht.

**Prompt-Karte 11.2a – Workflows prüfen**

```text
Du prüfst Vertriebs-Workflows auf Datenschutz und Transparenz. Grundlage sind diese Prüfpunkte:
1 Zweck, 2 Rechtsgrundlage, 3 Datenminimierung (nur nötige Felder an KI-Schritte), 4 sensible Daten im Freitext, 5 Auftragsverarbeitungsvertrag je Dienst, 6 Speicherort und Drittland, 7 Information der betroffenen Personen, 8 Mensch entscheidet, 9 Werberecht (keine Werbe-Mail ohne Einwilligung), 10 Speicherdauer, 11 Auskunft und Löschung, 12 Kennzeichnung KI-gestützter Ergebnisse.
Dazu die Transparenzpflichten des EU AI Act, Art. 50: KI-Chats als KI erkennbar; Deepfakes offenlegen; KI-Texte für die Öffentlichkeit kennzeichnen, außer menschlich geprüft.

Aufgabe: Prüfe jeden Workflow unten. Antworte mit einer Tabelle: Workflow | Prüfpunkt | Befund | Maßnahme. Nenne nur Lücken und offene Fragen, keine erfüllten Punkte. Erfinde keine Fakten über die Workflows; was nicht in der Beschreibung steht, markiere als „offen“. Keine Rechtsberatung, sondern Hinweise zur Klärung mit dem Datenschutz.

Workflows:
[Inhalt von workflow-steckbriefe.md einfügen]
```

**Prompt-Karte 11.2b – Hinweis im Formular**

```text
Schreibe für das Website-Formular des Lead-Eingangs einen Hinweis für Interessenten in Sie-Form, höchstens drei Sätze, sachlich und ohne Juristendeutsch. Inhalt: Anfragen werden mit Unterstützung von KI zusammengefasst und vorsortiert; jede Antwort prüft und versendet ein Mensch; Name und E-Mail-Adresse gehen nicht an KI-Dienste; bitte keine sensiblen Angaben in die Nachricht; Link zur Datenschutzerklärung www.nordwind-workspace.example/datenschutz.
```

**Checkpoint:** Der Assistent zeigt eine Tabelle mit Lücken je Workflow; das Testformular zeigt unter dem Titel den Transparenzhinweis.

**Erweiterung:** In Notion eine Seite „KI im Vertrieb – Verzeichnis“ anlegen, die die drei Workflows mit verantwortlicher Person und Datum der letzten Prüfung auflistet (Art. 4).

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Beispiel, gekürzt – KI-Antworten fallen jedes Mal etwas anders aus. Stand: 22.11.2026.

**1.–2. Tabelle des Assistenten, nach dem Abgleich**

| Workflow | Prüfpunkt | Befund | Maßnahme |
| --- | --- | --- | --- |
| Lead-Eingang | 7 Information | Formular sagt nicht, dass KI vorsortiert | Hinweis im Formular, Datenschutzerklärung um n8n, KI-Anbieter, Notion ergänzen |
| Lead-Eingang | 4 sensible Daten | Nachricht ist Freitext und geht an die KI | Bitte im Formular, keine sensiblen Angaben zu machen; beim Freigeben prüfen |
| Lead-Eingang | 6 Drittland | KI-Modell und Notion in den USA | Grundlage je Dienst mit dem Datenschutz klären (Tabelle Lab 11.1) |
| Gesprächsnotiz | 3 Datenminimierung | Notiz mit Namen, Funktionen und Telefonnummer geht an die KI | Notiz vor dem Absenden ohne Telefonnummer und Mail erfassen oder anonymisieren (Lab 1.3) |
| Gesprächsnotiz | 12 Kennzeichnung | Follow-up-Entwurf ohne Markierung „KI-gestützt“ | Kontrollkästchen `KI-gestützt` auch hier setzen |
| Pipeline-Briefing | 3 Datenminimierung | Namen der Verantwortlichen gehen an die KI | vertretbar (interne Rollen), alternativ Kürzel |
| alle | 10 Speicherdauer | Frist für Leads und Briefing-Seiten offen | Löschfrist festlegen, alte Briefings monatlich löschen |
| alle | Art. 4 | keine Liste mit Verantwortlichen | Verzeichnis „KI im Vertrieb“ anlegen |

Gestrichen: die Behauptung des Assistenten, das Briefing sei „hochriskant nach AI Act“ – ein internes Briefing ist minimales Risiko.

**3.–4. Feld „Form Description“ im Knoten „Lead-Anfrage“**

```text
Übungsformular mit fiktiven Daten: nur erfundene Angaben eintragen.
Ihre Anfrage wird mit Unterstützung von KI zusammengefasst und vorsortiert; jede Antwort prüft und versendet ein Mensch aus unserem Vertriebsteam. Name und E-Mail-Adresse geben wir nicht an KI-Dienste weiter – bitte schreiben Sie keine sensiblen Angaben in die Nachricht. Mehr dazu: www.nordwind-workspace.example/datenschutz
```

**5. Testformular:** Unter der Überschrift „Anfrage an Nordwind Workspace“ stehen der Übungssatz und der Hinweis, darunter die Felder Firma bis Nachricht und die Schaltfläche „Anfrage senden“.

Warum gut: Der Hinweis sagt in drei Sätzen, was passiert, was nicht passiert und wer entscheidet; er stimmt mit dem datensparsamen Workflow aus Lab 11.1 überein.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Assistent stuft alles als „Hochrisiko“ ein | Risikostufen ohne Beispiele vorgegeben | Tabelle „Vier Risikostufen“ in den Chat kopieren und nachfragen |
| Hinweis erscheint nicht im Formular | Workflow nicht gespeichert oder alte Formular-URL geöffnet | speichern, Test-URL im Knoten neu öffnen |
| Hinweis verspricht „keine Daten an KI“ | Text passt nicht zum Workflow (Nachricht geht an die KI) | genau formulieren: Name und E-Mail nicht, Nachricht schon |
| Zeilenumbrüche fehlen | Feld zeigt nur einfachen Text | Leerzeile einfügen oder `<br>` verwenden (laut n8n-Doku erlaubt) |

## Fazit

- Lead-Scoring und Antwortentwürfe sind im AI Act minimales Risiko; Chats, Deepfakes und KI-Texte für die Öffentlichkeit brauchen Transparenz.
- Art. 50 gilt seit 02.08.2026; verschoben hat der Omnibus nur Hochrisiko-Fristen und die Markierung bestehender Systeme bis 02.12.2026.
- KI-Kompetenz beginnt mit einer Liste: welche Werkzeuge, welche Daten, wer verantwortlich ist.

> **Merksatz:** Offen sagen, wo KI mitarbeitet – und dass am Ende ein Mensch entscheidet.
