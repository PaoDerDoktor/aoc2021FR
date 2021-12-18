# --- Jour 18 : Poisson-escargot ---

Vous descendez dans la fosse océanique et rencontrez des poissons-escargots. Ils disent avoir vu les clefs du traîneau ! Ils vous diront même où les clefs s'en sont allées si vous aidez un des plus petits poisson-escargots pour ses *devoirs de math*.

Les nombres poisson-escargot ne sont pas comme les nombres normaux. À la place, tous les nombres poisson-escargot sont des *paires* - des listes ordonnées de deux éléments. Chaque élément d'une paire peut être soit un nombre normal, soit une autre paire.

Les paires sont écrites sous le format ``[x, y]``, où `x` et `y` sont les éléments de la paire. Voici quelques exemples de nombres poisson-escargot, un nombre par ligne :

```snailfish
[1,2]
[[1,2],3]
[9,[8,7]]
[[1,9],[8,5]]
[[[[1,2],[3,4]],[[5,6],[7,8]]],9]
[[[9,[3,8]],[[0,9],6]],[[[3,7],[4,9]],3]]
[[[[1,3],[5,3]],[[1,3],[8,7]]],[[[4,9],[6,9]],[[8,2],[7,3]]]]
```

Le devoir du poisson-escargot porte sur *l'addition*. Pour additionner deux nombres poisson-escargot, formez une paire avec l'opérateur de droite et l'opérateur de gauche. Par exemple, ``[1, 2]`` + ``[[3, 4], 5]`` devient ``[[1,2],[[3,4],5]]``.

Il n'y a qu'un seul problème : *les nombres poisson-escargot doivent toujours être réduits*, et le processus d'addition de deux nombres peut donner un nombre ayant besoin d'être réduit.

Pour *réduire un nombre poisson-escargot*, vous devez effectuer la première action de cette liste s'appliquant au nombre traité, et ce autant que nécessaire :

- Si une ou plusieurs paires sont *nichées à l'intérieur de quatre autres paires*, la plus à gauche de ces paires nichées *explose*.
- Si un ou plusieurs nombres normaux sont *supérieurs ou égaux à 10*, le plus à gauche de ces nombre normaux *se sépare*.

Une fois que plus aucune action ne s'applique au nombre traité, le nombre poisson-escargot est réduit.

Pendant la réduction, une seule action s'applique à la fois, après quoi le processus retourne au début de la liste des actions. Par exemple, si une *séparation* produit une paire rencontrant les critères d'*explosion*, cette paire *explose* avant qu'une autre *séparation* ne se produise.

Pour *exploser* une paire, la valeur gauche de la paire est ajoutée au premier nombre normal directement à gauche de la paire explosant (s'il y en a un), et la valeur droite de la paire est ajoutée au premier nombre normal directement à droite de la paire explosant (s'il y en a un). Les paires explosant seront toujours composées de deux nombre normaux. Ensuite, l'entièreté de la paire explosant est remplacée par le nombre normal `0`.

Voici quelques exemple d'une seule explosion :

- <code>[[[[<em>[9,8]</em>,1],2],3],4]</code> devient <code>[[[[<em>0,9</em>],2],3],4]</code> (le `9` n'a pas de nombre normal à sa gauche, il n'est donc ajouté à aucun nombre normal).
- <code>[7,[6,[5,[4,<em>[3,2]</em>]]]]></code> devient <code>[7,[6,[5,[<em>7,0</em>]]]]</code> (le `2` n'a pas de nombre normal à sa droite, il n'est donc ajouté à aucun nombre normal).
- <code>[[6,[5,[4,<em>[3,2]</em>]]],1]</code> devient <code>[[6,[5,[<em>7,0</em>]]],<em>3</em>]</code>.
- <code>[[3,[2,[1,<em>[7,3]</em>]]],[6,[5,[4,[3,2]]]]]</code> devient <code>[[3,[2,[<em>8,0</em>]]],[<em>9</em>,[5,[4,[3,2]]]]]</code> (la paire ``[3,2]`` n'est pas affectée puisque la paire ``[7,3]`` est plus à gauche ; ``[3,2]`` exploserait à la prochaine action).
- <code>[[3,[2,[8,0]]],[9,[5,[4,<em>[3,2]</em>]]]]</code> devient <code>[[3,[2,[8,0]]],[9,[5,[<em>7,0</em>]]]]</code>.

Pour *séparer* un nombre normal, remplacez le par une paire : l'élément de gauche de cette paire est le nombre divisé par deux et arrondi *à l'entier inférieur* et l'élément de droite de cette paire est le nombre divisé par deux et arrondi *à l'entier supérieur*. Par exemple, `10` devient ``[5,5]``, `11` devient ``[5,6]``, `12` devient ``[6,6]`` et ainsi de suite.

Voici le processus requis pour trouver le résultat de la réduction de ``[[[[4,3],4],4],[7,[[8,4],9]]]`` + ``[1,1]`` :

<pre><code>after addition: [[[[<em>[4,3]</em>,4],4],[7,[[8,4],9]]],[1,1]]
Après une explosion:  [[[[0,7],4],[7,[<em>[8,4]</em>,9]]],[1,1]]
Après une explosion:  [[[[0,7],4],[<em>15</em>,[0,13]]],[1,1]]
Après une séparation: [[[[0,7],4],[[7,8],[0,<em>13</em>]]],[1,1]]
Après une séparation: [[[[0,7],4],[[7,8],[0,<em>[6,7]</em>]]],[1,1]]
Après une explosion:  [[[[0,7],4],[[7,8],[6,0]]],[8,1]]</code></pre>

Une fois que plus aucune action de réduction ne s'applique, le nombre poisson-escargot restant est le résultat de l'addition : ``[[[[0,7],4],[[7,8],[6,0]]],[8,1]]``.

Le devoir de math demande d'additionner une *liste de nombres poisson-escargot* (l'entrée de votre puzzle). Les nombres poisson-escargot sont chacun notés sur une ligne différente. Ajoutez le premier nombre poisson-escargot au deuxième, puis ajoutez ce résultat au troisième, puis ajoutez ce nouveau résultat au quatrième, et ainsi de suite jusqu'à ce que chaque nombre de la list ait été utilisé une fois.

Par exemple, la somme finale de la liste suivante est ``[[[[1,1],[2,2]],[3,3]],[4,4]]`` :

```snailfish
[1,1]
[2,2]
[3,3]
[4,4]
```

La somme finale de la liste suivante est ``[[[[3,0],[5,3]],[4,4]],[5,5]]`` :

```snailfish
[1,1]
[2,2]
[3,3]
[4,4]
[5,5]
```

La somme finale de la liste suivante est ``[[[[5,0],[7,4]],[5,5]],[6,6]]`` :

```snailfish
[1,1]
[2,2]
[3,3]
[4,4]
[5,5]
[6,6]
```

Voici un exemple légèrement plus grand L

```snailfish
[[[0,[4,5]],[0,0]],[[[4,5],[2,6]],[9,5]]]
[7,[[[3,7],[4,3]],[[6,3],[8,8]]]]
[[2,[[0,8],[3,4]]],[[[6,7],1],[7,[1,6]]]]
[[[[2,4],7],[6,[0,5]]],[[[6,8],[2,8]],[[2,1],[4,5]]]]
[7,[5,[[3,8],[1,4]]]]
[[2,[2,2]],[8,[8,1]]]
[2,9]
[1,[[[9,3],9],[[9,0],[0,7]]]]
[[[5,[7,4]],7],1]
[[[[4,2],2],6],[8,7]]
```

Sa somme finale ``[[[[8,7],[7,7]],[[8,6],[7,7]]],[[[0,7],[6,6]],[8,7]]]`` est trouvée après avoir additionné tous ses nombres poisson-escargot :

```snailfishAddition
  [[[0,[4,5]],[0,0]],[[[4,5],[2,6]],[9,5]]]
+ [7,[[[3,7],[4,3]],[[6,3],[8,8]]]]
= [[[[4,0],[5,4]],[[7,7],[6,0]]],[[8,[7,7]],[[7,9],[5,0]]]]

  [[[[4,0],[5,4]],[[7,7],[6,0]]],[[8,[7,7]],[[7,9],[5,0]]]]
+ [[2,[[0,8],[3,4]]],[[[6,7],1],[7,[1,6]]]]
= [[[[6,7],[6,7]],[[7,7],[0,7]]],[[[8,7],[7,7]],[[8,8],[8,0]]]]

  [[[[6,7],[6,7]],[[7,7],[0,7]]],[[[8,7],[7,7]],[[8,8],[8,0]]]]
+ [[[[2,4],7],[6,[0,5]]],[[[6,8],[2,8]],[[2,1],[4,5]]]]
= [[[[7,0],[7,7]],[[7,7],[7,8]]],[[[7,7],[8,8]],[[7,7],[8,7]]]]

  [[[[7,0],[7,7]],[[7,7],[7,8]]],[[[7,7],[8,8]],[[7,7],[8,7]]]]
+ [7,[5,[[3,8],[1,4]]]]
= [[[[7,7],[7,8]],[[9,5],[8,7]]],[[[6,8],[0,8]],[[9,9],[9,0]]]]

  [[[[7,7],[7,8]],[[9,5],[8,7]]],[[[6,8],[0,8]],[[9,9],[9,0]]]]
+ [[2,[2,2]],[8,[8,1]]]
= [[[[6,6],[6,6]],[[6,0],[6,7]]],[[[7,7],[8,9]],[8,[8,1]]]]

  [[[[6,6],[6,6]],[[6,0],[6,7]]],[[[7,7],[8,9]],[8,[8,1]]]]
+ [2,9]
= [[[[6,6],[7,7]],[[0,7],[7,7]]],[[[5,5],[5,6]],9]]

  [[[[6,6],[7,7]],[[0,7],[7,7]]],[[[5,5],[5,6]],9]]
+ [1,[[[9,3],9],[[9,0],[0,7]]]]
= [[[[7,8],[6,7]],[[6,8],[0,8]]],[[[7,7],[5,0]],[[5,5],[5,6]]]]

  [[[[7,8],[6,7]],[[6,8],[0,8]]],[[[7,7],[5,0]],[[5,5],[5,6]]]]
+ [[[5,[7,4]],7],1]
= [[[[7,7],[7,7]],[[8,7],[8,7]]],[[[7,0],[7,7]],9]]

  [[[[7,7],[7,7]],[[8,7],[8,7]]],[[[7,0],[7,7]],9]]
+ [[[[4,2],2],6],[8,7]]
= [[[[8,7],[7,7]],[[8,6],[7,7]]],[[[0,7],[6,6]],[8,7]]]
```

Pour vérifier si la réponse finale est vraie, le professeur poisson-escargot vérifie seulement la *magnitude* de la somme finale. La magnitude d'une paire est égale à 3 fois sa valeur de gauche ajouté à 2 fois sa valeur de droite. La magnitude d'un nombre normal est simplement la valeur de ce nombre.

Par exemple, la magnitude de ``[9,1]`` est <code>3*9 + 2*1 = <em>29</em></code>. Le calcul de la magnitude est récursif : la magnitude de ``[[9,1],[1,9]]`` est <code>3&ast;29 + 2&ast;21 = <em>129</em></code>.

Voici quelques exemple supplémentaires de magnitudes :

- ``[[1,2],[[3,4],5]]`` devient *`143`*
- ``[[[[0,7],4],[[7,8],[6,0]]],[8,1]]`` devient *`1384`*.
- ``[[[[1,1],[2,2]],[3,3]],[4,4]]`` devient *`445`*.
- ``[[[[3,0],[5,3]],[4,4]],[5,5]]`` devient *`791`*.
- ``[[[[5,0],[7,4]],[5,5]],[6,6]]`` devient *`1137`*.
- ``[[[[8,7],[7,7]],[[8,6],[7,7]]],[[[0,7],[6,6]],[8,7]]]`` devient *`3488`*.

Ainsi, étant donné l'énoncé de devoir suivant :

```snailfish
[[[0,[5,8]],[[1,7],[9,6]]],[[4,[1,2]],[[1,4],2]]]
[[[5,[2,8]],4],[5,[[9,9],0]]]
[6,[[[6,2],[5,6]],[[7,6],[4,7]]]]
[[[6,[0,7]],[0,9]],[4,[9,[9,0]]]]
[[[7,[6,4]],[3,[1,3]]],[[[5,5],1],9]]
[[6,[[7,3],[3,2]]],[[[3,8],[5,7]],4]]
[[[[5,4],[7,7]],8],[[8,3],8]]
[[9,3],[[9,9],[6,[4,9]]]]
[[2,[[7,7],7]],[[5,8],[[9,3],[0,2]]]]
[[[[5,2],5],[8,[3,7]]],[[5,[7,5]],[4,4]]]
```

La somme finale est :

```snailfish
[[[[6,6],[7,6]],[[7,7],[7,0]]],[[[7,7],[7,7]],[[7,8],[9,9]]]]
```

Additionnez tous les nombres poisson-escargot du devoir dans l'ordre dans lequel ils apparaissent. *Quelle est la magnitude de la somme finale ?*
