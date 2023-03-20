# Théorie de la complexité

En informatique théorique, la **théorie de la complexité** traite de la difficulté que pose, à la fois en temps et en ressources, la résolution de problèmes mathématiques. Un **problème** est une question que l'on se pose dans un cadre particulier. Cela peut être la résolution d'un jeu, la recherche de spécificités sur un graphe, ou pleins d'autres choses. De manière générale, c'est une question à laquelle on va répondre grâce à un algorithme.

## Sommaire

* [Théorie de la complexité](#théorie-de-la-complexité)
    * [Sommaire](#sommaire)
    * [Recherche et décision](#recherche-et-décision)
    * [Inclusions des classes](#inclusions-des-classes)
    * [P =? NP et complétude](#p-=-np-et-complétude)
    * [PRIMES](#primes)
    * [Autres problèmes](#autres-problèmes)
    * [Théorie des jeux](#théorie-des-jeux)
    * [Recherche opérationnelle](#recherche-opérationnelle)

<!-- table of contents created by Adrian Bonnet, see https://Relex12.github.io/Markdown-Table-of-Contents for more -->

## Recherche et décision

* Un problème de **décision** est un problème auquel on peut répondre par *oui* ou par *non*, par exemple : *Etant donné un entier n, n est-il premier ?* (PRIME)
* Un problème de **recherche** est un problème fonctionnel dans lequel la réponse consiste à fournir un élément, par exemple : *Etant donné un graphe G, donner un arbre couvrant de G*
* Un problème d'**optimisation** est un problème de recherche qui cherche à maximiser ou a minimiser la solution, par exemple : *Etant donné un ensemble ordonné E, c'est-à-dire doté d'une relation d'ordre, donner le plus petit élément de E*

Les problèmes de recherche, notamment les problèmes d'optimisation, **peuvent être transformés** en un problème de décision : par exemple, pour la recherche de plus court chemin entre A et B dans un graphe G, *Quel est le chemin le plus court entre A et B ?* peut être remplacé par *Existe-t-il un chemin entre A et B plus petit qu'une longueur L ?*.

Les problèmes d'optimisation sont notamment étudiés dans la **recherche opérationnelle**, qui regroupe l'ensemble des méthodes, modèles et outils relevant de l'optimisation d'un système complexe.

 ## Classes de complexité

Dans la théorie de la complexité, on ne s'intéresse qu'aux problèmes de décision, les autres problèmes pouvant être ramenés à un problème de décision. On distingue la complexité selon deux types : l'ordre de grandeur du **temps de résolution** et l'ordre de grandeur de l'**espace nécessaire** à la résolution.

La résolution se fait sur une **machine de Turing** qui peut être **déterministe** (les actions suivant différents choix sont faites **séparément**) ou **non-déterministe** (les actions suivant différents choix sont faites **simultanément**).

Les ordres de grandeur sont donnés en fonction de la taille des données d'entrées, notée *n*. La complexité peut être :

* logarithmique *O(n) = log(n)*
* polynomiale    *O(n) = (n^m^)*
* exponentielle  *O(n) = (r^n^)*

| <u>Complexité temporelle</u> | Temps polynomial | Temps exponentiel |
| :--------------------------: | :--------------: | :---------------: |
|   **Machine déterministe**   |    P ou PTIME    |      EXPTIME      |
| **Machine non-déterministe** |   NP ou NPTIME   |     NEXPTIME      |

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

## Inclusions des classes

On sait que :

* L ⊂ NL ⊂ NC ⊂ P ⊂ NP ⊂ PSPACE = NPSPACE ⊂ EXPTIME ⊂ NEXPTIME ⊂ EXPSPACE = NEXPSPACE
* P ⊂ Co-NP ⊂ PSPACE
* NL ⊂ PSPACE ⊂ EXPSPACE
* P ⊂ EXPTIME
* NP ⊂ NEXPTIME

On ne sait pas si :

* L = NL
* L = P
* NP = co-NP
* P = PSPACE
* NP = PSPACE
* EXPTIME = NEXPTIME

## P =? NP et complétude

En résumé :

* **P** est l'ensemble des problèmes de décision dont la résolution est "faisable" en temps polynomial par rapport à la taille de l'entrée.
* **NP** est l'ensemble des problèmes de décision dont la résolution ne peut pas se faire en temps polynomial, mais forcément en exponentiel.
* En revanche, il est toujours possible de vérifier en temps polynomial si une solution à un problème NP est correcte.
* P est inclus dans NP.

On définit une nouvelle classe **NP-complet**, qui contient tous les problèmes dont la vérification peut se faire en temps polynomial et auxquels chaque problème de la classe NP peut être ramené via une **réduction polynomiale**.

La réduction polynomiale implique que le passage de n'importe quel problème NP à un problème NP-complet peut se faire en temps polynomial (sur une machine de Turing déterministe).

La célèbre question **P =? NP** (l'un des sept problèmes du prix du millénaire) revient donc à une égalité d'ensemble, c'est-à-dire une double inclusion. On sait que P ⊂ NP, mais on ne sait pas si la réciproque est vraie. En termes vulgarisés, la question *P =? NP* peut se traduire comme ceci : tous les problèmes dont la vérification d'une solution peut être faite en temps polynomial sont-ils résolubles en temps polynomial, ou existe-t-il des problèmes qui ne seront jamais solubles en temps polynomial ?

Pour répondre à cette question, deux possibilités :

* si P = NP, alors il suffit de trouver un moyen de résoudre en temps polynomial un seul problème de la classe NP-complet, par réduction polynomiale, tous les problèmes NP seront inclus dans P
* si P ≠ NP, alors il suffit de trouver un contre-exemple, un problème NP qui ne peut pas être résolu en temps polynomial, notamment en trouvant une borne inférieur suffisamment grande du temps de résolution

Pour indication, dans un sondage réalisé en 2019, 87% des personnes interrogées estiment que P ≠ NP, et ce chiffre monte à 99% pour des spécialistes du sujets.[^1]

[^1]: [Hemaspaandra, L. A. (2019). SIGACT News Complexity Theory Column 100. *SIGACT News*, *50*(1), 35-37.](https://www.cs.umd.edu/users/gasarch/BLOGPAPERS/pollpaper3.pdf)

## PRIMES

Pour illustrer ce qu'est la complexité, voici plus en détail le problème de **test de primalité** sur les entiers naturel, PRIMES. La question est la suivante : *Etant donné un entier naturel n, est-ce que n est premier ?*.

La **méthode naïve** consiste à diviser *n* consécutivement par tous les entiers *k* ∈ ⟦ 2 ; *n*-1 ⟧, si la division de *n* par *k* donne un nombre entier, alors *n* n'est pas premier, si aucune division ne donne de nombre entier alors *n* est premier. On peut d'abord optimiser en limitant *k* inférieur à la racine carrée de *n*, *k* ∈ ⟦ 2 ; ⌊√*n*⌋ ⟧, car si il existe *p* et *q* tel que *n* = *p*.*q*, alors *p* ⩽ √*n* ou *q* ⩽ √*n*. On peut aussi choisir uniquement les *k* impairs, une fois que la division par 2 a échoué.

De la même manière, on peut exclure les *k* multiples de 3, de 5, etc. On construit ainsi le **crible d'Ératosthène**, qui consiste à tester la primalité de tous les nombres inférieur à une limite *N* donnée. On retire en premier tous les nombres pairs. 3 est ensuite le plus petit nombre qui n'a pas été retiré, c'est donc un nombre premier. On retire ensuite tous les multiples de 3, puis tous les multiples de 5, et ainsi de suite. Comme précédemment, on peut s'arrêter à la racine de *n*, tous les nombres supérieurs à √*n* qui n'ont pas été retirés sont des nombres premiers. Cependant, le crible d'd'Ératosthène et ses variantes donnent une réponse à la question de la primalité de *n* avec une complexité supérieure à la méthode naïve, puisqu'il faut construire le crible.

La complexité de la méthode naïve n'est pas de O(√*n*), même si on effectue moins de √*n* divisions, car elle est mesurée en **fonction de la taille de l'entrée** et non sa valeur[^2]. Dans le cas de PRIMES, la taille des entrées est donnée en binaire, donc pour un entier de taille *x*, l'ordre d'un grandeur de la valeur de *x* est O(2^*x*^). La méthode naïve a donc un ordre de grandeur de O(√2*^n^*), et n'est donc pas polynomial.

Pour rechercher des nombres premiers, il est possible d'avoir recourt à des tests de primalité **probabilistes** en utilisant des identités sur les nombres premiers. Chaque identité, si elle est vérifiée, tend à montrer que le nombre *n* testé est premier, avec une certaine probabilité. On dit alors que *n* est **pseudo-premier**. Lorsque *n* vérifie suffisamment de ces tests, il peut être déclarer premier avec une certaine marge de confiance. Un tel test est par exemple le test de primalité de Fermat, qui repose sur le petit théorème de Fermat : si *p* est un nombre premier alors pour tout 1 ⩽ *a* < *p*, *a^p-1^* ≡ 1 mod *p*, c'est-à-dire que *a^p-1^* est divisible par *p*. On peut donc essayer de calculer *a^p-1^* avec plusieurs valeurs de *a* tirées au hasard, si cela fonctionne à chaque fois, il est possible que *p* soit effectivement premier.

L'intérêt des tests probabilistes est qu'ils ont une complexité moins importante que des tests stricts. Ils sont donc notamment utilisés dans la cryptographie symétrique afin de trouver de (très) grands nombres premiers rapidement. En particulier l'algorithme de chiffrement RSA a besoin de tels nombres premiers, dont la sécurité repose notamment sur la complexité de décomposition en facteurs premiers. La décomposition en facteurs premiers est un problème différent de PRIMES, mais les tests de primalités sont utilisés lors de cette décomposition. Trouver un algorithme polynomial efficace pour PRIMES pourrait donc contribuer à casser l'algorithme de chiffrement RSA, qui est pourtant utilisés dans une grande partie des communications sur Internet, notamment dans des secteurs importants comme celui des banques.

L'algorithme de preuve de primalité AKS, du nom des mathématiciens M. Agrawal, N. Kayal et N. Saxena, permet de résoudre le problème PRIMES en Õ(n^12^), au minimum selon le système axiomatique. Ceci montre que PRIMES est dans P, puisque sa complexité temporelle est polynomiale. Cependant, AKS ne constitue pas une menace pour la robustesse du chiffrement asymétrique et la sécurité des communications sur Internet, puisqu'en pratique cet algorithme est beaucoup plus lent que les algorithmes de complexité exponentielle. L'algorithme AKS est plus rapide en théorie, mais cela ne s'applique qu'à des nombres premiers d'une grand extrême, bien plus grand que les nombres utilisés en cryptographie qui sont déjà très grands. La sécurité sur Internet ne sera donc pas remise en question par l'algorithme AKS et sa complexité polynomiale.

[^2]: [Computer Science Stack Exchange - Time Complexity of Basic Primality Test Algorithm](https://cs.stackexchange.com/questions/92624/time-complexity-of-basic-primality-test-algorithm)
[^3]: [Agrawal, M., Kayal, N., & Saxena, N. (2004). PRIMES is in P. *Annals of mathematics*, 781-793.](https://www.jstor.org/stable/3597229)

## Autres problèmes

Le tableau ci-dessous liste plusieurs problèmes de la théorie de la complexité :

| Catégorie           | Problème                                              | Complexité |
| :------------------ | ----------------------------------------------------- | :--------: |
| Divers              | Factorisation en nombres premiers                     |     NP     |
|                     | Optimisation linéaire                                 |     P      |
|                     | Primalité                                             |     P      |
|                     | Sac-à-dos                                             | NP-complet |
|                     | Satisfaisabilité                                      | NP-complet |
|                     | Restriction 2-SAT                                     |     P      |
|                     | Tri                                                   |     P      |
|                     |                                                       |            |
| Théorie des graphes | Arbre couvrant de poids minimal                       |     P      |
|                     | Coloration à k couleurs                               | NP-complet |
|                     | Connexité                                             |     P      |
|                     | Cycle hamiltonien (voyageur de commerce)              | NP-complet |
|                     | Nombre achromatique                                   | NP-complet |
|                     | Partition en cliques                                  | NP-complet |
|                     | Recherche de feuilles, de cycles ou de sommets isolés |     P      |
|                     | Recherche du plus court chemin                        |     P      |
|                     |                                                       |            |
| Jeux                | Démineur (Minesweeper)                                | NP-complet |
|                     | Go                                                    |    ⩾ NP    |
|                     | Lemmings                                              | NP-complet |
|                     | Mastermind                                            | NP-complet |
|                     | Sudoku                                                | NP-complet |
|                     | Taquin                                                |     NP     |
|                     | Tetris                                                | NP-complet |



Quelques compléments sur ce tableau :

* Le problème du **sac-à-dos** est un problème d'optimisation combinatoire, dans lequel sont à disposition plusieurs objets, de poids et de valeurs différentes. Le but est de choisir quels objets mettre dans un sac, en maximisant la valeur contenue dans le sac, sans dépasser le poids maximal que peut supporter le sac. Le problème du sac-à-dos est donc un problème d'optimisation, et peut être résolu grâce à la **recherche opérationnelle**. Sur ce problème, un **algorithme glouton** qui prendrait les objets dans l'ordre d'effectivité décroissante, c'est-à-dire de celui qui rapporte le plus par rapport à ce qu'il pèse à celui qui rapporte le moins, ne donne pas toujours la solution optimale.
    * *exemple* : soit quatre objets o~i~, de valeurs respectives 7, 4, 3, 3 et de poids respectifs 13, 12, 8, 10, et un sac de poids maximal 30 , alors les objets 1 et 3 maximisent la valeur du sac sans en dépasser le poids maximum.
* Le problème de **satisfaisabilité** booléenne, plus communément appelé **SAT**, consiste à déterminer s'il existe des valeurs de départ qui rendent une formule booléenne donnée *vraie*. Pour cela, on se place dans le corps des booléens, où les seules valeurs possibles sont *vrai* ou *faux*, et où les opérations sont *et* (noté ∧), *ou* (noté ∨) et *non* (noté ¬). SAT est NP-complet car n'importe quel problème NP peut être transformé en problème de satisfaisabilité en temps polynomial, pour cela il suffit de traduire le problème en une suite d'opérations booléennes.
    * *exemple* : *f* = (*p* ∨ *q*) ∧ (¬*p* ∨ *q*) ∧ (¬*p* ∨ ¬*q*) est satisfaisable car lorsque *p* est fausse et *q* vraie, alors *f* est vraie
    * SAT étant ainsi très large et générique, il en existe de nombreuses restrictions, notamment sur la nature des *formes normales conjonctives*. Une forme normale conjonctive est une expression booléenne composée de plusieurs expressions parenthésées avec uniquement des ∧ entre les expressions et uniquement des ∨ et des ¬ dans les parenthèses, comme l'exemple ci-dessus. On construit ainsi notamment la restriction 2-SAT, dans laquelle chaque expression parenthésée possède au plus deux variables, qui est dans la classe P. On peut remarquer notamment que NP-complet ∩ P ≠ ∅. La restriction 3-SAT est quant à elle dans la classe NP-complet.
* Les **algorithmes de tri** permettent d'organiser une collection d'objets selon une relation d'ordre, c'est-à-dire qu'on peut les comparer. Les meilleurs algorithmes ont une complexité temporelle en O(*n*.log(*n*)), soit quasiment linéaire, c'est le cas notamment du **tri rapide** (*quicksort*) et du **tri par tas** (*heapsort*). Un autre critère pour de tri est la **stabilité** d'un algorithme, c'est-à-dire sa capacité à conserver les éléments égaux dans l'ordre initial, ce qui peut être utile dans le cas d'une relation d'ordre qui ne prend en compte qu'un seul attribut des objets que l'on trie ; le **tri par insertion** (*insertion sort*) est un exemple d'algorithme stable. Lorsqu'un algorithme de tri a une complexité spatiale en O(1), c'est-à-dire qu'il utilise toujours autant de variables par rapport à la taille du tableau, on dit qu'il est **en place**, c'est le cas par exemple du **tri à bulles** (*bubble sort*), cela peut notamment être utile dans un environnement à mémoire réduite. Certains algorithmes ont une grande disparité entre le meilleur des cas (un ensemble de départ presque trié) et le pire des cas (une répartition au hasard). En pratique, il est possible d'associer un algorithme rapide et parallèle, c'est-à-dire qui peut être parallélisé, pour "presque trier" l'ensemble de départ, puis interrompre le tri et finir avec un algorithme plus efficace dans le meilleur des cas, par exemple en commençant par le **tri fusion** (*merge sort*) et en finissant avec le tri à bulles.
* La **théorie des graphes** est un champs des mathématiques qui s'intéresse à des objets . En *graphe* est défini comme un ensemble de sommets, au sens d'ensemble mathématique, et un ensemble d'arrête, c'est-à-dire un couple de deux sommets. Pour deux sommets appartenant, on dit qu'ils sont reliés si et seulement s'il existe une arrête entre eux. Dans le cas particuliers des graphes *orientés*, les arrêtes ont un sens, sinon par défaut elles n'en ont pas. On peut alors définir sur un graphe différentes propriétés. Par exemple, un graphe est dit **connexe** lorsqu'il existe une *chaîne* entre chaque paire de sommet de ce graphe, une chaîne étant une séquence d'arrêtes consécutives. Un **cycle hamiltonien** est une chaîne qui passe une et une seule fois par tous les sommets du graphe. Lorsque le graphe est muni d'une fonction poids qui attribue à chaque arrête une valeur, typiquement la distance correspondante, on peut chercher le cycle hamiltonien de poids minimal, ce qui correspond au problème du **voyageur de commerce**. Pour toutes ces propriétés et bien d'autres, il existe des algorithmes plus ou moins complexes. Il est également possible de rechercher dans un arbre des *feuilles*, des sommets qui n'ont qu'une seule arrête, des sommets isolés, sans arrête, ou des cycles. La **recherche du plus court chemin** peut aussi se définir dans le cadre d'un graphe muni d'un d'une fonction poids. 

## Théorie des jeux

La théorie des jeux est une sous-classe de la théorie de la décision, dont le but est de déterminer, dans un cadre rigoureusement défini, la meilleure décision possible. La théorie des jeux met en place un ou plusieurs *agents*, c'est-à-dire des participants ou des joueurs, mais elle est s'étend sur un domaine bien plus vaste que celui des jeux de stratégie, elle est notamment importante en économie. 

Sans rentrer dans les détails de ce champs des mathématiques, la théorie des jeux possède quelques notions faciles à appréhender. On parle d'un jeu à **somme nulle** lorsque la somme des gains est égale à la somme des pertes, c'est le cas notamment au poker ainsi que tous les jeux strictement compétitif pour lesquels, par exemple lorsqu'il y a un perdant et un gagnant sans mise préalable. Le *dilemme du prisonnier* est un exemple de jeux à somme non nulle. On distingue également les jeux **instantanés**, comme le pierre-feuille-ciseaux, des jeux **séquentiels**, puisque les joueurs décident chacun de leur stratégie en même temps, et ils ne peuvent pas prendre en considération la stratégie de l'autre. Un jeu peut cependant être **répété**, par plusieurs parties consécutives, ce qui peut influer sur la stratégie des joueurs y compris pour les jeux instantanés. Un jeu est dit **déterminé** ou résolu s'il existe une stratégie connue permettant d'arriver à la victoire à coup sûr, c'est le cas des jeux de Nim, dont le jeu des bâtonnets est le plus connu, ainsi que du morpion. Enfin, les jeux de **hasard** sont soumis à un élément aléatoire indépendant des stratégies des joueurs, tels qu'un mélange de cartes ou un jet de dés. 

Pour tous les jeux à deux joueurs séquentiels à somme nulle sans hasard, comme c'est le cas pour les jeux de plateau traditionnels, comme les échecs, les dames, les dames chinoises, le shōgi, Othello, ainsi que le morpion et le Puissance 4, un algorithme de décision basé sur la recherche exhaustive de tous les coups possibles peut permettre de trouver le meilleur coup à jouer à toute étape du jeu. Cet algorithme appelé **Minimax** vise à évaluer récursivement l'état du jeu après toutes les séquences de coups possibles. Pour cela, Minimax doit avoir recourt à une **fonction d'évaluation**. À noter que cet algorithme fonctionne aussi dans le cas des jeux à un joueur, tels que Tetris ou le casse-tête solitaire. Si le nombre de coups possibles à chaque tour est suffisamment limité, comme au morpion, il est possible de simuler le déroulement de la partie jusqu'à son terme, et utiliser la victoire, la défaite ou l'égalité comme valeurs d'évaluation. 

En revanche, lorsque ce n'est pas possible, comme aux échecs par exemple, il faut avoir recourt à une fonction d'évaluation basée sur l'état actuel des connaissances sur le jeu, en prenant par exemple le nombre de pièces restantes et leurs positions. Cependant, comme la profondeur de l'arbre de recherche reste déterminante pour proposer le meilleur coup à jouer, il existe de nombreuses optimisations possibles à Minimax pour accélérer la recherche. La première d'entre elles est l'**élagage *alpha-bêta*** (*alpha-beta pruning*) qui consiste à ne pas explorer certaines parties de l'arbre si celles-ci sont moins intéressantes que les parties déjà explorées, ce qui permet d'économiser l'évaluation de toutes les positions qui en découlent. Le principe repose sur le fait que chaque joueur cherche à optimiser son propre score, et si l'on sait à un moment donné que l'adversaire possède une meilleure alternative que celle qu'on est en train d'évaluer, alors on peut couper cette partie. 

Enfin, certains de ces jeux à deux joueurs nécessitent une stratégie qui s'étale sur l'ensemble de la partie et pour lesquels il est très difficile d'élaborer une fonction d'évaluation, comme c'est le cas pour le jeu de go, l'algorithme Minimax n'est très efficace, et il faut avoir recourt à des algorithmes d'intelligence artificielle pour avoir des résultats satisfaisants, comme c'est le cas pour AlphaGo développé par DeepMind, utilisant notamment l'apprentissage par renforcement.


## Recherche opérationnelle

Par opposition à la théorie de la complexité, il s'agit ici de s'attaquer à des problèmes d'**optimisation** et non de décision. 
