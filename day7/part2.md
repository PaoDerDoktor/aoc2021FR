# --- Partie Deux ---

Les crabes ne semblent pas interessés par votre solution. Peut-être que vous avez mal compris l'ingénierie crabe ?

En fait, les moteurs des sous-marins crabes ne consomment pas de carburant à vitesse constante. À la place, chaque mouvement de 1 unité de position horizontale  coûte une unité de carburant supplémentaire par rapport au précédent : le premier mouvement en coûte `1`, le deuxième en coûte `2`, le troisième en coûte `3`, etc.

À mesure que les crabes se déplacent, se déplacer encore plus devient de plus en plus cher. Ceci modifie la position d'alignement optimale : sur l'exemple ci-desssus, elle devient `5`:

- Mouvement de `16` à `5` : `66` unités de carburant
- Mouvement de `1` à `5` : `10` unités de carburant
- Mouvement de `2` à `5` : `6` unités de carburant
- Mouvement de `0` à `5` : `15` unités de carburant
- Mouvement de `4` à `5` : `1` unités de carburant
- Mouvement de `2` à `5` : `6` unités de carburant
- Mouvement de `7` à `5` : `3` unités de carburant
- Mouvement de `1` à `5` : `10` unités de carburant
- Mouvement de `2` à `5` : `6` unités de carburant
- Mouvement de `14` à `5` : `45` unités de carburant

Ceci coûte un total de *`168`* unités de carburant. Ceci est donc la nouvelle meilleure issue, l'ancienne (`2`) coûtant désormais `206` unités de carburant.

Déterminez la position horizontale sur laquelle les crabes peuvent s'aligner en utilisant le moins de carburant possible pour que vous puissiez trouver une issue de secours ! *Combien d'unités de carburant doivent-ils utiliser pour s'aligner sur cette position ?*
