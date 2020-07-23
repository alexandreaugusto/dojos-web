# expressjs:

Instalando o expressjs:

https://expressjs.com/pt-br/starter/installing.html

Criando a aplicação Hello World:

https://expressjs.com/pt-br/starter/hello-world.html

# Docker

Dockerizando uma aplicação nodejs: 

https://nodejs.org/de/docs/guides/nodejs-docker-webapp/

- Comandos utilizados no Dojo (by Leandro):
```
cd /home/leandro/Dev/cptec
mkdir nodedocker
cd nodedocker/
vim .dockerignore
sudo docker images
sudo docker build -t web-dojos/dojo .
sudo docker images
sudo docker run -p 3000:3000 web-dojos/dojo #casa a porta 3000 da máquina com a porta 3000 da imagem docker
sudo docker ps
sudo docker ps -a #mostra imagens stopped
sudo docker ps -a
sudo docker rm stupefied_pike

sudo docker rmi 03420934absea9c8as #remove imagem docker da máquina
sudo docker exec -it stupefied_pike /bin/bash #entra na imagem (no container), dentro do workdir definido no Dockerfile
sudo docker exec -it stupefied_pike /bin/sh #entra na imagem (no container) usando shell
```



