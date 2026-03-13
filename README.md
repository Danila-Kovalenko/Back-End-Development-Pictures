# Bilder-Microservice (Flask)

Dieser Service ist eine kleine REST-API zur Verwaltung von Bild-Metadaten.  
Die Anwendung ist mit **Python + Flask** umgesetzt und speichert die Daten aktuell in einer lokalen JSON-Datei (`backend/data/pictures.json`).

## Zweck des Projekts

Das Repository zeigt eine einfache Backend-Struktur für CRUD-Operationen auf einer Ressource `picture`:

- Bilder abrufen
- Einzelnes Bild per ID abrufen
- Neues Bild anlegen
- Bestehendes Bild aktualisieren
- Bild löschen
- Health- und Count-Endpunkt für Monitoring/Checks

Damit eignet sich das Projekt als Lern- und Übungsbasis für REST-APIs mit Flask sowie für API-Tests mit Pytest.

## Projektstruktur

- `app.py` – Einstiegspunkt zum lokalen Starten der Anwendung
- `backend/__init__.py` – Flask-App-Initialisierung
- `backend/routes.py` – API-Routen und CRUD-Logik
- `backend/data/pictures.json` – Beispieldaten (In-Memory geladen)
- `tests/` – API-Tests mit `pytest`
- `requirements.txt` – Python-Abhängigkeiten
- `Dockerfile` – Containerisierung

## API-Endpunkte

### Basis / System

- `GET /health` → `{"status": "OK"}`
- `GET /count` → Anzahl der vorhandenen Bilder

### Bilder

- `GET /picture` → Liste aller Bilder
- `GET /picture/<id>` → Ein Bild nach ID
- `POST /picture` → Neues Bild anlegen
- `PUT /picture/<id>` → Bild aktualisieren
- `DELETE /picture/<id>` → Bild löschen

## Lokal starten

```bash
python -m venv .venv
source .venv/bin/activate
pip install -r requirements.txt
python app.py
```

Standardmäßig läuft der Service auf `http://0.0.0.0:8080`.

## Tests ausführen

```bash
pytest
```

Die vorhandenen Tests prüfen zentrale API-Funktionalitäten wie Healthcheck, Anzahl, Abruf, Erstellung, Update und Löschung von Bildern.

## Hinweise

- Die Daten werden beim Start in den Speicher geladen; Änderungen per API sind daher nicht dauerhaft in der JSON-Datei persistiert.
- Der Service ist bewusst schlank gehalten und eignet sich gut als Grundlage für Erweiterungen (z. B. Datenbankanbindung, Validierung, Authentifizierung, Pagination).
