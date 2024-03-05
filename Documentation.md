Paul Baudinot, Romain Romain Pereira

<h1> <center> Documentation du projet </center></h1>

## Adaptation du notebook
Pour ce projet nous avons dû adapter le code afin que celui-ci fonctionne pour plusieurs modèles de classification différents. Nous avons donc choisi de créer un notebook par modèle afin d'éviter tout conflit entre les différents modèles.

## Algorithme Kmeans
Le premier modèle que nous avons implémenté est basé sur l'algorithme des K-means.
L'algorithme des K-means est un algorithme d'apprentissage non supervisé. Pour cet algorithme on choisit un nombre de centroïde équivalent au nombre de personnes présentes dans le dataset. Ensuite l'algorithme va clusteriser les points autour des centroïdes. 
Pour de la reconnaissance faciale cet algorithme n'est pas idéal, en effet celui-ci reconnaît bien les visages mais comme il est non supervisé, le modèle est incapable d'associer un nom au visage et renvoie seulement l'id du cluster.

## Algorithme de régression logistique
Nous avons ensuite implémenté l'algorithme de régression logistique. 
La régression logistique est un algorithme d'entraînement supervisé, il parviendra donc à associer des noms aux visages. 
Idéalement la régression logistique est utilisée pour faire de la classification binaire, mais peut tout de même être employée pour faire de la classification multiple. 
Nous avons donc décidé de tester cela. En effet dans son fonctionnement, la régression logistique ressemble à celui d'un perceptron, le modèle va calculer pour chaque entrée une combinaison linéaire pondérée par des poids. 
Ces combinaisons sont ensuite passées par une fonction sigmoïde afin d'avoir un pourcentage d'appartenance à une classe. Pour nos tests l'algorithme fonctionne très bien avec 3 à 4 personnes. Nous n'avons cependant pas testé avec plus de personnes.

## Algorithme d'arbre de décision
Ici nous avons implémenté le modèle qui selon nous devrait le mieux fonctionner pour une tâche de reconnaissance faciale multiple.
L'algorithme d'arbre de décision est basé sur les algorithmes diviser pour régner. 
On commence par le nœud racine qui contient l'ensemble du dataset. 
L'algorithme va ensuite de manière récursive, diviser en branches les éléments jusqu'au point d'arrêt. 
L'algorithme peut donc créer autant de branches que de personnes présentes dans le dataset, c'est donc en toute logique un très bon algorithme pour la reconnaissance faciale.

## Algorithme admis non admis
Pour cet algorithme nous avons décidé de garder l'algorithme des K plus proches voisins qui est un algorithme d'apprentissage supervisé. 
Nous avons ensuite ajouté une liste contenant l'ensemble des noms des personnes admises. Lorsque notre modèle détecte un visage il associe un nom à ce visage, si ce visage est dans la liste des personnes admises alors on ajoute à côté du nom que la personne est admise. 
Dans le cas contraire la personne est indiquée comme non admise.

## Algorithme réseau de neurones
Tout comme l'arbre de décision, les réseaux de neurones sont des algorithmes d'apprentissage parfaits pour la classification multiple. 
Cet algorithme est construit en plusieurs couches de perceptron. Chaque perceptron prend en entrée l'ensemble du dataset, les couches suivantes prennent en entrée l'ensemble des sorties de la couche précédente et ceux jusqu'à la couche finale. 
Pour cet algorithme nous avons réalisé plusieurs tests au niveau des couches. 
Avant de les présenter, pour comprendre la logique des tests il est important de savoir que pour que le modèle fonctionne correctement il est nécessaire que la dernière couche contienne au moins le même nombre de perceptrons que de personnes présentes dans le dataset. 
Nous avons d'abord testé un réseau de neurones d'une seule couche de 100 neurones. Ce qui fonctionnait. Pour essayer d'optimiser et d'exploiter pleinement les réseaux de neurones nous avons par la suite tenté un modèle prenant 100 neurones en première couche et 20 neurones pour la deuxième et dernière couches. Cela nous laissait une marge de test de 20 personnes dans le dataset ce qui a assez bien fonctionné.

## Algorithme réseau de neurones convolutionnels (CNN)
Le CNN est un réseau de neurones spécialisé dans la vision par ordinateur, donc idéal pour un projet comme celui-ci. 
La principale différence entre un réseau de neurones classique et un CNN est que dans un classique chaque neurone est connecté avec l'ensemble des neurones de la couche précédente ainsi que des neurones de la couche suivante tandis que dans un CNN chaque connexion entre neurones est locale et partagée. 
De plus dans un CNN les neurones partagés possèdent tous le même poids de filtre afin de limiter le nombre de paramètres. Cela permet d'avoir des couches spécialisées dans l'analyse d'une particularité.


