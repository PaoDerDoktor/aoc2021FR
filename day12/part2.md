# --- Partie Deux ---

Après avoir revu tous les chemins disponibles, vous réalisez que vous avez peut-être le temps de passer par une seule petite caverne *deux fois*. En d'autres mots, les grandes grottes peuvent être visitées autant de fois que nécessaire, une seule petite grotte peut être visitée deux fois, et toutes les autres petites grottes ne peuvent être visitées qu'une seule fois au maximum. Cependant, les grottes nommées `start` et `end` ne peuvent qu'être visitées *exactement une fois chacune* : une fois que vous quittez la grotte de départ, vous ne pouvez plus y retourner ; et une fois que vous atteignez la grotte `end`, le chemin se termine immédiatement.

À présent, les `36` chemins possibles du premier exemple sont :

```csv
start,A,b,A,b,A,c,A,end
start,A,b,A,b,A,end
start,A,b,A,b,end
start,A,b,A,c,A,b,A,end
start,A,b,A,c,A,b,end
start,A,b,A,c,A,c,A,end
start,A,b,A,c,A,end
start,A,b,A,end
start,A,b,d,b,A,c,A,end
start,A,b,d,b,A,end
start,A,b,d,b,end
start,A,b,end
start,A,c,A,b,A,b,A,end
start,A,c,A,b,A,b,end
start,A,c,A,b,A,c,A,end
start,A,c,A,b,A,end
start,A,c,A,b,d,b,A,end
start,A,c,A,b,d,b,end
start,A,c,A,b,end
start,A,c,A,c,A,b,A,end
start,A,c,A,c,A,b,end
start,A,c,A,c,A,end
start,A,c,A,end
start,A,end
start,b,A,b,A,c,A,end
start,b,A,b,A,end
start,b,A,b,end
start,b,A,c,A,b,A,end
start,b,A,c,A,b,end
start,b,A,c,A,c,A,end
start,b,A,c,A,end
start,b,A,end
start,b,d,b,A,c,A,end
start,b,d,b,A,end
start,b,d,b,end
start,b,end
```

L'exemple un peu plus gros ci-dessus est maintenant traversé par `103` chemins, alors que l'exemple plus gros encore est maintenant traversé par `3509` chemins.

Étant données ces nouvelles règles, *combien y-a-t'il de chemins traversant le système de grottes ?*
