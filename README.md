# historisk-samfund-api
Containerized datasette-backed API for the frontend client

## Todo
- find pdf'er
- deploy på virtuel server
  - hvordan skal Dockerfile se ud? Husk eks. -i for immutable db

## Development
Docker bruges direkte fra det officielle datasette-image på Docker Hub. Fra repo'ets rodmappe kan kan lave følgende kald i PS for at starte en datasette-container med db-fil, settings, metadata..:

````docker run -it -p 8001:8001 --mount type=bind,src="$(pwd)",target=/src datasetteproject/datasette datasette --reload --cors -h 0.0.0.0 /src/````

## Production
1. Either we use ````datasette package```` to include the local datasette, incl. db and static files, in a new image, that we publish on azurecr.io, from where we pull it via a docker-compose-file.
2. Or we just pull the base datasette-image in our docker-compose file, and then copy the files and db-file with docker-syntax, before we run ````CMD ["datasette", "..."]````

## DB
Db-filen er genereret ved at paste sql-forespørgslerne fra schema.sql ind i en ny DB i **DB Browser for SQLITE**, hvorefter en csv-fil med tabel-data er importeret til **articles**-tabellen via GUI'en.

## Static
Indeholder alle pdf-filer.
