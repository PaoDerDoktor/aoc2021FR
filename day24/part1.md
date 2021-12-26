# --- Jour 24 : Unité Arithmétique et Logique ---

De la [fumée magique](https://fr.wiktionary.org/wiki/magic_smoke#:~:text=Locution%20nominale&text=(%C3%89lectronique)%20(Par%20plaisanterie),bon%20fonctionnement%20des%20composants%20%C3%A9lectroniques.) commence à fuir de l'[unité arithmétique et logique](https://fr.wikipedia.org/wiki/Unit%C3%A9_arithm%C3%A9tique_et_logique) (en anglais *Arithmetic Logic Unit*, ALU). Sans la capacité d'exécuter des fonctions arithmétiques et logiques de base, votre sous-marin ne peut plus opérer ses lumières de Noël si cool !

Il ne peut d'ailleurs pas non plus naviguer. Ni faire fonctionner le système à oxygène.

Ne vous en faites pas, par contre - il vous reste *probablement* assez d'oxygène pour vous donner assez de temps pour construire une nouvelle ALU.

L'ALU est une unité de calcul quadridimensionnelle : elle possède des variables entières `w`, `x`, `y` et `z`. Ces variables commencent toutes avec la valeur `0`. L'ALU supporte également *six instructions* :

- `inp a` - Lit une valeur en entrée et l'écrit dans la variable `a`.
- `add a b` - Ajoute la valeur de `a` à la valeur de `b`, puis stocke le résultat dans la variable `a`.
- `mul a b` - Multiplie la valeur de `a` par la valeur de `b`, puis stocke le résultat dans la variable `a`.
- `div a b` - Divise la valeur de `a` par la valeur de `b`, tronque le résultat pour obtenir un entier, puis stocke le résultat dans la variable `a`  (ici, "tronquer" signifie arrondir la valeur vers zéro)
- `mod a b` - Divise la valeur de `a` par la valeur de `b`, puis stocke le *reste* dans la variable `a` (ceci est également appelé [modulo](https://fr.wikipedia.org/wiki/Modulo_(op%C3%A9ration))).
- `eql a b` - Si les valeurs de `a` et `b` sont égales, stocke la valeur `1` dans la variable `a`. Sinon, stocke la valeur `0` dans la variable `a`.

Dans toutes ces instructions, `a` et `b` sont des exemples ; `a` sera toujours la variable dans laquelle le résultat d'une opération est stocké tandis que `b` peut être soit une variable soit un nombre. Les nombres peuvent être positifs ou négatifs, mais seront toujours des entiers.

L'ALU n'a pas d'instruction de *saut* ; dans un programme d'ALU, toutes les instructions sont exécutées exactement une fois dans l'ordre de haut en bas. Le programme s'arrête après que la dernière instruction ait fini de s'exécuter.

(Les programmeurs devraient faire très attention : essayer d'exécuter une opération `div` avec ``b = 0`` ou essayer d'exécuter une opération `mod` avec ``a < 0`` ou ``b <= 0`` ferra crash le programme et pourrait même endommager l'ALU. Ces opérations ne sont jamais volontairement exécutées dans un programme d'ALU sérieux.)

Par exemple, voici un programme d'ALU qui prends en entrée un nombre, le met en négatif, et le stocke dans `x` :

```alu
inp x
mul x -1
```

Voici un programme d'ALU qui prends un nombre positif ou nul en entrée, le convertir en binaire, et stocke le bit le plus faible (1) dans `z`, le second bit le plus faible (2) dans `y`, le troisième bit le plus faible (4) dans `x`, et le quatrième bit le plus faible dans `w` :

```alu
inp w
add z w
mod z 2
div w 2
add y w
mod y 2
div w 2
add x w
mod x 2
div w 2
mod w 2
```

Une fois que vous avez fini de construire une ALU de remplacement, vous pouvez l'installer dans le sous-marin, qui reprendra immédiatement sa tâche là où l'ALU précédente s'est interrompue : la validation du *numéro de modèle* du sous-marin. Pour ce faire, l'ALU exécutera le programme MOdel Number Automatic Detector (MONAD, le Détecteur Automatique de Numéro de MOdèle, l'entrée de votre puzzle).

Les numéros de modèles des sous-marins sont toujours des *nombres de quatorze chiffres* ne contenant que des chiffres de `1` à `9`. Le nombre `0` *ne peut pas* apparaître dans le numéro de modèle.

Quand MONAD vérifie un hypothétique nombre de quatorze chiffres, il utilise quatorze instructions `inp` séparées, attendant chacune *un seul chiffre* du numéro dans l'ordre du plus au moins significatif (Donc, pour vérifier le numéro de modèle `13579246899999`, vous donneriez `1` à la première instruction `inp`, `3` à la deuxième instruction `inp`, `5` à la troisième instruction `inp`, et ainsi de suite). Ceci signifie qu'en exécutant MONAD, chaque instruction d'entrée devrait être approvisionnée d'une seule valeur entière d'au moins `1` et d'au plus `9`.

Ensuite, une fois que MONAD ait finit d'exécuter toutes ses instructions, il indiquera que le numéro de modèle était *valide* en laissant un `0` dans la variable `z`. Inversement, si le numéro de modèle était *invalide*, il laissera une valeur différente de `0` dans `z`.

MONAD imposes de mystérieuses restrictions supplémentaires sur les numéros de modèles, et la légende dit que la dernière copie du manuel de documentation de MONAD a été mangée par un [tanuki](https://universdujapon.com/blogs/japon/tanuki). Vous allez devoir *trouver ce que fait MONAD* d'une autre façon.

Pour activer autant de fonctionnalités du sous-marin que possible, trouvez le plus grand numéro de modèle valide qui ne contienne pas le chiffre `0`. *Quel est le plus grand numéro de modèle accepté par MONAD ?*
