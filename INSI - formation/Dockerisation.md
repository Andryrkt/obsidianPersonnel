creation compte github (hasina.andrianadison@gmail.com)
creation compte dockerhub (tsy mety mande)
mande amin'inty lien inty https://labs.play-with-docker.com/
login > connect docker (optionnel) > start > add new instance
```PYTHON
docker pull debian #recuperation de l'image dans dockerhub
docker images #pour afficher l'image
docker run <id ou name>
```

## 22/03/2025

explication du pdf partie 1

## 05/04/2025
installation du docker
- Windows : docker desktop (client docker)
- linux : docker cli (client docker) > création d'interface graphique  GUI (à partir d'un url) > activer le Daemon

first.academy.clt@gmail.com


exercice
maka image nginx 
```Bash
docker pull nginx
```
creation de container
```Bash

$ docker run --name some-nginx -d -p 8080:80 some-content-nginx

port : -p Port_host:port_docker
passer le main : -d (--detach)
nom du container : --name nom_container
nom de l'image: nom_image
```

port par défaut serveur web
http : 80
https: 443

