La problématique que nous rencontrons peut se réduire au problème du voyageur de commerce.

Or, avant de chercher à réaliser un algorithme de résolution, nous allons tout d'abord nous demander à quelle classe de complexité appartient ce problème. En effet, il est essentiel de déterminer la complexité d'un tel algorithme afin de savoir si nous pourrons réaliser le calcul de l'itinéraire dans un temps raisonnable. 

En particulier, l'enjeu va être de réaliser un algorithme "simple" de complexité polynomiale. Pour répondre à cette question, nous allons nous demander si le problème du voyageur du commerce est un problème P ou NP-complet. 

Pour qu'un algorithme soit de complexité P, il faut que 2 conditions soient remplises : 
- le calcul de la solution soit être réalisé avec un algorithme de complexité polynomiale
- la vérification du résultat doit également être réalisable en temps polynomial

A l'inverse pour qu'un problème soit catégorisé NP-difficile, il est nécessaire que :
- la vérification du résultat doit être réalisable en temps polynomial
- il est possible, par le biais d'une opération de réduction polynomiale, de se ramener à un problème connu comme étant NP-difficile

Dans notre cas de figure, on remarque aisément que la vérification d'une solution peut être opérée par un algorithme de complexité polynomial. En effet, il nous suffit de vérifier qu'aucune ville (hormis la ville de départ) n'apparait plusieurs fois dans la liste des villes traversées par le voyageur. On peut rapidement se convaincre que pour réaliser cette vérification, nous n'avons besoin que d'un algorithme de complexité linéaire.

Notre problème appartient donc à la classe NP, cependant nous ne savons toujours pas dans quel cas nous nous trouvons. 

Par un raisonnement naïf, on se rend compte qu'il est nécessaire de recourir à un algorithme de complexité factorielle si l'on veut tester toutes les possibilités en "brute force". Ceci nous oriente plutôt vers un problème difficile à résoudre.

De plus, on peut noter que le problème du voyageur du commerce ressemble fortement à un problème connu comme étant un problème difficile : le problème du cycle hamiltonien. Il va donc falloir que nous démontrions que le cycle hamiltomien est équivalent à celui du voyageur du commerce modulo une réduction polynomiale. De cette manière, nous montrerions que le problème du voyageur du commerce est NP-complet et qu'il faudra orienter nos recherches vers des approximations du problème initial. 

Cette démonstration est aisée puisque l'on se rend compte que si l'on ajoute une valeur unitaire de 1 à chacune des arêtes d'un cycle hamiltonien, nous retombons sur notre problème. Cette réduction peut tout à fait être réalisée avec un algorithme polynomial.

On peut donc en conclure que nous avons affaire à un algorithme NP-complet et qu'il va falloir envisager des alternatives pour parvenir à répondre à notre problématique.