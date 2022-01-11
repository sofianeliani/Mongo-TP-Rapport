# Rapport de TP sur MongoDB {

> Introduction du rapport 

Voici le rapport de la semaine de cours qui va nous permettre de suivre notre progression sur MongoDB et de répondre à la problématique posé par le formateur.

## Présentation de MongoDB

MongoDB est SGBD (Système de gestion de base de données) orienté documents et de surcroît non relationnel (à contrario de son confrère MySQL par exemple présenté un peu plus bas dans ce rapport).
Nous entendons orienter documents par le fait qu’un document dans mongo db peut-être vu comme un ensemble de clé valeur très simple à utiliser. 

Nous utilisons javascript comme langage natif avec MongoDB.
MongoDB se caractérise par son contenu, des documents et des collections réunies en base.
Voici un exemple de documents stocké dans une collections appelé Restaurants :

![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/img/Documents-Example.png?raw=true "Documents Example")


Ceci est un exemple d’une base de données par le formateur Mounir Bendahmane dans le cadre de ce cours. La base de données Restaurants possède également une collection du même nom.
Présent dans ces documents vous pouvez voir des données en format JSON, et c’est ce qui fait qu’un document à l’autre, la structure des données peut changer au fil du temps sans impacter le fonctionnement de notre base.
On dit que le modèle de document mappe les objets du code de nos applications, ce qui facilite grandement le traitement des données.


## Présentation du projet

Une chaine de restaurant souhaite récupérer des données clients afin de capitaliser
sur un flux de personnes sans cesse grandissant 
(plusieurs dizaine de milliers de clients par semaine dans toute la France).

Le but est de fournir un projet d'application centré sur un stockage des données avec MongoDB.

Bien évidement nous vous montrerons ci-dessous  les choix technologiques qui ont été fait et l'utilité que cela présente pour un projet de cette ampleur.


## Sommaire

0. [Les spécifications techniques](#les-spécifications-techniques)
1. [MongoDB vs MySQL](#mongodb-vs-mysql)
2. [Les fonctionnalités Avancées](#les-fonctionnalités-avancées)
3. [MongoDB du NoSQL](#mongodb-du-nosql)
3. [Elasticsearch une alternative NoSQL](#elasticsearch-une-alternative-nosql)
4. [Les requêtes géospatiales](#les-requêtes-géospatiales)
5. [Les requêtes géospatiales et notre projet](#les-requêtes-géospatiales-et-notre-projet)
6. [Agrégation avec MongoDB](#agrégation-avec-MongoDB)


## Les spécifications techniques

![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/icons/nodejs.png?raw=true "NodeJS")          ![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/icons/compass.png?raw=true "NodeJS")         ![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/icons/mongodb.png?raw=true "NodeJS")


Notre choix concernant les technologies à utiliser porte sur atlas, compass et la création d'une api NodeJS pour les requêtes.

Ceci étant nous vous montreros au fur et à mesure de ce rapport le parallèle entre les requêtes faite avec notre API nodeJS et les requêtes natives.

Concernant notre choix technologique, en vue des consignes du formateur, et du travail de groupe imposé, il était préférable de choisir un outil performant et que chacun sait manipuler. Atlas offre un service gratuit et performant afin d'héberger une base de données Mongo via un cluster (accessible avec une simple ligne à copier-coller dans l'outil prévu à cet effet).

C'est ensuite compass qui prend le relai, pour sa simplicité d'installation et d'utilisation. Compass va très facilement nous aider à naviguer dans notre base, à tester nos requêtes avec son terminal intégrer, et va également nous offrir une belle visu sur le jeux de données présent dans la base (voir screenshot ci-dessous).

![Alt text](https://github.com/sofianeliani/Mongo-TP-Rapport/blob/main/img/compass.png?raw=true "Compass")


## MongoDB vs MySQL

Comme vu plus haut dans ce rapport, MongoDB est une base de données orientée documents à contrario de MySQL. Et cela présente un avantage certain dans le cadre de ce projet vu en cours. 
Le fonctionnement de MongoDB ce distingue de MySQL en matière de mémorisation des données, malgré la similitude que l’on peut retrouver dans les deux cas :
Tout d’abord nous pouvons voir que les tableaux (MySQL) sont remplacés par des collections (MongoDB)
Les champs les lignes et les colonnes (MySQL) sont remplacés par des documents en format JSON
Toutes les lignes d’un tableau MySQL ont une composition identique à l’inverse de MongoDB ou chaque document peut évoluer au fil du temps de manière individuel sans impacter le fonctionnement de la base.

La clé doit être unique dans les documents (MongoDB) mais peut se retrouver dans d’autres documents, ce qui est impossible avec MySQL.
Sur MySQL il est obligatoire d’établir des relations (JOINS) entre les différents tableaux
Il existe bien évidement bien d’autres différences, mais nous en terminerons avec cette brève présentation et nous en verrons d’autres par la suite.


## Les fonctionnalités avancées

MongoDB et son langage d’interrogation est extrêmement puissant. Nous pouvons nous permettre d’effectuer toutes les requêtes possibles et de surcroît avoir un résultat beaucoup plus poussé, tout cela de manière simple contrairement à une base relationnelle tel que MySQL par exemple.

 L’avantage de ce fonctionnement dans ce cours est, qu’il va falloir faire croitre notre application au fil du temps et effectuer des recherches poussées à des fins de statistiques, tout en épargnant certaines informations, et ce sur important jeux de données.

Bien évidement nous verrons cela plus bas dans ce rapport.


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


Attention, bien que MongoDB est force de proposition sur ce type de projet, et que il est l’objet de ce cours, d’autre SGBD sont présente sur le marché et mérite que l’on s’y attarde. 


## Elasticsearch une alternative NoSQL

Elasticsearch est un outil se présentant comme un SGBD orienté document et qui va nous permettre de mettre en place un système de recherche très complexe.

Dans un premier temps nous pourrons stocker des informations, et dans un second temps nous pourrons les récupérer à l’aide de requêtes.

Les avantages certains que possède Elasticsearch sont que les recherches peuvent être basé sur du texte et peuvent contenir des critères très poussés, d’organiser les résultats par pertinence (très utile pour créer un moteur de recherche par exemple), et il possède également une API dite RESTful afin de pouvoir communiquer facilement avec lui.

Tout comme son confrère MongoDB, Elasticsearch stocke les données de manière non-structuré.
Nous pouvons également le distribuer et nous permettre d’avoir plusieurs instances au niveau du réseau afin d’obtenir des résultats plus rapides.
Une solution simple d’utilisation et efficace dans bien des domaines.


## Les requêtes géospatiales 

Sources : (https://rtavenar.github.io/teaching/nosql_fiche/html/td_textgeo.html)

Plusieurs points s’appuient sur le fait d’utiliser des données géospatiales :

Si l’on souhaite trouver des éléments présents dans la base les plus proches d’un point donné

Si l’on souhaite trouver des éléments présents dans la base entièrement inclus dans un polygone donné

Si l’on souhaite trouver des éléments présents dans la base partiellement inclus dans un polygone donné (pour représenter une rue par exemple)

C’est la que la notion d’index géospatiaux fait son entré : Sources :

(https://docs.mongodb.com/manual/geospatial-queries/)

(https://practicalprogramming.fr/mongodb-index)

Pour illustrer cela prenons le cas des Index 2d, qui permettent de placer des coordonnées sur un axe en 2 dimensions comme son nom l’indique. 

La requête suivante porte sur des documents situés dans un rectangle défini par [0, 0] dans le coin inférieur gauche et par [100, 100] dans le coin supérieur droit.

(https://docs.mongodb.com/manual/tutorial/query-a-2d-index/)

```ini
# MongoDB documentation

db.places.find({
    loc:
    {
        $geoWithin :
        {
            $box : [ 
                [0, 0], 
                [100, 100]
            ]   
        }
    }
})

```

Ou les index 2dsphere qui permettent de placer des coordonnées latitudes et longitudes.

Prenons un exemple de cas ou une collection se nommant « places » avec des documents, stockent des données de localisation sous forme de point GeoJSON dans un champs nommé loc  :

(https://docs.mongodb.com/manual/core/2dsphere/)

```ini
# MongoDB documentation

db.places.insertMany( [
    {
        loc : { type: "Point", coordinates: [ -73.97, 40.77 ] },
        name: "Central Park",
        category : "Parks"
    },
    {
        loc : { type: "Point", coordinates: [ -73.88, 40.78 ] },
        name: "La Guardia Airport",
        category : "Airport"
    }
    ])

```

Ou les index geoHaystack qui permettent de définir une aire suivant des points sur un axe en 2 dimensions.

(https://docs.mongodb.com/manual/tutorial/build-a-geohaystack-index/)

Pour ces documents en exemple : 

```ini
# MongoDB documentation

{ _id : 100, pos: { lng : 126.9, lat : 35.2 } , type : "restaurant"}
{ _id : 200, pos: { lng : 127.5, lat : 36.1 } , type : "restaurant"}
{ _id : 300, pos: { lng : 128.0, lat : 36.7 } , type : "national park"}

```

Les index suivants stockent des clés dans une unité de longitude ou de latitude : 

```ini
# MongoDB documentation

db.places.createIndex( 
    { pos : "geoHaystack", type : 1 } ,
    { bucketSize : 1 } 
)

```


## Les requêtes géospatiales et notre projet

Maintenant que nous en savons un peu plus sur les requêtes géospatiales et leur fonctionnement, la question suivante se pose.

Comment cela peut il s’intégrer au projet dans cette semaine de cours ? 
Dans notre projet et conformément aux conseils donnés par le formateur Mounir Bendahmane, celui-ci reposera sur la récupération de données clients.

Il serait donc très intéressant de créer un document se chargeant de récupérer et distribuer toutes les informations statistiques voulus : Les zones qui sont les plus fréquentés, lesquels restaurants sont les plus fréquentés, les menus les plus commandés, etc …

Nous pouvons également offrir une visu graphique sur la situation global et individuel de chaque restaurant, arrondissement, client ce qui ajoute du poids à notre argumentaire.
Tout cela peut aider grandement aux diverses études de marchés de la marque et est au fond un système obligatoire intégrer pour y parvenir.

MongoDB est force de proposition pour arriver à ce résultat pour toutes les raisons techniques cité plus haut.


## Agrégation avec MongoDB


>L’agrégation

Si nous restons sur la définition de l’agrégation d’après la documentation officielle mongo db, l’agrégation est le fait de traiter les informations de plusieurs documents afin d’en retourner le résultat calculé.

Nous pouvons utiliser une opération d’agrégation pour : 

Regrouper des valeurs lié à plusieurs documents, effectuer des opérations sur les données groupées pour renvoyer un résultat unique et enfin analyser l’évolution des données dans le temps (ce qui au passage est parfait pour notre projet de fin de semaine).

>L’agrégation « Pipelines »

Toujours d’après la documentation officielle, un pipeline d’agrégation se constitue par le fait de traité en une ou plusieurs étapes l’information.

Chaque étape effectue une opération sur les documents d’entrée pour par exemple : 

Filtrer des documents, regrouper des documents puis calculer leurs valeurs.
Les documents qui sortent d’une étape peuvent être utilisés par l’étape suivante.
Un pipeline d’agrégation peut renvoyer des résultats pour des groupe de documents, comme pour calculer des totaux, une moyenne maximale ou une moyenne minimale par exemple.





Afin d’illustrer correctement le terme d’agrégation, nous allons utiliser notre collection Restaurants vu en cours.

Celle-ci contient les adresses complètes, les arrondissements, le type de cuisine, la notation, le nom, la zone géographique et la longitude-latitude de chaque restaurant.
Nous pouvons donc calculer par exemple, le nombre total de commandes (si il y’en a) faite sur un restaurant en particulier et faire la somme de celle-ci.

La fonction aggregate() et les mots clés suivants :  $group, $sum pour sommer tous nos éléments



# }