# Übung 2: Notion mit dem KI-Assistenten verbinden und einen Agenten arbeiten lassen

**Zeit:** ca. 30 Minuten allein · **Werkzeug:** Claude oder ChatGPT im Browser + Notion (Gemini: im Paar, siehe unten) · **Material:** Datenbank `Leads` im „Nordwind CRM“ ([Lab 4.1](../m04-notion-crm/l01-crm-basics.md))

## Kurze Wiederholung

MCP (Model Context Protocol) ist ein offener Standard, über den ein KI-Assistent an andere Programme andockt, ähnlich wie USB-C: ein Stecker für viele Geräte. Claude nennt so eine Verbindung **Konnektor** (Connector), ChatGPT nennt sie **App** bzw. **Plugin**. Mit der Notion-Verbindung liest der Assistent die Datenbanken im Nordwind CRM selbst und kann Einträge ändern; niemand muss Daten hineinkopieren. Der Assistent arbeitet dabei als **Agent**: Er plant die Schritte, ruft die Notion-Werkzeuge auf und meldet das Ergebnis. Der Mensch prüft den Plan, gibt ihn frei und kontrolliert danach in Notion.

## Zum Nachschlagen

```text
KI-Assistent  ──(Notion-Verbindung = MCP)──►  Notion
  │                                            │
  plant, fragt nach Freigabe                   Seite „Nordwind CRM“ → Datenbank „Leads“
  liest und schreibt Felder                    Felder: Region, Rolle, Kaufsignal, Diese Woche, Nächster Schritt …
```

| | **Claude** | **ChatGPT** |
| --- | --- | --- |
| Notion verbinden | **Customize > Connectors > Browse** → **Notion** → **Connect** | **Settings > Plugins** (ältere Oberfläche: **Apps**) → **Notion** → **Connect** |
| im Chat einschalten | **+ > Connectors** → Notion einschalten | über **+** Notion auswählen oder im Prompt „Nutze Notion“ schreiben |
| vor Änderungen fragen lassen | **Customize > Connectors > Notion > Tool permissions**: Schreibwerkzeuge auf **Needs approval** | **Settings > Plugins > Permissions**: **Always ask** |
| Verbindung trennen | **Customize > Connectors > Notion > Disconnect** | **Settings > Plugins** → Notion → trennen |

In beiden Fällen öffnet sich ein Notion-Fenster: Übungs-Arbeitsbereich wählen und den Zugriff bestätigen.

**Gemini:** Für die Gemini-App ist eine Verbindung zu Notion offiziell nicht beschrieben (Stand 25.11.2026). Übung 2 deshalb im Paar mit einer Person machen, die Claude oder ChatGPT nutzt: abwechselnd Prompt senden und in Notion prüfen.

![Claude-Fenster „Connectors“: Verzeichnis mit Kacheln für Asana, Atlassian, Canva, Gmail, Google Calendar, Google Drive, Notion und weitere, je mit Plus-Zeichen zum Verbinden](https://assets.claude.com/78b167a1a7db601cd0ff39356d03e9925e59baba.png)
_Beispiel Claude. Quelle: Anthropic, „Discover tools that work with Claude“ (https://claude.com/blog/connectors-directory), 14.07.2025, abgerufen am 15.11.2026._

## Arbeitsauftrag

Eine neue Kollegin übernimmt ab sofort die Region **DE-Süd**. Der Assistent soll die Leads dieser Region im Nordwind CRM finden, sie für diese Woche markieren und bei jedem einen konkreten nächsten Schritt eintragen. Er zeigt vorher den Plan; geändert wird erst nach der Freigabe.

## Schritte

1. Verbinde Notion mit dem eigenen Assistenten (Tabelle oben, Zeile „Notion verbinden“). Ist Notion schon verbunden, weiter mit Schritt 2.
2. Öffne einen neuen Chat, schalte Notion ein und sende **Prompt-Karte 2a** (nur lesen).
3. Öffne in Notion die Datenbank `Leads` und vergleiche: Stehen in der Antwort genau die Leads mit Region „DE-Süd“, mit denselben Werten?
4. Sende im selben Chat **Prompt-Karte 2b**. Prüfe den Plan und antworte erst dann mit „OK, bitte ausführen.“ Fragt der Assistent nach der Erlaubnis für ein Notion-Werkzeug, erlaube es für diesen Schritt.
5. Lade die Datenbank `Leads` in Notion neu (F5) und prüfe die drei Einträge: Häkchen bei `Diese Woche`, Text in `Nächster Schritt`, sonst nichts verändert.

**Prompt-Karte 2a – lesen**

```text
Nutze Notion. Öffne die Seite "Nordwind CRM" und darin die Datenbank "Leads".
Liste alle Leads mit Region "DE-Süd" als Tabelle: Firma, Score, Stufe, Status,
Rolle, Kaufsignal. Nur lesen, nichts ändern. Schreib dazu, wenn ein Feld leer ist.
```

**Prompt-Karte 2b – arbeiten lassen**

```text
Diese Leads aus Region "DE-Süd" übernimmt ab sofort eine neue Kollegin.
Erledige in Notion für jeden dieser Leads:
1. Kontrollkästchen "Diese Woche" anhaken.
2. In "Nächster Schritt" einen Satz eintragen: wen anrufen (aus "Rolle") und mit
   welchem Aufhänger (aus "Kaufsignal").
Ändere keine anderen Felder und keine anderen Leads.
Zeige mir zuerst den Plan als Tabelle (Firma | Nächster Schritt) und warte auf mein OK.
```

## Hinweise und Tipps

| Wenn … | dann … |
| --- | --- |
| der Assistent antwortet „kein Zugriff auf Notion“ | Notion ist in diesem Chat nicht eingeschaltet (Tabelle, Zeile „im Chat einschalten“); Frage erneut senden. |
| „Nordwind CRM“ nicht gefunden wird | Beim Verbinden wurde ein anderer Arbeitsbereich gewählt. Verbindung trennen, neu verbinden, Übungs-Arbeitsbereich wählen. |
| mehr oder weniger als drei Leads genannt werden | In Notion prüfen: Steht bei `Region` wirklich „DE-Süd“? Dann: „Prüfe noch einmal genau die Eigenschaft Region.“ |
| der Assistent ändert, ohne vorher den Plan zu zeigen | Zeile „vor Änderungen fragen lassen“ einstellen. Falsche Einträge mit Prompt-Karte 2c zurücksetzen. |
| ChatGPT liest, aber nicht schreiben kann | Schreibrechte hängen bei ChatGPT von Tarif und Einstellungen ab. Plan aus 2b in Notion von Hand eintragen: Der Agent hat gelesen und geplant, der Mensch setzt um. |
| `Diese Woche` Text statt Häkchen bekommt | Die Eigenschaft ist noch Text. Spaltenkopf → **Eigenschaft bearbeiten** (Edit property) → **Typ** → **Kontrollkästchen** (Checkbox), dann Prompt-Karte 2b erneut. |
| Notion fehlt in der Liste oder lässt sich nicht verbinden | Im Paar arbeiten mit einer Person, bei der die Verbindung steht; Schritte 2–5 gemeinsam. |

## Erfolgskriterium

- [ ] Notion ist mit dem Assistenten verbunden (oder: Paar-Arbeit mit verbundenem Assistenten).
- [ ] Antwort auf 2a: genau drei Leads – Vogelsang Medizintechnik (75, heiß), Lechfeld Stahlhandel (59, warm), Isarblick Steuerberatung (55, warm) – mit denselben Werten wie in Notion.
- [ ] Vor dem Schreiben hat der Assistent einen Plan gezeigt und auf das OK gewartet.
- [ ] In Notion haben genau diese drei Leads ein Häkchen bei `Diese Woche` und einen Satz in `Nächster Schritt` mit Rolle und Aufhänger.
- [ ] Alle anderen Leads und Felder sind unverändert.

Musterlösung: [Lösung 2](loesungen/02-mcp-agent-loesung.md)

## Zurücksetzen und noch einmal

**Zurücksetzen** (auch eine gute zweite Aufgabe für den Agenten):

**Prompt-Karte 2c – zurücksetzen**

```text
Setze in Notion bei allen Leads mit Region "DE-Süd" das Kontrollkästchen
"Diese Woche" zurück (kein Häkchen) und leere das Feld "Nächster Schritt".
Ändere sonst nichts. Zeige zuerst den Plan und warte auf mein OK.
```

Ohne Schreibrechte: die drei Einträge in Notion von Hand zurücksetzen.

**Noch einmal mit anderer Region:** Prompt-Karte 2a und 2b mit Region **„CH“** und danach **„NL“** statt „DE-Süd“ senden. Erwartet: je ein Lead (Limmat Treuhand AG bzw. Grachtenwerk Coworking B.V.).

_Quellen: Claude-Hilfe, „Use connectors to extend Claude's capabilities“ (https://support.claude.com/en/articles/11176164-use-connectors-to-extend-claude-capabilities), Menüpfade Stand 15.11.2026; OpenAI-Hilfe, „Notion app and setup in ChatGPT“ (https://help.openai.com/en/articles/12532955) und „Managing app permissions“ (https://help.openai.com/en/articles/20001495); Notion-Hilfe, „Notion MCP“ (https://www.notion.com/help/notion-mcp); Gemini Release Notes (https://gemini.google/release-notes/); alle abgerufen am 25.11.2026. Model Context Protocol, „What is MCP?“ (https://modelcontextprotocol.io/docs/getting-started/intro). Bezeichnungen je nach Version, Tarif und Sprache der Oberfläche._
