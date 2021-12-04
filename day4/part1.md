# --- Jour 4 : Calamar Géant ---

Vous êtes déjà à une profondeur d'1.5km (presque un mile) sous la surface de l'océan, si profond que vous ne pouvez déjà plus apercevoir la lumière du jour. Se que vous *pouvez* voir, en revanche, c'est un calamar géant qui s'est attaché sur le bord de votre sous-marin.

Peut-être qu'il veut jouer au [bingo](https://fr.wikipedia.org/wiki/Bingo) ?

Le bingo est joué sur un ensemble de plateaux consistants en des grilles 5x5 de nombres. Les nombres sont ensuite tirés aléatoirement, et chaque nombre tiré est *marqué* sur toutes les planches sur lequel il apparaît (tous les nombres n'apparaissent pas forcément sur toutes les grilles). Si tous les nombres d'une colonne ou d'une grille sont marqués, la grille concernée *gagne* (les diagonales ne comptent pas).

Le sous-marin possède un *sous-système de bingo* pour aider les passagers (actuellement, vous et le calamar géant) à passer le temps. Il génère automatiquement un ordre aléatoire dans lequel tirer les nombres et un ensemble aléatoire de grilles (l'entrée de votre puzzle). Par exemple :

```bingo_with_input
7,4,9,5,11,17,23,2,0,14,21,24,10,16,13,6,15,25,12,22,18,20,8,19,3,26,1

22 13 17 11  0
 8  2 23  4 24
21  9 14 16  7
 6 10  3 18  5
 1 12 20 15 19

 3 15  0  2 22
 9 18 13 17  5
19  8  7 25 23
20 11 10 24  4
14 21 16 12  6

14 21 17 24  4
10 16 15  9 19
18  8 23 26 20
22 11 13  6  5
 2  0 12  3  7
```

Après que les cinq premiers nombres aient été tirés (`7`, `4`, `9`, `5`, et `11`), il n'y a pas de gagnant ; mais les grilles sont marquées comme ceci (représentées ici côte-à-côte pour gagner de la place) :

<pre><code>22 13 17 <em>11</em>  0         3 15  0  2 22        14 21 17 24  <em>4</em>
 8  2 23  <em>4</em> 24         <em>9</em> 18 13 17  <em>5</em>        10 16 15  <em>9</em> 19
21  <em>9</em> 14 16  <em>7</em>        19  8  <em>7</em> 25 23        18  8 23 26 20
 6 10  3 18  <em>5</em>        20 <em>11</em> 10 24  <em>4</em>        22 <emm>11</em> 13  6  <em>5</em>
 1 12 20 15 19        14 21 16 12  6         2  0 12  3  <em>7</em></code></pre>

Après que les six nombres suivants aient été tirés (`17`, `23`, `2`, `0`, `14` et `21`), il n'y a toujours pas de gagnant :

<pre><code>22 13 <em>17</em> <em>11</em>  <em>0</em>         3 15  <em>0</em>  <em>2</em> 22        <em>14</em> <em>21</em> <em>17</em> 24  <em>4</em>
 8  <em>2</em> <em>23</em>  <em>4</em> 24         <em>9</em> 18 13 <em>17</em>  <em>5</em>        10 16 15  <em>9</em> 19
<em>21</em>  <em>9</em> <em>14</em> 16  <em>7</em>        19  8  <em>7</em> 25 <em>23</em>        18  8 <em>23</em> 26 20
 6 10  3 18  <em>5</em>        20 <em>11</em> 10 24  <em>4</em>        22 <emm>11</em> 13  6  <em>5</em>
 1 12 20 15 19        <em>14</em> <em>21</em> 16 12  6         <em>2</em>  <em>0</em> 12  3  <em>7</em></code></pre>

Enfin, `24` est tiré :

<pre><code>22 13 <em>17</em> <em>11</em>  <em>0</em>         3 15  <em>0</em>  <em>2</em> 22        <em>14</em> <em>21</em> <em>17</em> <em>24</em>  <em>4</em>
 8  <em>2</em> <em>23</em>  <em>4</em> <em>24</em>         <em>9</em> 18 13 <em>17</em>  <em>5</em>        10 16 15  <em>9</em> 19
<em>21</em>  <em>9</em> <em>14</em> 16  <em>7</em>        19  8  <em>7</em> 25 <em>23</em>        18  8 <em>23</em> 26 20
 6 10  3 18  <em>5</em>        20 <em>11</em> 10 <em>24</em>  <em>4</em>        22 <emm>11</em> 13  6  <em>5</em>
 1 12 20 15 19        <em>14</em> <em>21</em> 16 12  6         <em>2</em>  <em>0</em> 12  3  <em>7</em></code></pre>

À ce moment-là, la troisième grille gagne puisqu'elle a au moins une ligne ou colonne complètement marquée (dans ce cas, la totalité de la première ligne en haut est marquée : *``14 21 17 24 4``*).

Le *score* de la grille gagnante peut maintenant être calculé, en commençant par par trouver la *somme de tous les nombres non-marqués* Dans ce cas, la somme est de `188`. Ensuite, multipliez cette somme par *le nombre venant tout juste d'être tiré* quand la grille a gagné, `24` ici, pour obtenir le score final, ici <pre><code>188 * 24 = <em>4512</em></code></pre>.

Pour garantir votre victoire contre le calamar géant, devinez quelle grille gagnera en premier. *Quel sera votre score final si vous choisissez cette grille ?*
