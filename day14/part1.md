# --- Jour 14 : Polymérisation étendue ---

L'immense pression à cette profondeur commence à peser lourdement sur votre sous-marin. Le sous-marin possède un équipement de [Polymérisation](https://fr.wikipedia.org/wiki/Polym%C3%A9risation) capable de produire des matériaux pouvant renforcer le sous-marin, et les cavernes volcaniquement actives alentours devraient vous apporter les éléments en entrée en quantités suffisantes.

Le manuel du sous-marin contient des instructions pour trouver la formule de polymère optimale. Pour être exact, il offre un *patron de polymère* et une liste de règle d'*insertion dans des paires* (l'entrée de votre puzzle). Vous avez simplement besoin de trouver quel polymère résultera de la répétition du processus d'insertion plusieurs fois.

Par exemple :

```polymerization
NNCB

CH -> B
HH -> N
CB -> H
NH -> C
HB -> C
HC -> B
HN -> C
NN -> C
BH -> H
NC -> B
NB -> B
BN -> B
BB -> N
BC -> B
CC -> N
CN -> C
```

La première ligne est le *patron de polymère* - il s'agit du point de départ du procédé.

La section suivante définit les règles d'*insertion dans les paires*. Une règle comme ``AB -> C`` signifie que quand des éléments `A` et`B` sont directement adjacents, un élément `C` doit être inséré entre eux. Les insertions se déroulent toutes simultanément.

Ainsi, en partant du patron de polymère ``NNCB``, le premier pas traite simultanément les trois paires :

- La première paire (``NN``) correspond à la règle ``NN -> C``, l'élément *`C`* est inséré entre le premier `N` et le deuxième `N`.
- La première paire (``NC``) correspond à la règle ``NC -> B``, l'élément *`B`* est inséré entre l'élément `N` et l'élément `C`.
- La première paire (``CB``) correspond à la règle ``CB -> H``, l'élément *`H`* est inséré entre l'élément `C` et l'élément `B`.

Notez que les paires se superposent : le deuxième élément d'une paire est le premier élément de la paire suivante. De plus, puisque toutes les paires sont traitées simultanément, les éléments insérés ne sont pas considérés comme faisant partie d'une paire jusqu'à l'étape suivante.

Après le premier tour de ce processus, le polymère devient <pre><code>N<em>C</em>N<em>B</em>C<em>H</em>B</code></pre>.

Voici les résultats pour quelques étapes en utilisant les règles ci-dessus :

```polymerization-results
Template:     NNCB
After step 1: NCNBCHB
After step 2: NBCCNBBBCBHCB
After step 3: NBBBCNCCNBBNBNBBCHBHHBCHB
After step 4: NBBNBNBBCCNBCNCCNBBNBBNBBBNBBNBBCBHCBHHNHCBBCBHCB
```

Ce polymère grandit rapidement. Après l'étape `5`, il possède `97` éléments ; après l'étape `10`, il possède `3073` éléments. Après l'étape `10`, `B` y est présent `1749` fois, `C` y est présent `298` fois, `H` y est présent `161` fois et `N` y est présent `865` fois ; prendre la quantité de l'élément le plus commun (`B`, `1749`) et y soustraire la quantité de l'élément le moins commun (`H`, `161`) produit <pre><code>1749 - 161 = <em>1588</em></code></pre>.

Appliquez 10 étapes d'insertions dans le patron de polymère et trouvez les élément le plus et le moins communs dans le résultat. *Qu'obtenez-vous si vous prenez la quantité de l'élément le plus commun et que vous y soustrayez la quantité de l'élément le moins commun ?*
