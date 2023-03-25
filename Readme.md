# README

## Projektübersicht
Dieses Projekt verwendet Docker Compose, um eine Anwendung aus drei Diensten aufzubauen: `frontend`, `api` und `db`. Die verwendete Docker Compose Version ist `3.8`.

Die Dienste sind wie folgt konfiguriert:

1. `frontend`: Eine Webanwendung, die auf dem Bild `frontend:latest` basiert.
2. `api`: Eine API-Anwendung, die auf dem Bild `api:latest` basiert und eine Verbindung zur Datenbank herstellt.
3. `db`: Eine PostgreSQL-Datenbank, die auf dem Bild `postgres:latest` basiert.

## Anforderungen
- Docker
- Docker Compose

## Dienstkonfiguration

### frontend
- Das `frontend:latest` Image wird verwendet.
- Es hängt vom `api` Dienst ab, um sicherzustellen, dass die API verfügbar ist, bevor der `frontend` Dienst gestartet wird.
- Der Port `80` des Hosts ist an den Port `80` des Containers gebunden.

### api
- Das `api:latest` Image wird verwendet.
- Es hängt vom `db` Dienst ab, um sicherzustellen, dass die Datenbank verfügbar ist, bevor der `api` Dienst gestartet wird.
- Der Port `8080` des Hosts ist an den Port `8080` des Containers gebunden.
- Die Umgebungsvariable `CONNECTION_STRING` wird verwendet, um die Verbindung zur PostgreSQL-Datenbank herzustellen.

### db
- Das `postgres:latest` Image wird verwendet.
- Die Umgebungsvariable `POSTGRES_PASSWORD` wird verwendet, um das Passwort für den `postgres`-Benutzer festzulegen.
- Die Umgebungsvariable `POSTGRES_DB` wird verwendet, um den Namen der Datenbank festzulegen, in diesem Fall `test-db`.
- Der Datenbankdatenordner wird an den Host-Ordner `./data` gebunden, um Datenpersistenz zu gewährleisten.

## Anwendung starten
Um die Anwendung mit Docker Compose zu starten, führen Sie den folgenden Befehl im Terminal aus:

```sh
docker-compose up -d
```

## Anwendung stoppen

Um die Anwendung zu stoppen und alle Container zu entfernen, führen Sie den folgenden Befehl im Terminal aus:

```sh
docker-compose down
```

## Anwendung aktualisieren

Um die Anwendung zu aktualisieren, ziehen Sie die neuesten Images und starten Sie die Anwendung erneut:

```sh
docker-compose pull
docker-compose up -d
```
