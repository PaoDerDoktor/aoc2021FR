# aoc2021FR

Traduction française des énoncés de l'Advent of Code 2021

Lien vers le site original : https://adventofcode.com/2021

Le script **[compile.bat](https://github.com/openhivefr/aoc2021fr/blob/master/compile.bat)** compile les fichiers *markdown* en *HTML partiel (.phtml)*, c'est-à-dire en HTML sans balises body/head/html etc.

Ceci fait, le script compile les fichier .phtml en fichiers complets .html, contenant deux sections contenant les deux parties du puzzle du jours (aux `id`s respectifs `translation_part_one` et `translation_part_two`).

Le script utilise **[pandoc](https://pandoc.org)**. Il est notamment installable sous windows grâce au gestionnaire de paquets [chocolatey](https://chocolatey.org/) :
```bat
choco install pandoc
```