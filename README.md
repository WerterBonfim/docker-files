# Meus container local

## MongoDB 
--
### Robo3t

Arquivo: utils-mongodb/Dockerfile.robo3t
```bash

# construindo a imagem
docker build -f Dockerfile.robo3t -t robo3t-imagem .

# rodando o container de modo grafico
docker run --rm --name robo3t -it --net=host --env="DISPLAY"  robo3t-imagem

# caso de um erro de permissão
# no seu host
xhost +

# ou
xhost +local:*

```
