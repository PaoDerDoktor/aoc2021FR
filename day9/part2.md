# --- Partie Deux ---

Ensuite, vous allez devoir trouver les plus grands bassins afin de savoir quelles zones éviter en priorité.

Un *bassin* est l'ensemble de tous les droits tombant finalement dans un seul point bas. Ainsi, chaque point bas possède un bassin, même si certains sont tès petits. Les endroits avec une hauteur de `9``  ne sont pas comptés comme étant dans un bassin, et tous les autres endroits feront toujours partie d'exactement un seul bassin.

La *taille* d'un bassin est le nombre d'endroits dans le bassin, incluant le point bas. L'exemple ci-dessus possède quatre bassins.

Le bassin en supérieur-gauche, d'une taille de `3` :

<pre><code><em>21</em>99943210
<em>3</em>987894921
9856789892
8767896789
9899965678</code></pre>

Le bassin supérieur-droit, d'une taille de `9` :

<pre><code>21999<em>43210</em>
398789<em>4</em>9<em>21</em>
985678989<em>2</em>
8767896789
9899965678</code></pre>

Le bassin du milieu, d'une taille de `14` :

<pre><code>2199943210
39<em>878</em>94921
9<em>85678</em>9892
<em>87678</em>96789
9<em>8</em>99965678</code></pre>

Le bassin inférieur-droit, d'une taille de `9` :

<pre><code>2199943210
3987894921
9856789<em>8</em>92
876789<em>678</em>9
98999<em>65678</em></code></pre>

Trouvez les trois plus grands bassins et multipliez leur tailles ensemble. Dans l'exemple ci-dessus, on trouve <pre><code>9 * 14 * 9 = <em>1134</em></code></pre>.

*Que trouvez-vous si vous multipliez ensemble les tailles de chacun des trois plus grands bassins ?*
