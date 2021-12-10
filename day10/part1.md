# --- Jour 10 : Notation de Syntaxe ---

Vous avez demandé au sous-marin de déterminer le meilleur tracé pour sortir de ces profondes grottes, mais vous réponds seulement :

```submarineError
Erreur de syntaxe sur des lignes du sous-système de navigation : chacune d'entre elles
```

*Chacune d'entre elle ?!* les dégâts sont plus importants que ce que vous pensiez. Vous sortez une copie du sous-système de navigation (l'entrée de votre puzzle).

La syntaxe du sous-système de navigation est faite de plusieurs lignes contenant des *tronçons*. Il y a un ou plusieurs tronçons sur chaque ligne, et les tronçons contiennent zéro ou plusieurs autres tronçons. Les tronçons adjacents ne sont séparés par aucun délimiteur : si un tronçon s'arrête, le tronçon suivant (s'il existe) peut démarrer immédiatement. Chaque tronçon doit être *ouvert* puis *fermé* avec l'une des quatre paires acceptables de caractères correspondants :

- Si un tronçon s'ouvre par `(`, il doit se fermer par `)`.
- Si un tronçon s'ouvre par `[`, il doit se fermer par `]`.
- Si un tronçon s'ouvre par `{`, il doit se fermer par `}`.
- Si un tronçon s'ouvre par `<`, il doit se fermer par `>`.

Ainsi, ``()`` est un tronçon valide qui ne contient pas d'autre tronçon, comme ``[]``. D'autres tronçons plus complexes mais valides sont ``([])``, ``{()()()}``, ``<([{}])>``, ``[<>({}){}[([])<>]]``, et même ``(((((((((())))))))))`` .

Certaines lignes sont *incomplètes*, mais d'autres sont *corrompues*. Trouvez et retirez d'abord les lignes corrompues.

Une ligne corrompue est une ligne où un tronçon *se ferme avec le mauvais caractère* - c'est-à-dire, où le caractère qui l'ouvre et celui qui le ferme ne forment pas une des paires listées plus haut.

Des exemples de lignes corrompues sont ``(]``, ``{()()()>``, ``(((()))}``, et ``<([]){()}[{}])``. De tels tronçons peuvent apparaître n'importe où dans une ligne, et leur présence corrompt la ligne entière.

Par exemple, considérer le sous-système de navigation suivant :

```navigation
[({(<(())[]>[[{[]{<()<>>
[(()[<>])]({[<{<<[]>>(
{([(<{}[<>[]}>{[]{[(<()>
(((({<>}<{<{<>}{[]{[]{}
[[<[([]))<([[{}[[()]]]
[{[{({}]{}}([{[{{{}}([]
{<[[]]>}<{[{[{[]{()[[[]
[<(<(<(<{}))><([]([]()
<{([([[(<>()){}]>(<<{{
<{([{{}}[<[[[<>{}]]]>[]]
```

Certaines de ces lignes ne sont pas corrompues mais simplement incomplètes, vous pouvez les ignorer pour l'instant. Les cinq lignes restantes sont corrompues :

- ``{([(<{}[<>[]}>{[]{[(<()>`` -  `]` attendu, mais `}` trouvé à la place.
- ``[[<[([]))<([[{}[[()]]]`` -  `]` attendu, mais `)` trouvé à la place.
- ``[{[{({}]{}}([{[{{{}}([]`` -  `)` attendu, mais `]` trouvé à la place.
- ``[<(<(<(<{}))><([]([]()`` -  `>` attendu, mais `)` trouvé à la place.
- ``<{([([[(<>()){}]>(<<{{`` -  `]` attendu, mais `>` trouvé à la place.

Arrêtez-vous à la première fermeture incorrecte sur chaque ligne.

Saviez-vous que les vérificateurs syntaxiques font en fait des concours pour voir lequel est capable d'obtenir le meilleur score pour une erreur de syntaxe dans un fichier ? C'est vrai ! Pour calculer la note de l'erreur de syntaxe d'un fichier, prenez le *premier caractère erroné* de la ligne et regardez sa valeur dans la table suivante :

- `)` : ``3`` points.
- `]` : ``57`` points.
- `}` : ``1197`` points.
- `>` : ``25137`` points.

Dans l'exemple ci-dessus, un `)` erroné est trouvé deux fois (<pre><code>2&ast;3 = <em>6</em></code></pre> points), un `]` erroné est trouvé une fois (*`57`* points), un `}` erroné est trouvé une fois (*`1197`* points), et un `>` erroné est trouvé une fois (*`25137`* points). En conséquence, la note totale des erreurs de syntaxe pour ce fichier est de <pre><code>6+57+1197+25137 = <em>26397</em></code></pre> points !

Trouvez le premier caractère erroné de chaque ligne corrompue du sous-système de navigation. *Quel est la note totale des erreurs de syntaxe pour ces erreurs ?*
