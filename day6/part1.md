# --- Jour 6 : Poisson-Lanterne ---

Le plancher océanique est de plus en plus profond. Peut-être que les clefs du traîneau ont été emportées par ici ?

Un énorme banc de [poisson-lanternes](https://fr.wikipedia.org/wiki/Myctophidae) vous double. Ils doivent se reproduire rapidement pour atteindre de telles proportions - peut-être *exponentiellement* ? Vous devriez modéliser leur rapidité de croissance pour en être sur.

Bien que vous ne connaissiez rien de cette espèce spécifique de poisson-lanterne, vous faites quelques assomptions sur leurs propriétés. À tous les coups, chaque poisson-lanterne crée un nouveau poisson-lanterne tous les *7* jours.

Cependant, ce processus n'est pas forcément synchrone entre tous les poisson-lanterne : l'un des poisson-lanternes pourrait être à deux jours de créer un nouveau poisson-lanterne, alors qu'un autre en serait à *4* jours. Ainsi, vous pouvez modéliser chaque poisson en tant que simple entier représentant *le nombre de jours avant qu'il ne crée un nouveau poisson-lanterne*.

De plus, vous vous dites, un *nouveau* poisson-lanterne devrait sûrement avoir besoin d'un peu plus de jours avant de produire plus de poisson-lanternes : deux jours de plus pour son premier cycle.

Ainsi, supposez que vous ayez un poisson-lanterne avec un minuteur interne de `3` (`3` jours avant de créer un nouveau poisson, donc) :

- Après un jour, son minuteur interne deviendrait `2`.
- Après un autre jour, son minuteur interne passerait à `1`.
- Après un autre jour, son minuteur interne passerait à `0`.
- Après un autre jour, son minuteur interne se réinitialiserait à `6`, et il créerait un *nouveau* poisson-lanterne avec un minuteur interne de `8`.
- Après un autre jour, le premier poisson-lanterne verrait son minuteur interne passer à `5`, alors que le second verrait le sien passer à `7`.

Un poisson-lanterne qui crée un nouveau poisson réinitialise son minuteur à `6`, *pas à `7`* (vu que `0` est compris comme valeur valide de minuteur). Le nouveau poisson-lanterne démarre avec un minuteur interne de `8` et ne commence pas à le décompter avant le jour suivant.

Réalisant ce que vous devez faire, le sous-marin produit automatiquement une liste de l'âge de plusieurs centaines de poisson-lanternes alentours (l'entrée de votre puzzle). Par exemple, supposez que vous obteniez la liste suivante :

```csv
3,4,3,1,2
```

La liste signifie que le premier poisson possède un minuteur interne de `3`, que le second possède un minuteur interne de `4`, et ainsi de suite jusqu'au cinquième poisson possédant un minuteur interne de `2`. Simuler ces poissons sur plusieurs jours se passerait comme ceci :

```fishes
État initial  : 3,4,3,1,2
Après  1 jour : 2,3,2,0,1
Après  2 jours: 1,2,1,6,0,8
Après  3 jours: 0,1,0,5,6,7,8
Après  4 jours: 6,0,6,4,5,6,7,8,8
Après  5 jours: 5,6,5,3,4,5,6,7,7,8
Après  6 jours: 4,5,4,2,3,4,5,6,6,7
Après  7 jours: 3,4,3,1,2,3,4,5,5,6
Après  8 jours: 2,3,2,0,1,2,3,4,4,5
Après  9 jours: 1,2,1,6,0,1,2,3,3,4,8
Après 10 jours: 0,1,0,5,6,0,1,2,2,3,7,8
Après 11 jours: 6,0,6,4,5,6,0,1,1,2,6,7,8,8,8
Après 12 jours: 5,6,5,3,4,5,6,0,0,1,5,6,7,7,7,8,8
Après 13 jours: 4,5,4,2,3,4,5,6,6,0,4,5,6,6,6,7,7,8,8
Après 14 jours: 3,4,3,1,2,3,4,5,5,6,3,4,5,5,5,6,6,7,7,8
Après 15 jours: 2,3,2,0,1,2,3,4,4,5,2,3,4,4,4,5,5,6,6,7
Après 16 jours: 1,2,1,6,0,1,2,3,3,4,1,2,3,3,3,4,4,5,5,6,8
Après 17 jours: 0,1,0,5,6,0,1,2,2,3,0,1,2,2,2,3,3,4,4,5,7,8
Après 18 jours: 6,0,6,4,5,6,0,1,1,2,6,0,1,1,1,2,2,3,3,4,6,7,8,8,8,8
```

Chaque jour, un `0` devient un `6` et ajoute un nouveau `8` à la fin de la liste, pendant que chaque autre nombre est décrémenté de 1 si il était présent au début de la journée.

Dans cet exemple, après 18 jours, il y a un total de `26` poissons. Après 80 jours, il y en aurait un total de *`5934*.

Trouvez un moyen de simuler les poisson-lanternes. *Combien y auraient-ils de poison-lanternes après 80 jours ?*
