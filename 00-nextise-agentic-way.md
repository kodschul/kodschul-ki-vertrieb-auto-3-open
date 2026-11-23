# The Nextise Agentic Way – KI nutzen, um KI zu bauen

- Dieser Kurs ist keine Klick-Schulung für einzelne Werkzeuge. Das Ziel: Vertriebsaufgaben so mit KI lösen, dass am Ende eine Automatisierung steht, die die KI selbst mitentworfen hat.
- Die KI kann bereits fast alles formulieren, bewerten und entwerfen. Die eigene Rolle ist nicht mehr, ihr jeden Handgriff beizubringen, sondern sie zu führen, damit sie das Richtige tut.

## Häufigster Fehler beim Bauen mit KI

Wer der KI direkt eine Lösung bestellt („bau mir einen Workflow, der Leads bewertet“), überträgt ein unausgereiftes eigenes Lösungsbild. Stimmt das Problemverständnis nicht, baut die KI zuverlässig die falsche Lösung für das falsche Problem.

## Drei Schritte von Problem zu Lösung

```text
1. Problem verstehen    →   2. Lösung konzipieren   →   3. Lösung bauen
   von Hand, im Chat,          Auslöser, Schritte,         Workflow in n8n,
   mit echten Fällen           Daten, Freigaben            Anweisungen für die KI
```

| Schritt | Leitfrage | Im Kurs |
| --- | --- | --- |
| **1. Problem verstehen** | Was genau ist das Problem, unabhängig von jeder Lösungsidee? | Tag 1: Leads finden, bewerten, ansprechen, im CRM pflegen – alles erst von Hand mit dem KI-Assistenten |
| **2. Lösung konzipieren** | Welche Schritte, Daten und Freigaben lösen dieses Problem? | Tag 2–3: Workflow-Konzepte mit dem Workflow-Architekten |
| **3. Lösung bauen** | Wie wird das Konzept konkret umgesetzt und getestet? | Tag 2–3: Workflows in n8n, Systemanweisungen vom Systemanweisungs-Generator |

> **Merksatz:** Der Mensch entscheidet in jedem Schritt: welches Problem gelöst wird, welches Konzept überzeugt und was an Kunden rausgeht.

## Drei-Assistenten-Kette

Statt eines einzigen Chats für alles arbeiten drei spezialisierte Assistenten nacheinander. Jeder bekommt das Ergebnis des vorherigen als Eingabe und kennt damit den Zusammenhang. Die Rollen-Prompts stehen in [`material/assistenten-prompts.md`](material/assistenten-prompts.md); jeder Prompt wird am Anfang eines eigenen, neuen Chats eingefügt und funktioniert in ChatGPT, Claude, Perplexity und Microsoft 365 Copilot.

```text
Vertriebsproblem
  → [1] Use-Case-Coach              → Use-Case-Canvas, Bewertung, Top-1-Empfehlung
  → [2] Workflow-Architekt          → Workflow-Konzept, Business Case, Übergabepaket
  → [3] Systemanweisungs-Generator  → getestete Anweisung für den KI-Schritt in n8n
```

| # | Assistent | Eingabe | Ausgabe | Angewendet in |
| - | --------- | ------- | ------- | ------------- |
| 1 | **Use-Case-Coach** | frei formuliertes Vertriebsproblem | Canvas (Problem, Zielgruppe, Ist- und Soll-Ablauf, Nutzen, Daten, Risiken), Bewertung je 1–5 Punkte, Top-1-Empfehlung | [Lab 12.1](m12-strategy-business-case/l01-use-case.md) |
| 2 | **Workflow-Architekt** | Problem + gewählter Use Case | Auslöser, Schritte, Felder, KI-Schritte, Freigabepunkte, Testfälle, Business Case und Pilotplan | [Lab 9.2](m09-sales-automation/l02-daily-briefing.md), [Lab 12.2](m12-strategy-business-case/l02-solution-design.md) |
| 3 | **Systemanweisungs-Generator** | Problem + Konzept + ein KI-Schritt | Systemanweisung für den KI-Schritt, Testfälle, Verbesserung nach beobachteten Fehlern | [Lab 7.2](m07-ai-workflows/l02-auto-scoring.md), [Lab 7.3](m07-ai-workflows/l03-testing.md), [Lab 9.2](m09-sales-automation/l02-daily-briefing.md), [Lab 12.2](m12-strategy-business-case/l02-solution-design.md) |

## Warum die Kette bessere Ergebnisse liefert

- Jeder Assistent hat eine einzige Aufgabe und fragt gezielt nach, statt alles auf einmal zu raten.
- Das Ergebnis jedes Schritts ist sichtbar und wird geprüft, bevor der nächste beginnt.
- Fehler fallen früh auf: ein falsch verstandenes Problem im Canvas, nicht erst im fertigen Workflow.

## Weg durch die drei Kurstage

| Tag | Schritt | Ergebnis |
| --- | ------- | -------- |
| 1 | Problem verstehen | Zielkundenprofil, bewertete Leads, Erstansprache, Nordwind-CRM in Notion |
| 2 | Konzipieren und bauen am Nordwind-Fall | Workflow „Lead-Eingang“ mit KI-Bewertung, Anreicherung und Antwortentwurf |
| 3 | Konzipieren und bauen mit der Kette, dann am eigenen Fall | Follow-up- und Briefing-Workflow, eigener Business Case mit Workflow-Konzept |
