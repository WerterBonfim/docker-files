# Filtros 

| **Information** | **Variable** |
|:---------------:|:------------:|
| CONTAINER ID    | ID           |
| IMAGE           | Image        |
| COMMAND         | Command      |
| CREATED         | RunningFor   |
| STATUS          | Status       |
| PORTS           | Ports        |
| NAMES           | Names        |


# Comandos Uteis
```bash
# listar

 docker container ls --format "table {{.ID}}\t{{.Image}}\t{{.Names}}"
 docker container ls -a --format "table {{.ID}}\t{{.Image}}\t{{.Names}}"

 alias nome_alias="docker container ls --format 'table {{.ID}}'"

 docker container ls --format "table {{.ID}}\t{{.Image}}\t{{.Names}}\t{{.Status}}"

 ## filtro 
 # listar container por nome
 docker container ls -a -f name=asdf


 docker rm -v $(docker ps -a -q -f status=exited)





# remover imagens não utilizadas/intermediarias
docker rmi $(docker images -f dangling=true -q)


```



# Sql Server

```bash
    docker run --rm --name sql \
    -d \
    -e ACCEPT_EULA='y' \
    -e SA_PASSWORD='!123Senha' \
    -p 1433:1433 \
    -e 'TZ=America/Sao_Paulo' \
    -v sql-volume:/var/opt/mssql \
    --memory="4G"
    mcr.microsoft.com/mssql/server



# health check
    docker exec -it sql /opt/mssql-tools/bin/sqlcmd \
    -S localhost -U SA -P '!123Senha' \
    -Q 'SELECT @@VERSION GO; SELECT GETDATE()'


```

## Sql Server no Alpine
```bash

# build da imagem 
docker build -t mssql-alpine -f sql-alpine .

# teste
docker run --rm --name temp-alpine -it -p 1433:1433 mssql-alpine sqlcmd -S 'localhost, 1433' -U sa -P '!123Senha'


```


# Rabbitmq

```bash
docker run --rm \
    --name rabbit -d \
    --hostname rabbit-host \
    -p 15672:15672 \
    -p 5672:5672 \
    --memory="4G"
    rabbitmq:management
```


# MongoDB

```bash
docker run --rm --name mongodb -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME='mongo' -e MONGO_INITDB_ROOT_PASSWORD='!123Senha' --memory="4G" mongo

```


# ExceptionLess

```bash
    docker run --rm -d \
        --name exceptionless \
        -p 5000:80 \
        -v exceptionless_data:/usr/share/elasticsearch/data \
        --memory="4G" \
        --cpus="1.5" \
        exceptionless/exceptionless:latest
```
