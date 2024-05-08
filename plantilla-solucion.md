# Respuestas

## Respuesta de la **Actividad 1.1**

```
    docker volume create boston-data

```

## Respuesta de la **Actividad 1.2**

```
sudo docker run -d --name boston-db -p 5432:5432 -e POSTGRES_USER=postgres -e POSTGRES_PASSWORD=postgres -e POSTGRES_DB=BOSTON -v boston-data:/var/lib/postgresql/data --rm postgres:latest

```

## Respuesta de la **Actividad 1.3**

```
sudo docker exec -it boston-db psql -U postgres -d BOSTON -c "CREATE TABLE IF NOT EXISTS product (id SERIAL PRIMARY KEY, name VARCHAR(255) UNIQUE, description TEXT, price NUMERIC, stock INTEGER);"

Comando para confirmar que la tabla se creo correctamente:
sudo docker exec -it boston-db psql -U postgres -d BOSTON -c "\dt"


sudo docker inspect -f '{{range .NetworkSettings.Networks}}{{
.IPAddress}}{{end}}' boston-db
172.17.0.2

```

## Respuesta de la **Actividad 3.1**

```Dockerfile

```


## Respuesta de la **Actividad 3.2**

```
    docker build -f Dockerfile -t app:v1.0 .

```


## Respuesta de la **Actividad 3.3**

```bash
# Comando incompleto
docker run -e DB_HOST=$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' boston-db)

# Comando completo
docker run -e DB_HOST=$(docker inspect -f '{{range .NetworkSettings.Networks}}{{.IPAddress}}{{end}}' boston-db) app:v1.0

```

## Respuesta de la **Actividad 4.1**

```yml
    https://hub.docker.com/r/nicofg/app

```

## Respuesta de la **Actividad 5.1**

```
 docker-compose up -d

```

## Respuesta de la **Actividad 5.2**

```
docker-compose up -d
docker-compose ps

```