# Comandos Uteis
```bash
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
docker run --rm --name rabbit -d --hostname rabbit-host -p 15672:15672 -p 5672:5672 rabbitmq:management
```


# MongoDB

```bash
docker run --rm --name mongodb -d -p 27017:27017 -e MONGO_INITDB_ROOT_USERNAME='mongo' -e MONGO_INITDB_ROOT_PASSWORD='!123Senha' mongo

```


# ExceptionLess

```bash
    docker run --rm -d \
        --name exceptionless \
        -p 5000:80 \
        -v exceptionless_data:/usr/share/elasticsearch/data \
        exceptionless/exceptionless:latest
```