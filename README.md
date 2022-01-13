# Rapport de TP sur MongoDB {

> Introduction du rapport 

Voici le rapport de la semaine de cours qui va nous permettre de suivre notre progression sur MongoDB et de répondre à la problématique posé par le formateur.

## Présentation de la base MongoDB

MongoDB est SGBD (Système de gestion de base de données) orienté documents et de surcroît non relationnel (à contrario de son confrère MySQL par exemple présenté un peu plus bas dans ce rapport).
Nous entendons orienter documents par le fait qu’un document dans mongo db peut-être vu comme un ensemble de clé valeur très simple à utiliser. 

Nous utilisons javascript comme langage natif avec MongoDB.
MongoDB se caractérise par son contenu, des documents et des collections réunies en base.
Voici une capture d'écran de la création de notre collection "Clients" stocké dans la base:

![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/img/projetCreateCollectionClient.PNG?raw=true "projet Create Collection Client")

Ici on créer la collection "Clients" en insérant directement les données.

Nous allons reproduire cette opération pour nos : "Restaurants"

Nous avons décidé de créer la collection sans insérer de données au départ :

![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/img/projetCreateCollectionRestaurant.PNG?raw=true "projet Create Collection Restaurant")

Et voici la réponse de MongoDB après avoir inséré les données : 

![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/img/projetCreateCollectionRestaurantResponse.PNG?raw=true "projet Create Collection Restaurant Response")


Voici un visuel de la collection Restaurants après l'insertion des données : 

![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/img/projetDbRestaurant.PNG?raw=true "projet Db Restaurant")


Présent dans ces documents vous pouvez voir des données en format JSON, et c’est ce qui fait qu’un document à l’autre, la structure des données peut changer au fil du temps sans impacter le fonctionnement de notre base.
On dit que le modèle de document mappe les objets du code de nos applications, ce qui facilite grandement le traitement des données.


## Présentation du projet

Une chaine de restaurant souhaite récupérer des données clients afin de capitaliser
sur un flux de personnes sans cesse grandissant 
(plusieurs dizaine de milliers de clients par semaine dans toute la France).

Le but est de fournir un projet d'application centré sur un stockage des données avec MongoDB.

Bien évidement nous vous montrerons ci-dessous  les choix technologiques qui ont été fait et l'utilité que cela présente pour un projet de cette ampleur.

Le but de notre projet étant d'accumuler, stocker et filtrer les données clients.

Le fonctionnement sera le suivant : les clients pourrons renseigner leurs informations personnelles qui seront utilisé par la suite.

Notez qu'a chaque fois qu'un utilisateur entrera un numéro de téléphone portable, celui-ci se verra attribuer des points de fidelités qu'il pourra utiliser pour son usage personnel sous forme de réductions ou d'offres diverses.

Afin d'éviter les abus sur cette fonctionnalité un délai de 5h sera attribué à chaque utilisateur pour récupérer ses points de fidelité, bien sûr plus le client aura renseigné d'informations plus il gagnera de points.

>Pourquoi MongoDB et non MySQL

Comme vu plus haut dans ce rapport, MongoDB est une base de données orientée documents à contrario de MySQL. Et cela présente un avantage certain dans le cadre de ce projet. 
Le fonctionnement de MongoDB ce distingue de MySQL en matière de mémorisation des données, malgré la similitude que l’on peut retrouver dans les deux cas :
Tout d’abord nous pouvons voir que les tableaux (MySQL) sont remplacés par des collections (MongoDB)
Les champs les lignes et les colonnes (MySQL) sont remplacés par des documents en format JSON
Toutes les lignes d’un tableau MySQL ont une composition identique à l’inverse de MongoDB ou chaque document peut évoluer au fil du temps de manière individuel sans impacter le fonctionnement de la base.

La clé doit être unique dans les documents (MongoDB) mais peut se retrouver dans d’autres documents, ce qui est impossible avec MySQL.
Sur MySQL il est obligatoire d’établir des relations (JOINS) entre les différents tableaux
Il existe bien évidement bien d’autres différences, mais nous en terminerons avec cette brève présentation.

## Sommaire

0. [Les spécifications techniques](#les-spécifications-techniques)
1. [MongoDB du NoSQL](#mongodb-du-nosql)
2. [Elasticsearch une alternative NoSQL](#elasticsearch-une-alternative-nosql)
3. [Les fonctionnalités Avancées](#les-fonctionnalités-avancées)
4. [Les requêtes géospatiales](#les-requêtes-géospatiales)
5. [Agrégation avec MongoDB](#agrégation-avec-MongoDB)
6. [La méthode explain](#la-methode-explain)


## Les spécifications techniques

![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/icons/nodejs.png?raw=true "NodeJS")          ![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/icons/compass.png?raw=true "NodeJS")         ![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/icons/mongodb.png?raw=true "NodeJS")


Notre choix concernant les technologies à utiliser porte sur atlas, compass et la création d'une api NodeJS pour les requêtes.

Ceci étant nous vous montrerons au fur et à mesure de ce rapport le parallèle entre les requêtes faite avec notre API nodeJS et les requêtes natives.

Concernant notre choix technologique, en vue des consignes du formateur, et du travail de groupe imposé, il était préférable de choisir un outil performant et que chacun sait manipuler. Atlas offre un service gratuit et performant afin d'héberger une base de données Mongo via un cluster (accessible avec une simple ligne à copier-coller dans l'outil prévu à cet effet).

C'est ensuite compass qui prend le relai, pour sa simplicité d'installation et d'utilisation. Compass va très facilement nous aider à naviguer dans notre base, à tester nos requêtes avec son terminal intégrer, et va également nous offrir une belle visu sur le jeux de données présent dans la base (voir screenshot ci-dessous).

Pour les tests de requêtes nous privilégions quand même le terminal visual studio code avec son plugin MongoDB pour plus de praticité.

## MongoDB du NoSQL

A contrario des SGBDR (Système de gestion de base de données relationnel), MongoDB qui lui s’appui sur le NoSQL s’écarte de cette notion relationnelle pour des problèmes de performance et de scalabilité.
Une application est dite « Scalable » quand celle-ci s’adapte à des tailles en base possédant un important flux de données, un grand volume, que celle-ci gère un espace-temps, etc…

Dans le cadre de notre exemple vu en cours, ce restaurant se doit de manipuler un nombre important de données afin de récupérer un maximum de données utilisateurs, et pouvoir bien évidement en faire des statistiques.

D’après le site : https://analyticsinsights.io/
Les avantages d’une telle installation sont les suivants :

•	Possibilité de déployer de nouvelles fonctionnalités en peu de temps

•	Un très bon support technique

•	Grandes capacités d’analyse grâce à la librairie spark

•	Une haute performance et la capacité de récupérer des documents ultra 
rapidement tout en gérant un important flux de données

•	A l’aide de test de performance, il est vu que la sécurité est améliorée avec 
la communication https entre les nœuds de jeux de réplicas


Attention, bien que MongoDB est force de proposition sur ce type de projet, et que il est l’objet de ce cours, d’autre SGBD sont présents sur le marché et mérite que l’on s’y attarde. 


## Elasticsearch une alternative NoSQL

Elasticsearch est un outil se présentant comme un SGBD orienté document et qui va nous permettre de mettre en place un système de recherche très complexe.

Dans un premier temps nous pourrons stocker des informations, et dans un second temps nous pourrons les récupérer à l’aide de requêtes.

Les avantages certains que possède Elasticsearch sont que les recherches peuvent être basé sur du texte et peuvent contenir des critères très poussés, d’organiser les résultats par pertinence (très utile pour créer un moteur de recherche par exemple), et il possède également une API dite RESTful afin de pouvoir communiquer facilement avec lui.

Tout comme son confrère MongoDB, Elasticsearch stocke les données de manière non-structuré.
Nous pouvons également le distribuer et nous permettre d’avoir plusieurs instances au niveau du réseau afin d’obtenir des résultats plus rapides.
Une solution simple d’utilisation et efficace dans bien des domaines.

## Les fonctionnalités avancées

MongoDB et son langage d’interrogation est extrêmement puissant. Nous pouvons nous permettre d’effectuer toutes les requêtes possibles et de surcroît avoir un résultat beaucoup plus poussé, tout cela de manière simple contrairement à une base relationnelle tel que MySQL par exemple.

L’avantage de ce fonctionnement dans ce cours est, qu’il va falloir faire croitre notre application au fil du temps et effectuer des recherches poussées à des fins de statistiques, tout en épargnant certaines informations, et ce sur un important jeu de données.

Nous allons donc voir certaines de ces fonctionnalités avancées.

## Les requêtes géospatiales 

Sources : (https://rtavenar.github.io/teaching/nosql_fiche/html/td_textgeo.html)

Plusieurs points s’appuient sur le fait d’utiliser des données géospatiales :

Si l’on souhaite trouver des éléments présents dans la base les plus proches d’un point donné

Si l’on souhaite trouver des éléments présents dans la base entièrement inclus dans un polygone donné

Si l’on souhaite trouver des éléments présents dans la base partiellement inclus dans un polygone donné (pour représenter une rue par exemple)

C’est la que la notion d’index fait son entré : 

Sources :

(https://docs.mongodb.com/manual/geospatial-queries/)

(https://practicalprogramming.fr/mongodb-index)

Pour illustrer le cas pratique de notre projet nous avons utilisé un index de type "2dsphere" sur notre champ "localisation", qui va nous servir à récupérer les documents compris dans une zone circulaire défini (grâce à leurs coordonnées).

Voici l'exemple pratique ci-dessous : 

![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/img/projetCreateIndex2dsphere.PNG?raw=true "projet Create Index 2dsphere")

Nous pouvons visualiser l'index sur atlas par exemple : 

![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/img/projetCreateIndex2dsphere2.PNG?raw=true "projet Create Index 2dsphere2.PNG")

En vous montrant un exemple concret de l'utilisation d'une requête géospatiale de type 2dsphere vous comprendrez pourquoi cela est primordial dans un projet de cette ampleur : 

![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/img/projetNearSphereResult1.PNG?raw=true "projet Near Sphere Result1.PNG")

Sur la capture d'écran nous voyons un résultat, tentons d'augmenter la distance maximale :

![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/img/projetNearSphereResult2.PNG?raw=true "projet Near Sphere Result2.PNG")

En augmentant la distance maximale, nous récupérons les informations d'un autre restaurant.

Cela prouve que nous pouvons bien retourner à l'utilisateur tous les restaurants présents dans une certaine zone.

Il est très intéressant voir indispensable de combiner ce type de requête avec de l'agrégation afin de filtrer nos recherches.

C'est ce que nous allons voir par la suite.


## Agrégation avec MongoDB


>L’agrégation

Si nous restons sur la définition de l’agrégation d’après la documentation officielle mongo db, l’agrégation est le fait de traiter les informations de plusieurs documents afin d’en retourner le résultat calculé.

Nous pouvons utiliser une opération d’agrégation pour : 

Regrouper des valeurs lié à plusieurs documents, effectuer des opérations sur les données groupées pour renvoyer un résultat unique et enfin analyser l’évolution des données dans le temps (ce qui au passage est parfait pour notre projet de fin de semaine).

>L’agrégation « Pipelines »

Toujours d’après la documentation officielle, un pipeline d’agrégation se constitue par le fait de traiter, en une ou plusieurs étapes, l’information.

Chaque étape effectue une opération sur les documents d’entrée pour par exemple : 

Filtrer des documents, regrouper des documents puis calculer leurs valeurs.
Les documents qui sortent d’une étape peuvent être utilisés par l’étape suivante.
Un pipeline d’agrégation peut renvoyer des résultats pour des groupe de documents, comme pour calculer des totaux, une moyenne maximale ou une moyenne minimale par exemple, c'est pour cela que dans ce projet nous utiliserons exclusivement des pipelines.


Afin d’illustrer correctement le terme d’agrégation, nous allons utiliser la database de notre projet et voir comment l'agrégation peut nous servir.

Celle-ci contient deux collections.

Une collection restaurants qui contient : les adresses complètes, les villes, le type de cuisine, le nom, la zone géographique et la longitude-latitude de chaque restaurant.

Une collection clients qui contient : le noms, prénom, email, intérêts, age, ville, téléphone, restaurants visités et point de fidélité 

Nous pouvons donc récupérer les informations clients en les filtrant afin de savoir quels clients ont visité le restaurant numéro un comme on peut le voir ci-dessous : 

![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/img/projetAggregateRequestWithResponse.PNG?raw=true "Aggregate Request")

Comme nous pouvons le voir dans la réponse sur l'encadré droit de visual studio code, Mongo nous renvoi la liste des clients ayant visités le restaurant numéro un, et nous affiche leur nom et prénom respectif.


Pour notre dernier test avec la base et nous montrer l'importance de combiné agrégation avec les requêtes géospatiales, voyons la requête et sa réponse :

![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/img/projectCombineGeoSWithAggregation.PNG?raw=true "project Combine GeoS With Aggregation")


Ici nous pouvons voir très clairement que nous pouvons récpérer les restaurants autour d'un point donné, et que l'on filtre par la suite à l'aide de notre agrégation tous les restaurants sur la ville de Lyon.

Ce système va être très pratique pour récupérer les données clients et les filtrer : 


![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/img/projetClientsGeoNearResult1.PNG?raw=true "projet Clients GeoNear Result")



Sur la capture d'écran ci-dessus, nous récupérons tout d'abord avec une requête géospatial les clients autour de coordonnées.

notez qu'un filtre dans le paramètre $geoNear est en place :  

>query : { "localisation.city" : "Lyon"}

Pour notre requêtes nous filtrons à l'aide de l'agrégation le résultat obtenu (anciennement filtré par le paramètre query), ce qui nous retourne la liste des clients habitant sur Lyon et faisant partie d'une sphère défini par nos coordonnées stocké dans la clé coordinates et par la distance maximale.

Grâce au paramètre 

>distanceField : "distance.estimation"

Nous nous retrouverons en base avec l'estimation de la distance entre le client et les coordonnées donnés.


Notez bien que nous avons effectué le traitement de cette requêtes dans une pipeline, appelé en bas de notre requête complète : 

>db.Clients.aggregate(pipeline)


## La methode explain

La méthode explain décrite dans cette partie va nous permettre d'afficher à l'écran un document qui contiendra toutes les étapes et les informations de la requêtes, ici grâce au paramètre "executionStats" 

>db.Clients.aggregate(pipeline).explain("executionStats")

Nous pouvons afficher toutes les statistiques d'éxécution au niveau de la collection.


![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/img/projectMethodExplain.PNG?raw=true "project Method Explain")


![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/img/projectMethodExplain2.PNG?raw=true "project Method Explain")


Il existe bien évidemment bien d'autres paramètres pour la méthode explain comme : 

>explain(informations)

>explain(queryPlanner)

>explain(allPlansExecution)

Tous pouvant se suivre par une méthode également comme find() par exemple


# }