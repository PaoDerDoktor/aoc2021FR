# --- Jour 12 : Chercher un passage ---

Puisque les sous-systèmes sous-terrains de votre sous-marin fonctionnent de manière sous-optimale, la seule manière pour vous de sortir de ces cavernes est de trouver un chemin par vous-même. Pas seulement *un* chemin - la seule façon de savoir si vous avez trouvé le *meilleur* chemin est de *tous* les trouver.

Heureusement, la plupart des senseurs marchent encore, vous créez donc une grossière carte des cavernes restantes (l'entrée de votre puzzle). Par exemple:

```caveMap
start-A
start-b
A-c
A-b
b-d
A-end
b-end
```

Ceci est une liste représentant les connexions des grottes. Vous démarrez dans une grotte nommée `start`, et votre destination est une grotte nommée `end`. Une ligne ``b-d`` signifie que la grotte `b` communique avec la grotte `d` - vous pouvez vous déplacer de l'une à l'autre.

Du coup, le système ci-dessus ressemble grossièrement à ça :

```caveGraph
    start
    /   \
c--A-----b--d
    \   /
     end
```

Votre but est de trouver le nombre de *chemins* distincts démarrant à `start`, se terminant à `end`, et ne visitant pas la même petite grotte plus d'une fois. Il y a deux types de grottes les *grandes* grottes (écrite en majuscules, comme `A`) et les *petites* grottes (écrites en minuscules, comme `b`). Visiter une petite grotte deux fois serait une perte de temps, mais les grandes grottes sont assez vastes pour que les visiter plusieurs fois vaille le coup. Alors, tous les chemins que vous trouverez devraient *passer par les petites grottes une fois au maximum*, et peut *visiter les grandes grottes autant que nécessaire.*

Avec ces règles, il y a *`10`* chemins à travers cet exemple de système de grottes :

```csv
start,A,b,A,c,A,end
start,A,b,A,end
start,A,b,end
start,A,c,A,b,A,end
start,A,c,A,b,end
start,A,c,A,end
start,A,end
start,b,A,c,A,end
start,b,A,end
start,b,end
```

(Chaque ligne de la liste ci-dessus correspond à un eul chemin, les grottes par lesquelles passent ce chemin sont listées dans l'ordre où elles sont visitées et séparées par des virgules)


Notez que dans ce système de grottes, la grotte `d` n'est jamais visitée par aucun chemin : pour ce faire, il faudrait passer deux fois par la grotte `b` (une fois en allant vers `d` et une autre fois en repartant de `d`), et puisque la grotte `b` est petite, ce n'est pas autorisé.

Voici un exemple un peu plus grand :

```caveMap
dc-end
HN-start
start-kj
dc-start
dc-HN
LN-dc
HN-end
kj-sa
kj-HN
kj-dc
```

Il y a `19` chemins le traversant, ceux-ci :

```csv
start,HN,dc,HN,end
start,HN,dc,HN,kj,HN,end
start,HN,dc,end
start,HN,dc,kj,HN,end
start,HN,end
start,HN,kj,HN,dc,HN,end
start,HN,kj,HN,dc,end
start,HN,kj,HN,end
start,HN,kj,dc,HN,end
start,HN,kj,dc,end
start,dc,HN,end
start,dc,HN,kj,HN,end
start,dc,end
start,dc,kj,HN,end
start,kj,HN,dc,HN,end
start,kj,HN,dc,end
start,kj,HN,end
start,kj,dc,HN,end
start,kj,dc,end
```

Enfin, voici un exemple encore plus gros avec `226` chemins le traversant :

```caveMap
fs-end
he-DX
fs-he
start-DX
pj-DX
end-zg
zg-sl
zg-pj
pj-he
RW-he
fs-DX
pj-RW
zg-RW
start-pj
he-WI
zg-he
pj-fs
start-RW
```

*Combien de chemins traversant le système de grottes et ne passant pas plus d'une fois par chaque petite grotte existent-ils ?*
