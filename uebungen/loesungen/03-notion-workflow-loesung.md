# Lösung 3: Einen Workflow im Notion-CRM bauen – Schaltfläche „Gespräch erledigt“

Zurück zur [Übung 3](../03-notion-workflow.md).

## Schritt 2–4: Einstellungen der Schaltfläche

Eigenschaft `Gespräch erledigt`, Typ **Schaltfläche** (Button), Aktionen in dieser Reihenfolge:

| Nr. | Aktion | Einstellung |
| --- | --- | --- |
| 1 | Bestätigung anzeigen (Show confirmation) | `Gespräch wirklich erledigt?` |
| 2 | Eigenschaft bearbeiten (Edit property) | `Status` → Gespräch geführt |
| | | `Diese Woche` → kein Häkchen |
| | | `Nächster Schritt` → `Follow-up-Mail senden, Wiedervorlage in 7 Tagen` |

Gespeichert mit **Speichern** (Save). Alle drei Änderungen stehen in **einer** Aktion „Eigenschaft bearbeiten“; drei einzelne Aktionen funktionieren genauso.

Gut, weil die Aktion nur die Zeile ändert, in der geklickt wird, und die Rückfrage einen versehentlichen Klick abfängt.

## Schritt 5: Test an Vogelsang Medizintechnik

| Eigenschaft | vorher | nach dem Klick |
| --- | --- | --- |
| `Status` | Neu | Gespräch geführt |
| `Diese Woche` | ☑ | ☐ |
| `Nächster Schritt` | leer bzw. Text aus Übung 2 | Follow-up-Mail senden, Wiedervorlage in 7 Tagen |
| alle anderen Felder und Leads | – | unverändert |

Gut, weil derselbe Ablauf jetzt bei jedem Lead gleich läuft: ein Klick statt drei Felder von Hand, und kein Schritt geht verloren.

## Noch einmal: Schaltfläche „Später pflegen“

| Nr. | Aktion | Einstellung |
| --- | --- | --- |
| 1 | Bestätigung anzeigen | `Lead wirklich zurückstellen?` |
| 2 | Eigenschaft bearbeiten | `Status` → Später pflegen · `Diese Woche` → kein Häkchen · `Nächster Schritt` → `In 3 Monaten erneut prüfen` |

Test an „Lechfeld Stahlhandel GmbH“: `Status` = Später pflegen, `Diese Woche` ohne Häkchen, `Nächster Schritt` = „In 3 Monaten erneut prüfen“.
