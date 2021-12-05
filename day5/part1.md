# --- Jour 5 : Aventure Hydrothermale ---

Vous tombez sur un champs de [https://fr.wikipedia.org/wiki/Mont_hydrothermal](cheminées hydrothermales) sur le plancher océanique ! Ces cheminées produisent de gros nuages opaques, il serait donc mieux de les éviter si possible.

Ils ont tendance à former des *lignes* ; le sous-marin peut heureusement produire une liste des cheminées alentours (l'entrée de votre puzzle) que vous pouvez inspecter. Par exemple :

```lines
0,9 -> 5,9
8,0 -> 0,8
9,4 -> 3,4
2,2 -> 2,1
7,0 -> 7,4
6,4 -> 2,0
0,9 -> 2,9
3,4 -> 1,4
0,0 -> 8,8
5,5 -> 8,2
```

Chaque ligne de cheminée est donnée en tant que segment sous le format ``x1, y1 -> x2, y2`` où ``x1, y1`` sont les coordonnées de l'un des bouts du segment et ``x2, y2`` sont les coordonnées de l'autre bout. Ces segments incluent les points formant les bouts. En d'autres mots :

- Une entrée ``1,1 -> 1,3`` couvre les points ``1,1``, ``1,2`` et ``1,3``.
- Une entrée ``9,7 -> 7,7`` couvre les points ``9,7``, ``8,7`` et ``7,7``.

Pour le moment, *ne prenez en compte que les lignes horizontales et verticales* : les lignes où l'on retrouve ``x1 = x2`` ou ``y1 = y2``.

Ainsi, les lignes horizontales et verticales de la liste ci-dessus formeraient le diagramme suivant :

```countArray
.......1..
..1....1..
..1....1..
.......1..
.112111211
..........
..........
..........
..........
222111....
```

Dans ce diagramme, le coin en haut à gauche est ``0,0`` et le coin en bas à droite est ``9,9``. Chaque position contient *le nombre de lignes passant par ce point*, ou le signe `.` s'il n'y en a aucune. La paire de `1` en haut à gauche, par exemple, résulte de ``2,2 -> 2,1`` ; la ligne toute en bas est formée par les lignes se chevauchant ``0,9 -> 5,9`` et ``0,9 -> 2,9``.

Pour éviter les zones les plus dangereuses, vous devrez déterminer le *nombre de points où au moins deux lignes se chevauchent*. Dans l'exemple ci-dessus, il ss'agit de n'importe quel emplacement du diagramme où est écrit `2` ou plus - un total de *`5`* points.

Ne considérez que les lignes horizontales et verticales. *À combien de points au moins deux lignes se chevauchent-elles ?*
