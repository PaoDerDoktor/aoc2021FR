# --- Partie Deux --

Vous remarquez une seconde question au dos de l'énoncé du devoir :

Quel est la plus grande magnitude obtenable en additionnant seulement deux des des nombres poisson-escargot ?

Notez que l'addition poisson-escargot n'est pas [commutative](https://fr.wikipedia.org/wiki/Loi_commutative) - c'est-à-dire que ``x + y`` et ``y + x`` peuvent produire des résultats différents.

Considérez encore une fois l'énoncé suivant :

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

La plus grande magnitude de la somme de n'importe quelle paire de deux nombres poisson-escargot dans cette liste est *`3993`*. C'est la magnitude de ``[[2,[[7,7],7]],[[5,8],[[9,3],[0,2]]]]`` + ``[[[0,[5,8]],[[1,7],[9,6]]],[[4,[1,2]],[[1,4],2]]]``, qui se réduit en ``[[[[7,8],[6,6]],[[6,0],[7,7]]],[[[7,8],[8,8]],[[7,9],[0,6]]]]``.

*Quelle est la plus grande magnitude d'une somme de deux nombres poisson-escargots provenant de l'énoncé du devoir ?*
