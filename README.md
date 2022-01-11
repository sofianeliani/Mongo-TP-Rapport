# Rapport de TP sur MongoDB {

> Introduction du rapport 

Voici le rapport de la semaine de cours qui va nous permettre de suivre notre progression sur MongoDB et de répondre à la problématique posé par le formateur.

## Présentation de MongoDB

MongoDB est SGBD (Système de gestion de base de données) orienté documents et de surcroît non relationnel (à contrario de son confrère MySQL par exemple présenté un peu plus bas dans ce rapport).
Nous entendons orienter documents par le fait qu’un document dans mongo db peut-être vu comme un ensemble de clé valeur très simple à utiliser. 

Nous utilisons javascript comme langage natif avec MongoDB.
MongoDB se caractérise par son contenu, des documents et des collections réunies en base.
Voici un exemple de documents stocké dans une collections appelé Restaurants :

//insert-image

Ceci est un exemple d’une base de données par le formateur Mounir Bendahmane dans le cadre de ce cours. La base de données Restaurants possède également une collection du même nom.
Présent dans ces documents vous pouvez voir des données en format JSON, et c’est ce qui fait qu’un document à l’autre, la structure des données peut changer au fil du temps sans impacter le fonctionnement de notre base.
On dit que le modèle de document mappe les objets du code de nos applications, ce qui facilite grandement le traitement des données.


## Sommaire

1. [MongoDB vs MySQL](#mongodb-vs-mysql)
2. [Les fonctionnalités Avancées](#les-fonctionnalités-avancées)
3. [MongoDB du NoSQL](#mongodb-du-nosql)
3. [Elasticsearch une alternative NoSQL](#elasticsearch-une-alternative-nosql)
4. [Les requêtes géospatiales](#les-requêtes-géospatiales)


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




# }