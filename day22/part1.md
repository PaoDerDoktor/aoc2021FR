# Jour 22 : Redémarrage du Réacteur ---

Opérer à ces profondeurs extrêmes de l'océan a surchargé le réacteur du sous-marin, il doit être redémarré.

Le cœur du réacteur est fait d'une grande grille en 3 dimensions constituée entièrement de cubes, un cube par coordonnée tridimensionnelle (``x, y, z``). Chaque cube peut être soit *allumé* soit *éteint* ; au départ du processus de redémarrage, ils sont tous *éteints* (peut-être s'agit-il d'un vieux modèle de réacteur que vous avez déjà vu [auparavant](https://adventofcode.com/2020/day/17 ?)).

Pour redémarrer le réacteur, vous devez simplement *allumer* ou *éteindre* chaque cube en suivant une liste d'*étapes de redémarrage* (l'entrée de votre puzzle). Chaque étape indique un [pavé droit](https://fr.wikipedia.org/wiki/Pav%C3%A9_droit) (l'ensemble des cubes ayant des coordonnées tombant dans les intervalles pour `x`, `y` et `z`) et s'il faut l'*allumer*  ou l'*éteindre*.

Par exemple, considérant ces étapes de redémarrage :

```rebootSteps
on x=10..12,y=10..12,z=10..12
on x=11..13,y=11..13,z=11..13
off x=9..11,y=9..11,z=9..11
on x=10..10,y=10..10,z=10..10
```

La première étape (``on x=10..12,y=10..12,z=10..12``) *allume* un pavé droit de 3x3x3 contenant 27 cubes :

- ``10,10,10``
- ``10,10,11``
- ``10,10,12``
- ``10,11,10``
- ``10,11,11``
- ``10,11,12``
- ``10,12,10``
- ``10,12,11``
- ``10,12,12``
- ``11,10,10``
- ``11,10,11``
- ``11,10,12``
- ``11,11,10``
- ``11,11,11``
- ``11,11,12``
- ``11,12,10``
- ``11,12,11``
- ``11,12,12``
- ``12,10,10``
- ``12,10,11``
- ``12,10,12``
- ``12,11,10``
- ``12,11,11``
- ``12,11,12``
- ``12,12,10``
- ``12,12,11``
- ``12,12,12``

La deuxième étape (``on x=11..13,y=11..13,z=11..13``) *allume* un pavé droit de 3x3x3 qui se superpose avec le premier. Du coup, seulement 19 cubes supplémentaires s'allument, le reste est déjà allumé par l'étape précédente :

- ``11,11,13``
- ``11,12,13``
- ``11,13,11``
- ``11,13,12``
- ``11,13,13``
- ``12,11,13``
- ``12,12,13``
- ``12,13,11``
- ``12,13,12``
- ``12,13,13``
- ``13,11,11``
- ``13,11,12``
- ``13,11,13``
- ``13,12,11``
- ``13,12,12``
- ``13,12,13``
- ``13,13,11``
- ``13,13,12``
- ``13,13,13``

La troisième étape (``off x=9..11,y=9..11,z=9..11``) *éteint* un pavé droit de 3x3x3 qui se superpose partiellement avec certains cubes allumés, éteignant au final 8 cubes :

- ``10,10,10``
- ``10,10,11``
- ``10,11,10``
- ``10,11,11``
- ``11,10,10``
- ``11,10,11``
- ``11,11,10``
- ``11,11,11``

L'étape finale (``on x=10..10,y=10..10,z=10..10``) *allume* un seul cube, ``10,10,10``. Après cette dernière étape, *`39`* cubes sont *allumés*.

La procédure d'initialisation nm'utilise que les cubes ayant leurs positions `x`, `y` et `z` d'au moins `-50` et d'au plus `50`. Pour le moment, ignorez les cubes hors de cette région.

Voici un plus grand exemple :

```rebootSteps
on x=-20..26,y=-36..17,z=-47..7
on x=-20..33,y=-21..23,z=-26..28
on x=-22..28,y=-29..23,z=-38..16
on x=-46..7,y=-6..46,z=-50..-1
on x=-49..1,y=-3..46,z=-24..28
on x=2..47,y=-22..22,z=-23..27
on x=-27..23,y=-28..26,z=-21..29
on x=-39..5,y=-6..47,z=-3..44
on x=-30..21,y=-8..43,z=-13..34
on x=-22..26,y=-27..20,z=-29..19
off x=-48..-32,y=26..41,z=-47..-37
on x=-12..35,y=6..50,z=-50..-2
off x=-48..-32,y=-32..-16,z=-15..-5
on x=-18..26,y=-33..15,z=-7..46
off x=-40..-22,y=-38..-28,z=23..41
on x=-16..35,y=-41..10,z=-47..6
off x=-32..-23,y=11..30,z=-14..3
on x=-49..-5,y=-3..45,z=-29..18
off x=18..30,y=-20..-8,z=-3..13
on x=-41..9,y=-7..43,z=-33..15
on x=-54112..-39298,y=-85059..-49293,z=-27449..7877
on x=967..23432,y=45373..81175,z=27513..53682
```

Les deux dernières étapes sont complètement hors de la zone de la procédure d'initialisation ; toutes les autres étapes sont complètement à l'intérieur de cette même zone. Après avoir exécuté les étapes dans la zone de la procédure d'initialisation, *`590784`* cubes sont *allumés*.

Exécutez les étapes de redémarrage. Après coup, en ne prenant en compte que les cubes de la région ``x=-50..50,y=-50..50,z=-50..50``, *combien de cubes sont allumés ?*
