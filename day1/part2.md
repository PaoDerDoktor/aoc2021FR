# --- Partie Deux ---

Au final, prendre en compte toutes les mesures n'est pas aussi utile que ce que vous pensiez : il y a simplement trop de bruit dans les données.

À la place, prenez en compte les sommes de *fenêtres de trois mesures glissantes* . Une fois encore, en prenant le même exemple :

```int
199  A      
200  A B    
208  A B C  
210    B C D
200  E   C D
207  E F   D
240  E F G  
269    F G H
260      G H
263        H
```

Commençons par comparer la première et la deuxième fenêtre de trois mesures. Les mesures dans la première fenêtre sont marquées `A` (``199``, ``200``, ``208``) ; leur somme est ``199 + 200 + 208 = 607``. La deuxième fenêtre est marquée `B` (``200``, ``208``, ``210``) ; sa somme est de ``618``. La somme des mesures de la deuxième fenêtre est plus grande que la somme de la première, donc la première comparaison a *augmenté*.

Votre but est maintenant de *compter le nombre de fois que la somme des mesures dans une fenêtre augmente* par rapport à la fenêtre précédente. Ainsi, comparez `A` avec `B`, `B` avec `C`, `C`avec `D`, et ainsi de suite. Arrêtez quand il n'y a plus assez de mesures pour créer une nouvelle fenêtre de trois mesures.

Dans l'exemple ci-dessous, la somme de chaque fenêtre de trois mesures sont :

<pre><code>A: 607 (N/A - pas de somme précédente)
B: 618 (<em>augmentée</em>)
C: 618 (pas de changement)
D: 617 (baissée)
E: 647 (<em>augmentée</em>)
F: 716 (<em>augmentée</em>)
G: 769 (<em>augmentée</em>)
H: 792 (<em>augmentée</em>)</code></pre>

Dans cet exemple, il y a *`5`* sommes plus grande que la somme précédente.

Considérez les sommes de fenêtres de trois mesures glissantes. *Combien de sommes sont plus grandes que la somme précédente ?*
