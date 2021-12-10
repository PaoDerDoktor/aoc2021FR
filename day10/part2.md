# --- Partie Deux ---

À présent, retirez les lignes corrompues. Les lignes restantes sont *incomplètes*.

Les lignes incomplètes n'ont aucun caractère incorrect : à la place, il leur manque des caractères fermants à la fin de la ligne. Pour réparer le sous-système de navigation, vous devrez trouver *quelle séquence de caractères fermants* complète chaque tronçons de la ligne.

Vous ne pouvez utiliser que des caractères fermants (`)`, `]`, `}` ou `>`) et vous devez les ajouter dans le bon ordre pour que seules des paires acceptables soient formées et que tous les tronçons soient fermés.

Dans l'exemple ci-dessus, cinq lignes sont incomplètes :

- ``[({(<(())[]>[[{[]{<()<>>`` - Complétée en y ajoutant ``}}]])})]``.
- ``[(()[<>])]({[<{<<[]>>(`` - Complétée en y ajoutant ``)}>]})``.
- ``(((({<>}<{<{<>}{[]{[]{}`` - Complétée en y ajoutant ``}}>}>))))``.
- ``{<[[]]>}<{[{[{[]{()[[[]`` - Complétée en y ajoutant ``]]}}]}]}>``.
- ``<{([{{}}[<[[[<>{}]]]>[]]`` - Complétée en y ajoutant ``])}>``.

Saviez-vous que les outils d'autocomplétion ont *eux aussi* des concours ? C'est vrai ! La note est déterminée en considérant la chaîne de complétion caractère-par-caractère. Démarrez avec un score total de `0`. Ensuite, pour chaque caractère, multipliez le score total par 5 puis augmentez le score total par la valeur en points donnée pour la caractère dans la table suivante :

- `)` : `1` point.
- `]` : `2` points.
- `}` : `3` points.
- `>` : `4` points.

Ainsi, la dernière chaîne de complétion plus haut - ``])}>`` - serait notée de cette manière :

- Commencez avec une note totale de `0`
- Multipliez la note totale par 5 pour obtenir `0`, puis ajoutez la valeur de `]` (2) pour obtenir une nouvelle note de `2`
- Multipliez la note totale par 5 pour obtenir `10`, puis ajoutez la valeur de `)` (1) pour obtenir une nouvelle note de `11`
- Multipliez la note totale par 5 pour obtenir `55`, puis ajoutez la valeur de `}` (3) pour obtenir une nouvelle note de `58`
- Multipliez la note totale par 5 pour obtenir `290`, puis ajoutez la valeur de `}` (4) pour obtenir une nouvelle note de `294`

Les cinq chaînes de complétion des cinq lignes ont ces notes totales :

- ``}}]])})]`` - 288957 points totaux.
- ``)}>]})`` - 5566 points totaux.
- ``}}>}>))))`` - 1480781 points totaux.
- ``]]}}]}]}>`` - 995444 points totaux.
- ``])}>`` - 294 points totaux.

Les outils d'autocomplétion sont des machins bizarres : le gagnant est trouvé en *triant* toutes les notes et en prenant la note du *milieu* (il y aura toujours un nombre impair de notes à traiter). Dans cet exemple, la note médiane est *`288957`* puisque qu'il y a le même nombre de notes plus petites et plus grandes qu'elle.

Trouvez les chaînes de complétion pour chacune des lignes incomplètes, notez les chaînes de complétion, puis triez les notes. *Quelle est la note médiane ?*
