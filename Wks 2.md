Considérons le problème Voyageur De Commerce :
Voyageur De Commerce 
Données : Un graphe complet G arêtes-valué, et un entier k.
Question : Existe-t-il un circuit passant au moins une fois par chaque sommet de G et dont la somme des valeurs des arêtes est au plus k ?
Montrer que Voyageur de Commerce est NP-complet.



Le problème est dans NP car étant donné une suite de sommets, on peut vérifier en temps polynomial (plus précisément en temps linéaire) si c’est un circuit, s’il passe au moins une fois par chaque sommet, et si son coût est inférieur à k.

Nous allons faire la réduction à partir du problème Cycle Hamiltonien. Le but est de démontrer que, si on était capable de résoudre Voyageur de Commerce en temps polynomial, on pourrait aussi utiliser l'algorithme pour résoudre Cycle Hamiltonien. Or, comme celui-ci est NP-Complet, on en déduit que Voyageur de Commerce est NP-Difficile (et puisqu'il appartient à NP, il est NP-Complet). Pour cela, il faut trouver un moyen de transformer, en temps polynomial, une instance de Cycle Hamiltonien en instance de Voyageur de Commerce, de manière à ce que les deux instances admettent la même réponse.

Voyageur de Commerce considère un graphe complet arête-valué, mais qu'il autorise à passer plusieurs fois par certains sommets, du moment que le circuit total est de taille inférieure à k (on considère le problème de décision sur lequel est basé le problème d'optimisation, k est donc un paramètre d'entrée). L'idée générale de cette réduction polynomiale est de construire l’instance de Cycle Hamiltonien en rajoutant les arêtes manquantes, mais avec une valeur de 2 (et en considérant une valeur de 1 pour les arêtes déjà présentes) de manière à rendre leur usage trop couteux, et en considérant un k correspondant au nombre de sommets (on notera que cette transformation se fait en temps polynomial). De cette manière, si la réponse à l'instance de Voyageur de Commerce est oui, on sait que le circuit auquel correspond cette réponse passe une et une seule fois par les sommets du graphe, et n'emprunte que les arêtes du graphe de Cycle Hamiltonien. Tout cycle empruntant une des arêtes manquantes dans Cycle Hamiltonien aurait une taille supérieure à k, puisque les autres arêtes qu'on a ajoutées ont une taille supérieure à 1. Idem pour les cycles passant plusieurs fois par un sommet. Donc la réponse pour l'instance de Cycle Hamiltonien est oui aussi. Idem si la réponse est non. Puisqu'on est capable de transformer en temps polynomial une instance de Cycle Hamiltonien en instance de Voyageur de Commerce, de manière à conserver la réponse, Voyageur de Commerce est au moins aussi difficile que Cycle Hamiltonien. Comme Cycle Hamiltonien est NP-Complet, et que Voyageur de Commerce est dans NP, Voyageur de Commerce est NP-Complet.
 
Plus formellement :
Le problème est dans NP car étant donné une suite de sommets, on peut vérifier en temps en temps linéaire :
	si cette suite de sommets constitue bien un circuit : il faut vérifier qu’elle parcourt bien les sommets de proche en proche (chaque sommet est le voisin du précédent). Cette vérification se fait en temps linéaire.
	si elle passe au moins une fois par chaque sommet. Cette vérification se fait en temps linéaire.
	si son coût est inférieur à k : il faut faire la somme des valeurs des arêtes parcourues par le circuit, et vérifier si cette somme est inférieure à k. Cette vérification se fait en temps linéaire.

Soit ICH une instance du problème Cycle Hamiltonien, constitué du graphe G=(V,E).
Soit IVdC l’instance de Voyageur de Commerce définie par :
	le graphe arête-valué G ’=(V, E(G)+E(G ̅), v : E(G )+E(G ̅) ↦ ℕ) avec v(u)=1 ∀ u ∈ E(G ) et v(u)=2 ∀ u ∈ E(G ̅) (Rappel : G ̅ est le complémentaire de G, il contient les mêmes sommets, et toutes les arêtes qui ne sont pas dans G ).
	l’entier k=|V |-1
Cette instance se construit en temps polynomial : Rechercher toutes les combinaisons de sommets (origine, destination) non présentes dans G se fait en O(|V |²)
Supposons qu’il existe un algorithme résolvant Voyageur de Commerce en temps polynomial. En appliquant cet algorithme sur IVdC :
	Soit on obtient la réponse oui. Dans ce cas, on sait qu’il existe un cycle hamiltonien dans G. En effet, la solution de IVdC est un circuit de longueur |V |-1 par construction de IVdC. Ce circuit ne peut passer que par des arêtes de G, puisque celles de G ̅ ont un cout de 2, la longueur de cette solution serait supérieure à |V |-1. Par ailleurs, cette solution ne passe qu’une seule fois par chaque sommet, car sinon sa longueur serait supérieure à |V |-1. Ce circuit constitue donc un cycle hamiltonien dans G, la réponse à ICH est donc oui.
	Symétriquement, si la réponse est non, on en déduit qu’il n’existe pas de cycle hamiltonien dans G, car sinon il constituerait une solution à IVdC et la réponse serait oui.

Cycle hamiltonien ⩽ Voyageur de Commerce. Dans la mesure ou Cycle Hamiltonien est dans NP, le problème est NP-Complet.