# --- Jour 2 : Plongez ! ---

Maintenant, vous devez comprendre comment piloter cet engin.

On dirait que le sous-marin peut prendre une série de commandes comme ``forward 1``, ``down 2``, ou ``up 3`` :

- ``forward X`` ("avant X" en anglais) augmente votre position horizontale de `X` unités.
- ``down X`` ("bas X" en anglais) *augmente* votre profondeur de `X` unités.
- ``up X`` ("haut X" em anglais) *diminue* votre profondeur de `X` unités.

Notez que comme vous êtes dans un sous-marin, ``down`` et ``up`` ("haut" et "bas" donc) affectent votre *profondeur*, et ont donc un effet qui peut être opposé à ce à quoi vous pourriez vous attendre.

Le sous-marin semble déjà avoir un parcours planifié (l'entrée de votre puzzle). Vous devriez essayer de voir où il va. Par exemple :

```path
forward 5
down 5
forward 8
up 3
down 8
forward 2
```

Votre position horizontale et votre profondeur démarrent toutes deux à `0`. Les étapes ci-dessus les modifieraient ensuite ainsi :

- ``forward 5`` ajoute `5` à votre position horizontale, pour un total de `5`.
- ``down 5`` ajoute `5` à votre profondeur, pour un total de `5`.
- ``forward 8`` ajoute `8` à votre position horizontale, pour un total de `13`.
- ``up 3`` retire `3` à votre profondeur, pour un total de `2`.
- ``down 8`` ajoute `8` à votre profondeur, pour un total de `10`.
- ``forward 2`` ajoute `2` à votre position horizontale, pour un total de `15`.

Après avoir suivi ces instructions, vous devriez avoir une position horizontale de `15` et une profondeur de `10` (multiplier les deux ensemble donne *`150`*).

Calculez la position horizontale et la profondeur que vous auriez après avoir suivi le chemin programmé. *Qu'obtenez-vous si vous multipliez votre position horizontale finale et votre profondeur finale ?*
