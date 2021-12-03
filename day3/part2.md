# --- Partie Deux ---

Ensuite, vous devriez vérifier l'*état des systèmes de survie*, qui peut être déterminée en multipliant l'*activité du générateur d'oxygène* et l'*activité de l'éliminateur de CO2*.

L'activité du générateur d'oxygène et celle de l'éliminateur de CO2 peuvent être trouvées dans votre rapport de diagnostic - les trouver, c'est le plus compliqué. Les deux valeurs sont décelables en suivant un processus similaire, impliquant de filtrer les valeurs jusqu'à ce qu'une seule ne subsiste. Avant de chercher l'une des valeurs, commencez avec la liste complète des nombres binaires de votre rapport de diagnostic et prenez en compte *uniquement le premier bit* de ces nombres. Alors :

- Gardez seulement les nombres sélectionnés par le *critère de bit* pour l'activité que vous étudiez. Rejetez les nombres qui ne correspondent pas au critère.
- S'il ne vous reste qu'un seul nombre,m arrêtez-vous ; il s'agit du nombre représentant la valeur que vous recherchez.
- Sinon, répétez le processus, en prenant en compte le bit suivant sur la droite.

Le *critère de bit* dépend de ce que vous cherchez :

- Pour trouver l'*activité du générateur d'oxygène*, déterminez la *valeur la plus commune* (`0` ou `1`) dans la position de bit actuelle, et gardez uniquement les nombres qui ont cette valeur dans cette position. Si `0` et `1` sont en quantité égale, gardez les nombres possédant un `1` dans la position évaluée.
- Pour trouver l'*activité de l'éliminateur de CO2*, déterminez la *valeur la moins commune* (`0` ou `1`) dans la position de bit actuelle, et gardez uniquement les nombres qui ont cette valeur dans cette position. Si `0` et `1` sont en quantité égale, gardez les nombres possédant un `1` dans la position évaluée.

Par exemple, pour déterminer la valeur de l'*activité du générateur d'oxygène* en utilisant le même rapport de diagnostic que l'exemple précédent :

- Commencez avec tous les douze nombres et ne considérez que le premier bit de chacun d'entre eux. Il y a plus de bits valant `1` (sept) que de bits valant `0` (cinq) ; ne gardez donc que les sept nombres avec un `1` dans la première position : `11110`, `10110`, `10111`, `10101`, `11100`, `10000` et `11001`.
- Ensuite, considérez le deuxième bit des sept nombres restants : il y a plus de bits valant `0` (quatre) que de bits valant `1` (trois) ; ne gardez donc que les quatre nombres avec un `0` dans la seconde position : `10110`, `10111`, `10101`et `10000`.
- Dans la troisième position, trois des quatre nombres restants ont un `1` ; gardez donc ces trois-là : `10110`, `10111`, et `10101`.
- Dans la quatrième position, deux des trois nombres restants ont un `1` ; gardez donc ces deux-là : `10110` et `10111`.
- Dans la cinquième position, il y a un nombre égal de `1` et de `0` (un chacun). Ainsi, pour trouver l'*activité du générateur d'oxygène*, gardez le nombre ayant un `1` dans cette position : `10111`.
- Puisqu'il ne reste plus qu'un nombre, arrêtez-vous. l'*activité du générateur d'oxygène* est `10111`, ou *`23`* en décimal.

Ensuite, pour déterminer la valeur de l'*activité de l'éliminateur de CO2* en utilisant les même valeurs que ci-dessus :

- Recommencez avec tous les douze nombres et ne considérez que le premier bit de chacun d'entre eux. Il y a moins de bits valant `0` (cinq) que de bits valant `1` (sept) ; ne gardez donc que les cinq nombres avec un `0` dans la première position : `00100`, `01111`, `00111`, `00010` et `01010`.
- Ensuite, considérez le deuxième bit des cinq nombres restants : il y a moins de bits valant `1` (deux) que de bits valant `0` (trois) ; ne gardez donc que les deux nombres avec un `1` dans la deuxième position : `01111` et `01010`.
- Dans la troisième position, il y a un nombre égal de `1` et de `0` (un chacun). Ainsi, pour trouver l'*activité de l'éliminateur de CO2*, gardez le nombre avec un `0` dans cette position : `01010`.
- Puisqu'il ne reste plus qu'un nombre, arrêtez-vous. l'*activité de l'éliminateur de CO2* est `01010`, ou *`10`* en décimal.

Enfin, pour trouver l'état des systèmes de survie, multipliez l'activité du générateur d'oxygène (`23`) par l'activité de l'éliminateur de CO2 (`10`) pour obtenir *`230`*.

Utilisez les nombres binaires de votre rapport de diagnostic pour calculer l'activité du générateur d'oxygène et l'activité de l'éliminateur de CO2, puis ;multipliez-les ensembles. *Quel est l'état des systèmes de survie du sous-marin ?* Assurez-vous de représenter votre réponse en décimal, et non en binaire.
