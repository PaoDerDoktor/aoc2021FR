# --- Jour 8 : Recherche à Sept Segments ---

Vous avez à peine réussi à vous mettre en sécurité dans la grotte que le cachalot donne un grand coup dans son entrée, la faisant s'écrouler. Vos senseurs vous indiquent une autre sortie bien plus profonde, vous n'avez donc d'autre choix que de continuer.

Alors que votre sous-marin progresse lentement dans le réseau de cavernes, vous remarquez que vos [affichages à sept segments](https://fr.wikipedia.org/wiki/Affichage_%C3%A0_sept_segments) à quatre chiffres sont défaillants ; ils ont sûrement été endommagés pendant la fuite. Vous aurez bien des problèmes sans eux, vous feriez donc bien de trouver ce qui ne va pas.

Chaque chiffre d'un affichage à sept segments est affiché en allumant ou éteignant chacun des sept segments nommés de `a` à `g` :

<pre><code>  0:      1:      2:      3:      4:
 <em>aaaa</em>    ....    <em>aaaa</em>    <em>aaaa</em>    ....
<em>b</em>    <em>c</em>  .    <em>c</em>  .    <em>c</em>  .    <em>c</em>  <em>b</em>    <em>c</em>
<em>b</em>    <em>c</em>  .    <em>c</em>  .    <em>c</em>  .    <em>c</em>  <em>b</em>    <em>c</em>
 ....    ....    <em>dddd</em>    <em>dddd</em>    <em>dddd</em>
<em>e</em>    <em>f</em>  .    <em>f</em>  <em>e</em>    .  .    <em>f</em>  .    <em>f</em>
<em>e</em>    <em>f</em>  .    <em>f</em>  <em>e</em>    .  .    <em>f</em>  .    <em>f</em>
 <em>gggg</em>    ....    <em>gggg</em>    <em>gggg</em>    ....

  5:      6:      7:      8:      9:
 <em>aaaa</em>    <em>aaaa</em>    <em>aaaa</em>    <em>aaaa</em>    <em>aaaa</em>
<em>b</em>    .  <em>b</em>    .  .    <em>c</em>  <em>b</em>    <em>c</em>  <em>b</em>    <em>c</em>
<em>b</em>    .  <em>b</em>    .  .    <em>c</em>  <em>b</em>    <em>c</em>  <em>b</em>    <em>c</em>
 <em>dddd</em>    <em>dddd</em>    ....    <em>dddd</em>    <em>dddd</em>
.    <em>f</em>  <em>e</em>    <em>f</em>  .    <em>f</em>  <em>e</em>    <em>f</em>  .    <em>f</em>
.    <em>f</em>  <em>e</em>    <em>f</em>  .    <em>f</em>  <em>e</em>    <em>f</em>  .    <em>f</em>
 <em>gggg</em>    <em>gggg</em>    ....    <em>gggg</em>    <em>gggg</em></code></pre>

Ainsi, pour afficher un `1`, seuls les segments `c` et `f` seraient allumés. Le reste serait éteint. Pour afficher un `7`, seuls les segments `a`, `c` et `f` seraient allumés.

Le souci est que les signals qui contrôlent les segments ont été mélangés sur chaque afficheur. Le sous-marin essaie toujours d'afficher des chiffres en produisant un signal sur les câbles de `a` à `g`, mais ces câbles sont connectés *aléatoirement* aux segments. Pire, les connections câbles/segment sont mélangées différemment pour chaque afficheur à quatre chiffres (Par contre, tous les chiffres *dans* un afficheur sont affichés selon les mêmes connection) !

Du coup, vous pourriez savoir si les signaux `b` et `g` sont allumés, mais cela ne signifierait pas que les *segments* `b` et `g` seraient allumés. Le seul chiffre n'utilisant que deux segments est `1`, ça veut donc dire que les segments `c` et `f` sont supposés être allumés. Fort de cette seule information, vous ne pouvez pas savoir quel câble (`b`/`g`) va vers quel segment (`c`/`f`). Pour ceci, vous aurez besoin de collecter plus d'informations.

Pour chaque afficheur, vous regardez les signaux changeants pendant un moment, notez *tous les dix motifs de signaux uniques* que vous y remarquez, puis notez une seule *valeur de sortie à quatre chiffres* (l'entrée de votre puzzle). En utilisant les motifs de signaux, vous devriez être capable de trouver quel motif correspond à quel chiffre.

Par exemple, voici ce que vous pourriez observe comme entrée dans vos notes :

```fdd
acedgfb cdfbe gcdfa fbcad dab cefabd cdfgeb eafb cagedb ab |
cdfeb fcadb cdfeb cdbaf
```

(L'entrée est ici sur deux lignes pour des raisons de clarté, mais elle est sur une ligne dans vos notes).

Chaque entrée consiste en dix *motifs de signaux uniques*, un délimiteur `|`, et enfin la *valeur de sortie à quatre chiffres*. dans cette entrée, les mêmes connections câbles/segments sont toujours utilisées (bien que vous ne connaissiez pas les connections elles-mêmes). Les motifs de signaux uniques correspondent aux dix différentes manières desquelles le sous-marin essaie d'afficher des chiffres en utilisant les connections câble/segment de l'afficheur concerné. Étant donné que `7` est le seul chiffre utilisant trois segments, `dab` dans l'exemple ci-dessus signifie que pour afficher un `7`, les signaux `d`, `a` et `b` sont allumés. Étant donné que `4` est le seul chiffre utilisant quatre segments, ``eafb`` signifie que pour afficher un `4`, les signaux `e`, `a`, `f` et `b` sont allumés ; et ainsi de suite.

Grâce à ces informations, vous devriez pouvoir trouver quelle combinaison de signaux correspond à chacun des dix chiffres. Ensuite, vous pourrez décoder les quatre chiffres de sortie. Hélas, dans l'exemple ci-dessus, tous les chiffres en sortie utilisent cinq segments et sont plus difficiles à déduire.

Pour le moment, *ne considérez que les chiffres simples*. Considérez ce plus grand exemple :

<pre><code>be cfbegad cbdgef fgaecd cgeb fdcge agebfd fecdb fabcd edb |
<em>fdgacbe</em> cefdb cefbgd <em>gcbe</em>
edbfga begcd cbg gc gcadebf fbgde acbgfd abcde gfcbed gfec |
fcgedb <em>cgb</em> <em>dgebacf</em> <em>gc</em>
fgaebd cg bdaec gdafb agbcfd gdcbef bgcad gfac gcb cdgabef |
<em>cg</em> <em>cg</em> fdcagb <em>cbg</em>
fbegcd cbd adcefb dageb afcb bc aefdc ecdab fgdeca fcdbega |
efabcd cedba gadfec <em>cb</em>
aecbfdg fbg gf bafeg dbefa fcge gcbea fcaegb dgceab fcbdga |
<em>gecf</em> <em>egdcabf</em> <em>bgf</em> bfgea
fgeab ca afcebg bdacfeg cfaedg gcfdb baec bfadeg bafgc acf |
<em>gebdcfa</em> <em>ecba</em> <em>ca</em> <em>fadegcb</em>
dbcfg fgd bdegcaf fgec aegbdf ecdfab fbedc dacgb gdcebf gf |
<em>cefg</em> dcbef <em>fcge</em> <em>gbcadfe</em>
bdfegc cbegaf gecbf dfcage bdacg ed bedf ced adcbefg gebcd |
<em>ed</em> bcgafe cdgba cbgef
egadfb cdbfeg cegd fecab cgb gbdefca cg fgcdab egfdb bfceg |
<em>gbdfcae</em> <em>bgc</em> <em>cg</em> <em>cgb</em>
gcafb gcf dcaebfg ecagb gf abcdeg gaef cafbge fdbac fegbdc |
<em>fgae</em> cfgab <em>fg</em> bagce</code></pre>

Puisque les chiffres `1`, `4`, `7` et `8` utilisent chacun un nombre unique de segments, vous pourrez sans doute deviner quelle combinaison de signaux correspond à ces chiffres. En ne comptant *que les chiffres de la valeur de sortie* (la partie après le `|` de chaque ligne), dans l'exemple ci-dessus, il y a *`26`* instances de chiffres utilisant un nombre unique de segments (mis en évidence ci-dessus).

*Dans la valeur de sortie, combien de fois les nombres `1`, `4`, `7` ou `8` apparaissent-ils?*
