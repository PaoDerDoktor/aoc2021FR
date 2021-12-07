# --- Jour 7 : La Trahison des Cachalots ---

Un [cachalot](https://fr.wikipedia.org/wiki/Grand_cachalot) géant a décidé de faire du sous-marin son prochain repas, et il est beaucoup plus rapide que vous. Il n'y a aucune issue !

Soudain, une nuée de crabes (chacun dans son propre petit sous-marin - sinon il serait trop profond pour eux) descends en piqué pour vous sauver ! Ils ont l'air de se préparer à créer un trou dans le plancher océanique ; vos senseurs vous indiquent un *énorme réseau de grottes souterraines* pile en-dessous de leur cible !

Les sous-marins crabes ont besoin d'être tous alignés pour avoir assez de puissance pour faire un trou assez gros pour votre sous-marin. Malheureusement, il semble qu'ils ne seront jamais alignés avant que le cachalot ne vous rattrape ! Peut-être que vous pouvez les aider ?

Par contre, il y a un gros souci : les sous-marins crabes ne peuvent bouger qu'horizontalement.

Vous établissez rapidement la liste des *positions horizontales de chaque crabe* (l'entrée de votre puzzle). Les sous-marins crabes ont des réserves de carburant limitées, vous devez donc trouver un moyen de faire correspondre leurs position horizontales tout en leur faisant dépenser le moins de carburant possible.

Par exemple, considérez les positions horizontales suivantes :

```intcode
16,1,2,0,4,2,7,1,2,14
```

Ceci veut dire qu'il y a un crabe avec une position de `16`, un crabe avec une position de `1`, et ainsi de suite.

Chaque changement de 1 unité de position horizontale coûte une unité de carburant. Vous pourriez prendre n'importe quelle position pour les aligner, mais celle minimisant le coût en carburant est la position horizontale `2` :

- Mouvement de `16` à `2` : `14` unités de carburant
- Mouvement de `1` à `2` : `1` unités de carburant
- Mouvement de `2` à `2` : `0` unités de carburant
- Mouvement de `0` à `2` : `2` unités de carburant
- Mouvement de `4` à `2` : `2` unités de carburant
- Mouvement de `2` à `2` : `0` unités de carburant
- Mouvement de `7` à `2` : `5` unités de carburant
- Mouvement de `1` à `2` : `1` unités de carburant
- Mouvement de `2` à `2` : `0` unités de carburant
- Mouvement de `14` à `2` : `12` unités de carburant

Tout ceci coûte un total de *`37`* unités de carburant. Il s'agit du résultat le moins coûteux, mais des résultats plus chers existent, comme l'alignement sur la position `1` (`41` unités de carburant), la position `3` (`39` unités de carburant) ou la position `10` (`71` unités de carburant).

Déterminez la position horizontale sur laquelle les crabes peuvent s'aligner en utilisant le moins de carburant possible. *Combien d'unités de carburant doivent-ils utiliser pour s'aligner sur cette position ?*
