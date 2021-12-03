# --- Partie Deux ---

Selon vos calculs, le chemin programmé a l'air de n'avoir aucun sens. Vous trouvez le manuel du sous-marin et découvrez que le processus est en fait un tout petit peu plus compliqué.

En plus de la position horizontale et de la profondeur, vous aurez aussi besoin de vérifier une troisième valeur, la *cible*, qui commence également à `0`. De plus, les commandes ont en réalité des significations un peu différentes de ce que vous aviez pensé :

- ``down X`` *augmente* votre cible de `X` unités.
- ``up X`` *diminue* votre cible de `X` unités.
- ``forward X`` fait deux choses :
  - Elle augmente votre position horizontale de `X` unités.
  - Elle augmente votre profondeur par votre cible *multipliée par* `X`.

Notez à nouveau que puisque vous êtes dans un sous-marin, `down` et `up` font l'opposé de ce que vous pourriez penser à première vue : "down" signifie en fait cibler vers une direction positive (puisqu'on mesure la profondeur).

À présent, l'exemple du dessus fait quelque chose de différent :

- ``forward 5`` ajoute `5` à votre position horizontale, pour un total de `5`. Puisque votre cible est de `0`, la profondeur ne change pas.
- ``down 5`` ajoute `5` à votre cible, pour un total de `5`.
- `forward 8` ajoute `8` à votre position horizontale, pour un total de `13`. Puisque votre cible est de `5`, votre profondeur augmente de ``8*5=40``.
- ``up 3`` ajoute `3` à votre cible, pour un total de `2`.
- ``down 8`` ajoute `8` à votre cible, pour un total de `10`.
- ``forward 2`` ajoute `2` à votre position horizontale, pour un total de `15`. Puisque votre cible est de `10`, votre profondeur augmente de ``2*10=20`` pour un total de ``60``.

Après avoir suivi ces nouvelles instructions, vous auriez une position horizontale de `15` et une profondeur de `60` (les multiplier ensemble donne *`900`*).

En utilisant cette nouvelle interprétation des commandes, calculez la position horizontale et la profondeur que vous auriez après avoir suivi le chemin programmé. *Qu'obtenez-vous si vous multipliez votre position horizontale finale avec votre profondeur finale ?*
