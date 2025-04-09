## création de fichier Dockerfile
FROM: specifie la base de l'image
MAINTAINER : specifie l'image à maintenir
RUN : Run les commande
ADD: ajouter un fichier ou repertoire
Expose: exposer un ports pour l'accessible
ENV: Créer un variable d'environnement
VOLUME: indisue le repertoire ou on stock les données
CMD: avec quel commende le container va demmarer

## construction d'image
```Bash
docker build -t <nom image>:<version> <chemin du dossier contient dockerfile>
```

## vérification de l'image
```Bash
docker images
```

## démarrer un container
```Bash
docker run --name <nom image> -d -p <port exterieur>:<port interieur> <nom image>:<versiion>
```

## envoie de l'image dans docker hub
on a droit que 1 repository privée
```Bash
docker login
docker tag <id image> <username docker hub>/<nom image>:<version>
docker push <username docker hub>/<nom image>:<version>
```
