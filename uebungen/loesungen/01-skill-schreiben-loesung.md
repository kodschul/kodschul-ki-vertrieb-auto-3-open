# Lösung 1: Einen Skill schreiben – Gesprächsnotiz ins CRM

Zurück zur [Übung 1](../01-skill-schreiben.md). _Beispiel – KI-Antworten fallen jedes Mal etwas anders aus. Entscheidend ist, dass das Erfolgskriterium erfüllt ist._

## Schritt 1: Rückfragen des Assistenten (Beispiel)

> 1. Soll der Skill auch eine Follow-up-Mail schreiben oder nur die fünf Felder?
> 2. Sollen Produktwünsche des Kunden unter „Bedarf“ stehen?
> 3. Wie lang darf ein Feld höchstens sein?

Passende Antworten: „Nur die fünf Felder.“ · „Ja.“ · „Zwei bis vier Sätze, Nächster Schritt als Liste.“

## Schritt 2–3: Fertiger Skill

| Werkzeug | So sieht es nach dem Speichern aus |
| --- | --- |
| Claude | `nordwind-gespraechsnotiz.zip` (Ordner `nordwind-gespraechsnotiz/` mit `SKILL.md`) hochgeladen; der Skill steht unter **Customize > Skills**, Schalter an |
| ChatGPT Business / Enterprise | Skill `nordwind-gespraechsnotiz` steht unter **Plugins > Plugin Directory > Skills** |
| ChatGPT Free / Plus / Pro | Projekt `Nordwind`, Text der `SKILL.md` in den **Anweisungen** des Projekts |
| Gemini | Skill unter **Anpassen > Skills** gespeichert |

Musterfassung zum Vergleich oder als Ersatz: [`nordwind-gespraechsnotiz/SKILL.md`](nordwind-gespraechsnotiz/SKILL.md) · fertig zum Hochladen: [`nordwind-gespraechsnotiz.zip`](nordwind-gespraechsnotiz.zip)

Kopfbereich der Musterfassung:

```markdown
---
name: nordwind-gespraechsnotiz
description: Macht aus einer rohen Gesprächsnotiz nach einem Kundentermin fünf CRM-Felder (Bedarf, Budget, Entscheider, Zeitrahmen, Nächster Schritt). Nutzen bei Gesprächsnotiz, Terminnotiz, CRM-Eintrag.
---
```

Gut, weil die Beschreibung sagt, **was** der Skill tut, und die Wörter enthält, die im Alltag getippt werden („Notiz“, „Termin“, „CRM“). Daran erkennt der Assistent, wann der Skill passt.

## Schritt 4–5: Test mit der Rheinpark-Notiz

**Benutzt?** Claude zeigt im Arbeitsverlauf einen Schritt wie „Using nordwind-gespraechsnotiz“. In ChatGPT und Gemini zeigt sich der Skill am Ergebnis: Ohne Hinweis im Prompt kommt genau die Tabelle mit fünf Zeilen und Prüfliste.

**Antwort:**

| Feld | Inhalt |
| --- | --- |
| Bedarf | ca. 120 Mitarbeitende, heute 9 Besprechungsräume, ab Februar 2027 drei neue im 4. OG → 12 Räume. Ständige Doppelbuchungen, v. a. großer Raum „Rhein“ (16 Personen); Buchung über Outlook (Microsoft 365) mit ungepflegten Raumpostfächern. 4 Räume sollen videokonferenzfähig werden (großer Raum eher Vista Plus, 3 kleine Vista). [Office Management] wünscht Auslastungsberichte → Book Pro. |
| Budget | Kein Budget genannt. [GF] wünscht 10 % Rabatt auf alles – **nicht zugesagt**. Einwand: „RaumPilot ist viel billiger“ (Antwort: nur Software, keine Hardware). |
| Entscheider | [GF] entscheidet; [Office Management] ist Ansprechperson; [IT-Leitung] muss wegen SSO und Netzwerk (PoE) zustimmen, war nicht dabei. |
| Zeitrahmen | Drei neue Räume ab Februar 2027. Lieferung bis Mitte Dezember 2026 gewünscht – **nicht zugesagt**, mit Logistik klären. |
| Nächster Schritt | - Angebot bis 04.12.2026 (12 × Panel 10, 3 × Vista, 1 × Vista Plus, Book Pro für 12 Räume, Care, Installation)<br>- Demo im Showroom Köln mit [Office Management] und [IT-Leitung] vorschlagen<br>- Logistik wegen Lieferung Mitte Dezember fragen<br>- klären, ob die AVV-Vorlage an [Office Management] geht<br>- Wiedervorlage: 07.12.2026 |

> Prüfliste: ☑ alles aus der Notiz ☑ nicht Zugesagtes markiert ☑ Daten aufgelöst ☑ keine Namen, Telefonnummern, Mailadressen

Gut, weil Rabatt und Liefertermin als Wunsch dastehen, nicht als Zusage, die fehlende IT-Leitung sichtbar ist und jeder nächste Schritt ein Datum hat.

## Noch einmal: Hafenkontor-Notiz

| Feld | Inhalt |
| --- | --- |
| Bedarf | Umzug der Zentrale in die HafenCity im April 2027 mit 18 geplanten Besprechungsräumen. Heute Papierlisten an den Raumtüren, niemand sieht, was frei ist. Buchung soll über Google Workspace laufen (kein Microsoft 365). |
| Budget | ca. 60.000 € für das Raumprojekt, von der Geschäftsführung freigegeben. Leasing angefragt – **nicht zugesagt**, wird geklärt. |
| Entscheider | [Leitung Facility Management] ist Ansprechperson; [GF] hat das Budget freigegeben; [Einkauf] vergleicht drei Angebote. |
| Zeitrahmen | Umzug April 2027. |
| Nächster Schritt | - Grundriss kommt vom Kunden bis 02.12.2026<br>- Angebot bis 11.12.2026<br>- Leasing klären<br>- Wiedervorlage: 03.12.2026 |

Gut, weil derselbe Skill ohne neue Anleitung auch eine ganz andere Notiz in dasselbe Format bringt: Dafür ist ein Skill da.
