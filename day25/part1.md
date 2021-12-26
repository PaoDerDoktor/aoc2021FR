# --- Jour 25 : Concombre de Mer ---

Vous y êtes : le fond de la fosse océanique, le dernier endroit où peuvent être les clefs du traîneau. L'antenne expérimentale de votre sous-marin *n'est pas encore assez boostée* pour détecter les clefs, mais elles sont *forcément* ici. Tout ce qu'il vous reste à faire, c'est *atteindre le plancher océanique* et les trouver.

En tout cas, vous toucheriez le plancher océanique si vous pouviez, mais malheureusement, il est complètement recouvert par deux immenses troupeaux de [concombres de mer](https://fr.wikipedia.org/wiki/Holothurie), et il n'y a pas assez d'espace libre assez grand pour votre sous-marin.

Vous soupçonnez les elfes d'avoir déjà fait ça auparavant. puisque vous découvrez le numéro de téléphone d'un biologiste des profondeurs marines sur une note manuscrite scotchée au mur du cockpit du sous-marin.

"Les concombres des mers ? Ouais, ils chassent sûrement de la nourriture. Mais ne vous inquiétez pas, ce sont des créatures prévisibles : ils bougent en lignes parfaitement droites, uniquement quand il y'a l'espace nécessaire devant eux. Ils sont plutôt polis, en fait !"

Vous expliquez que vous aimeriez prévoir où faire atterrir votre sous-marin.

"Oh, c'est facile, ils vont finir par s'entre-bloquer et ils laisseront assez d'espace pour -- attendez, vous avez dit sous-marin ? Et le seul endroit avec autant de concombres des mers à un seul endroit serait au fonde la fosse des Mariannes, j--" vous raccrochez le téléphone.

Il y a deux troupeaux de concombres des mers qui se partagent la même région ; l'un va toujours vers l'*est* (`>`), tandis que l'autre va toujours vers le *sud* (`v`). Chaque emplacement peut contenir au plus un concombre des mers ; les emplacement restants sont *vides* (`.`). Votre sous-marin génère une carte de la situation (l'entrée de votre puzzle). Par exemple :

```cucumbers
v...>>.vv>
.vv>>.vv..
>>.>v>...v
>>v>>.>.v.
v>v.vv.v..
>.>>..v...
.vv..>.>v.
v.v..>>v.v
....v..v.>
```

À chaque *pas*, le troupeaux de concombres des mers faisant face à l'est essaiera de bouger un emplacement en avant. Quand un troupeau avance, tous les concombres des mers vérifient d'abord simultanément si il y a ou non un concombre des mers sur la position juste devant eux dans la direction vers laquelle ils sont tournés (même s'il s'agit d'un concombre des mers faisant face à la même direction que le concombre vérifiant), et chaque concombre ayant remarqué qu'il était devant un espace vide avance en simultané vers cet emplacement.

Ainsi, dans une situation comme celle-ci :

```cucumbers
...>>>>>...
```

Après un pas, seul le concombre le plus à droite se serait déplacé :

```cucumbers
...>>>>.>..
```

Après le pas suivant, deux concombres se seraient déplacés :

```cucumbers
...>>>.>.>.
```

Durant un seul pas, les concombres des mers faisant face à l'est bougent en premier, puis les concombres des mers faisant face au sud se déplacent à leur tour. Ainsi, étant donnée cette situation :

```cucumbers
..........
.>v....v..
.......>..
..........
```

Après un seul pas, de tous les concombres des mers sur la gauche, seul le concombre des mers faisant face au sud s'est déplacé (puisqu'il n'était pas décalé à temps pour que le concombre faisant face à l'est ne se déplace), mais les deux concombres des mers sur la droite ont bougé (puisque le concombre des mers faisant face à l'est s'est décalé du chemin de celui faisant face au sud) :

```cucumbers
..........
.>........
..v....v>.
..........
```

À cause des *forts courants d'eau* dans cette zone, les concombres des mers qui se sortent par la bordure de droite de la carte se retrouvent à la bordure de gauche, et les concombres der mers qui sortent par la bordures du bas réapparaissent à la bordure du haut. Les concombres des mers vérifient toujours si l'espace devant eux est libre, même si cette destination est au côté opposé de la carte :

```cucumbersMulti
État initial:
...>...
.......
......>
v.....>
......>
.......
..vvv..

Après 1 pas:
..vv>..
.......
>......
v.....>
>......
.......
....v..

Après 2 pas:
....v>.
..vv...
.>.....
......>
v>.....
.......
.......

Après 3 pas:
......>
..v.v..
..>v...
>......
..>....
v......
.......

Après 4 pas:
>......
..v....
..>.v..
.>.v...
...>...
.......
v......
```

Pour trouver un endroit sûr où poser votre sous-marin, les concombres des mers doivent s'arrêter de bouger. considérez à nouveau le premier exemple :

```cucumbersMulti
État initial:
v...>>.vv>
.vv>>.vv..
>>.>v>...v
>>v>>.>.v.
v>v.vv.v..
>.>>..v...
.vv..>.>v.
v.v..>>v.v
....v..v.>

Après 1 pas:
....>.>v.>
v.v>.>v.v.
>v>>..>v..
>>v>v>.>.v
.>v.v...v.
v>>.>vvv..
..v...>>..
vv...>>vv.
>.v.v..v.v

Après 2 pas:
>.v.v>>..v
v.v.>>vv..
>v>.>.>.v.
>>v>v.>v>.
.>..v....v
.>v>>.v.v.
v....v>v>.
.vv..>>v..
v>.....vv.

Après 3 pas:
v>v.v>.>v.
v...>>.v.v
>vv>.>v>..
>>v>v.>.v>
..>....v..
.>.>v>v..v
..v..v>vv>
v.v..>>v..
.v>....v..

Après 4 pas:
v>..v.>>..
v.v.>.>.v.
>vv.>>.v>v
>>.>..v>.>
..v>v...v.
..>>.>vv..
>.v.vv>v.v
.....>>vv.
vvv>...v..

Après 5 pas:
vv>...>v>.
v.v.v>.>v.
>.v.>.>.>v
>v>.>..v>>
..v>v.v...
..>.>>vvv.
.>...v>v..
..v.v>>v.v
v.v.>...v.

...

Après 10 pas:
..>..>>vv.
v.....>>.v
..v.v>>>v>
v>.>v.>>>.
..v>v.vv.v
.v.>>>.v..
v.v..>v>..
..v...>v.>
.vv..v>vv.

...

Après 20 pas:
v>.....>>.
>vv>.....v
.>v>v.vv>>
v>>>v.>v.>
....vv>v..
.v.>>>vvv.
..v..>>vv.
v.v...>>.v
..v.....v>

...

Après 30 pas:
.vv.v..>>>
v>...v...>
>.v>.>vv.>
>v>.>.>v.>
.>..v.vv..
..v>..>>v.
....v>..>v
v.v...>vv>
v.v...>vvv

...

Après 40 pas:
>>v>v..v..
..>>v..vv.
..>>>v.>.v
..>>>>vvv>
v.....>...
v.v...>v>>
>vv.....v>
.>v...v.>v
vvv.v..v.>

...

Après 50 pas:
..>>v>vv.v
..v.>>vv..
v.>>v>>v..
..>>>>>vv.
vvv....>vv
..v....>>>
v>.......>
.vv>....v>
.>v.vv.v..

...

Après 55 pas:
..>>v>vv..
..v.>>vv..
..>>v>>vv.
..>>>>>vv.
v......>vv
v>v....>>v
vvv...>..>
>vv.....>.
.>v.vv.v..

Après 56 pas:
..>>v>vv..
..v.>>vv..
..>>v>>vv.
..>>>>>vv.
v......>vv
v>v....>>v
vvv....>.>
>vv......>
.>v.vv.v..

Après 57 pas:
..>>v>vv..
..v.>>vv..
..>>v>>vv.
..>>>>>vv.
v......>vv
v>v....>>v
vvv.....>>
>vv......>
.>v.vv.v..

Après 58 pas:
..>>v>vv..
..v.>>vv..
..>>v>>vv.
..>>>>>vv.
v......>vv
v>v....>>v
vvv.....>>
>vv......>
.>v.vv.v..
```

Dans cet exemple, les concombres des mers se sont arrêté de bouger après *`58`* pas.

Trouvez un endroit sûr où poser votre sous-marin. *Quel est le premier pas au cours duquel aucun concombre des mers ne bouge ?*
