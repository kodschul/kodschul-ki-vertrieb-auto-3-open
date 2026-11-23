# Lab 1.3: Welche Daten in ein KI-Werkzeug dürfen

**Leitfragen:**

<details>
<summary>Welche Informationen aus dem Vertrieb würden nie per Mail an einen Fremden gehen?</summary>

Kontaktdaten und Gesprächsinhalte von Kunden, Konditionen und Rabatte, die Pipeline, interne Einschätzungen zu Wettbewerbern, Zugangsdaten. Genau diese Grenze gilt auch für KI-Werkzeuge.

</details>

<details>
<summary>Macht es einen Unterschied, ob ein Text in einem privaten oder einem Firmenkonto landet?</summary>

Ja. Für das Firmenkonto gilt ein Vertrag zwischen Anbieter und Unternehmen, meist ohne Training mit den Eingaben. Beim kostenlosen Privatkonto gelten die allgemeinen Bedingungen, meist mit Training, solange es nicht abgeschaltet ist.

</details>

<details>
<summary>Ist der Name eines Ansprechpartners in einer Firma eine schützenswerte Angabe?</summary>

Ja. Name, Mailadresse und Durchwahl einer Ansprechperson sind personenbezogene Daten im Sinne der Datenschutz-Grundverordnung (DSGVO), auch im B2B. Öffentlich ist die Firma, nicht automatisch die Person.

</details>

- Jede Eingabe in ein KI-Werkzeug ist eine Weitergabe an einen Anbieter – wie eine Mail an einen externen Dienstleister.
- Die Art der Information und das Konto entscheiden, was hinein darf: grün, gelb oder rot. Im Kurs werden nur fiktive Nordwind-Daten verwendet.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| DSGVO | Datenschutz-Grundverordnung der EU; regelt, wie mit Angaben über Personen umgegangen werden darf |
| personenbezogene Daten | alles, womit sich eine Person erkennen lässt: Name, Mail, Telefonnummer, aber auch Gesprächsinhalte, die einer Person zuzuordnen sind |
| Geschäftsgeheimnis | interne Information mit wirtschaftlichem Wert, z. B. Preise, Konditionen, Pipeline, Kalkulation |
| Firmenkonto / Privatkonto | Anmeldung über einen Vertrag des Arbeitgebers (z. B. ChatGPT Business, Microsoft 365 Copilot mit Arbeitskonto) oder über ein privates bzw. kostenloses Konto |
| Verlauf | gespeicherte Liste der bisherigen Chats im Konto |
| Training mit Eingaben | Anbieter nutzt Chats, um künftige Modelle zu verbessern; bei Privatkonten meist per Schalter abschaltbar |
| Anonymisieren | Angaben so ersetzen oder weglassen, dass niemand mehr auf eine bestimmte Person oder einen bestimmten Kunden schließen kann |
| Platzhalter | Stellvertreter in eckigen Klammern, z. B. `[Kunde]`, `[Ansprechperson]` – wie ein leeres Feld in einem Formular |

## Was mit einer Eingabe beim Anbieter passiert

```text
Eingabe im Chat ──► Server des Anbieters ──► Modell erzeugt die Antwort
                          │
                          ├─ gespeichert im Verlauf (Dauer je nach Konto)
                          └─ je nach Konto und Schalter: Nutzung zum Training künftiger Modelle
```

Die Grundregel gilt bei allen vier Assistenten (Stand: 22.11.2026):

- **Kostenloses bzw. privates Konto:** Eingaben dürfen meist zum Training genutzt werden, solange der Schalter dafür nicht ausgeschaltet ist. Abschalten wirkt nur für neue Chats.
- **Firmenkonto** (z. B. ChatGPT Business, Microsoft 365 Copilot mit Arbeitskonto): Vertrag mit dem Unternehmen, standardmäßig kein Training mit den Eingaben.
- Menüpfade und Quellen je Anbieter stehen im Abschnitt „Vertiefung“ am Ende.

So sieht der Schalter in ChatGPT aus (hier ausgeschaltet):

![ChatGPT-Einstellungen „Data controls“, darüber der Dialog „Model improvement“ mit dem ausgeschalteten Schalter „Improve the model for everyone“, darunter Schalter für Sprach- und Videoaufnahmen und die Schaltfläche „Done“](https://images.ctfassets.net/j22is2dtoxu1/lbas_img_rGElX1CXOTWK5Natf8g0cBTFhmjGa4IffPYCGrVSXS0/ecff7853d713d32e9370913530e9ad04/lbas_img_rGElX1CXOTWK5Natf8g0cBTFhmjGa4IffPYCGrVSXS0.png)
_Quelle: OpenAI Help Center, „Data controls in ChatGPT“ (https://help.openai.com/en/articles/7730893-data-controls-faq), © OpenAI, abgerufen am 22.11.2026._

## Datenampel für Vertriebsdaten

| Farbe | Art der Information | Beispiele aus dem Vertrieb | Regel |
| --- | --- | --- | --- |
| grün | öffentlich | eigene Website, Pressemitteilung, Geschäftsbericht eines Interessenten | in jedes KI-Werkzeug |
| gelb | intern | Preisliste, Produktunterlagen, Wettbewerbs-Einschätzung, Notiz ohne Personen- und Kundenbezug | nur mit Firmenkonto und Freigabe des Unternehmens |
| rot | personenbezogen, vertraulich, sensibel | Kontaktdaten, Gesprächsnotiz mit Namen, CRM-Export, Konditionen eines bestimmten Kunden, Gesundheitsangaben | weglassen oder anonymisieren |
| rot, immer | Zugangsdaten | Passwörter, Codes, Zugangsschlüssel (z. B. ein Integration Secret, der geheime Schlüssel einer App-Verbindung) | nie, auch nicht anonymisiert |

Mit einem kostenlosen Privatkonto bleibt nur Grün. Die Nordwind-Daten im Kurs sind erfunden und dürfen deshalb in jedes Werkzeug.

## Anonymisieren in drei Schritten

| Schritt | Was passiert | Beispiel |
| --- | --- | --- |
| 1 Erkennen | alles markieren, was auf eine Person oder einen Kunden schließen lässt: Namen, Kontaktdaten, Firma, Ort, seltene Details | Fall 4: „Frau Katrin Vogel, Leiterin Facility Management, Hansa Wohnbau eG, Lübeck, Mobil 0151 …, k.vogel@…“ |
| 2 Ersetzen | durch Platzhalter ersetzen, Unnötiges streichen; die Zuordnung „Platzhalter → Original“ bleibt außerhalb des Chats | „Telefonat mit [Ansprechperson], Leitung Facility Management, [Kunde], [Ort]. Interesse an Panel 10 für 22 Räume …“, Mobilnummer und Mail gestrichen |
| 3 Zurücksetzen | nach der KI-Antwort im eigenen Text die Platzhalter wieder durch die Originale ersetzen | „[Ansprechperson]“ → „Frau Vogel“, „[Kunde]“ → „Hansa Wohnbau eG“ |

Name streichen reicht selten: Firma, Ort oder ein seltenes Detail verraten den Kunden ebenso. Anonymisiert wird vor der Eingabe, nicht durch die KI.

## Übung: Einstellungen prüfen und Fälle einordnen

**Material:** [`datenampel-faelle.md`](../material/datenampel-faelle.md) · **Werkzeug:** KI-Assistent

**Ausgangslage:** Bevor im Nordwind-Vertrieb echte Aufgaben im KI-Assistenten landen, wird geprüft, was das eigene Konto mit Eingaben macht, und an drei erfundenen Fällen geübt, was hinein darf.

1. Öffne die Einstellungen des eigenen Assistenten (Menüpfad in der Tabelle „Training mit Eingaben je Anbieter“ im Abschnitt Vertiefung) und prüfe, ob die Nutzung für Training an oder aus ist.
2. Öffne einen neuen Chat und sende Prompt-Karte 1.3a mit Fall 2 aus `datenampel-faelle.md`.
3. Sende im selben Chat Prompt-Karte 1.3b zweimal: einmal mit Fall 3, einmal mit Fall 4.
4. Vergleiche die drei Einordnungen mit dem Musterergebnis; weicht der Assistent ab, sende Prompt-Karte 1.3c.

**Prompt-Karte 1.3a – Datenampel anwenden**

```text
Wir nutzen im Vertrieb eine Datenampel für KI-Werkzeuge:
- grün = öffentlich, darf in jedes KI-Werkzeug
- gelb = intern (Preise, Produktunterlagen, interne Einschätzungen ohne Personenbezug), nur mit Firmenkonto und Freigabe des Unternehmens
- rot = personenbezogen, vertraulich oder sensibel (Kontaktdaten, Gesprächsinhalte mit Namen, Konditionen eines bestimmten Kunden, Gesundheitsangaben), weglassen oder anonymisieren; Zugangsdaten nie
Ist die folgende Eingabe grün, gelb oder rot – und warum? Antworte mit Farbe, Begründung in zwei Sätzen und einer Empfehlung, was vor der Eingabe zu tun ist.

[Situation und Eingabe aus dem Fall einfügen]
```

**Prompt-Karte 1.3b – Nächster Fall**

```text
Gleiche Frage für diese Eingabe: grün, gelb oder rot – und warum?

[Situation und Eingabe aus dem Fall einfügen]
```

**Prompt-Karte 1.3c – Nachfragen**

```text
Unsere Datenampel ordnet diesen Fall als [Farbe] ein. Welche Angabe im Text hast du anders gewichtet?
```

**Checkpoint:** Der Status der Trainings-Einstellung ist bekannt; der Assistent zeigt für drei Fälle je eine Farbe mit Begründung und Empfehlung.

**Erweiterung:** Fall 4 in drei Schritten anonymisieren und erneut einordnen lassen.

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Beispiel, gekürzt – KI-Antworten fallen jedes Mal etwas anders aus. Menüs: Stand 22.11.2026.

**1. Einstellung:** Bei einem kostenlosen ChatGPT-Konto steht „Improve the model for everyone“ zunächst auf „On“; nach dem Abschalten zeigt „Data controls“ „Off“. Bei Perplexity steht „AI data retention“ zunächst auf an.

**2.–3. Einordnung durch den Assistenten**

> **Fall 2 – grün.** Der Auszug stammt aus einem veröffentlichten Geschäftsbericht und betrifft ein Unternehmen, keine Person. Empfehlung: Quelle mit Link angeben.
>
> **Fall 3 – gelb.** Die Preisliste ist intern und ein Geschäftsgeheimnis, enthält aber keine Personen. Empfehlung: nur mit Firmenkonto und Freigabe verwenden.
>
> **Fall 4 – rot.** Name, Mobilnummer und Mailadresse machen die Ansprechperson eindeutig erkennbar. Empfehlung: vor der Eingabe anonymisieren oder die Mail selbst schreiben.

**4. Alle acht Fälle mit Lösung**

| Fall | Farbe | Begründung |
| --- | --- | --- |
| 1 Text der eigenen Website | grün | öffentlich, ohne Personenbezug |
| 2 Geschäftsbericht eines Interessenten | grün | öffentlich, betrifft ein Unternehmen, keine Person |
| 3 Interne Preisliste | gelb | intern, Geschäftsgeheimnis ohne Personen → nur mit Firmenkonto und Freigabe |
| 4 Gesprächsnotiz mit Kontaktdaten | rot | Name, Mobilnummer und Mail machen die Ansprechperson erkennbar → anonymisieren |
| 5 Interne Wettbewerbs-Einschätzung | gelb | intern, ausdrücklich nicht für Kunden, ohne Personen |
| 6 Pipeline-Export aus dem CRM | rot | Ansprechpersonen, Mailadressen, Dealwerte und Rabatte vieler Kunden; nicht hochladen |
| 7 Persönliche Information in einer Kundenmail | rot, sensibel | Gesundheitsangabe über einen Dritten (Art. 9 DSGVO); Antwort ohne diese Angabe selbst schreiben |
| 8 Zugangsdaten für die Notion-Verbindung in n8n | rot, immer | das Integration Secret ist ein Zugangsschlüssel zu den Notion-Daten; nie eingeben, nur die Fehlermeldung ohne Secret schicken |

Warum gut: Die Begründung folgt der Art der Information, nicht dem Nutzen der Antwort – genau wie die Datenampel.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Einstellung nicht zu finden | Menü umbenannt oder App statt Browser | im Browser öffnen, in den Einstellungen nach „Data“, „Privacy“ oder „Datenschutz“ suchen |
| Fall 3 als grün eingeordnet | Datenampel nicht mitgeschickt | Prompt-Karte 1.3a vollständig senden |
| Schalter im Firmenkonto gesperrt | Firma legt die Einstellung fest | nichts ändern; maßgeblich ist die Vorgabe der eigenen IT |

## Fazit

- Jede Eingabe ist eine Weitergabe; Konto und Trainings-Schalter entscheiden mit, was der Anbieter damit tun darf.
- Grün überall, gelb nur mit Firmenkonto und Freigabe, rot weglassen oder anonymisieren; Zugangsdaten nie.
- Datenschutz im Vertrieb aus rechtlicher Sicht: vertieft in Modul 11. Keine Rechtsberatung.

> **Merksatz:** Im Zweifel weglassen – die Art der Information entscheidet, nicht die Nützlichkeit der Antwort.

## Vertiefung: Training, Speicherung und Datenarten je Anbieter

### Datenarten aus dem Vertrieb

| Art | Beispiele aus dem Vertrieb | warum heikel |
| --- | --- | --- |
| personenbezogen (DSGVO) | Name, Mail, Telefonnummer der Ansprechperson; Gesprächsinhalte; Visitenkarte | die Person hat der Weitergabe an einen KI-Anbieter nicht zugestimmt |
| besonders sensibel (Art. 9 DSGVO) | Krankheit, Religion, Gewerkschaft – etwa in einer Kundenmail erwähnt | gehört nie in ein KI-Werkzeug |
| Geschäftsgeheimnis | Preise, Rabatte, Konditionen, Pipeline, Wettbewerbs-Einschätzung | Schaden, wenn es nach außen gelangt |

### Training mit Eingaben je Anbieter

| Assistent | kostenloses bzw. privates Konto | Firmenkonto |
| --- | --- | --- |
| ChatGPT | Training standardmäßig an; abschalten: Einstellungen → „Data controls“ → „Improve the model for everyone“ | Business, Enterprise, Edu: standardmäßig kein Training |
| Claude | Training per Schalter; abschalten: Einstellungen → „Privacy“ → Schalter zur Modellverbesserung („Help improve Claude“) | Claude for Work: standardmäßig kein Training, Ausnahme Feedback per Daumen |
| Perplexity | „AI data retention“ standardmäßig an; abschalten: Einstellungen → „Preferences“ → „Artificial Intelligence“ → „AI data retention“ | Enterprise: nie Training |
| Microsoft Copilot | privates Microsoft-Konto: Nutzung für Training jederzeit abschaltbar (Copilot-Einstellungen, Bezeichnung je nach Version) | Microsoft 365 Copilot mit Arbeitskonto: Prompts und Antworten trainieren keine Basismodelle |

- Abschalten wirkt nur für neue Chats; was vorher gesammelt wurde, bleibt (laut Perplexity und Anthropic).
- Temporärer bzw. Inkognito-Chat: erscheint nicht im Verlauf; bei ChatGPT nicht fürs Training, bis zu 30 Tage für Sicherheitszwecke gespeichert.

_Quellen: OpenAI, „Data controls in ChatGPT“ (https://help.openai.com/en/articles/7730893-data-controls-faq); Anthropic Privacy Center, „How do I change my model improvement privacy settings?“ (https://privacy.claude.com/en/articles/12109829-how-do-i-change-my-model-improvement-privacy-settings) und „Is my data used for model training?“ (https://privacy.claude.com/en/articles/7996868-is-my-data-used-for-model-training); Perplexity Help Center, „Data Collection at Perplexity“ (https://www.perplexity.ai/help-center/en/articles/11564572-data-collection-at-perplexity); Microsoft Support, „Privacy FAQ for Microsoft Copilot“ (https://support.microsoft.com/en-us/topic/privacy-faq-for-microsoft-copilot-27b3a435-8dc9-4b55-9a4b-58eeb9647a7f); Microsoft Learn, „Data, Privacy, and Security for Microsoft 365 Copilot“ (https://learn.microsoft.com/en-us/copilot/microsoft-365/microsoft-365-copilot-privacy); alle abgerufen am 22.11.2026. Keine Rechtsberatung; verbindlich sind die Regeln des eigenen Unternehmens. Stand: 22.11.2026, vor Kursbeginn prüfen._

Bei privaten Claude-Konten fragt Anthropic seit August 2025 per Dialog nach dem Training; der Schalter steht dort bereits auf „an“:

![Claude-Dialog „Updates to Consumer Terms and Policies“: Schalter „You can help improve Claude“ eingeschaltet, darunter der Hinweis auf fünf Jahre Speicherdauer, Schaltflächen Accept und Not now](https://www-cdn.anthropic.com/images/4zrzovbb/website/0d48d7f71fe2b5ccc537b48394313a91636bb329-3840x2160.png)
_Quelle: Anthropic, „Updates to Consumer Terms and Privacy Policy“, 28.08.2025 (https://www.anthropic.com/news/updates-to-our-consumer-terms), © Anthropic, abgerufen am 22.11.2026._

In Perplexity heißt die Einstellung „AI data retention“ (hier eingeschaltet):

![Perplexity-Einstellungen, Bereich „Artificial Intelligence“: Zeilen „Model“, „Image generation model“ und „AI data retention“ mit eingeschaltetem Schalter und dem Hinweis, dass Enterprise-Kunden automatisch ausgenommen sind](https://mintcdn.com/perplexity-help-center/kBGsQkSG8SPEk_Ye/help-center/assets/img/e0efb68471_Screenshot_2B2025-06-13_2Bat_2B3_56_14-E.png)
_Quelle: Perplexity Help Center, „Data Collection at Perplexity“ (https://www.perplexity.ai/help-center/en/articles/11564572-data-collection-at-perplexity), © Perplexity, Ansicht Juni 2025, abgerufen am 22.11.2026._
