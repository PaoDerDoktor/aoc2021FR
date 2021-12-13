# --- Jour 13 : Origami Transparent ---

Vous atteignez une nouvelle région volcaniquement active des grottes. Ce serait bien si vous pouviez récupérer une sorte d'image thermique afin que vous puissiez connaître au préalable quelles grottes seront trop chaudes pour votre sous-marin.

Heureusement, le sous-marin semble être équipé d'une caméra thermique ! Quand vous l'activez, vous êtes accueilli par ce message :

```log
Félicitations pour votre achat ! Afin d'activer ce système d'imagerie par caméra infrarouge, entrez le code figurant sur la page 1 de votre manuel.
```

Apparemment, les elfes n'ont jamais utilisé cette fonctionnalité. À votre grande surprise, vous parvenez à trouver le manuel. Alors que vous alliez l'ouvrir, la page 1 tombe : c'est un grand [transparent](https://fr.wikipedia.org/wiki/Transparent_(projection)) ! Le transparent est marqué de plusieurs points et inclus des instructions sur comment le plier (l'entrée de votre puzzle). Par exemple :

```transparent
6,10
0,14
9,10
0,3
10,4
4,11
6,0
6,12
4,1
0,13
10,12
3,4
3,0
8,4
1,10
2,14
8,10
9,0

fold along y=7
fold along x=5
```

La première section est une liste de points sur le papier transparent. ``0,0`` représente le coin supérieur-gauche. La première valeur, `x`, augmente vers la droite. La seconde valeur, `y`, augmente vers le bas. Ainsi. les coordonnées ``3,0`` sont à droite de ``0,0`` et les coordonnées ``0,7`` sont en-dessous de ``0,0``. Les coordonnées dans cette exemple forment le schéma suivant, où `#` est un point sur le transparent et `.` est une position vide, non-marquée :

```dots
...#..#..#.
....#......
...........
#..........
...#....#.#
...........
...........
...........
...........
...........
.#....#.##.
....#......
......#...#
#..........
#.#........
```

Ensuite se trouve une série d'*instructions de pliage*. Chaque instruction indique une ligne sur le transparent et dit s'il faut le plier vers le *haut* (pour les lignes horizontales ``y=...``) où vers la *gauche* (pour les lignes verticales ``x=...``). Dans cet exemple, la première instruction de pliage est ``fold along y=7``, ce qui désigne la ligne formée par toutes les positions où `y` vaut `7` (marquées ici d'un `-`) :

```dots
...#..#..#.
....#......
...........
#..........
...#....#.#
...........
...........
-----------
...........
...........
.#....#.##.
....#......
......#...#
#..........
#.#........
```

Puisque c'est une ligne horizontale, pliez le transparent à sa moitié *vers le haut*. Certains des points peuvent finir par se superposer une fois le papier plié, mais aucun point n'apparaîtra jamais sur une ligne de pliage. Le résultat de ce pliage donne ceci :

```dots
#.##..#..#.
#...#......
......#...#
#...#......
.#.#..#.###
...........
...........
```

Il y a maintenant seulement `17` points visibles.

Remarquez, par exemple, les deux points dans le coin inférieur-gauche avant que le transparent ne soit plié. Une fois le pliage terminé, ces points apparaissent dans le coin supérieur-gauche (à ``0,0`` et ``0,1``). Comme le papier est transparent, le point juste en-dessous d'eux (à ``0,3``) reste visible, vu qu'il peut être aperçu à travers le transparent lui-même.

Remarquez aussi que certains points finissent par *se superposer* ; dans ce cas, les points fusionnent et deviennent un seul point.

La deuxième instruction de pliage est ``fold around x=5``, ce qui indique la ligne suivante :

```dots
#.##.|#..#.
#...#|.....
.....|#...#
#...#|.....
.#.#.|#.###
.....|.....
.....|.....
```

Puisque c'est une ligne verticale, pliez *vers la gauche* :

```dots
#####
#...#
#...#
#...#
#####
.....
.....
```

Ces instructions ont formé un carré !

Le transparent est plutôt grand, donc contentez-vous pour l'instant de faire la premier pliage. Après le premier pliage, dans l'exemple ci-dessus, *`17`* points sont visibles - les points finissant par se superposer après le premier pliage comptent comme un seul point.

*Combien de points sont visibles après n'avoir terminé que le premier pliage de votre transparent ?*
