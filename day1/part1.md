# --- Jour 1 : Balayage Sonar ---

Vous vous vaquez tranquillement à vos occupations à bord d'un bateau sur la mer, quand soudain l'arma d'homme-à-la-mer retentit ! Vous accourez pour voir si vous pouvez aider. Apparemment, l'un des elfes a trébuché et a accidentellement envoyé voler les clefs du traîneau dans l'océan !

Avant même que vous ne vous en rendiez compte, vous êtes à l'intérieur d'un sous-marin que les elfes gardent prêtes pour ce genre de situations. Il est couvert de loupiottes de Noël (parce que bien sûr qu'il l'est), et est même équipé d'une antenne expérimentale qui devrait être capable de pister les clefs si vous pouvez augmenter assez fort la puissance de son signal. Il y a une petite jauge qui indique la force du signal de l'antenne en affichant de `0` à `50` **étoiles**.

Votre instinct vous dit que pour sauver Noël, vous devrez réunir toutes les **cinquante étoiles** avant le 25 Décembre.

Collectez des étoiles en résolvant des puzzles. Deux puzzles seront rendus disponibles chaque jour du calendrier de l'Avent ; le second puzzle est débloqué lorsque vous résolvez le premier. Chaque puzzle rapporte **une étoile**. Bonne chance !

Alors que le sous-marin descends en-dessous de la surface de l'océan, il démarre automatiquement un balayage sonar du plancher océanique proche. Sur un petit écran, le rapport de balayage sonar (l'entrée de votre puzzle) apparaît : chaque ligne est une mesure de la profondeur du plancher océanique,  alors que le balayage s'éloigne de plus en plus du sous-marin.

Par exemple, si vous aviez le rapport suivant :

```int
199
200
208
210
200
207
240
269
260
263
```

Ce rapport indique que, en regardant vers l'extérieur du sous-marin, le balayage sonar a trouvé des profondeurs de ``199``, ``200``, ``208``, ``210``, etc.

Votre première priorité est de trouver à quelle vitesse augmente la profondeur, histoire que vous sachiez à quoi vous avez affaire - On ne sais jamais si les clefs ne vont pas être emportées par un courant océanique, ou un poisson, ou n'importe quoi.

À cette fin, comptez *le nombre de fois que la mesure de profondeur augmente* par rapport à la mesure précédent (Il n'y a aucune mesure avant la première mesure). Dans l'exemple ci-dessus, les changements sont comme suit :

<pre><code>199 (N/A - pas de mesure précédente)
200 (<em>augmentée</em>)
208 (<em>augmentée</em>)
210 (<em>augmentée</em>)
200 (baissée)
207 (<em>augmentée</em>)
240 (<em>augmentée</em>)
269 (<em>augmentée</em>)
260 (baissée)
263 (<em>augmentée</em>)</code></pre>

Dans cet exemple, il y a *``7``* mesures plus grandes que la mesure précédente.

*Combien de mesures sont plus grandes que la mesure précédente ?*
