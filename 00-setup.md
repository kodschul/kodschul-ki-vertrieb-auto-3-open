# Vorbereitung: Konten und Browser

Im Kurs wird nichts installiert, alles läuft im Browser. Nötig sind drei Konten und ein aktueller Browser. Diese Seite einmal vor dem ersten Kurstag durcharbeiten; Dauer etwa 20 Minuten.

## Drei Werkzeuge im Kurs

| Werkzeug | Wofür im Kurs | Konto | Ab |
| --- | --- | --- | --- |
| **KI-Assistent** | recherchieren, bewerten, Texte entwerfen, Daten auswerten, Business Case | ChatGPT, Claude oder Perplexity (kostenloses Konto genügt) oder Microsoft 365 Copilot | Tag 1 |
| **Notion** | Übungs-CRM mit den Datenbanken `Leads` und `Deals`, Ergebnisse | kostenloses Konto mit eigenem Arbeitsbereich | Tag 1 |
| **n8n Cloud** | Workflows, die Anfragen bewerten, Notion pflegen und Entwürfe schreiben | kostenlose Testphase | Tag 2 |

```text
Formular / Zeitplan ──▶ n8n (Workflow) ──▶ KI-Schritt ──▶ Notion (CRM)
                              ▲                               │
                              └──── KI-Assistent im Chat: verstehen, konzipieren, prüfen
```

## Browser und Netzwerk

- Aktueller Chrome oder Edge.
- Diese Seiten müssen im Firmennetz erreichbar sein: `chatgpt.com`, `claude.ai`, `perplexity.ai`, `n8n.io`, `app.n8n.cloud` bzw. die eigene `*.app.n8n.cloud`-Adresse, `notion.so`, `raw.githubusercontent.com` (Firmenprofile für Lab 8.1).
- Pop-ups für `notion.so` und `n8n.cloud` erlauben (Anmeldefenster beim Verbinden).

## KI-Assistent einrichten

1. Öffne einen der Assistenten und registriere ein Konto bzw. melde das vorhandene an: [chatgpt.com](https://chatgpt.com), [claude.ai](https://claude.ai), [perplexity.ai](https://www.perplexity.ai) oder Microsoft 365 Copilot im Firmenkonto.
2. Stelle eine Testfrage („Nenne drei Aufgaben im Vertrieb, bei denen KI hilft.“).
3. Prüfe, ob die Websuche funktioniert („Was ist heute die wichtigste Nachricht zu KI? Nenne die Quelle.“).

Ein Konto genügt. Kostenlose Konten haben Tageslimits für Datei-Uploads und Websuche (Stand: 22.11.2026, je Anbieter unterschiedlich). Die Übungsdaten sind deshalb so klein, dass sie notfalls als Text in den Chat kopiert werden können.

## Notion einrichten

1. Registriere ein kostenloses Konto auf [notion.so](https://www.notion.so) (E-Mail, Google- oder Apple-Konto).
2. Lege einen eigenen Arbeitsbereich an, z. B. „Kurs KI im Vertrieb“; einen bestehenden Firmen-Arbeitsbereich nicht verwenden.
3. Lege eine leere Seite „Nordwind CRM“ an. Die Datenbanken entstehen im Kurs per Import (Lab 4.1 und 4.2, Anleitung: [`material/notion/notion-import-anleitung.md`](material/notion/notion-import-anleitung.md)).

## n8n Cloud einrichten

> **Zeitpunkt:** Die Testphase läuft 14 Tage ab der Registrierung. Das Konto frühestens etwa eine Woche vor Kursbeginn anlegen, damit die Testphase alle drei Kurstage abdeckt.

1. Öffne [n8n.io](https://n8n.io) und starte die kostenlose Testphase („Get started“ bzw. „Start free trial“, Bezeichnung je nach Version); eine Kreditkarte ist nicht nötig.
2. Bestätige die E-Mail-Adresse und wähle einen Namen für den Arbeitsbereich; daraus entsteht die eigene Adresse `<name>.app.n8n.cloud`.
3. Öffne die Arbeitsfläche einmal und lege einen leeren Workflow an. Mehr ist vor dem Kurs nicht nötig.

| Testphase n8n Cloud | Stand: 22.11.2026 |
| --- | --- |
| Dauer | 14 Tage, Funktionsumfang des Pro-Tarifs |
| Ausführungen | 1000 |
| KI-Schritte | enthaltene „Gateway credits“, kein eigener API-Schlüssel nötig; Aufladen in der Testphase nicht möglich |
| Nach Ablauf | Instanz wird gelöscht; Workflows vorher exportieren (Lab 9.3) |

_Quelle: n8n Docs, „Start your free trial“ (https://docs.n8n.io/deploy/use-n8n-cloud/start-your-free-trial) und „Gateway credits“ (https://docs.n8n.io/deploy/use-n8n-cloud/gateway-credits), abgerufen am 22.11.2026._

## Kurzcheck vor Tag 1

| Prüfpunkt | Erwartung |
| --- | --- |
| KI-Assistent | Testfrage beantwortet, Websuche liefert eine Quelle |
| Notion | Seite „Nordwind CRM“ sichtbar |
| n8n | Arbeitsfläche öffnet sich unter `<name>.app.n8n.cloud` |
| Kursmaterial | Ordner [`material/`](material/) erreichbar |

## Was nicht in die Werkzeuge gehört

Im Kurs werden nur die fiktiven Nordwind-Daten verwendet. Echte Kundendaten, Namen, Preise und Zugangsdaten gehören nicht in die Übungskonten. Die Regeln dazu folgen in [Lab 1.3](m01-ai-sales-basics/l03-data-rules.md).
