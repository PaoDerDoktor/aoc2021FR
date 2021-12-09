# --- Jour 9 : Bassin de Fumée ---

Ces grottes semblent être constituées de [tunnels de lave](https://fr.wikipedia.org/wiki/Tunnel_de_lave). Certaines parties sont même encore actives au niveau volcanique. De petites cheminées hydrothermales libèrent de la fumée dans les cavernes qui se dépose lentement comme de la pluie.

Si vous pouvez modéliser la façon dont la fumée se déplace à travers les grottes, vous pourriez peut-être l'éviter et être bien plus en sécurité. Le sous-marin génère une carte de la hauteur du plancher océanique des cavernes alentours.

La fumée se déplace vers le point le plus bas de la zone dans laquelle elle se trouve. Par exemple, prenez en compte la carte de hauteur suivante :

<pre><code>2<em>1</em>9994321<em>0</em>
3987894921
98<em>5</em>6789892
8767896789
989996<em>5</em>678</code></pre>

Chaque nombre corresponds à la hauteur d'un endroit, où `9` est au plus haut et `0` au plus bas.

Votre premier objectif est de trouver les *points bas* - les endroits qui sont plus bas que tous ses endroits adjacents. La plupart des endroits ont quatre endroits adjacents (en haut, en bas, à gauche et à droite) ; les endroits sur la bordure ou dans un coin ont respectivement trois et deux endroits adjacents chacun (les diagonales ne comptent pas comme adjacentes).

Dans l'exemple ci-dessus, il y a *quatre* points bas, tous mis en évidence : deux sont sur la première ligne (un `1` et un `0`), un autre est sur la troisième ligne (un `5`) et le dernier est sur la dernière ligne (encore un `5`). Tous les autres endroits sur la carte de hauteur ont des endroits adjacents plus bas, mais ne sont pas des points bas.

Le *niveau de risque* d'un point bas est de *1 additionné à sa hauteur*. Dans l'exemple ci-dessus, les niveaux de risque des points bas sont `2`, `1`, `6` et `6`. La somme des niveaux de risque de tous les points bas de la carte de hauteur est donc *`15`*

Trouvez tous les points bas de la carte de hauteur. *Quelle est la somme des niveaux de risque de tous les points bas de votre carte de hauteur ?*
