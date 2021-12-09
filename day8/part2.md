# --- Partie Deux ---

Grâce à un peu de déduction, vous devriez maintenant pouvoir détermine les chiffres restants. Considérez à nouveau l'exemple ci-dessus :

```fdd
acedgfb cdfbe gcdfa fbcad dab cefabd cdfgeb eafb cagedb ab |
cdfeb fcadb cdfeb cdbaf
```

Après une analyse minutieuse, l'association entre les signaux des câbles et les segments ne font sens que dans cette configuration :

```fddd
 dddd
e    a
e    a
 ffff
g    b
g    b
 cccc
```

Ainsi, les motifs de signaux uniques correspondraient aux chiffre suivants :

- acedgfb: `8`
- cdfbe: `5`
- gcdfa: `2`
- fbcad: `3`
- dab: `7`
- cefabd: `9`
- cdfgeb: `6`
- eafb: `4`
- cagedb: `0`
- ab: `1`

Ensuite, les quatre chiffres en sortie peuvent être décodés :

- `cdfeb`: `5`
- `fcadb`: `3`
- `cdfeb`: `5`
- `cdbaf`: `3`

La valeur de sortie pour cette entrée est donc *`5353`*.

En suivant le même procédé pour chaque entrée dans le deuxième exemple, le plus gros ci-dessus, la valeur de sortie de chaque entrée peut être déterminée :

- ``fdgacbe cefdb cefbgd gcbe``: `8394`
- ``fcgedb cgb dgebacf gc``: `9781`
- ``cg cg fdcagb cbg``: `1197`
- ``efabcd cedba gadfec cb``: `9361`
- ``gecf egdcabf bgf bfgea``: `4873`
- ``gebdcfa ecba ca fadegcb``: `8418`
- ``cefg dcbef fcge gbcadfe``: `4548`
- ``ed bcgafe cdgba cbgef``: `1625`
- ``gbdfcae bgc cg cgb``: `8717`
- ``fgae cfgab fg bagce``: `4315`

Additionner toutes les sorties du plus grand exemple donne *`61229`*.

Pour chaque entrée, déterminez toutes les connections câble/segment et décodez la valeur de sortie à quatre chiffre. *Qu'obtenez-vous si vous additionnez toutes les valeurs de sortie ?*
