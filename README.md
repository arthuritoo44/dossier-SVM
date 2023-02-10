# dossier-SVM
L'objectif de ce projet est de mesurer l'efficacité d'un attaquant. Pour cela, nous analyserons tout d'abord notre variable à expliquer continue à savoir le ratio buts/minutes.

Le jeu de données utilisé regroupe différentes statistiques sur de nombreux matchs de football entre 2014 et 2023. Il est mis à jour chaque semaine par rapport aux matchs joués. 

Nous allons nous concentrer sur les statistiques qui nous intéressent à savoir, toutes les statistiques pouvant impacter le nombre de buts marqués par un attaquant.

Par la suite nous chercherons à faire la différence entre un attaquant étant souvent efficace et un attaquant marquant peu. Ceci se fera par la détermination de deux catégories, l'une comprenant les attaquants les plus efficaces et l'autre les attaquants peu efficaces.

## Visualisation des données

Afin d'avoir le maximum d'informations pour déterminer l'efficacité d'un attaquant, nous allons regrouper les jeux de données pour avoir le maximum de variables explicatives.

![Capture d'écran_20230210_105640](https://user-images.githubusercontent.com/118133724/218061581-38ca17ce-75fe-4c56-a7bf-6a7d3d904330.png)


Nous allons également passer le nom de nos variables en francais afin que ce soit plus compréhensible.

La visualisation du jeu de données nous permet de remarquer que certaines variables possèdent des valeurs manquantes. Nous allons les supprimer tout comme les valeurs aberrantes. Par exemple pour la variable Taille, certains individus ont la valeur 0.

## Création variable à expliquer

Nous cherchons à mesurer l'efficacité d'un attaquant. Dans le cas ou nous prenions le nombre de buts comme variable à expliquer, cette variable pourrait etre discriminante du fait qu'elle ne prend pas en compte le temps de jeu par rapport au nombres de buts marqués.

Nous allons donc créer une variable divisant le nombres de minutes jouées par le nombres de buts marqués afin de créer un ratio du nombres de minutes jouées entre deux buts. Afin d'avoir un échantillon représentatif, nous garderons les individus ayant marqués au moins un but et avec un temps de jeu minimum de 500 minutes.

Afin de se concentrer sur les joueurs qui marquent le plus, nous allons nous concentré sur les attaquants de cette base de données. On remarque logiquement que les attaquants ont un ratio plus faible entre deux buts marqués par rapport aux défenseurs et aux milieux de terrains.
![Capture d'écran_20230210_105327](https://user-images.githubusercontent.com/118133724/218061145-f647d45b-f6e3-40b3-aed2-79ac39468ebc.png)

## Analyse de la variable à expliquer

Nous avons commencé par analyser la distribution de notre variable. 
On remarque que la distribution est légèrement allongé vers la droite du fait que certains attaquants sont très peu efficaces et ont pour certains joueurs une moyenne d'un but marqués toutes les 3500 minutes soit plus de 40 matchs.

![Capture d'écran_20230210_105800](https://user-images.githubusercontent.com/118133724/218061816-9c9852d7-0cbd-43f4-9915-fb6e27d43442.png)


En analysant le boxplot de la variable on remarque que les individus marquant 1 but toutes les 2000 minutes ou plus sont considérés comme des individus atypiques.

![Capture d'écran_20230210_105831](https://user-images.githubusercontent.com/118133724/218061886-f62085c7-3afd-47fb-b1d0-e4de3f5a2a05.png)


Néanmoins l'objectif final étant de classifier les attaquants efficaces par rapport aux attaquants peu efficaces nous allons garder ces individus qui sont très nombreux afin de comprendre pourquoi ces attaquants marquent très peu.


## Visualisation des corrélations

### Séléction des variables les plus influentes

Afin de comprendre quelles variables influencent la ratio de buts marqués d'un attaquant, une matrice de corrélation va être effectué par rapport à notre variable à expliquer.

![Capture d'écran_20230210_105907](https://user-images.githubusercontent.com/118133724/218062016-4d44d932-5fa2-4a17-aaa5-94b2c5074eec.png)


L'étude des corrélation nous montrent que le ratio buts/minute est corrélée à 24% avec le nombres de minutes jouées, 4.9% avec le nombre de passes décisives, 10% avec la valeur marchande du joueur et à 22% avec la taille.

### Etude des variables catégorielles par rapport à la variable à expliquer

Nous avons étudié à l'aide de différents graphiques les liens entre les variables catégorielles et notre variable à expliquer. On ne remarque pas forcément plus d'effeiacité pour les attquants d'un championnat. Mis à part le championnat italien qui semble avoir une mèdiane légèrement plus faible.

![Capture d'écran_20230210_105944](https://user-images.githubusercontent.com/118133724/218062131-7c9863f0-b9bf-4335-b677-5af110dca04d.png)


Ensuite nous avons regardé si le pied favori du buteur nous permet d'avoir des informations sur son efficacité. On remarque que les gauxhers marquent relativement moins souvent, mais il est difficile de généraliser cela à l'ensemble des footballeurs.

![Capture d'écran_20230210_110010](https://user-images.githubusercontent.com/118133724/218062228-08c2e4a1-4779-442e-9faa-339866788d92.png)


### Nuages de points avec les variables quantitatives

![Capture d'écran_20230210_110052](https://user-images.githubusercontent.com/118133724/218062399-d823b757-5b9b-4dc9-8f0c-b869bb854b3d.png)


Nous avons ensuite regardé si un ajustement linéaire était présent entre nos variables qualitatives.
On remarque une ceratine linéraité entre la valeur marchande et l'efficacité. En effet, plus un attaquant marque, plus sa valeur marchande est importante, il ya toutefois beaucoup d'observations avec un ratio très élevé ce qui limite l'interprétation.

## Modélisation

Une fois cette analyse exploratoire effectuée nous avons exporté notre fichier afin de transformer notre variable à expliquer en variable catégorielle, l'objectif étant de ne garder que les individus les plus efficaces ainsi que ceux qui ne marquent pas beaucoup.
