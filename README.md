# dossier-SVM
L'objectif de ce projet est de mesurer l'efficacité d'un attaquant. Pour cela, nous analyserons tout d'abord notre variable à expliquer continue à savoir le ratio buts/minutes.

Le jeu de données utilisé regroupe différentes statistiques sur de nombreux matchs de football entre 2014 et 2023. Il est mis à jour chaque semaine par rapport aux matchs joués. 

Par la suite nous chercherons à faire la différence entre un attaquant étant souvent efficace et un attaquant marquant peu. Ceci se fera par la détermination de deux catégories, l'une comprenant les attaquants les plus efficaces et l'autre les attaquants peu efficaces.

## Visualisation des données

Afin d'avoir le maximum d'informations pour déterminer l'efficacité d'un attaquant, nous allons regrouper les jeux de données pour avoir le maximum de variables explicatives.

Nous allons également passer le nom de nos variables en francais afin que ce soit plus compréhensible.

La visualisation du jeu de données nous permet de remarquer que certaines variables possèdent des valeurs manquantes. Nous allons les supprimer tout comme les valeurs aberrantes. Par exemple pour la variable Taille, certains individus ont la valeur 0.

## Création variable à expliquer

Nous cherchons à mesurer l'efficacité d'un attaquant. Dans le cas ou nous prenions le nombre de buts comme variable à expliquer, cette variable pourrait etre discriminante du fait qu'elle ne prend pas en compte le temps de jeu par rapport au nombres de buts marqués.

Nous allons donc créer une variable divisant le nombres de minutes jouées par le nombres de buts marqués afin de créer un ratio du nombres de minutes jouées entre deux buts. Afin d'avoir un échantillon représentatif, nous garderons les individus ayant marqués au moins un but et avec un temps de jeu minimum de 500 minutes.
