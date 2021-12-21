# --- Jour 21 : Dé de Dirac ---

Il n'y a pas grand chose à faire pendant que vous descendez lentement vers le fond de l'océan. L'ordinateur du sous-marin vous défie à une partie de *Dé de Dirac*.

Le jeu consiste en un seul [dé](https://fr.wikipedia.org/wiki/D%C3%A9), deux [pions](https://fr.wikipedia.org/wiki/Pion#Jeux) et un plateau de jeu possédant une piste circulaire de dix emplacements marqués de `1` à `10` dans le sens horaire. L'*emplacement de départ* de chacun des joueurs est tiré au hasard (l'entrée de votre puzzle). Le joueur 1 commence.

Les joueurs se déplacent chacun leur tour. Pendant le tour d'un joueur, celui-ci lance le un dé *trois fois de suite* et additionne les résultats ensemble. Ensuite, le joueur bouge son pion autant de fois qu'indiqué par la somme des résultats du dé *vers l'avant* sur la piste (c'est-à-dire en suivant le sens horaire sur les emplacements dans l'ordre croissant, retournant à `1` après `10`). Donc, si un joueur est sur l'emplacement `7` et tire `2`, `2` et `1` au dé, il avancerait 5 fois, passant par les emplacements `8`, `9`, `10`, `1`  et s'arrêtant finalement sur `2`.

Après le mouvement d'un joueur, le *score* de ce joueur est augmenté par la valeur de la case sur laquelle son pion s'est arrêté. Les scores des joueurs commencent à `0`. Ainsi, si le premier joueur démarre sur l'emplacement `7` et fait un total de `5` au dé s'arrêtant donc sur la case `2`, il ajoute `2` à son score (pour un score total de `2`). Le jeu s'arrête immédiatement comme une victoire pour le premier joueur qui atteint *au moins `1000`*.

Puisque la première partie est une partie d'entraînement, le sous-marin ouvre un compartiment étiqueté *dé déterministe* duquel un dé à 100 faces tombe. ce dé donne toujours `1` d'abord, puis `2`, puis `3`, et ainsi de suite jusqu'à `100`, après quoi il recommence à `1`. Jouez en l'utilisant.

Par exemple, étant données ces positions de départ :

```startPositions
Player 1 starting position: 4
Player 2 starting position: 8
```

Voici comment se passerait la partie :

- Le joueur 1 obtient `1`+`2`+`3` au dé et avance à l'emplacement `10` pour un score total de`10`.
- Le joueur 2 obtient `4`+`5`+`6` au dé et avance à l'emplacement `3` pour un score total de`3`.
- Le joueur 1 obtient `7`+`8`+`9` au dé et avance à l'emplacement `4` pour un score total de`14`.
- Le joueur 2 obtient `10`+`11`+`12` au dé et avance à l'emplacement `6` pour un score total de `9`.
- Le joueur 1 obtient `13`+`14`+`15` au dé et avance à l'emplacement `6` pour un score total de `20`.
- Le joueur 2 obtient `16`+`17`+`18` au dé et avance à l'emplacement `7` pour un score total de `16`.
- Le joueur 1 obtient `19`+`20`+`21` au dé et avance à l'emplacement `6` pour un score total de `26`.
- Le joueur 2 obtient `22`+`23`+`24` au dé et avance à l'emplacement `6` pour un score total de `22`.

... Puis après de nombreux de tours...

- Le joueur 2 obtient `82`+`83`+`84` et avance à l'emplacement `6` pour un score total de `742`.
- Le joueur 1 obtient `85`+`86`+`87` et avance à l'emplacement `4` pour un score total de `990`.
- Le joueur 2 obtient `88`+`89`+`90` et avance à l'emplacement `3` pour un score total de `745`.
- Le joueur 1 obtient `91`+`92`+`93` et avance à l'emplacement `10` pour un score total de `1000`.

Puisque le joueur 1 a au moins `1000` points, le joueur 1 gagne et la partie se termine. À ce moment là, le joueur perdant avait `745` points et le dé à été lancé un total de `993` fois ; <code>745 * 993 = <em>739785</em></code>.

Jouez la partie d'entraînement avec le dé déterministe à 100 faces. Au moment où l'un des joueurs gagne, *qu'obtenez-vous si vous multipliez le score du joueur perdant par le nombre de fois où le dé à été lancé durant la partie ?*
