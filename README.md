# Data Science Workshop II (Microsoft Fabric)

Hands-on-Workshop zu **AI Functions** und **Data Science auf unstrukturierten Daten** in Microsoft Fabric. Alles läuft über die in Fabric **eingebauten** AI Functions (`df.ai.*`) — kein eigener API-Key, kein Deployment.

## Integrierte AI Functions
Die AI Functions sitzen direkt auf dem DataFrame und nutzen die von Fabric bereitgestellten Modelle ([Microsoft-Docs](https://learn.microsoft.com/fabric/data-science/ai-functions/overview)):
- `ai.classify` — Freitext auf eigene Labels mappen (Normalisieren)
- `ai.generate_response` — freie Prompts, optional mit **JSON-Schema** für typisierte Felder (unstrukturiert → strukturiert)
- `ai.extract` — Entitäten/Themen je Label als Spalte
- `ai.analyze_sentiment` — Stimmung, auch mit eigenen Labels
- `ai.embed` — Text → Vektor als Basis für Clustering, Anomalie-Erkennung, semantische Suche
- weitere: `ai.summarize`, `ai.translate`

## Struktur
- `tasks/` — Aufgaben-Notebooks (`w3_00` – `w3_04`). Kontext (Label-Listen, JSON-Schemas, Prompts, Parsing/Speichern) ist vorgegeben; offen ist nur der jeweilige `ai.*`-Aufruf.
- `solution/` — vollständige Lösungs-Notebooks (Referenz / Trainer-Hand), inkl. `w3_05_fabric_integration` (Power BI / Activator).
- `wagon/` — lizenzgeprüfte Demobilder für den CV-Teaser, je 1 Bild pro Schadensklasse (`00_rost` … `05_kein_schaden`). Quellen & Lizenzen: `wagon/CREDITS.md` (Wikimedia Commons, CC0/Public Domain/CC BY(-SA)).

## Ablauf
1. `w3_00_setup` — erzeugt die Ausgangsdaten (Tabelle `asset_meldungen`) und lädt die Wagon-Fotos automatisch aus diesem Repo (`wagon/`) als ZIP.
2. `w3_01` Stammdaten heilen — `ai.classify` + `ai.generate_response`
3. `w3_02` Kommentare — `ai.analyze_sentiment` + `ai.extract`
4. `w3_03` CV-Teaser — `ai.generate_response` auf Bildern
5. `w3_04` Unstructured ML — `ai.embed` + Clustering / Anomalien / semantische Suche
6. `w3_05` Fabric-Integration — Ergebnisse nach Power BI (Direct Lake) & Activator

**Voraussetzung:** Ein Fabric-Lakehouse ist an die Notebooks angehängt.
