# --- Jour 23 : Amphipode ---

Un groupe d'[amphipodes](https://fr.wikipedia.org/wiki/Amphipoda) remarque votre superbe sous-marin et vos font signe. "avec une coquille si impressionnante", dit l'un d'eux, "vous pouvez sûrement nous aider sur une question qui fait s'arracher la carapace à nos plus grands scientifiques".

Ils vous expliquent ensuite qu'un groupe d'amphipodes timides et têtus vivent dans une tanière proche. Quatre types d'amphipodes vivent là-bas : *Ambrés* (`A`), *Bronze* (`B`), *Cuivre* (`C`) et *Désert* (`D`). Ils vivent dans une tanière consistant en un *couloir* et quatre *pièces latérales*. Initialement, ces pièces latérales sont pleines d'amphipodes, et le couloir est vide.

Ils vous donnent un *diagramme de la situation* (l'entrée de votre puzzle), incluant les emplacements de chaque amphipode (`A`, `B`, `C` et `D`, chacun occupant un espace qui s'ils n'étaient pas là serait vide), des murs (`#`) et des espaces vides (`.`).

Par exemple :

```amphiDia
#############
#...........#
###B#C#B#D###
  #A#D#C#A#
  #########
```

Les amphipodes voudraient une méthode pour organiser chaque amphipode dans une pièce latérale pour que chaque pièce latérale contienne un type d'amphipode et que les types soient rangés de `A` à `D` de gauche à droite, comme ceci :

```amphiDia
#############
#...........#
###A#B#C#D###
  #A#B#C#D#
  #########
```

Les amphipodes peuvent se déplacer en haut, en bas, à gauche, à droite tant qu'ils bougent vers un espace inoccupé. Chaque type d'amphipode requiert un taux d'énergie différent pour bouger d'un emplacement : `1` unité pour les Ambrés, `10` pour les Bronze, `100` pour les Cuivre et `10000` pour les déserts. Les amphipodes voudraient trouver un moyen d'organiser les amphipodes avec *le moins d'énergie possible*.

Cependant, puisqu'ils sont timides et têtus, les amphipodes ont des règles supplémentaires :

- Les amphipodes ne *s'arrêteront jamais dans l'espace directement au-dessus d'une pièce*. Ils peuvent se déplacer dans ces espaces tant qu'ils continuent immédiatement à se déplacer (pour être exact, ceci fait référence aux quatre espaces dans le couloir qui sont exactement au-dessus des amphipodes à leur positions de départ).
- Les amphipodes ne *se déplaceront jamais depuis le couloir vers une pièce* à moins que celle-ci ne soit leur pièce de destination *et* que cette pièce ne contiennent pas d'amphipode qui n'ont pas cette pièce comme leur pièce de destination. Si un amphipode ne démarre pas dans sa pièce de destination, il peut rester dans cette pièce jusqu'à ce qu'il la quitte (par exemple, un amphipode Ambré ne se déplacera pas depuis le couloir vers une des trois pièces de droite, et ne se déplacera dans la pièce la plus à gauche que si elle est vide ou qu'elle ne contient que d'autres amphipodes ambrés).
- Une fois qu'un amphipode s'est arrête dans le couloir, *il reste à son emplacement jusqu'à ce qu'il puisse se déplacer vers une pièce* (c'est-à-dire qu'une fois qu'un amphipode commence à se déplace, tous les autres amphipodes situés dans le couloir à ce moment-là sont bloqués et ne se déplaceront plus pour autre chose que se ranger dans leur pièce.)

Dans l'exemple ci-dessus, les amphipodes peuvent être organisés en un minimum de *`12521`* unités d'énergie. Une façon de faire est montrée ci-dessous.

Configuration de départ :

```amphiDia
#############
#...........#
###B#C#B#D###
  #A#D#C#A#
  #########
```

Un amphipode Bronze se déplace vers le couloir, faisant 4 pas et utilisant `40` unités d'énergie :

```amphiDia
#############
#...B.......#
###B#C#.#D###
  #A#D#C#A#
  #########
```

Le seul amphipode Cuivre qui n'est pas dans sa chambre latérale se déplace vers celle-ci, faisant 4 pas et utilisant `400` unités d'énergie :

```amphiDia
#############
#...B.......#
###B#.#C#D###
  #A#D#C#A#
  #########
```

Un amphipode Désert se déplace, faisant 3 pas et utilisant `3000` unités d'énergie, puis l'amphipode Bronze prends sa place, faisant 3 pas et utilisant `30` unités d'énergie :

```amphiDia
#############
#.....D.....#
###B#.#C#D###
  #A#B#C#A#
  #########
```

L'amphipode Bronze le plus à gauche se déplace dans sa chambre en utilisant `40` unités d'énergie :

```amphiDia
#############
#.....D.....#
###.#B#C#D###
  #A#B#C#A#
  #########
```

Les deux amphipodes dans la pièce la plus à droite se déplacent vers le couloir, utilisant `2003` unités d'énergie au total :

```amphiDia
#############
#.....D.D.A.#
###.#B#C#.###
  #A#B#C#.#
  #########
```

Les deux amphipodes Désert se déplacent dans la pièce la plus à droite en utilisant `7000` unités d'énergie :

```amphiDia
#############
#.........A.#
###.#B#C#D###
  #A#B#C#D#
  #########
```

Enfin, le dernier amphipode Ambré se déplace dans sa pièce en utilisant `8` unités d'énergie :

```amphiDia
#############
#...........#
###A#B#C#D###
  #A#B#C#D#
  #########
```

*Quelle est l'énergie minimale requise pour organiser les amphipodes ?*
