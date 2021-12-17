# --- Partie Deux ---

Maintenant que vous avez décodé la structure de votre transmission, vous pouvez calculer la valeur de l'expression qu'elle représente.

Les valeurs littérales (identifiant de type `4`) représentent un seul nombre, comme décrit plus haut. Les autres identifiants de types sont plus intéressants :

- Les paquets avec un identifiant de type `0` sont des paquets *somme* - leur valeur est la somme des valeurs de leurs sous-paquets. S'ils n'ont qu'un sous-paquet, leur valeur est la valeur de leur sous-paquet.
- Les paquets avec un identifiant de type `1` sont des paquets *produit* - leur valeur est le produit des valeurs de leurs sous-paquets. S'ils n'ont qu'un sous-paquet, leur valeur est la valeur de leur sous-paquet.
- Les paquets avec un identifiant de type `2` sont des paquets *minimum* - leur valeur est le minimum des valeurs de leurs sous-paquets.
- Les paquets avec un identifiant de type `3` sont des paquets *maximum* - leur valeur est le maximum des valeurs de leurs sous-paquets.
- Les paquets avec un identifiant de type `5` sont des paquets *plus-grand-que* - leur valeur est de *1* si la valeur du premier sous-paquet est plus grande que la valeur de leur second sous-paquet ; sinon leur valeur est de *0*. Ces paquets ont toujours exactement deux sous-paquets.
- Les paquets avec un identifiant de type `6` sont des paquets *plus-petit-que* - leur valeur est de *1* si la valeur du premier sous-paquet est plus petite que la valeur de leur second sous-paquet ; sinon leur valeur est de *0*. Ces paquets ont toujours exactement deux sous-paquets.
- Les paquets avec un identifiant de type `7` sont des paquets *égal-à* - leur valeur est de *1* si la valeur du premier sous-paquet est égale à la valeur de leur second sous-paquet ; sinon leur valeur est de *0*. Ces paquets ont toujours exactement deux sous-paquets.

En utilisant ces règles, vous pouvez maintenant trouver la valeur du paquet le plus extérieur de votre transmission BITS.

par exemple :

- `C200B40A82` trouve la somme de `1` et `2`, résultant en la valeur *`3`*.
- `04005AC33890` trouve le produit de `6` et `9`, résultant en la valeur *`54`*.
- `880086C3E88112` trouve le minimum de `7`, `8` et `9`, résultant en la valeur *`7`*.
- `CE00C43D881120` trouve le maximum de `7`, `8` et `9`, résultant en la valeur *`9`*.
- `D8005AC2A8F0` donne *`1`*, puisque `5` est inférieur à `15`.
- `F600BC2D8F` donne *`0`*, puisque `5` n'est pas supérieur à `15`.
- `9C005AC2F8F0` donne *`0`*, puisque `5` n'est pas égal à `15`.
- `9C0141080250320F1802104A08` donne *`1`* , puisque `1` + `3` = `2` * `2`.

*Qu'obtenez-vous si vous évaluez l'expression représentée par votre transmission BITS encodée en hexadécimal ?*
