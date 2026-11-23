# Datenampel: acht Fälle aus dem Vertrieb

Fiktives Unternehmen, alle Angaben erfunden. Auch alle Personen, Telefonnummern und Mailadressen sind erfunden. Die Telefonnummern stammen aus den Rufnummern, die die Bundesnetzagentur für Medienproduktionen freihält („Drama Numbers“, https://www.bundesnetzagentur.de/DE/Fachthemen/Telekommunikation/Nummerierung/DramaNumbers/artikel.html, abgerufen am 23.11.2026).

Stand: 22.11.2026 · Übungsmaterial für Lab 1.3. Jeder Fall beschreibt eine Situation im Nordwind-Vertrieb und die Eingabe, die jemand in ein KI-Werkzeug geben möchte. Die Einordnung (grün, gelb, rot) mit Begründung steht im Musterergebnis von [Lab 1.3](../m01-ai-sales-basics/l03-data-rules.md).

Die Fälle sind erfunden und dürfen deshalb zum Üben in einen KI-Assistenten eingegeben werden. Echte rote Daten gehören nie in ein KI-Werkzeug, auch nicht „nur zur Prüfung".

## Fall 1 – Text der eigenen Website

**Situation:** Ein Kollege möchte den Produkttext von der Nordwind-Website ins Englische übersetzen lassen.

```text
Nordwind Panel 10 zeigt an jeder Tür, ob ein Besprechungsraum frei ist. Gebucht wird mit einem Fingertipp direkt am Display oder über Outlook und Google Kalender.
```

## Fall 2 – Geschäftsbericht eines Interessenten

**Situation:** Vor einem Erstkontakt soll ein Abschnitt aus dem veröffentlichten Geschäftsbericht eines börsennotierten Unternehmens zusammengefasst werden.

```text
Auszug aus dem Geschäftsbericht 2025 (öffentlich auf der Investorenseite des Unternehmens): „Im Geschäftsjahr 2026 bündeln wir unsere Verwaltung in einem neuen Bürogebäude und führen ein hybrides Arbeitsmodell mit Desk-Sharing ein."
```

## Fall 3 – Interne Preisliste

**Situation:** Eine Kollegin möchte die Nordwind-Preisliste mit Staffelrabatten hochladen, um ein Rechenbeispiel für zwölf Räume erstellen zu lassen.

```text
Datei: preisliste.xlsx (intern) – Panel 10: 590 €, Vista: 1.890 €, Book Pro: 14 € pro Raum und Monat, Staffelrabatt ab 20 Räumen 8 %, ab 50 Räumen 12 %.
```

## Fall 4 – Gesprächsnotiz mit Kontaktdaten

**Situation:** Nach einem Telefonat soll die Notiz zu einer Follow-up-Mail verarbeitet werden.

```text
Telefonat mit Frau Katrin Vogel, Leiterin Facility Management, Hansa Wohnbau eG, Lübeck. Mobil 0171 39200 47, k.vogel@hansa-wohnbau.example. Interesse an Panel 10 für 22 Räume, will bis Freitag ein Angebot.
```

## Fall 5 – Interne Wettbewerbs-Einschätzung

**Situation:** Vor einem Kundengespräch soll aus der internen Wettbewerbsübersicht eine Gesprächshilfe gegen MeetSpace Pro entstehen.

```text
Interne Einschätzung (nicht für Kunden): MeetSpace Pro ist ca. 20 % teurer, Lieferzeit 6–8 Wochen, Service nur auf Englisch und Niederländisch.
```

## Fall 6 – Pipeline-Export aus dem CRM

**Situation:** Der Teamleiter möchte den CRM-Export aller offenen Deals hochladen und fragen, welche Deals gefährdet sind.

```text
Datei: deals_export.csv – 48 Zeilen mit Firmenname, Ansprechperson, Mailadresse, Dealwert, Phase, gewährtem Rabatt und letzter Notiz.
```

## Fall 7 – Persönliche Information in einer Kundenmail

**Situation:** Eine Kundenmail soll beantwortet werden. Darin steht, warum sich das Projekt verzögert.

```text
Lieber Herr Aydin, leider verschiebt sich unser Projekt: Mein Kollege Thomas Reiter, der die Raumplanung leitet, ist nach einer Operation für mehrere Wochen krankgeschrieben. Viele Grüße, Anja Lorenz, Prokuristin, Lorenz Steuerberatung
```

## Fall 8 – Zugangsdaten für die Notion-Verbindung in n8n

**Situation:** Beim Einrichten der Verbindung zwischen n8n und Notion erscheint eine Fehlermeldung. Jemand möchte den KI-Assistenten um Hilfe bitten und kopiert dafür den Inhalt des Zugangsfensters (Credential) samt Integration Secret in den Chat. Das Integration Secret ist der geheime Schlüssel, mit dem n8n im Namen der Notion-Integration Daten lesen und schreiben darf.

```text
n8n Credential „Notion account“ · Internal Integration Secret: ntn_FIKTIV-0000-UEBUNG-NICHT-ECHT-7Kq2 · Fehlermeldung: Could not find database with ID 1a2b3c4d. Make sure the relevant pages and databases are shared with your integration.
```
