# Lab 10.1: Customer Journey und Kampagnen mit KI

**Leitfragen:**

<details>
<summary>Was passiert heute mit einem Lead, der „vielleicht nächstes Jahr“ sagt?</summary>

Oft nichts: Er steht im CRM, bis ihn jemand zufällig wiederfindet. Bis dahin hat er sich längst woanders informiert. Eine kurze Mail-Folge mit nützlichen Inhalten hält den Kontakt, ohne dass jemand daran denken muss.

</details>

<details>
<summary>An welchen Stellen hat ein Kunde vor dem ersten Gespräch schon Kontakt mit dem Unternehmen?</summary>

Website, Fachartikel, Messestand, Empfehlung, Bewertungen, das Anfrageformular, die erste Antwortmail. Jeder dieser Kontakte prägt das Bild vom Anbieter, bevor der Vertrieb das erste Wort sagt.

</details>

<details>
<summary>Wie oft darf sich ein Anbieter melden, bevor es nervt?</summary>

Eine feste Zahl gibt es nicht; entscheidend sind Nutzen je Mail, Abstand und eine einfache Abmeldung. Für Werbe-Mails gilt zusätzlich: nur mit Einwilligung. Im Kurs gilt als Richtwert: höchstens drei Mails, mindestens sieben Tage Abstand.

</details>

- Die Customer Journey beschreibt den Weg eines Kunden vom ersten Kontakt bis zum Ausbau; an jeder Stufe gibt es Kontaktpunkte und eine Kennzahl.
- Leads, die noch nicht bereit sind, werden über Wochen gepflegt (Nurturing); KI entwirft die Inhalte, der Mensch prüft, und versendet wird nur mit Einwilligung.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| Customer Journey | Weg eines Kunden vom ersten Kontakt bis zum Wiederkauf, in Stufen gegliedert – wie eine Reiseroute mit Stationen |
| Kontaktpunkt (Touchpoint) | jede Stelle, an der ein Kunde dem Unternehmen begegnet: Website, Mail, Messe, Anruf, Rechnung |
| Nurturing | Lead-Pflege: Leads, die noch nicht kaufbereit sind, bekommen über Wochen passende Inhalte, bis ein Gespräch sinnvoll ist |
| Kampagne | geplante Folge von Mails oder Beiträgen für eine Zielgruppe mit einem Ziel und einer Kennzahl |
| Marketing-Automatisierung | Software, die Mails an Segmente zeitgesteuert versendet, Abmeldungen verwaltet und Öffnungen, Klicks und Antworten misst |
| Einwilligung (Opt-in) | vorherige Zustimmung einer Person, Werbe-Mails zu bekommen |
| Double-Opt-in | Einwilligung in zwei Schritten: Eintrag im Formular, dann Klick auf einen Bestätigungslink in einer Mail; belegt, dass die Adresse der Person gehört |
| Kennzahl (KPI) | messbare Größe, an der der Erfolg einer Stufe oder Mail abgelesen wird, z. B. Klickrate oder Terminanfragen |

## Customer Journey im B2B

![Customer Journey als Pfeilkette mit fünf Stufen Awareness, Consideration, Purchase, Retention und Advocacy; an jeder Stufe farbige Punkte mit Kontaktpunkten wie PR, Online ads, Reviews, E-Mail, Website, Webshop, Newsletter, FAQ, Community, Social Media und Word-of-mouth](https://upload.wikimedia.org/wikipedia/commons/thumb/5/58/Customer_journey_with_touchpoints_English.png/960px-Customer_journey_with_touchpoints_English.png)
_Quelle: Wikimedia Commons, „Customer journey with touchpoints English.png“ (https://commons.wikimedia.org/wiki/File:Customer_journey_with_touchpoints_English.png), Nick Nijhuis, CC BY-SA 4.0, abgerufen am 23.11.2026._

Das Bild zeigt das verbreitete Fünf-Stufen-Modell. Im B2B-Geschäft wird die Kaufphase meist in Bewertung und Entscheidung geteilt, weil mehrere Personen prüfen; nach dem Kauf folgen Einführung und Ausbau. Für Nordwind:

| Stufe | Was der Kunde tut | Kontaktpunkte bei Nordwind | KI und Automatisierung im Kurs | Kennzahl |
| --- | --- | --- | --- | --- |
| **Aufmerksamkeit** | bemerkt ein Problem (Doppelbuchungen, schlechter Ton) | Fachartikel, Messe, Empfehlung, LinkedIn | Inhalte je Segment und Persona (Lab 3.1, 3.4) | Website-Besuche, neue Leads |
| **Interesse** | sucht Lösungen, stellt eine Anfrage | Website, Formular „Lead-Anfrage“, erste Antwort | Lead-Eingang mit Bewertung und Antwortentwurf (Lab 7.2, 8.2) | Anfragen pro Monat, Reaktionszeit |
| **Bewertung** | vergleicht Anbieter, sieht eine Vorführung | Bedarfsgespräch, Showroom, Angebot | Gesprächsnotiz und Follow-up (Lab 9.1), Briefing (Lab 9.2) | Anteil Angebote, die gewonnen werden (Nordwind: 33,3 %, Lab 5.2) |
| **Entscheidung** | Geschäftsführung, IT und Einkauf stimmen zu | Verhandlung, Datenschutzvertrag | Nachfass-Entwürfe, Einwände vorbereiten | Abschlussquote, Tage bis Abschluss |
| **Einführung** | Installation, erste Wochen im Betrieb | Installation, Einweisung, Care-Hotline | Einweisungs-Mails, Antworten auf häufige Fragen | Zeit bis Installation (Ziel zwei Wochen), Zufriedenheit |
| **Ausbau** | mehr Räume, Book Pro, Care | Customer Success, Jahresgespräch | Ausbaukandidaten erkennen (Lab 5.1, [`kundensegmente.md`](../material/kundensegmente.md)) | Ausbauumsatz, Weiterempfehlungen |

```text
Aufmerksamkeit → Interesse → Bewertung → Entscheidung → Einführung → Ausbau
                    │
                    └─ Score unter 70: Status „Später pflegen“ (Lab 7.2)
                          └─► nur mit Einwilligung Werbung: Nurturing, 3 Mails in 5 Wochen ──► Antwort oder Klick ──► zurück zu Interesse
```

## Nurturing für Leads mit Status „Später pflegen“

Seit Lab 7.2 landen Anfragen mit Score unter 70 als „Später pflegen“ in `Leads`, zum Beispiel die Steuerkanzlei Lorenzen & Partner mit sechs Räumen und einer Informationsanfrage zu Kamera-Sets (T1 aus [`testanfragen.md`](../material/testanfragen.md), Score 61 im Musterergebnis von Lab 7.2). Für ein Gespräch ist es zu früh, zum Vergessen zu schade.

| Baustein | Inhalt im Kurs |
| --- | --- |
| Zielgruppe | Leads mit Status „Später pflegen“ in einem Segment und Kontrollkästchen `Einwilligung Werbung` angehakt; Leads mit Segment „Kein Fit“ nicht |
| Inhalt | je Mail ein Nutzen, passend zu Ziel und Einwand der Persona; Fakten nur aus dem Produktblatt |
| Rhythmus | 3 Mails, Abstand 0, 14 und 21 Tage |
| Ende | Antwort, Klick oder Terminanfrage → Status zurück auf „Prüfen“ für den Vertrieb; sonst Kampagne endet |
| Kennzahl | je Mail eine: Klickrate, Antworten, Terminanfragen |

Im Übungs-CRM hat kein Lead eine dokumentierte Einwilligung: Die recherchierten Leads haben nie zugestimmt, und eine Anfrage über das Formular ist keine Einwilligung in Werbung. `Einwilligung Werbung` (Kontrollkästchen seit dem Import in Lab 4.1) ist deshalb überall leer, und die Übung erzeugt einen Kampagnenplan, keinen Versand. Die Struktur und alle Regeln stehen in [`kampagnen-vorlage.md`](../material/kampagnen-vorlage.md).

## Kampagnen in Marketing-Werkzeugen

Marketing-Automatisierung versendet Mails an Segmente nach Zeitplan, verwaltet Ein- und Abmeldungen und misst Klicks. Viele Werkzeuge entwerfen ganze Kampagnen inzwischen per KI; das Ergebnis geht vor dem Versand in eine Prüfung.

![ActiveCampaign „Active Intelligence“: links der Auftrag „Create 3 spring sale emails for my clothing brand“ und die Antwort „I created 3 spring sale emails for you to review“; rechts die Vorschau einer Mail mit Betreff „Spring has sprung. Save up to 40%.“, Schaltflächen „Review & Send“ und „Send test“ und dem Knopf „DON'T MISS OUT“](https://active-campaign.files.svdcdn.com/production/general/Active-Intelligence-2.8-Overview-1_1-1.png)
_Quelle: ActiveCampaign, „AI“ (https://www.activecampaign.com/ai), Produktbild © ActiveCampaign, abgerufen am 23.11.2026._

Das Beispiel zeigt den Ablauf „KI entwirft drei Mails, Mensch prüft und sendet“. Es zeigt auch, was im B2B-Nurturing vermieden wird: Rabatt im Betreff und künstliche Dringlichkeit („Don't miss out“).

| Regel für Werbe-Mails | Bedeutung | Grundlage |
| --- | --- | --- |
| Einwilligung vor dem Versand | Werbung per E-Mail ohne vorherige ausdrückliche Einwilligung gilt als unzumutbare Belästigung, auch im B2B; eine Anfrage ist keine Einwilligung in Werbung | [§ 7 Abs. 2 Nr. 2 UWG](https://www.gesetze-im-internet.de/uwg_2004/__7.html), Lab 3.4 |
| Einwilligung nachweisen | wer eine Einwilligung nutzt, muss sie belegen können; Double-Opt-in ist dafür der übliche Weg | [Art. 7 Abs. 1 DSGVO](https://dsgvo-gesetz.de/art-7-dsgvo/) |
| Abmeldelink und Absender | jede Mail nennt den Absender und eine Adresse zum Abbestellen; Widerspruch gegen Werbung wird sofort beachtet | [§ 7 Abs. 2 Nr. 3 UWG](https://www.gesetze-im-internet.de/uwg_2004/__7.html), [Art. 21 DSGVO](https://dsgvo-gesetz.de/art-21-dsgvo/) |
| Ausnahme Bestandskunden | Werbung für eigene ähnliche Produkte an Kunden, die die Adresse beim Kauf angegeben haben, mit Widerspruchshinweis bei jeder Mail | [§ 7 Abs. 3 UWG](https://www.gesetze-im-internet.de/uwg_2004/__7.html) |

Keine Rechtsberatung; Stand 22.11.2026, vor dem Einsatz mit Datenschutz bzw. Rechtsabteilung klären. Vertieft in Modul 11. Im Kurs versendet nichts: Der Kampagnenplan liegt in Notion, der Versand gehört in ein Marketing-Werkzeug mit Einwilligungsverwaltung (Lab 10.2).

## Übung: Nurturing-Kampagne für ein Segment planen

**Material:** [`kampagnen-vorlage.md`](../material/kampagnen-vorlage.md), [`kundensegmente.md`](../material/kundensegmente.md), [`produktblatt.md`](../material/produktblatt.md), `zielkundenprofil.md` mit der Persona aus [Lab 3.1](../m03-lead-generation/l01-ideal-customer.md) · **Werkzeug:** KI-Assistent, Texteditor, Notion

**Ausgangslage:** In `Leads` stehen Interessenten mit Status „Später pflegen“, aber keiner mit `Einwilligung Werbung`. Für ein Segment entsteht deshalb ein geprüfter Plan mit drei Mails, kein Versand; der Plan liegt als Datenbank `Kampagnen` im Nordwind-CRM.

1. Öffne in Notion `Leads`, filtere auf Status „Später pflegen“ und `Einwilligung Werbung` angehakt (die Liste bleibt leer) und wähle ein Segment außer „Kein Fit“ für den Plan (im Musterergebnis: Mittelstand-Büro, das Segment der Persona aus Lab 3.1).
2. Öffne einen neuen Chat, hänge `kampagnen-vorlage.md`, `produktblatt.md` und `kundensegmente.md` an (oder füge den Text ein), sende Prompt-Karte 10.1a mit der Persona aus `zielkundenprofil.md`.
3. Prüfe die drei Mails mit der Prüfliste der Vorlage und lass Abweichungen im selben Chat korrigieren.
4. Speichere den CSV-Block der Antwort im Texteditor als `kampagnen.csv` und importiere ihn in die Seite „Nordwind CRM“ als Datenbank `Kampagnen` (Schritte in der Vorlage).
5. Kopiere Prompt-Karte 10.1a als „Nurturing-Kampagne (v1)“ in `meine-prompts.md`.

**Prompt-Karte 10.1a – Nurturing-Kampagne entwerfen**

```text
Rolle: Du bist B2B-Marketingreferentin bei Nordwind Workspace GmbH (Lösungen für Besprechungsräume).

Aufgabe: Entwirf eine Nurturing-Kampagne mit genau drei Mails für Leads im Segment [Segment], die Status „Später pflegen“ haben und in Werbe-Mails eingewilligt haben („Einwilligung Werbung“ = ja): Interesse ist da, ein Gespräch ist noch zu früh.

Kontext: Angehängt sind die Kampagnen-Vorlage, das Produktblatt und die Kundensegmente. Persona: [Persona aus zielkundenprofil.md einfügen]

Format:
1. Tabelle: Nr | Abstand in Tagen | Betreff | Kernaussage | Handlungsaufforderung | Segment | Kennzahl
2. Je Mail ein Entwurf mit höchstens 120 Wörtern in Sie-Form, mit Platzhalter [Abmeldelink] im Fuß.
3. Ein CSV-Block mit genau dieser Kopfzeile und drei Zeilen, Freigabe „Freigabe offen“:
Mail,Kampagne,Segment,Nr,Abstand in Tagen,Betreff,Kernaussage,Handlungsaufforderung,Kennzahl,Zielgruppe,Freigabe

Rahmenbedingungen: Fakten nur aus dem Produktblatt; keine Preise, Rabatte oder Liefertermine; je Mail ein Nutzen und eine kleine Handlungsaufforderung; mindestens 7 Tage Abstand; keine künstliche Dringlichkeit. Jede Mail greift Ziel oder Einwand der Persona auf.
```

**Checkpoint:** In „Nordwind CRM“ liegt die Datenbank `Kampagnen` mit drei Zeilen; jede Zeile hat Betreff, Kernaussage, Handlungsaufforderung, Abstand in Tagen, Segment, Kennzahl und Freigabe „Freigabe offen“; keine Mail nennt einen Preis, und nichts wird versendet.

**Erweiterung:** Ergänze in `Leads` die Auswahl-Eigenschaft `Kampagne` und baue in n8n den Workflow „Kampagne zuordnen“: Manual Trigger → Notion „Get Many“ aus `Leads` mit Filter Status = „Später pflegen“ und Segment = „Mittelstand-Büro“ → If-Knoten „Einwilligung Werbung?“ (Feld `property_einwilligung_werbung` ist wahr) → im Ja-Zweig Notion „Update“ mit `Kampagne` = `Nurturing Mittelstand-Büro`; im Übungs-CRM bleibt der Ja-Zweig leer.

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Beispiel aus ChatGPT, Segment Mittelstand-Büro, Persona „Sabine Berger, Leitung Facility Management“ aus Lab 3.1, Stand 22.11.2026 – KI-Antworten fallen jedes Mal etwas anders aus.

**Kampagnenplan „Nurturing Mittelstand-Büro“**

| Nr | Abstand in Tagen | Betreff | Kernaussage | Handlungsaufforderung | Segment | Kennzahl |
| --- | --- | --- | --- | --- | --- | --- |
| 1 | 0 | Doppelbuchungen trotz Outlook? | Panel 10 an der Tür zeigt frei oder belegt und gibt einen Raum frei, wenn innerhalb von 10 Minuten niemand eincheckt; gebucht wird weiter über Outlook bzw. Microsoft 365 | Produktseite Panel 10 öffnen | Mittelstand-Büro | Klickrate auf den Link |
| 2 | 14 | Welche Besprechungsräume werden kaum genutzt? | Book Pro zeigt in Auslastungsberichten, welcher Raum wie oft genutzt wird; die Daten liegen in Frankfurt am Main (EU) | auf die Mail antworten und einen Beispielbericht anfordern | Mittelstand-Büro | Antworten |
| 3 | 21 | Hybride Meetings ohne Laptop-Kamera | Vista bzw. Vista Plus für Räume bis 12 bzw. 20 Personen, ein USB-C-Kabel, kompatibel mit Teams, Zoom und Google Meet | Termin für eine Vorführung vereinbaren | Mittelstand-Büro | Terminanfragen |

**Entwurf Mail 1 (gekürzt)**

> Betreff: Doppelbuchungen trotz Outlook?
>
> Guten Tag Frau Berger,
>
> in vielen Büros sind Räume in Outlook gebucht, aber niemand erscheint – und der nächste sucht vergeblich. Nordwind Panel 10 zeigt an der Tür in Ampelfarben, ob ein Raum frei ist. Checkt innerhalb von 10 Minuten niemand ein, gibt das Display den Raum wieder frei. Gebucht wird weiter wie gewohnt über Outlook bzw. Microsoft 365.
>
> Wie das an der Tür aussieht, zeigt die Produktseite: [Link]
>
> Viele Grüße
> Nordwind Workspace GmbH · [Impressum] · [Abmeldelink]

**Prüfung mit der Prüfliste:** Persona ✓ Mail 1 greift den Einwand „Wir buchen doch schon über Outlook“ auf, Mail 2 das Ziel „Flächen besser auslasten“ · Fakten ✓ alle Angaben im Produktblatt · Zusagen ✓ kein Preis, kein Rabatt, kein Liefertermin · Ton ✓ im ersten Entwurf stand „Nur noch diese Woche: Vorführtermine sichern“ – als künstliche Dringlichkeit gestrichen · Abstand ✓ 14 und 21 Tage · Recht ✓ Abmeldelink und Absender im Fuß; Versand nur an Leads mit `Einwilligung Werbung` = ja, im Übungs-CRM keiner, daher bleibt es beim Plan.

**`kampagnen.csv`**

```text
Mail,Kampagne,Segment,Nr,Abstand in Tagen,Betreff,Kernaussage,Handlungsaufforderung,Kennzahl,Zielgruppe,Freigabe
Mittelstand-Büro – Mail 1,Nurturing Mittelstand-Büro,Mittelstand-Büro,1,0,Doppelbuchungen trotz Outlook?,"Panel 10 zeigt frei oder belegt und gibt Räume frei, wenn nach 10 Minuten niemand eincheckt; Buchung weiter über Outlook",Produktseite Panel 10 öffnen,Klickrate auf den Link,"Status Später pflegen, Segment Mittelstand-Büro, Einwilligung Werbung = ja",Freigabe offen
Mittelstand-Büro – Mail 2,Nurturing Mittelstand-Büro,Mittelstand-Büro,2,14,Welche Besprechungsräume werden kaum genutzt?,"Book Pro zeigt in Auslastungsberichten, wie oft jeder Raum genutzt wird; Daten in Frankfurt am Main (EU)",Antworten und Beispielbericht anfordern,Antworten,"Status Später pflegen, Segment Mittelstand-Büro, Einwilligung Werbung = ja",Freigabe offen
Mittelstand-Büro – Mail 3,Nurturing Mittelstand-Büro,Mittelstand-Büro,3,21,Hybride Meetings ohne Laptop-Kamera,"Vista und Vista Plus für Räume bis 12 bzw. 20 Personen, ein USB-C-Kabel, Teams, Zoom und Google Meet",Termin für eine Vorführung vereinbaren,Terminanfragen,"Status Später pflegen, Segment Mittelstand-Büro, Einwilligung Werbung = ja",Freigabe offen
```

**In Notion:** Datenbank `Kampagnen` unter „Nordwind CRM“, 3 Zeilen, `Nr` und `Abstand in Tagen` als Zahl, `Segment` und `Freigabe` als Auswahl.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Mail nennt Preise oder „10 % Einführungsrabatt“ | Rahmenbedingung fehlt oder Preisliste mitgegeben | Regel „keine Preise, Rabatte, Liefertermine“; nur Produktblatt anhängen |
| Drei Mails mit derselben Botschaft | Format ohne „je Mail ein Nutzen“ | Kernaussage je Mail in der Tabelle vorgeben |
| Import ergibt eine Spalte oder verschobene Werte | Kommas im Text ohne Anführungszeichen | Werte mit Komma in `"…"`, CSV erneut erzeugen lassen |
| Umlaute kaputt nach dem Import | Datei nicht als UTF-8 gespeichert | im Texteditor UTF-8 wählen, nicht über Excel speichern |
| Kampagne zielt auf Leads mit Segment „Kein Fit“ | Filter nur auf Status | zusätzlich Segment filtern |
| Plan sieht Versand an alle Website-Anfragen vor | Anfrage mit Einwilligung in Werbung verwechselt | eine Anfrage ist keine Einwilligung; Zielgruppe „Einwilligung Werbung = ja“ in jede Zeile |
| Filter auf `Einwilligung Werbung` zeigt keinen Lead | im Übungs-CRM hat niemand eingewilligt (gewollt) | Plan trotzdem erstellen; versendet wird nichts |
| `Einwilligung Werbung` fehlt als Filter | Spalte beim Import in Lab 4.1 nicht als Kontrollkästchen eingestellt | Typ auf Kontrollkästchen ändern ([Importanleitung](../material/notion/notion-import-anleitung.md)) |

## Fazit

- Die Customer Journey ordnet jeden Kontaktpunkt einer Stufe und einer Kennzahl zu; die Workflows aus Tag 2 und 3 decken Interesse und Bewertung ab.
- Nurturing hält Leads mit „Später pflegen“ warm: drei Mails, ein Nutzen je Mail, Abstand von Wochen.
- Werbe-Mails brauchen Einwilligung, Absender und Abmeldelink; die KI entwirft, der Mensch prüft und gibt frei.

> **Merksatz:** Nurturing bringt Nutzen in Abständen, nicht Druck in Serie.
