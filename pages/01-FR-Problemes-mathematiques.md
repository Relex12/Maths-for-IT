# Problèmes, Algorithmes et Intelligence artificielle

Ce dépôt traite d'algorithmes et l'intelligence artificielle, donne une classification des problèmes, liste les principaux algorithmes existants et les méthodes d'intelligence artificielle, ainsi que leurs applications.

* [Problèmes, Algorithmes et Intelligence artificielle](#problèmes,-algorithmes-et-intelligence-artificielle)
    * [Problèmes](#problèmes)
        * [Recherche et décision](#recherche-et-décision)
        * [Inclusions des classes](#inclusions-des-classes)
        * [P = NP et complétude](#p-=-np-et-complétude)
        * [Exemples de problèmes](#exemples-de-problèmes)
    * [[Algorithmes](https://fr.wikipedia.org/wiki/Liste_d%27algorithmes)](#[algorithmes](https://fr.wikipedia.org/wiki/liste_d%27algorithmes))
    * [Intelligence artificielle](#intelligence-artificielle)
* [Usage](#usage)
    * [Input / Output systems](#input-/-output-systems)
    * [Jeux](#jeux)
        * [Jeux solitaires](#jeux-solitaires)
        * [Jeux 1 contre 1](#jeux-1-contre-1)
        * [Autres jeux](#autres-jeux)

<!-- table of contents created by Adrian Bonnet, see https://github.com/Relex12/Markdown-Table-of-Contents for more -->

## Problèmes

**Théorie de la complexité**

En informatique théorique, la théorie de la complexité traite de la difficulté que pose, à la fois en temps et en ressources, la résolution de certains problèmes. 

C'est donc un bon point d'entrée avant de parler l'algorithmes et d'intelligence artificielle.

Un **problème** est une question que l'on se pose dans un cadre particulier. Cela peut être la résolution d'un jeu, la recherche de spécificités sur un graphe, ou pleins d'autres choses. De manière générale, c'est une question à laquelle on va résoudre grâce à un algorithme.

### Recherche et décision

* Un problème de **décision** est un problème auquel on peut répondre par *oui* ou par *non*, par exemple : "Etant donné un entier n, n est-il premier ?" (PRIME)
* Un problème de **recherche** est un problème fonctionnel dans lequel la réponse consiste à fournir un élément, par exemple : "Etant un ensemble ordonné E, c'est-à-dire doté d'une relation d'ordre, donner le plus petit élément de E"
* Un problème d'**optimisation** est un problème de recherche qui cherche à maximiser ou a minimiser la solution, par exemple : "Etant donnés dans un graphe G, donner le plus court cycle hamiltonien de G" (Voyageur de commerce)

Les problèmes de recherche, notamment les problèmes d'optimisation, **peuvent être transformés** en un problème de décision : par exemple, pour la recherche de plus court chemin entre A et B dans un graphe G, "*Quel est le chemin le plus court entre A et B ?*" peut être remplacé par "*Existe-t-il un chemin entre A et B plus petit qu'une longueur L ?*".

Les problèmes d'optimisation sont notamment étudiés dans la **recherche opérationnelle**, qui regroupe l'ensemble des méthodes, modèles et outils relevant de l'optimisation d'un système complexe.

 ### Classes de complexité

On ne s'intéresse qu'aux problèmes de décision, les autres problèmes pouvant être ramenés à un problème de décision.

On distingue la complexité selon deux types, l'ordre de grandeur du **temps de résolution** et l'ordre de grandeur de l'**espace nécessaire** à la résolution.

La résolution se fait sur une **machine de Turing** qui peut être **déterministe** (les actions suivant différents choix sont faites **séparément**) ou **non-déterministe** (les actions suivant différents choix sont faites **simultanément**).

Les ordres de grandeur sont donnés en fonction de la taille des données d'entrées, notée *n*. La complexité peut être :

* logarithmique 	$O(n) = log(n)$
* polynomiale	    $O(n) = (n^m),\space m \in \mathbb{N}$
* exponentiel 		$O(n) = (r^n),\space r \in \mathbb{R}$

| <u>**Complexité temporelle**</u> | **Temps polynomial** | **Temps exponentiel** |
| :------------------------------: | :------------------: | :-------------------: |
|     **Machine déterministe**     |      P ou PTIME      |        EXPTIME        |
|   **Machine non-déterministe**   |     NP ou NPTIME     |       NEXPTIME        |

Pour chaque problème de *NP*, on peut construire le problème dual : on forme aussi le complémentaire de *NP*, noté *co-NP*.

|  <u>Complexité spatiale</u>  | Espace logarithmique | Espace polynomial | Espace exponentiel |
| :--------------------------: | :------------------: | :---------------: | :----------------: |
|   **Machine déterministe**   |     L ou LSPACE      |      PSPACE       |      EXPSPACE      |
| **Machine non-déterministe** |    NL ou NLSPACE     |      NPSPACE      |     NEXPSPACE      |

En particulier, PSPACE est égal à NPSPACE, et EXPSPACE est égal à NEXPSPACE (d'après le théorème de Savitch).

Il est possible de créer des classes sur d'autres modèles de calculs que les machines de Turing déterministes et non-déterministes, par exemple :

* NC et P/poly avec des circuits booléens
* ZPP, RP et BPP avec des machines de Turing probabilistes
* BQP avec des ordinateurs quantiques

### Inclusions des classes

On sait que :

* L ⊆ NL ⊆ NC ⊆ P ⊆ NP ⊆ PSPACE = NPSPACE ⊆ EXPTIME ⊆ NEXPTIME ⊆ EXPSPACE = NEXPSPACE
* P ⊆ Co-NP ⊆ PSPACE
* NL ⊊ PSPACE ⊊ EXPSPACE 
* P ⊊ EXPTIME 
* NP ⊊ NEXPTIME

On ne sait pas si :

* L = NL
* L = P
* NP = co-NP
* P = PSPACE
* NP = PSPACE
* EXPTIME = NEXPTIME

### P = NP et complétude

En résumé :

* **P** est l'ensemble des problèmes de décision dont la résolution est "faisable" en temps polynomial par rapport à la taille de l'entrée. 
* **NP** est l'ensemble des problèmes de décision dont la résolution ne peut pas se faire en temps polynomial, mais forcément en exponentiel. 
* En revanche, il est toujours possible de vérifier en temps polynomial si une solution à un problème NP est correcte.
* P est inclus dans NP.

On définit une nouvelle classe **NP-complet**, qui contient tous les problèmes dont la vérification peut se faire en temps polynomial et auxquels chaque problème de la classe NP peut être ramené via une **réduction polynomiale**.

La réduction polynomiale implique que le passage de n'importe quel problème NP à un problème NP-complet peut se faire en temps polynomial (sur une machine de Turing déterministe).

La célèbre question **P = NP ?** (l'un des sept problèmes du prix du millénaire) revient donc à une égalité d'ensemble, c'est-à-dire une double inclusion. On sait que P ⊆ NP, mais on ne sait pas si la réciproque est vraie. En termes vulgarisés, la question P = NP ? peut se traduire comme ceci : tous les problèmes dont la vérification d'une solution peut être faite en temps polynomial sont-ils résolubles en temps polynomial, ou existe-t-il des problèmes qui ne seront jamais solubles en temps polynomial ? 

Pour répondre à cette question, deux possibilités : 

* si P = NP, alors il suffit de trouver un moyen de résoudre en temps polynomial un seul problème de la classe NP-complet, par réduction polynomiale, tous les problèmes NP seront inclus dans P
* si P ≠ NP, alors il suffit de montrer qu'un seul problème NP ne peut pas être résolu en temps polynomial, notamment en trouvant une borne inférieur suffisamment grande du temps de résolution

Pour indication, 

### Exemples de problèmes

* **Tri** : le tri d'une liste de nombre peut se faire de manière naïve avec une complexité en $O(n^2)$, les meilleurs algorithmes (Tri rapide ou Tri fusion par exemple) ont une complexité en $O(n.log(n))$. Tri est un un problème fonctionnel dont la version décisionnelle appartient à la classe P
* **Primalité** :

Le tableau ci-dessous résume les problèmes les plus connus :

| Catégorie           | Problème                                 | Complexité |
| :------------------ | ---------------------------------------- | ---------- |
| Jeux                | Démineur (Minesweeper)                   | NP-complet |
|                     | Sudoku                                   | NP-complet |
|                     | Tetris                                   | NP-complet |
|                     | Mastermind                               | NP-complet |
|                     | Lemmings                                 | NP-complet |
|                     | Taquin                                   | NP         |
|                     | Go                                       | > NP       |
|                     |                                          |            |
| Théorie des graphes | Cycle hamiltonien (voyageur de commerce) | NP-complet |
|                     | Coloration à k couleurs                  | NP-complet |
|                     | Nombre achromatique                      | NP-complet |
|                     | Partition en cliques                     | NP-complet |
|                     | Plus court chemin                        | P          |
|                     | Connexité                                | P          |
|                     |                                          |            |
| Autre               | SAT                                      | NP-complet |
|                     | Sac-à-dos                                | NP-complet |
|                     | Factorisation en nombres premiers        | NP         |
|                     | Primalité                                | P          |
|                     | Optimisation linéaire                    | P          |
|                     | Restriction 2-SAT                        | P          |
|                     | Tri                                      | P          |



* Flotteurs dérivants
* Prime
* Graphes
  * Voyageur de commerce
  * Arbre couvrant minimal
  * Recherche feuille, cycles, sommets isolés
* SAT
* Sac-à-dos
* Jeu de taquin

## Aléatoire

Nos ordinateurs sont très puissants lorsqu'il s'agit de réaliser des calculs formels, à vrai dire c'est tout ce qu'ils savent faire. Pour autant, il y a des domaines où les programmeurs ont besoin de générer des valeurs aléatoires

### Aléatoire pur - Phénomènes physiques

L'aléatoire pur est réalisé par la mesure d'un phénomène physique

* Mur de lampe à lave
* Rayonnement avec antenne

### Pseudo aléatoire - Chaos mathématique

PRNG - pseudo random number generator

* Fonction de hachage
* Mersenne Twister PRNG
* 

## [Algorithmes](https://fr.wikipedia.org/wiki/Liste_d%27algorithmes)

* Recherche (Dichotomie, ABR, filtre Bloom, table de hachage etc)

* Tri

* Cryptographie

  * Chiffrement subsitution, cryptographie asymétrique, cryptographie symétrique, hachage,

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

## Intelligence artificielle

* Apprentissage automatique (machine learning)
  * Classification automatique
  * Régression
  * SVM
  * Réseaux de neurones
    * Deep learning ()

# Usage

## Input / Output systems

* Recognition
* Classification
* Generation : you give it a

## Jeux

### Jeux solitaires

* Tetris
* Démineur (Minesweeper)

### Jeux 1 contre 1

* Echec (Chess)
* Go
* Othello

### Autres jeux

* Jeopardy!
* Poker





---

Questions :

* est-ce que Minimax est vraiment de l'intelligence artificielle ?