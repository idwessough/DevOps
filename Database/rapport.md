# Rapport TP01    
Create Dockerfile in the root folder of the project
Build this image and start the container 

Pour ne pas avoir à mettre des sudo à chaque fois et être sûr de travailler sur le même environnement :
docker newgrp

Installation des dépendances (ici on veut postgres:11.6-alpine)
docker pull postgres:11.6-alpine

Dans le répertoire du Dockerfile on build (créer) l'image docker (on l'appel par convention USER/NAME_OF_THE_DOCKER_IMAGE) avec le point à la fin de la commande pour spécifier que le Dockerfile se trouve dans ce dossier, sinon spécifier son chemin d'accès :
docker build -t idwes/postgres_database .
L'IMAGE S'APPELERA "idwes/postgres_database"..

Création d'une image permettant 
Dans le Dockerfile ajouter les fichiers / scripts du projet à mettre 
copy dockerfile -scripts SQl

docker build
docker build -t idwes/postgres_database .
docker run --name idwes-postgres -e POSTGRES_PASSWORD=pwd -e POSTGRES_USER=usr -e POSTGRES_DB=db -d --network=app-network -p 5432:5432 postgres 
Pour créer le volume :
=> docker run --name idwes-postgres -e POSTGRES_PASSWORD=pwd -e POSTGRES_USER=usr -e POSTGRES_DB=db --network=app-network -p 5432:5432 -v /scripts/01-CreateScheme.sql:/docker-entrypoint.sh/01-CreateScheme.sql postgres

docker run --network=app-network -p 8081:8080 adminer
=> docker run --name idwes-adminer -d --network=app-network -p 8081:8080 adminer

aller sur http://localhost:8081/ pour accéder à l'interface d'Adminer admin bdd/php


docker pull adminer

Pour supprimer un conteneur :
docker rm -f CONTAINER_NAME

we need a volume to be attached to our postgres container if the container is remooved or destroyed we can retrieve data on the volume 





BackendAPI
Création dossier puis du Dockerfile (partie désormais en commentaire)
Hello world :
idwes@LAPTOP-61C5CBJS:~/DockerCPE/TP01/BackendAPI$ docker build -t idwes-java .
docker run idwes-java

Javaapi :
idwes@LAPTOP-61C5CBJS:~/DockerCPE/TP01/BackendAPI/simple-api$ docker build -t idwes-javaapi .

Final de l'API Java backend :

Configuration du fichier YAML, difficultés d'accès à la base de données car url: "jdbc:postgresql://idwes-postgres:5432/db" et non 'postgressql'
idwes@LAPTOP-61C5CBJS:~/DockerCPE/TP01/APIBack/simple-api-main/simple-api-main/simple-api$ docker build -t idwes-backapi .

idwes@LAPTOP-61C5CBJS:~/DockerCPE/TP01/APIBack/simple-api-main/simple-api-main/simple-api$ docker run -p 8080:8080 --network=app-network idwes-backapi


HTTPServer :$
idwes@LAPTOP-61C5CBJS:~/DockerCPE/TP01/HTTPServer$ docker build -t idwes-apache .

Concernant la partie Ansible (validée) le code est en cours de récupération sur mon ordinateur afin de l'ajouter dans le repo avant minuit.

