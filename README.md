# Auto-DevOps

## Sommaire
* [Informations générales](#informations-générales)
* [Technologies](#technologies)
* [Steup](#steup)

## Informations générales
Ce projet est pour économiser le temps passé sur la configuration des pipelines en mettant en place une pipeline multi-envirenments fonctionemlle, ontrôlée par une application web. 

## Technologies
Ce projet a été réaliser en utilisant :
* Tearraform version: 0.13.3
* Angular version: 7.2.11
* Node.js version: 14.15.4
* Docker
* Gitlab CI/CD 

## Steup
les commandes pour installer les libraries ou pour executer les codes:

#### Terraform
```$ tearraform init``` : initialiser le tfstate.tf<br/>
```$ terraform validate``` : valider la syntaxe de code<br/> 
```$ terraform plan``` : création d'un plan d'éxecution avant le déploiement<br/>
```$ terraform apply```: pour le déploiement de l'infrastructure (le flag "-target=ressource" pour deployer une source visé / "-auto-aaprove" pour la validation automatique )<br/>
```$ tearrform destroy```: supprimmer l'infrastructure déployé

#### Angular
```$ npm install```: installer les modules<br/>
```$ ng serve```: lancer l'application en mode dev en local (http://localhost:4200)<br/>
```$ ng build --prod```: build de l'application

#### Node.js
```$ npm install```: installer les modules<br/>
```$ nodemon server```: lancer le serveur en mode dev en local et les changement seront automatique sans besoin de relancer le serveur (http://localhost:4000)<br/>
```$ node server```: lancer le serveur

#### Docker
```$ docker build -t [tag] .```: build l'image en utilisant le Dockerfile<br/>
```$ docker --tag [tag-existe] [tag-new]```: changer un tag d'une image<br/>
```$ docker push```: pusher l'image vers les repository de stockage
