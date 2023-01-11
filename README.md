# historisk-samfund-api
Containerized datasette-backed API for the frontend client

## Development
Docker bruges direkte fra det officielle datasette-image på Docker Hub. Fra repo'ets rodmappe kan kan lave følgende kald i PS for at starte en datasette-container med db-fil, settings, metadata..:

````docker run -it -p 8001:8001 --mount type=bind,src="$(pwd)",target=/src datasetteproject/datasette datasette --reload -h 0.0.0.0 /src/````

## DB
Db-filen er genereret ved at paste sql-forespørgslerne fra schema.sql ind i en ny DB i **DB Browser for SQLITE**, hvorefter en csv-fil med tabel-data er importeret til **articles**-tabellen via GUI'en.

## Static
Indeholder alle pdf-filer
