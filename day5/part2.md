# --- Partie Deux ---

Malheureusement, ne considérer que les lignes verticales et horizontales ne vous montre pas la situation comme elle est réellement, vous aurez également besoin des *lignes diagonales*.

En raison des limites du système de cartographie des cheminées hydrothermales, les lignes de votre listes seront toujours soit verticales, soit horizontales, soit des diagonales à exactement 45 degrés. En d'autres mots :

- Une entrée ``1,1 -> 3,3`` couvre les points ``1,1``, ``2,2`` et ``3,3``.
- Une entrée ``9,7 -> 7,9`` couvre les points ``9,7``, ``8,8`` et ``7,9``.

En prenant en compte toutes les lignes de l'exemple ci-dessus, on obtient désormais le diagramme suivant :

```countArray
1.1....11.
.111...2..
..2.1.111.
...1.2.2..
.112313211
...1.2....
..1...1...
.1.....1..
1.......1.
222111....
```

Vous avez encore besoin de déterminer *le nombre de points où au moins deux lignes se chevauchent*. Dans l'exemple ci-dessus, c'est encore une fois à n'importe quel endroit du diagramme où est écrit `2` ou plus - désormais un total de *`12`* points.

Prenez toutes les lignes en compte. *À combien de points au moins deux lignes se chevauchent-elles ?*
