# --- Jour 15 : Chiton ---

Vous êtes presque sortis des grottes, mais les murs n'arrêtent pas de se rapprocher. Votre sous-marin peut à peine passer. Le principal problème est que les murs sont couverts de [chitons](https://fr.wikipedia.org/wiki/Polyplacophora), et il serait mieux de ne pas vous cogner dans l'un d'eux.

La grotte est large, mais à un plafond très bas, ce qui vous oblige à ne vous déplacer qu'en deux dimensions. La grotte a une forme carrée; une rapide reconnaissance de la densité de chitons produit une carte du *niveau de risque* à travers la grotte (l'entrée de votre puzzle). Par exemple :

```riskMap
1163751742
1381373672
2136511328
3694931569
7463417111
1319128137
1359912421
3125421639
1293138521
2311944581
```

Vous démarrez dans le coin supérieur-gauche, votre destination est dans le coin inférieur-droit, et vous ne pouvez pas vous déplacer en diagonale. Le nombre en chaque position est son *niveau de risque* ; pour déterminer le risque total d'un chemin entier, additionnez le niveau de risque de chaque position dans laquelle vous *entrez* (c'est-à-dire que vous ne devez pas compter le niveau de risque de la position de départ à moins que vous n'y entriez ultérieurement : la quitter n'ajoute pas de risque au risque total).

Votre but est de trouver un chemin avec *un risque total minimal*. Dans cet exemple, le chemin avec le risque total minimal est mis en évidence ici :

<pre class="riskmap"><code><em>1</em>163751742
<em>1</em>381373672
<em>2136511</em>328
369493<em>15</em>69
7463417<em>1</em>11
1319128<em>13</em>7
13599124<em>2</em>1
31254216<em>3</em>9
12931385<em>21</em>
231194458<em>1</em></code></pre>

Le risque total de ce chemin est de *`40`* (la position de départ n'est jamais entrée, son risque n'est donc pas compté).

*Quel est le risque total le plus bas parmi ceux de chacun des chemins depuis le coin supérieur-gauche et le coin inférieur-droit ?*
