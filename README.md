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

## MongoDB vs MySQL

Comme vu plus haut dans ce rapport, MongoDB est une base de données orientée documents à contrario de MySQL. Et cela présente un avantage certain dans le cadre de ce projet vu en cours. 
Le fonctionnement de MongoDB ce distingue de MySQL en matière de mémorisation des données, malgré la similitude que l’on peut retrouver dans les deux cas :
Tout d’abord nous pouvons voir que les tableaux (MySQL) sont remplacés par des collections (MongoDB)
Les champs les lignes et les colonnes (MySQL) sont remplacés par des documents en format JSON
Toutes les lignes d’un tableau MySQL ont une composition identique à l’inverse de MongoDB ou chaque document peut évoluer au fil du temps de manière individuel sans impacter le fonctionnement de la base.

La clé doit être unique dans les documents (MongoDB) mais peut se retrouver dans d’autres documents, ce qui est impossible avec MySQL.
Sur MySQL il est obligatoire d’établir des relations (JOINS) entre les différents tableaux
Il existe bien évidement bien d’autres différences, mais nous en terminerons avec cette brève présentation et nous en verrons d’autres par la suite.

# }