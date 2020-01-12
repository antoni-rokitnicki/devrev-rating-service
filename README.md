# Rating Service [DevRev.pl](https://devrev.pl "DevRev pl")

## Start application
```bash
chmod +x *.sh
./start.sh
```

Go to http://localhost:8080

### Description of start script steps:
1. Install node modules
2. Build frontend
3. Build backend 
4. Build docker images
5. Start docker compose

## Stop application
```bash
./stop.sh
```

## Clean script
Removes all things generated by build process
```bash
./clean.sh
```

## MongoDB initialization 
MongoDB initialization is enabled by default.

Data file: `src/main/resources/data.json`

In order to disable initialization of mongodb by initial data change `MOVIESDB_POPULATEBYINITDATA` to `false` in docker-compose.yml
```yaml
...
    container_name: "movies-app"
    environment:
      - SPRING_DATA_MONGODB_URI=mongodb://mongo:27017/moviesDb
      - MOVIESDB_POPULATEBYINITDATA=false
    links:
      - mongo-db:mongo
...
```