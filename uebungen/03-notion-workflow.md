# Übung 3: Einen Workflow im Notion-CRM bauen – Schaltfläche „Gespräch erledigt“

**Zeit:** ca. 30 Minuten allein · **Werkzeug:** Notion im Browser (ohne KI, kostenloses Konto genügt) · **Material:** Datenbank `Leads` im „Nordwind CRM“ ([Lab 4.1](../m04-notion-crm/l01-crm-basics.md))

## Kurze Wiederholung

Ein Workflow ist ein fester Ablauf: Auslöser → Schritte → Ergebnis. In Notion geht das ohne KI und ohne Zusatzwerkzeug mit einer **Schaltfläche** (Button) als Eigenschaft der Datenbank. Jede Zeile bekommt einen Knopf; ein Klick ändert mehrere Eigenschaften dieses Eintrags auf einmal. So läuft der Ablauf im Team immer gleich, und niemand vergisst einen Schritt. Eine Bestätigungsfrage vor dem Ausführen schützt vor versehentlichen Klicks.

## Zum Nachschlagen

```text
Auslöser:   Klick auf „Gespräch erledigt“ in der Zeile eines Leads
Schritte:   1. Bestätigung anzeigen   „Gespräch wirklich erledigt?“
            2. Eigenschaft bearbeiten  Status           → Gespräch geführt
                                       Diese Woche      → kein Häkchen
                                       Nächster Schritt → Follow-up-Mail senden, Wiedervorlage in 7 Tagen
Ergebnis:   der Lead ist fertig bearbeitet und verschwindet aus der Wochenliste
```

| Begriff | Bedeutung |
| --- | --- |
| Schaltfläche (Button) | Eigenschaftstyp in einer Datenbank: ein Knopf in jeder Zeile, der festgelegte Aktionen ausführt |
| Aktion (Action) | ein Schritt, den die Schaltfläche ausführt, z. B. eine Eigenschaft ändern |
| Eigenschaft bearbeiten (Edit property) | Aktion, die Felder **der Zeile ändert, in der geklickt wurde** |
| Seiten bearbeiten in (Edit pages in) | Aktion, die **viele Einträge einer Datenbank** auf einmal ändert – hier nicht verwenden |
| Bestätigung anzeigen (Show confirmation) | Rückfrage vor dem Ausführen |

## Arbeitsauftrag

Nach jedem Kundengespräch werden im CRM immer dieselben drei Felder geändert: Status, Wochenliste und nächster Schritt. Baue in der Datenbank `Leads` die Schaltfläche **„Gespräch erledigt“**, die das mit einem Klick erledigt, und teste sie am Lead Vogelsang Medizintechnik.

## Schritte

1. Öffne in Notion die Datenbank `Leads` und prüfe: `Status` hat die Option „Gespräch geführt“, `Diese Woche` ist ein Kontrollkästchen (sonst Typen nach [Importanleitung](../material/notion/notion-import-anleitung.md) setzen).
2. Lege eine neue Eigenschaft an: **+** am Ende der Spaltenköpfe (oder **•••** → **Eigenschaften** (Properties) → **Neue Eigenschaft** (New property)) → Typ **Schaltfläche** (Button). Name: `Gespräch erledigt`.
3. Klicke **Automatisierung bearbeiten** (Edit automation) → **Neue Aktion** (New action) → **Bestätigung anzeigen** (Show confirmation) und trage ein: `Gespräch wirklich erledigt?`
4. Klicke **Neue Aktion** → **Eigenschaft bearbeiten** (Edit property) und lege drei Änderungen fest: `Status` → „Gespräch geführt“, `Diese Woche` → kein Häkchen, `Nächster Schritt` → `Follow-up-Mail senden, Wiedervorlage in 7 Tagen`. Klicke **Speichern** (Save).
5. Teste: Setze bei „Vogelsang Medizintechnik GmbH“ das Häkchen bei `Diese Woche` (falls noch nicht gesetzt), klicke in dieser Zeile auf **Gespräch erledigt**, bestätige und prüfe die drei Felder.

## Hinweise und Tipps

| Wenn … | dann … |
| --- | --- |
| der Typ „Schaltfläche“ fehlt | In der englischen Oberfläche heißt er **Button**; in der Typliste nach unten scrollen oder „Schalt“ bzw. „Button“ ins Suchfeld tippen. |
| „Gespräch geführt“ in der Auswahl fehlt | Spaltenkopf `Status` → **Eigenschaft bearbeiten** (Edit property) → Option „Gespräch geführt“ ergänzen, Schreibweise exakt. |
| `Diese Woche` sich nicht auf „kein Häkchen“ stellen lässt | Die Eigenschaft ist noch Text: Typ auf **Kontrollkästchen** (Checkbox) ändern, dann Aktion neu einstellen. |
| der Klick **alle** Leads verändert hat | Es wurde **Seiten bearbeiten in** (Edit pages in) statt **Eigenschaft bearbeiten** gewählt. Aktion löschen, richtige Aktion anlegen; die geänderten Werte von Hand zurücksetzen (Übungsdaten, nichts geht verloren). |
| nach dem Klick nichts passiert | Aktionen wurden nicht gespeichert: Schaltfläche erneut öffnen, **Automatisierung bearbeiten**, Aktionen prüfen, **Speichern**. |
| die Bestätigung nicht kommt | Aktion „Bestätigung anzeigen“ fehlt oder steht nicht an erster Stelle; per Ziehen nach oben schieben. |

Automatisch ohne Klick, etwa „wenn Status geändert wird, dann …“, geht in Notion mit Datenbank-Automationen; die gibt es nur in bezahlten Plänen (Stand 25.11.2026). Die Schaltfläche funktioniert in jedem Plan.

## Erfolgskriterium

- [ ] In `Leads` gibt es die Spalte `Gespräch erledigt` mit einem Knopf in jeder Zeile.
- [ ] Ein Klick fragt zuerst „Gespräch wirklich erledigt?“.
- [ ] Nach dem Bestätigen hat Vogelsang Medizintechnik: `Status` = Gespräch geführt, `Diese Woche` ohne Häkchen, `Nächster Schritt` = „Follow-up-Mail senden, Wiedervorlage in 7 Tagen“.
- [ ] Alle anderen Leads sind unverändert.

Musterlösung: [Lösung 3](loesungen/03-notion-workflow-loesung.md)

## Zurücksetzen und noch einmal

**Zurücksetzen:** Bei Vogelsang `Status` von Hand wieder auf „Neu“ stellen, `Nächster Schritt` leeren und `Diese Woche` anhaken. Danach kann der Test aus Schritt 5 beliebig oft wiederholt werden.

**Noch einmal mit zweiter Schaltfläche:** Schritte 2–5 mit einer Schaltfläche **„Später pflegen“** wiederholen: Bestätigung `Lead wirklich zurückstellen?`, `Status` → „Später pflegen“, `Diese Woche` → kein Häkchen, `Nächster Schritt` → `In 3 Monaten erneut prüfen`. Test am Lead „Lechfeld Stahlhandel GmbH“.

_Quellen: Notion-Hilfe, „Database buttons“ (https://www.notion.com/help/database-buttons), „Buttons“ (https://www.notion.com/help/buttons), „Database automations“ (https://www.notion.com/help/database-automations), alle abgerufen am 25.11.2026. Bezeichnungen je nach Version und Sprache der Oberfläche; deutsche Bezeichnung zuerst, englische in Klammern._
