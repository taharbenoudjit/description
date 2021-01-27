# Auto-DevOps

## Sommaire
* [Description](#description)
* [Technologies](#technologies)
* [Steup](#steup)
* [information générales](#informations-générales)
* [To-do](#to-do)

## Description
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
```$ docker push```: pusher l'image vers les repositories de stockage

## Informations générales
* Le nom d'utilisateur de la base de données documentDb: Accetal<br/>
* Le mot de passe de la base de données documentDb: testtest (a changé plus tard)<br/>
* Lien vers le front de l'application de l'envirenment prod: http://main-lb-prod-669981901.eu-west-1.elb.amazonaws.com<br/>
* Lien vers le front de l'application de l'envirenment dev:  http://main-lb-dev-449684148.eu-west-1.elb.amazonaws.com<br/>
* Lien vers le back de l'application de l'envirenment prod:  http://main-lb-prod-669981901.eu-west-1.elb.amazonaws.com:4000/api<br/>
* Lien vers le back de l'application de l'envirenment dev:   http://main-lb-dev-449684148.eu-west-1.elb.amazonaws.com:4000/api<br/>

## To-do
#### a-infra/
###### En local :
* Dans ../src/app/service/api.service.ts<br>
* ../src/app/service/auth.service.ts<br>
* ../src/app/service/feature.service.ts<br>

l'utilisation de :

`baseUri: string = 'http://localhost:4000';`

###### Avant le push :
* Dans ../src/app/service/api.service.ts<br>
* ../src/app/service/auth.service.ts<br>
* ../src/app/service/feature.service.ts<br>

l'utilisation de :

`baseUri:string = 'http://main-lb-prod-669981901.eu-west-1.elb.amazonaws.com:4000';` : pour la branche master<br/>
`baseUri:string = 'http://main-lb-dev-449684148.eu-west-1.elb.amazonaws.com:4000';`  : pour la branche dev<br/>

#### b-back/
###### En local :
* Dans ../back/database/db.js<br>
l'utilisation de :
`db: 'mongodb://localhost:27017/[nom_de_base]'`

* Dans ../server.js
`mongoose.Promise = global.Promise;
mongoose.connect(dbConfig.db,{
    useNewUrlParser: true,
    useUnifiedTopology: true
}).then(() =>{
    console.log('Database is connected')
},
error => {
    console.log('Database Not connected:' + error)
}
)
`
###### Avant le push :
* Dans ../back/database/db.js<br>
`db: 'lien documentDb_(prod/dev)'`
* Dans ../server.js
`mongoose.Promise = global.Promise;
mongoose.connect(dbConfig.db,{
    sslValidate: true,
    sslCA:ca,
    useNewUrlParser: true,
    useUnifiedTopology: true
}).then(() =>{
    console.log('Database is connected')
},
error => {
    console.log('Database Not connected:' + error)
}
)
`

* Dans ../rds-combined-ca-bundle.pem : changement de certificat en fonction de la base donnée 
