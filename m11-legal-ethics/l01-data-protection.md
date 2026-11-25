# Lab 11.1: Datenschutz und Compliance in KI-Vertriebsprozessen

**Leitfragen:**

<details>
<summary>Welche Angaben aus einer Anfrage braucht die KI wirklich, um eine Firma zu bewerten?</summary>

Nur Firmendaten und Bedarf: Firma, Website, Mitarbeitende, Räume, Region, Nachricht. Name, E-Mail und Rolle der Ansprechperson zählen in der Bewertungsmatrix aus 3.3 nicht: Name und E-Mail bleiben seit Lab 7.2 draußen, die Rolle ab diesem Lab.

</details>

<details>
<summary>Wer darf erfahren, welche Daten über ihn im CRM stehen?</summary>

Jede Person, deren Daten gespeichert sind: Die DSGVO gibt ein Recht auf Auskunft (Art. 15), auf Berichtigung und Löschung (Art. 16, 17) und auf Widerspruch gegen Werbung (Art. 21).

</details>

<details>
<summary>Darf eine Software allein entscheiden, dass ein Interessent nie zurückgerufen wird?</summary>

Bei Entscheidungen mit erheblicher Wirkung auf eine Person nur in engen Ausnahmen (Art. 22 DSGVO). Im Kurs bleibt der Score eine Empfehlung: Ein Mensch prüft jeden Lead und entscheidet.

</details>

- Ein KI-Workflow im Vertrieb verarbeitet personenbezogene Daten an mehreren Stellen: Formular, n8n, KI-Anbieter, Notion. Für jede Stelle gilt die DSGVO.
- Datenminimierung ist die wirksamste Maßnahme: Was nie an die KI geht, muss dort auch nicht geschützt werden.

Keine Rechtsberatung. Stand: 22.11.2026, vor Kursbeginn prüfen; verbindlich sind die Vorgaben des eigenen Unternehmens und seiner Datenschutzbeauftragten.

## Begriffe

| Begriff | Bedeutung |
| --- | --- |
| Rechtsgrundlage | Erlaubnis aus Art. 6 DSGVO, ohne die keine Verarbeitung personenbezogener Daten zulässig ist |
| Einwilligung | ausdrückliche, freiwillige Zustimmung einer Person, jederzeit widerrufbar |
| berechtigtes Interesse | Erlaubnis, wenn das eigene Interesse (z. B. Kundenpflege) die Interessen der Person überwiegt; braucht eine Abwägung |
| Datenminimierung | nur die Daten verarbeiten, die für den Zweck nötig sind (Art. 5 DSGVO) |
| Auftragsverarbeitung | ein Dienstleister verarbeitet Daten im Auftrag und nach Weisung, z. B. n8n oder Notion; geregelt im Auftragsverarbeitungsvertrag (AVV, Art. 28) |
| Unterauftragsverarbeiter | Dienstleister des Dienstleisters, z. B. der KI-Anbieter hinter den Gateway credits von n8n |
| Drittland | Staat außerhalb der EU bzw. des EWR, z. B. die USA |
| Angemessenheitsbeschluss | Entscheidung der EU-Kommission, dass ein Drittland ein vergleichbares Schutzniveau bietet (Art. 45) |
| Data Privacy Framework (DPF) | Angemessenheitsbeschluss für US-Unternehmen, die sich zertifiziert haben (seit 10.07.2023) |
| Standardvertragsklauseln | von der EU-Kommission vorgegebene Vertragstexte für Übermittlungen in Drittländer ohne Angemessenheitsbeschluss |
| automatisierte Einzelentscheidung | Entscheidung über eine Person, die ausschließlich eine Software trifft, ohne prüfenden Menschen (Art. 22) |

## DSGVO-Regeln im Vertriebsalltag

![Erste Seite der Verordnung (EU) 2016/679 im Amtsblatt der Europäischen Union L 119 vom 04.05.2016 (englische Fassung): Titel „Regulation (EU) 2016/679 … General Data Protection Regulation“ und die ersten drei Erwägungsgründe](https://upload.wikimedia.org/wikipedia/commons/thumb/2/28/GDPR_p1.svg/500px-GDPR_p1.svg.png)
_Quelle: Wikimedia Commons, „GDPR p1.svg“ (https://commons.wikimedia.org/wiki/File:GDPR_p1.svg), Europäisches Parlament und Rat, Amtsblatt der EU, gemeinfrei, abgerufen am 22.11.2026._

Die DSGVO gilt seit 25.05.2018 in allen EU-Staaten direkt. Firmen sind nicht geschützt, Personen schon: Name, Mail und Durchwahl einer Ansprechperson sind personenbezogen (Lab 1.3).

| Regel | Artikel | Im Vertrieb |
| --- | --- | --- |
| Rechtsgrundlage: Vertrag bzw. Anfrage | Art. 6 Abs. 1 b | Antwort auf eine Anfrage, Angebot auf Wunsch des Interessenten |
| Rechtsgrundlage: Einwilligung | Art. 6 Abs. 1 a | Newsletter, Werbe-Mails, Kampagnen aus Lab 10.1 |
| Rechtsgrundlage: berechtigtes Interesse | Art. 6 Abs. 1 f | Kontakt eines Bestandskunden im CRM pflegen, Ansprechperson mit Rolle recherchieren; Abwägung dokumentieren |
| Datenminimierung, Speicherbegrenzung | Art. 5 Abs. 1 c, e | nur nötige Felder, Leads ohne Kontakt nach festgelegter Frist löschen |
| Information | Art. 13 | Datenschutzhinweis am Formular: wer, wozu, welche Dienstleister, wie lange |
| Auskunft, Löschung, Widerspruch | Art. 15, 17, 21 | Anfrage „Was speichern Sie über mich?“ binnen eines Monats beantworten; Widerspruch gegen Werbung stoppt jede Werbung |
| Auftragsverarbeitung | Art. 28 | AVV mit n8n, Notion, KI-Anbieter, CRM-Anbieter |
| Drittland | Art. 44–46 | Daten in die USA nur mit DPF-Zertifizierung des Empfängers oder Standardvertragsklauseln |
| automatisierte Einzelentscheidung | Art. 22 | Score als Empfehlung, Mensch entscheidet |

_Quellen: Verordnung (EU) 2016/679 (https://eur-lex.europa.eu/eli/reg/2016/679/oj); Gesetzestext mit Artikeln, z. B. Art. 6 (https://dsgvo-gesetz.de/art-6-dsgvo/), Art. 22 (https://dsgvo-gesetz.de/art-22-dsgvo/), Art. 28 (https://dsgvo-gesetz.de/art-28-dsgvo/); abgerufen am 22.11.2026._

Änderungen an der DSGVO im „Digital Omnibus“ (Vorschlag der EU-Kommission vom 19.11.2025, u. a. zu Art. 22) sind Stand 22.11.2026 nicht beschlossen, das Verfahren 2025/0360(COD) läuft noch; prüfen.

## Werbung per Mail und Telefon nach UWG § 7

Wiederholung aus Lab 3.4: Datenschutz erlaubt eine Verarbeitung, das Werberecht regelt den Kontaktweg. Beides muss passen.

| Kanal | Regel | Fundstelle |
| --- | --- | --- |
| Werbe-Mail, auch B2B | nur mit vorheriger ausdrücklicher Einwilligung | § 7 Abs. 2 Nr. 2 UWG |
| Werbe-Mail an Bestandskunden | erlaubt für eigene ähnliche Produkte, wenn kein Widerspruch vorliegt und bei jeder Mail auf das Widerspruchsrecht hingewiesen wird | § 7 Abs. 3 UWG |
| Telefon B2B | mit zumindest mutmaßlicher Einwilligung | § 7 Abs. 2 Nr. 1 UWG |
| Antwort auf eine Anfrage | erlaubt, ist keine unerwünschte Werbung | – |

_Quelle: § 7 UWG (https://www.gesetze-im-internet.de/uwg_2004/__7.html), abgerufen am 22.11.2026._

Deshalb versendet kein Workflow im Kurs selbst: Der Antwortentwurf auf eine Formular-Anfrage wartet in Notion mit „Freigabe offen“ (Lab 8.2).

## Dienstleister im Lead-Eingang und ihr Speicherort

```text
Formular (n8n) ──► n8n Cloud ──► KI-Modell (Gateway credits) ──► Ergebnis zurück an n8n ──► Notion
   Anfrage         Azure, EU      OpenAI, USA                                                 AWS, USA
```

| Dienst | Rolle | Speicherort laut Anbieter | Grundlage für Drittland | Quelle |
| --- | --- | --- | --- | --- |
| n8n Cloud | Auftragsverarbeiter (AVV vorhanden) | Microsoft Azure in der EU | – | n8n „Security“ (https://n8n.io/legal/security/), „Data Processing Agreement“ (https://n8n.io/legal/data-processing-agreement/) |
| KI-Modell über Gateway credits | Unterauftragsverarbeiter von n8n | OpenAI und Anthropic: USA | Vertrag zwischen n8n und Anbieter; im Einzelfall prüfen | n8n „Sub-processors“, Stand 22.09.2026 (https://n8n.io/legal/sub-processors/) |
| OpenAI direkt (eigener API-Schlüssel) | Auftragsverarbeiter mit eigenem Data Processing Addendum | Server außerhalb des EWR, u. a. USA; EU-Datenresidenz für API und Enterprise wählbar | Angemessenheitsbeschlüsse, Standardvertragsklauseln | OpenAI „EU Privacy Policy“, Stand 24.08.2026 (https://openai.com/policies/eu-privacy-policy/), „Data Processing Addendum“ (https://openai.com/policies/data-processing-addendum/) |
| Notion | Auftragsverarbeiter (DPA mit Standardvertragsklauseln) | standardmäßig USA (AWS); EU (Frankfurt) nur im Enterprise-Tarif | Standardvertragsklauseln laut Notion; DPF-Teilnahme in der DPF-Liste prüfen | Notion „Data residency“ (https://www.notion.com/help/data-residency), „GDPR at Notion“ (https://www.notion.com/help/gdpr-at-notion) |

Stand: 22.11.2026, alle Angaben vor Kursbeginn prüfen. Der DPF-Angemessenheitsbeschluss gilt; das Gericht der EU hat eine Klage am 03.09.2025 abgewiesen, ein Rechtsmittel beim EuGH (C-703/25 P) ist anhängig. Zertifizierte US-Firmen stehen in der DPF-Liste (https://www.dataprivacyframework.gov/list).

So sieht die Wahl des Speicherorts in Notion aus (Enterprise-Tarif; kostenlose und kleine Tarife speichern in den USA):

![Notion-Einstellungen „Data residency“: Bereich „Workspace regions – View where your data is stored“ und Auswahl „Default data residency“ mit den Regionen United States, Europe, Japan und South Korea](https://images.ctfassets.net/spoqsaf9291f/1y5ltYVaaSbXOly3vW7TxJ/3392f4942fff8f4c9307d3b89857cfd1/image__2_.png)
_Quelle: Notion Help Center, „Data residency for Notion“ (https://www.notion.com/help/data-residency), © Notion Labs, abgerufen am 22.11.2026._

## Lead-Scoring und automatisierte Entscheidungen nach Art. 22

- Art. 22 DSGVO: Niemand muss eine Entscheidung hinnehmen, die ausschließlich eine Software trifft und die rechtlich wirkt oder ähnlich erheblich beeinträchtigt.
- Der EuGH hat am 07.12.2023 entschieden (C-634/21, „SCHUFA“): Schon ein Score kann eine solche Entscheidung sein, wenn er das Ergebnis maßgeblich bestimmt.
- Lead-Scoring bewertet Firmen, berührt aber Personen: Wer „nie zurückgerufen“ wird, weil eine Zahl unter 40 liegt, wurde von der Software aussortiert.
- Im Kurs deshalb: Der Score setzt nur einen Status-Vorschlag („Heiß“, „Später pflegen“, „Prüfen“); aussortiert („Kein Fit“) wird nur von Hand, jede Bewertung hat eine Begründung.

_Quelle: EuGH, Urteil vom 07.12.2023, C-634/21 (https://eur-lex.europa.eu/legal-content/DE/TXT/?uri=CELEX:62021CJ0634), abgerufen am 22.11.2026._

## Prüfliste für einen KI-Workflow

| Nr. | Prüfpunkt | Frage | Lead-Eingang nach diesem Lab |
| --- | --- | --- | --- |
| 1 | Zweck | Wofür werden die Daten verarbeitet? | Anfragen beantworten und priorisieren |
| 2 | Rechtsgrundlage | Welcher Buchstabe in Art. 6 Abs. 1 trägt? | b: Anfrage der Person |
| 3 | Datenminimierung | Welche Felder bekommt jeder KI-Schritt, und braucht er sie? | nur Firmendaten und Nachricht |
| 4 | Rote Daten | Können Gesundheits- oder andere Art.-9-Daten im Freitext stehen? | Hinweis im Formular, Prüfung beim Freigeben |
| 5 | Auftragsverarbeitung | Gibt es mit jedem Dienst einen AVV? | n8n, Notion, KI-Anbieter |
| 6 | Drittland | Wo liegen die Daten, auf welcher Grundlage? | Tabelle oben |
| 7 | Information | Erfährt die Person, dass KI und welche Dienste beteiligt sind? | Datenschutzhinweis, Formularhinweis (Lab 11.2) |
| 8 | Entscheidung | Entscheidet am Ende ein Mensch? | Score nur Vorschlag, Freigabe offen |
| 9 | Werberecht | Geht etwas ohne Einwilligung als Werbung raus? | nein, nur Antwort auf Anfrage nach Freigabe |
| 10 | Speicherdauer | Wann wird gelöscht, auch in Ausführungsprotokollen? | Leads ohne Kontakt nach festgelegter Frist; n8n Cloud hält Ausführungsprotokolle je Tarif 7 Tage (Starter) oder 30 Tage (Pro), Enterprise unbegrenzt |
| 11 | Betroffenenrechte | Lassen sich Auskunft und Löschung in allen Systemen erfüllen? | Lead in Notion suchen, löschen, Ausführungen in n8n löschen |
| 12 | Kennzeichnung | Ist sichtbar, was die KI bewertet oder entworfen hat? | Feld „KI-gestützt“ |

_Quelle Zeile 10: n8n Docs, „Cloud data management“ (https://docs.n8n.io/manage-cloud/cloud-data-management/), Stand 22.11.2026, prüfen._

## Übung: Lead-Eingang datensparsam umbauen

**Material:** Workflow „Lead-Eingang“ aus Lab 8.2, [`testanfragen.md`](../material/testanfragen.md) (T1) · Rückfallebene: Musterworkflow [`m11-l01-datensparsam.json`](../material/workflows/m11-l01-datensparsam.json) importieren ([Anleitung](../material/workflows/README.md)) · **Werkzeug:** n8n, Notion

**Ausgangslage:** Im Lead-Eingang aus Lab 8.2 bekommen „Lead bewerten“ und „Antwortentwurf schreiben“ noch die Rolle der Ansprechperson (Name und E-Mail schon seit Lab 7.2 nicht), und den Namen in der Anrede ergänzt bisher ein Mensch. Die Matrix braucht die Rolle nicht, und die Anrede mit Namen lässt sich ohne KI setzen. Menü- und Feldnamen: Bezeichnung je nach Version.

1. Öffne in n8n den Workflow „Lead-Eingang“, öffne den Knoten „Lead bewerten“ und lösche im Feld „Text“ die Zeile `Rolle der Ansprechperson:`. Ergänze in der Systemanweisung die Regel aus Prompt-Karte 11.1a.
2. Öffne „Antwortentwurf schreiben“, lösche im Feld „Prompt (User Message)“ die Zeile `Rolle:` und ersetze in der Systemnachricht die Anrede-Regel durch Prompt-Karte 11.1b. Ergänze in „Anfrage zusammenfassen“ ebenfalls die Regel aus 11.1a.
3. Prüfe in Notion, dass die Eigenschaft `KI-gestützt` den Typ Kontrollkästchen hat, und gib ihr die Beschreibung „KI-gestützt bewertet, vom Menschen geprüft“.
4. Öffne „Lead in Notion anlegen“: Setze im Feld `Antwortentwurf` (Modus „Expression“) den Ausdruck aus dem Block „Anrede im Notion-Knoten“ und füge über „Add Property“ die Eigenschaft `KI-gestützt` mit Häkchen hinzu. Speichere den Workflow.
5. Sende T1 über das Testformular und vergleiche den neuen Notion-Eintrag mit dem T1-Eintrag aus Lab 8.2: Score, Stufe, Begründung, Entwurf. Öffne die Ausführung und prüfe die Eingabe jedes KI-Knotens.

**Prompt-Karte 11.1a – Regel gegen Personendaten in der Nachricht**

```text
- Personennamen und Kontaktdaten aus der Nachricht werden nicht übernommen; bewertet wird nur die Firma und ihr Bedarf.
```

**Prompt-Karte 11.1b – Antwortentwurf ohne Namen**

```text
- Beginne direkt mit dem ersten Satz nach der Anrede; die Anrede mit Namen ergänzt der Workflow.
```

**Anrede im Notion-Knoten** (Feld `Antwortentwurf`, Ausdruck):

```text
Guten Tag {{ $('Lead-Anfrage').item.json.Name }},

{{ $('Antwortentwurf schreiben').item.json.text }}
```

**Checkpoint:** Kein KI-Knoten bekommt die Formularfelder Name, E-Mail oder Rolle (ein Name im Gruß der Nachricht bleibt, siehe Musterergebnis). Der neue T1-Eintrag in Notion hat dieselbe Stufe wie in Lab 8.2, einen Entwurf, der mit „Guten Tag Johanna Weiß,“ beginnt, und ein Häkchen bei `KI-gestützt`.

**Erweiterung:** Die Prüfliste oben Zeile für Zeile für den Workflow „Gesprächsnotiz“ aus Lab 9.1 durchgehen; dort enthält die Notiz selbst Namen.

## Musterergebnis

<details>
<summary>Musterergebnis anzeigen</summary>

Beispiel – KI-Ergebnisse fallen jedes Mal etwas anders aus. Knotennamen und Ausdrücke wie im Musterworkflow `m11-l01-datensparsam.json`, Stand 22.11.2026.

**Welche Felder welcher Knoten bekommt**

| Knoten | vorher (Lab 8.2) | nachher (Lab 11.1) |
| --- | --- | --- |
| Firmenprofil zusammenfassen | Website, Seiteninhalt | unverändert |
| Anfrage zusammenfassen | Firma, Mitarbeitende, Anzahl Räume, Region, Nachricht | unverändert, plus Regel 11.1a |
| Lead bewerten | Firma, Website, **Rolle**, Mitarbeitende, Anzahl Räume, Region, Nachricht, Firmenprofil | Firma, Website, Mitarbeitende, Anzahl Räume, Region, Nachricht, Firmenprofil; Regel 11.1a |
| Antwortentwurf schreiben | Firma, **Rolle**, Nachricht, Bewertung; Anrede „Guten Tag,“ ohne Namen | Firma, Nachricht, Bewertung; Regel 11.1b |
| Lead in Notion anlegen | alle Felder, Entwurf von der KI, Name in der Anrede von Hand | alle Felder (Name und E-Mail für das CRM), Anrede mit Namen vor dem Entwurf, `KI-gestützt` = angehakt |

**Notion-Eintrag T1 – Steuerkanzlei Lorenzen & Partner mbB**

| Eigenschaft | Wert |
| --- | --- |
| Score | 79 (in Lab 8.2: 79) |
| Stufe / Status | heiß / Heiß |
| Begründung | Fit 46/60: Kanzlei (20), 48 MA (6), 6 Räume (10), DE-Süd (10). Interesse 33/40: zweiter Standort Offenburg ab 01.03.2027 laut Firmenprofil (25), Termin März 2027 (8). |
| Ansprechperson / E-Mail | Johanna Weiß / j.weiss@lorenzen-partner.example (direkt aus dem Formular) |
| KI-gestützt | ☑ |
| Freigabe | Freigabe offen |

**Antwortentwurf in Notion**

> Guten Tag Johanna Weiß,
>
> vielen Dank für Ihre Anfrage. Für Videokonferenzen mit Mandanten in Ihren sechs Besprechungsräumen passt unser Kamera-Set Nordwind Vista: 4K-Kamera, die der sprechenden Person folgt, Lautsprecher-Mikrofon-Leiste und ein USB-C-Kabel zum Laptop, kompatibel mit Microsoft Teams, Zoom und Google Meet. Für Ihre zwei größeren Räume lohnt ein Blick auf Vista Plus. Einen Preisrahmen besprechen wir gern in einem 20-minütigen Telefonat, in dem wir auch Ihren neuen Standort berücksichtigen. Passt Ihnen ein Termin in den nächsten Tagen?
>
> Viele Grüße
> Vertriebsteam Nordwind Workspace

Warum gut: Score und Stufe bleiben gleich, weil die Matrix keine Personendaten bewertet; die Anrede stimmt sicher, weil sie aus dem Formular kommt statt von Hand oder aus der KI. Grenze: Was in der Nachricht selbst steht (hier der Gruß „Johanna Weiß“), erreicht die KI weiterhin; Regel 11.1a verhindert nur, dass es in die Ergebnisse übernommen wird.

</details>

## Typische Fehler

| Symptom | Ursache | Lösung |
| --- | --- | --- |
| Entwurf beginnt mit „Guten Tag Johanna Weiß, Guten Tag,“ | alte Anrede-Regel steht noch in der Systemnachricht | Regel durch Prompt-Karte 11.1b ersetzen |
| Entwurf beginnt mit „Guten Tag ,“ | Ausdruck verweist auf ein falsches Feld | `$('Lead-Anfrage').item.json.Name` genau so schreiben, Knotenname „Lead-Anfrage“ prüfen |
| Notion meldet einen Fehler bei `KI-gestützt` | Eigenschaft fehlt, ist Text statt Kontrollkästchen oder anders geschrieben | Typ in Notion auf Kontrollkästchen setzen, Schreibweise mit Bindestrich prüfen |
| Name taucht in der Zusammenfassung auf | Name steht im Gruß der Nachricht | Regel 11.1a auch in „Anfrage zusammenfassen“ ergänzen |
| Score deutlich anders als in Lab 8.2 | Firmenprofil-Zeile beim Löschen mit entfernt | Feld „Text“ in „Lead bewerten“ mit der Tabelle im Musterergebnis abgleichen |

## Fazit

- Für jeden Schritt eines Workflows gilt: Rechtsgrundlage, AVV, Speicherort, nur nötige Felder.
- Name, E-Mail und Rolle helfen der Bewertung nicht; ohne sie bleibt der Score gleich und weniger Daten verlassen das CRM.
- Der Score ist eine Empfehlung; entschieden und freigegeben wird von einem Menschen.
- Werbung per Mail braucht eine Einwilligung; eine Antwort auf eine Anfrage nicht.

> **Merksatz:** Was die KI nicht braucht, bekommt sie nicht – die Anrede setzt der Workflow, die Entscheidung der Mensch.
