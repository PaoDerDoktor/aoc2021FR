# --- Décodeur de Paquets ---

Alors que vous quittez le réseau de grottes pour arriver en eaux libres, vous recevez une transmission des elfes depuis le bateau.

La transmission a été émise en utilisant le Buoyancy Interchange Transmission System (BITS), en français le Système de transmission par échange de flottage, une méthode empaquetant des expressions numériques dans une séquence binaire. L'ordinateur de votre sous-marin a sauvegardé cette transmission en format [hexadécimal](https://fr.wikipedia.org/wiki/Syst%C3%A8me_hexad%C3%A9cimal) (l'entrée de votre puzzle).

Le premier pas pour décoder le message est de convertir la représentation hexadécimale en binaire. Chaque caractère hexadécimal correspond à quatre bits de données binaires :

```bitToHex
0 = 0000
1 = 0001
2 = 0010
3 = 0011
4 = 0100
5 = 0101
6 = 0110
7 = 0111
8 = 1000
9 = 1001
A = 1010
B = 1011
C = 1100
D = 1101
E = 1110
F = 1111
```

La transmission BITS contient un sul *paquet* à sa couche la plus extérieure qui contient lui-même d'autres paquets. La représentation hexadécimale de ce paquet peut encoder quelques `0` supplémentaires à la fin ; ceux-ci ne font pas partie de la transmission et doivent être ignorés.

Chaque paquet démarre par un en-tête standardisé : les trois premiers bits encodent la *version* du paquet, et les trois suivants encodent l'*identifiant de type* du paquet. Ces deux valeurs sont des nombres ; tous les nombres encodés dans un paquet sont représentés avec le bit poids fort en premier (à gauche donc). Par exemple, une version encodée en tant que ``100`` représente le nombre `4`.

Les paquets avec l'identifiant de type `4` représente une *valeur littérale*. Les paquets de valeur littérale encodent un seul nombre binaire. À cette fin, le nombre binaire est rembourré avec des zéros en tête jusqu'à ce que sa longueur soit multiple de quatre, est ensuite séparé en groupes de quatre bits. Chaque groupe est préfixé par un bit de valeur `1`, à l'exception du dernier groupe, préfixé lui par un bit de valeur `0`. Ces groupes de cinq bits suivent immédiatement l'en-tête du paquet. Par exemple, la chaîne hexadécimale ``D2FE28```devient :

```bitTag
110100101111111000101000
VVVTTTAAAAABBBBBCCCCC
```

En-dessous de chaque bit se trouve un identifieur indiquant son rôle:

- Les trois bits identifiés d'un `V` (`110`) sont la version du paquet, `6`.
- Les trois bits identifiés d'un `T` (`100`) sont l'identifiant de type du paquet, `4`, ce qui signifie que le paquet est une valeur littérale.
- Les cinq bits identifiés d'un `A` (`10111`) commencent avec un `1` (pas le dernier groupe, continuez le traitement) et contiennent les quatre premiers bits du nombre, `0111`.
- Les cinq bits identifiés d'un `B` (`11110`) commencent avec un `1` (pas le dernier groupe, continuez le traitement) et contiennent les quatre bits suivants du nombre, `1110`.
- Les cinq bits identifiés d'un `C` (`0010`) commencent avec un `1` (dernier groupe, fin du paquet) et contiennent les quatre derniers bits du nombre, `1110`.
- Les trois bits de valeur `0` sans identifieur sont des bits en trop, existant à cause de la représentation hexadécimale, et doivent être ignorés.

Ainsi, le paquet représente une valeur littérale de représentation binaire `011111100101`, soit en décimal `2021`.

N'importe quel autre type de paquet (n'importe quel paquet avec un identifiant de type différent de `4`) représente un *opérateur* qui effectue une forme de calcul sur un ou plusieurs sous-paquets contenus en lui. Pour l'instant, les opérations spécifiques ne sont pas importantes, concentrez-vous sur la récupération de la hiérarchie des sous-paquets.

Un paquet opérateur contient un ou plusieurs paquets. Pour indiquer quelles données binaires successives forment ses sous-paquets, un paquet opérateur peut utiliser l'un des deux modes disponibles, indiqué par le bit suivant immédiatement l'en-tête, appelé l'*identifiant de type de longueur* :

- Si l'identifiant de type de longueur vaut `0`, alors les *15* bits suivants sont un nombre qui représente la *longueur total en bits* des sous-paquets contenus dans ce paquet.
- Si l'identifiant de type de longueur vaut `1`, alors les *11* bits suivants sont un nombre qui représente le *nombre de sous-paquets* contenus directement dans ce paquet.

Enfin, après l'identifiant de type de longueur et le champs de 15 ou 11 bits, les sous-paquets apparaissent.

Par exemple, la chaîne hexadécimale `38006F45291200` représente un opérateur de paquet avec un identifiant de type de longueur de `0` contenant deux sous-paquets :

```bitTag
00111000000000000110111101000101001010010001001000000000
VVVTTTILLLLLLLLLLLLLLLAAAAAAAAAAABBBBBBBBBBBBBBBB
```

- Les trois bits identifiés d'un `V` (`001`) sont la version du paquet, `1`.
- Les trois bits identifiés d'un `T` (`110`) sont l'identifiant de type du paquet, `6`, ce qui signifie que le paquet est une opérateur.
- Le bit identifié d'un `I` (`0`) est l'identifiant de type de longueur, qui indique que la longueur est un nombre sur 15 bits représentant le nombre de bits total des sous-paquets.
- Les 15 bits identifiés d'un `L` (`000000000011011000000000011011`) contiennent la longueur des sous-paquets en bits, `27`.
- Les 11 bits identifiés d'un `A` contiennent le premier sous-paquet, une valeur littérale représentant le nombre `10`.
- Les 11 bits identifiés d'un `B` contiennent le deuxième sous-paquet, une valeur littérale représentant le nombre `20`.

Après avoir lu les 11 et 16 bits de données des sous-paquets, la longueur totale indiquée en `L` (27) est atteinte, et le traitement de ce paquet s'arrête.

Autre exemple, la chaîne hexadécimale `EE00D40C823060` d'identifiant de type de longueur `1` contient trois sous-paquets :

```bitTag
11101110000000001101010000001100100000100011000001100000
VVVTTTILLLLLLLLLLLAAAAAAAAAAABBBBBBBBBBBCCCCCCCCCCC
```

- Les trois bits identifiés d'un `V` (`111`) sont la version du paquet, `7`.
- Les trois bits identifiés d'un `T` (`011`) sont l'identifiant de type du paquet, `3`, ce qui signifie que le paquet est une opérateur.
- Le bit identifié d'un `I` (`1`) est l'identifiant de type de longueur, qui indique que la longueur est un nombre sur 11 bits représentant le nombre de sous-paquets.
- Les 11 bits identifiés d'un `L` (`00000000011`) contiennent la longueur des sous-paquets en bits, `3`.
- Les 11 bits identifiés d'un `A` contiennent le premier sous-paquet, une valeur littérale représentant le nombre `1`.
- Les 11 bits identifiés d'un `B` contiennent le deuxième sous-paquet, une valeur littérale représentant le nombre `2`.
- Les 11 bits identifiés d'un `C` contiennent le troisième sous-paquet, une valeur littérale représentant le nombre `3`.

Après avoir lu les 3 sous-paquets, le nombre de sous-paquets indiqué en `L` (3) est atteint et le traitement de ce paquet s'arrête.

Pour le moment, analysez la hiérarchie des paquets au fil de la transmission et *additionnez tous les numéros de version*.

Voici quelques exemples de transmission encodées en hexadécimal supplémentaires :

- `8A004A801A8002F478` représente un paquet opérateur (version 4) contenant un paquet opérateur (version 1) contenant lui une valeur littérale (version 6) ; ce paquet a une somme de versions de *`16`*
- `620080001611562C8802118E34` représente un paquet opérateur (version 3) contenant deux sous-paquets ; chaque sous-paquet est un paquet opérateur contenant deux valeurs littérales. ce paquet a une somme de versions de *`12`*.
- `C0015000016115A2E0802F182340` possède la même structure que l'exemple précédent, mais le paquet extérieur utilise un identifiant de type de longueur différent. Ce paquet a une somme de versions de *`23`*.
- `A0016C880162017C3686B18A3D4780` est un paquet opérateur contenant un paquet opérateur contenant lui-même un paquet opérateur contenant, lui, cinq valeurs littérales. Ce paquet a une somme de versions de *`31`*.

Décodez la structure de cotre transmission BITS encodée en hexadécimal, *qu'obtenez-vous si vous additionnez les numéros de version de tous les paquets ?*
