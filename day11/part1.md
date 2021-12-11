# --- Jour 11 : Pieuvre Dumbo ---

Vous entrez dans une caverne pleine de [Pieuvre Dumbo](https://fr.wikipedia.org/wiki/Grimpoteuthis) bioluminescents rares ! Ils ne semblent pas apprécier les loupiotes de Noël de votre sous-marin, vous les éteignez donc pour le moment.

Il y a 100 pieuvres réparties équitablement dans une grille de 10 par 10. Chaque pieuvre gagne doucement de l'*énergie* au fil du temps et *flash* vivement pendant un instant quand son énergie est pleine. Bien que vos lumières soient éteintes, vous pourriez peut-être naviguer à travers la caverne sans déranger les pieuvres si vous prédisiez les moments où les flash arrivaient.

Chaque pieuvre a un *niveau d'énergie*. Votre sous-marin peut mesurer à distance le niveau d'énergie de chaque pieuvre (l'entrée de votre puzzle). Par exemple :

```dumboocctopus
5483143223
2745854711
5264556173
6141336146
6357385478
4167524645
2176841721
6882881134
4846848554
5283751526
```

Le niveau d'énergie de chaque pieuvre est une valeur entre `0` et `9`. Ici, la pieuvre dans le coin supérieur-gauche a un niveau d'énergie de `5`, celle dans le coin inférieur-droit a un niveau d'énergie de 6, et ainsi de suite.

Vous pouvez modéliser les niveaux d'énergie et les flashs de lumière en *pas*. Pendant un pas, tout ceci se produit :

- D'abord, le niveau d'énergie de chaque pieuvre est incrémenté de `1`.
- Ensuite, toutes pieuvre avec un niveau d'énergie plus grand que `9` *flash*. Ceci augmente l'énergie de chaque pieuvre adjacente d'`1`, incluant les pieuvres  adjacentes diagonalement. Si cette augmentation conduit une pieuvre a avoir un niveau d'énergie supérieur à `9`, elle *flash également*. Ce processus se poursuit tant que de nouvelles pieuvres voient leur niveau d'énergie augmenter au-delà de `9` (une pieuvre peut flasher *une fois par pas au maximum*).
- Enfin, toute pieuvre ayant flashé pendant ce pas voit son niveau d'énergie passer à `0`, puisqu'elle a utilisé toute son énergie pour flasher.

Les flash adjacents peuvent conduire une pieuvre à flasher pendant un pas où elle a commencé avec très peu d'énergie. par exemple, étudions le cas de la pieuvre du milieu commençant avec `1` d'énergie dans cette situation :

<pre><code>Avant le premier pas:
11111
19991
19191
19991
11111

Après le 1er pas:
34543
4<em>000</em>4
5<em>000</em>5
4<em>000</em>4
34543

Après le 2ème pas:
45654
51115
61116
51115
45654</code></pre>

Une pieuvre est *mise en évidence* lorsqu'elle a flashé durant le pas donné.

Voici la progression du plus grand exemple :

<pre><code>Avant le premier pas:
5483143223
2745854711
5264556173
6141336146
6357385478
4167524645
2176841721
6882881134
4846848554
5283751526

Après le 1er pas:
6594254334
3856965822
6375667284
7252447257
7468496589
5278635756
3287952832
7993992245
5957959665
6394862637

Après le 2ème pas :
88<em>0</em>7476555
5<em>0</em>89<em>0</em>87<em>0</em>54
85978896<em>0</em>8
84857696<em>0</em><em>0</em>
87<em>0</em><em>0</em>9<em>0</em>88<em>0</em><em>0</em>
66<em>0</em><em>0</em><em>0</em>88989
68<em>0</em><em>0</em><em>0</em><em>0</em>5943
<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>7456
9<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>876
87<em>0</em><em>0</em><em>0</em><em>0</em>6848

Après le 3ème pas :
<em>0</em><em>0</em>5<em>0</em>9<em>0</em><em>0</em>866
85<em>0</em><em>0</em>8<em>0</em><em>0</em>575
99<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>39
97<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>41
9935<em>0</em>8<em>0</em><em>0</em>63
77123<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>
791125<em>0</em><em>0</em><em>0</em>9
221113<em>0</em><em>0</em><em>0</em><em>0</em>
<em>0</em>421125<em>0</em><em>0</em><em>0</em>
<em>0</em><em>0</em>21119<em>0</em><em>0</em><em>0</em>

Après le 4ème pas :
2263<em>0</em>31977
<em>0</em>923<em>0</em>31697
<em>0</em><em>0</em>3222115<em>0</em>
<em>0</em><em>0</em>41111163
<em>0</em><em>0</em>76191174
<em>0</em><em>0</em>53411122
<em>0</em><em>0</em>4236112<em>0</em>
5532241122
1532247211
113223<em>0</em>211

Après le 5ème pas :
4484144<em>0</em><em>0</em><em>0</em>
2<em>0</em>44144<em>0</em><em>0</em><em>0</em>
2253333493
1152333274
11873<em>0</em>3285
1164633233
1153472231
6643352233
2643358322
2243341322

Après le 6ème pas :
5595255111
3155255222
33644446<em>0</em>5
2263444496
2298414396
2275744344
2264583342
7754463344
3754469433
3354452433

Après le 7ème pas :
67<em>0</em>7366222
4377366333
4475555827
34966557<em>0</em>9
35<em>0</em><em>0</em>6256<em>0</em>9
35<em>0</em>9955566
3486694453
8865585555
486558<em>0</em>644
4465574644

Après le 8ème pas :
7818477333
5488477444
5697666949
46<em>0</em>876683<em>0</em>
473494673<em>0</em>
474<em>0</em><em>0</em>97688
69<em>0</em><em>0</em><em>0</em><em>0</em>7564
<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>9666
8<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>4755
68<em>0</em><em>0</em><em>0</em><em>0</em>7755

Après le 9ème pas :
9<em>0</em>6<em>0</em><em>0</em><em>0</em><em>0</em>644
78<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>976
69<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>8<em>0</em>
584<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>82
5858<em>0</em><em>0</em><em>0</em><em>0</em>93
69624<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>
8<em>0</em>2125<em>0</em><em>0</em><em>0</em>9
222113<em>0</em><em>0</em><em>0</em>9
9111128<em>0</em>97
7911119976

Après le 10ème pas :
<em>0</em>481112976
<em>0</em><em>0</em>31112<em>0</em><em>0</em>9
<em>0</em><em>0</em>411125<em>0</em>4
<em>0</em><em>0</em>811114<em>0</em>6
<em>0</em><em>0</em>991113<em>0</em>6
<em>0</em><em>0</em>93511233
<em>0</em>44236113<em>0</em>
553225235<em>0</em>
<em>0</em>53225<em>0</em>6<em>0</em><em>0</em>
<em>0</em><em>0</em>3224<em>0</em><em>0</em><em>0</em><em>0</em></code></pre>

Après le 10ème pas se seront produits un total de `204` flashs. En avançant plus rapidement, voici la même configurations tous les 10 pas :

<pre><code>Après le 20ème pas:
3936556452
56865568<em>0</em>6
449655569<em>0</em>
444865558<em>0</em>
445686557<em>0</em>
568<em>0</em><em>0</em>86577
7<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>9896
<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>344
6<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>364
46<em>0</em><em>0</em><em>0</em><em>0</em>9543

Après le 30ème pas:
<em>0</em>643334118
4253334611
3374333458
2225333337
2229333338
2276733333
2754574565
5544458511
9444447111
7944446119

Après le 40ème pas:
6211111981
<em>0</em>421111119
<em>0</em><em>0</em>42111115
<em>0</em><em>0</em><em>0</em>3111115
<em>0</em><em>0</em><em>0</em>3111116
<em>0</em><em>0</em>65611111
<em>0</em>532351111
3322234597
2222222976
2222222762

Après le 50ème pas:
9655556447
48655568<em>0</em>5
448655569<em>0</em>
445865558<em>0</em>
457486557<em>0</em>
57<em>0</em><em>0</em><em>0</em>86566
6<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>9887
8<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>533
68<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>633
568<em>0</em><em>0</em><em>0</em><em>0</em>538

Après le 60ème pas:
25333342<em>0</em><em>0</em>
274333464<em>0</em>
2264333458
2225333337
2225333338
2287833333
3854573455
1854458611
1175447111
1115446111

Après le 70ème pas:
8211111164
<em>0</em>421111166
<em>0</em><em>0</em>42111114
<em>0</em><em>0</em><em>0</em>4211115
<em>0</em><em>0</em><em>0</em><em>0</em>211116
<em>0</em><em>0</em>65611111
<em>0</em>532351111
7322235117
5722223475
4572222754

Après le 80ème pas:
1755555697
59655556<em>0</em>9
448655568<em>0</em>
445865558<em>0</em>
457<em>0</em>86557<em>0</em>
57<em>0</em><em>0</em><em>0</em>86566
7<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>8666
<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>99<em>0</em>
<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>8<em>0</em><em>0</em>
<em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em><em>0</em>

Après le 90ème pas:
7433333522
2643333522
2264333458
2226433337
2222433338
2287833333
2854573333
4854458333
3387779333
3333333333

Après le 100ème pas:
<em>0</em>397666866
<em>0</em>749766918
<em>0</em><em>0</em>53976933
<em>0</em><em>0</em><em>0</em>4297822
<em>0</em><em>0</em><em>0</em>4229892
<em>0</em><em>0</em>53222877
<em>0</em>532222966
9322228966
7922286866
6789998766</code></pre>

Après 100 pas se seront produits un total de ``1656`` flash.

Étant donnés les niveaux d'énergie de chaque pieuvre dumbo de votre caverne au démarrage, simulez 100 pas. *Combien de flash se seront produits après 100 pas ?*
