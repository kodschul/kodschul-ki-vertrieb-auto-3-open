# Vorlage: Nurturing-Kampagne und Notion-Datenbank „Kampagnen“

Fiktives Unternehmen, alle Angaben erfunden. Verwendet in [Lab 10.1](../m10-journey-tools/l01-customer-journey.md).

Eine Nurturing-Kampagne ist eine kurze Folge von Mails, die Leads über Wochen mit nützlichen Inhalten begleitet, bis sie für ein Gespräch bereit sind. Die Vorlage legt fest, was jede Mail enthält, und wie der Plan als Datenbank `Kampagnen` ins Übungs-CRM kommt.

## Aufbau des 3-Mail-Plans

| Nr | Abstand in Tagen | Betreff | Kernaussage | Handlungsaufforderung | Segment | Kennzahl |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | 0 (bei Aufnahme in die Kampagne) | höchstens 60 Zeichen, nennt ein Problem des Segments | ein Nutzen, belegt mit einer Angabe aus dem Produktblatt | ein kleiner Schritt, z. B. Seite ansehen, kurz antworten | eines der drei Nordwind-Segmente | z. B. Klickrate |
| 2 | Tage nach Mail 1, z. B. 14 | | zweiter Nutzen oder Antwort auf den typischen Einwand | | dasselbe Segment | z. B. Antworten |
| 3 | Tage nach Mail 2, z. B. 21 | | Einladung zum Gespräch oder zur Vorführung | Termin vereinbaren | dasselbe Segment | z. B. Terminanfragen |

| Spalte | Regel |
| --- | --- |
| Betreff | konkret und ehrlich; keine künstliche Dringlichkeit („nur heute“), keine Großbuchstaben |
| Kernaussage | genau eine Botschaft je Mail; Fakten nur aus [`produktblatt.md`](produktblatt.md) und [`nordwind-unternehmen.md`](nordwind-unternehmen.md); keine Preise, Rabatte oder Liefertermine |
| Handlungsaufforderung | ein einziger, kleiner nächster Schritt; je Mail höchstens ein Link |
| Abstand in Tagen | mindestens 7 Tage zwischen zwei Mails; die ganze Kampagne höchstens 3 Mails |
| Segment | Ansprache und Einwand passend zu [`kundensegmente.md`](kundensegmente.md) und zur Persona aus Lab 3.1 |
| Kennzahl | eine messbare Größe je Mail, die zum Ziel der Mail passt |

## Pflichtangaben in jeder Mail

- Versand nur an Leads, die dem Empfang von Werbe-Mails zugestimmt haben (Einwilligung, bestätigt per Double-Opt-in); in `Leads` ist dann das Kontrollkästchen `Einwilligung Werbung` angehakt. Eine Anfrage ist keine Einwilligung. Im Übungs-CRM hat kein Lead eine dokumentierte Einwilligung, deshalb entsteht in Lab 10.1 nur der Plan, kein Versand. Details in [Lab 10.1](../m10-journey-tools/l01-customer-journey.md) und [Lab 3.4](../m03-lead-generation/l04-first-contact.md).
- Absender erkennbar: Nordwind Workspace GmbH, Impressum im Mailfuß.
- Abmeldelink in jeder Mail; Abmeldungen werden sofort berücksichtigt.
- Hinweis auf KI-Unterstützung entscheidet das Team vor dem Versand (vertieft in Modul 11).

## Datenbank „Kampagnen“ in Notion

Jede Zeile ist eine Mail der Kampagne. Die Datenbank liegt in der Seite „Nordwind CRM“ neben `Leads` und `Deals`.

| Eigenschaft | Typ | Beispielwert |
| --- | --- | --- |
| `Mail` | Titel | Mittelstand-Büro – Mail 1 |
| `Kampagne` | Text | Nurturing Mittelstand-Büro |
| `Segment` | Auswählen | Mittelstand-Büro, Kanzleien und Beratungen, Coworking und Flexible Office |
| `Nr` | Zahl | 1 |
| `Abstand in Tagen` | Zahl | 0 |
| `Betreff` | Text | |
| `Kernaussage` | Text | |
| `Handlungsaufforderung` | Text | |
| `Kennzahl` | Text | Klickrate auf den Link |
| `Zielgruppe` | Text | Leads mit Status „Später pflegen“ im Segment, Einwilligung Werbung = ja |
| `Freigabe` | Auswählen | Freigabe offen, Freigegeben |

### Kopfzeile der CSV-Datei

```text
Mail,Kampagne,Segment,Nr,Abstand in Tagen,Betreff,Kernaussage,Handlungsaufforderung,Kennzahl,Zielgruppe,Freigabe
```

### Import in Notion

Wie der Import von `Leads` in Lab 4.1 ([Importanleitung](notion/notion-import-anleitung.md)), Bezeichnungen je nach Version:

1. Speichere die drei Zeilen mit der Kopfzeile oben im Texteditor als `kampagnen.csv` (Kodierung UTF-8).
2. Tippe in der Seite „Nordwind CRM“ in einer leeren Zeile `/csv`, wähle die Datei und bestätige eine neue Datenbank.
3. Benenne die Datenbank in `Kampagnen` um.
4. Stelle `Nr` und `Abstand in Tagen` auf Zahl, `Segment` und `Freigabe` auf Auswählen; ergänze bei `Freigabe` die Option „Freigegeben“.
5. Prüfe: 3 Zeilen, erste Spalte `Mail` ist der Titel, alle Zeilen mit Freigabe „Freigabe offen“.

Enthält ein Text ein Komma, steht der ganze Wert in Anführungszeichen, z. B. `"Doppelbuchungen, Geister-Buchungen"`; KI-Assistenten setzen sie meist selbst.

## Prüfliste vor der Freigabe

| Prüfpunkt | Frage |
| --- | --- |
| Persona | Spricht jede Mail Ziel und Einwand der Persona an? |
| Fakten | Steht jede Produktangabe so im Produktblatt? |
| Zusagen | Kein Preis, kein Rabatt, kein Liefertermin? |
| Ton | Sachlich, ohne künstliche Dringlichkeit und ohne falsche Nähe? |
| Abstand | Mindestens 7 Tage zwischen den Mails? |
| Recht | Zielgruppe nur mit `Einwilligung Werbung` = ja, Absender und Abmeldelink vorgesehen? |
