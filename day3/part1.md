# --- Jour 3 : Diagnostic Binaire ---

Le sous-marin fait de drôles de bruits de craquements, alors vous lui demandez de vous faire un rapport de diagnostic, juste au cas où.

Le rapport de diagnostic (l'entrée de votre puzzle) consiste en une liste de nombres binaires qui, une fois décodés de la bonne manière, peuvent vous indiquer beaucoup de choses utiles à propos de la condition du sous-marin. Le premier paramètre à vérifier est la *consommation énergétique*.

Vous aurez besoin d'utiliser les nombres binaires du rapport de diagnostic pour générer deux nouveaux nombres binaires (appelé *l'indice gamma* et *l'indice epsilon*). La consommation énergétique peut être trouvée en multipliant l'indice gamma par l'indice epsilon.

Chaque bit de l'indice gamma peut être déterminé en trouvant le *bit le plus commun à la position correspondante* de tous les nombres du rapport de diagnostic. Par exemple, étant donné le rapport de diagnostic suivant :

```bin
00100
11110
10110
10111
10101
01111
00111
11100
10000
11001
00010
01010
```

En considérant uniquement le premier bit de chaque nombre, il y a cinq bits valant `0` et sept bits valant `1`, le premier bit de l'indice gamma est donc `1`.

Le deuxième bit le plus commun du rapport de diagnostic est `0`, donc le deuxième bit de l'indice gamma est `0`.

Les valeurs les plus courantes des troisième, quatrième et cinquième bits sont `1`, `1` et `0` respectivement, ainsi les trois bits finaux de l'indice gamma sont `110`.

Ainsi, l'indice gamma est le nombre binaire `10110`, ou *`22`* en décimal.

L'échelle epsilon est calculée d'une façon similaire ; mais plutôt qu'en utilisant la valeur la plus commune, la valeur la moins commune est utilisée. En conséquence, la valeur de l'échelle epsilon est `01001`, soit *`9`* en décimal. Multiplier l'indice gamma (`22`) par l'indice epsilon (`9`) donne la consommation énergétique, *`198`*.

Utilisez les nombres binaires de votre rapport de diagnostic pour calculer les indices gamma et epsilon, puis multipliez-les ensemble. *Quelle est la consommation énergétique du sous-marin ?* Assurez-vous de représenter votre réponse en décimal, et non en binaire.
