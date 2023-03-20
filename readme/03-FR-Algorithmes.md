# [Algorithmes](https://fr.wikipedia.org/wiki/Liste_d%27algorithmes)


## Autres algorithmes

### Minimax

<!---
Dans Problemes mathématiques - Théorie des jeux
===============================================

En revanche, lorsque ce n'est pas possible, comme aux échecs par exemple, il faut avoir recourt à une fonction d'évaluation basée sur l'état actuel des connaissances sur le jeu, en prenant par exemple le nombre de pièces restantes et leurs positions. Cependant, comme la profondeur de l'arbre de recherche reste déterminante pour proposer le meilleur coup à jouer, il existe de nombreuses optimisations possibles à Minimax pour accélérer la recherche. La première d'entre elles est l'**élagage *alpha-bêta*** (*alpha-beta pruning*) qui consiste à ne pas explorer certaines parties de l'arbre si celles-ci sont moins intéressantes que les parties déjà explorées, ce qui permet d'économiser l'évaluation de toutes les positions qui en découlent. Le principe repose sur le fait que chaque joueur cherche à optimiser son propre score, et si l'on sait à un moment donné que l'adversaire possède une meilleure alternative que celle qu'on est en train d'évaluer, alors on peut couper cette partie.

A ajouter en plus
=================

Grâce à l'élagage *alpha-bêta*, on peut chercher à évaluer les positions qui semblent les meilleures en premier, pour cela on effectue d'abord l'algorithme Minimax avec une profondeur de un, puis on effectue Minimax à nouveau avec une profondeur de deux en évaluant les coups les plus intéressants en premier. Même si cela peut sembler contre-intuitif, grâce à l'élagage précédent, ceci améliore considérablement la vitesse de calcul, puisque les meilleurs coups sont évalués en premiers, à chaque exécution de Minimax, une grande partie de l'arbre
--->
### Régression linéaire

[régression linéaire](https://fr.wikipedia.org/wiki/Régression_linéaire)

### Régression logistique

[régression logistique](https://fr.wikipedia.org/wiki/Régression_logistique)

### Méthode des k plus proches voisins

[méthode des k plus proches voisins](https://fr.wikipedia.org/wiki/Méthode_des_k_plus_proches_voisins) pour un apprentissage supervisé

### Méthodes statistiques

[méthodes statistiques](https://fr.wikipedia.org/wiki/Statistique) comme le [modèle de mixture gaussienne](https://fr.wikipedia.org/wiki/Modèle_de_mixture_gaussienne)

### Analyse discriminante linéaire

[analyse discriminante linéaire](https://fr.wikipedia.org/wiki/Analyse_discriminante_linéaire)

### Analyse en composantes principales

[analyse en composantes principales](https://fr.wikipedia.org/wiki/Analyse_en_composantes_principales)



[Algorithmes utilisés - Wikipédia](https://fr.wikipedia.org/wiki/Apprentissage_automatique#Algorithmes_utilis%C3%A9s)


* Recherche (Dichotomie, ABR, filtre Bloom, table de hachage etc)
* Tri
* Graphes

  * Arbre couvrant minimal, recherche de chemin (Pathfinding)
* Recherche de motif (pattern matching)



* Recherche opérationnelle

  * simplexe, Branch&Bound

* glouton

* MinMax, élagage alpha-bêta

* évolutionnistes

  * génétiques, mémétiques

* récursifs

  * tours de Hanoï, factorielle, fractales (Tapis de Sierpiński)

* Euclide

* Le lièvre et la tortue

* heuristiques :

  * Las Vegas, Monte-Carlo

* Apprentissage profond
