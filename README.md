# Faire un site sur le langage Lua en français

Perso je me vois bien faire un tuto comme avec [golang](https://gobyexample.com/) à savoir par l'exemple plutôt que de faire de long discourts

Prendre en compte les infos suivantes:
[10:44:08] <TsT> Chipster1 les tables en lua etant tellement importante que je serait d'avis de séparé le fichier tables.md en 3 ou 4 ...
[10:44:39] <TsT> 1) table -> indexe numerique (comme les arrays(?) dans d'autres language)
[10:44:52] <TsT> 2) table -> clé+valeure (comme les hash table dans d'autres languages?)
[10:45:38] <TsT> 3) le mixe des 2, que quasiment seul le lua supporte, et comment bien parcourir quand on veut que l'un et l'autre
[10:45:39] <TsT> 4) un peu de metatable ?
[10:45:46] <TsT> dans 1) je parlerais de ipairs() de facon simple
[10:45:56] <TsT> dans 2) je parlerais de pairs() de facon simple
[10:47:07] <TsT> dans 3) je reparlerais de ipairs, pairs et d'exemple pour ne parcourir que les clés (for k,v in pairs(t) do if type(k)~="number" then ... end end )
[10:48:06] <TsT> en 4) au lieu de metatable qui devra sans doute avoir un chapitre a lui tout seul ... je parlerais plutot des fonctions de table.*
[10:48:40] <TsT> genre le débat entre table.insert(t,v) et t[#t+1]=v
[10:48:40] <TsT> ou table.remore(t,2) et t[2]=nil
[10:49:40] <TsT> je placerais les coroutines et les metatables a la fin (dans une section "avancé")
[10:49:40] <TsT> et je retourne bosser

---

[Site](http://fengari.io/) pour tester lua sans installation
[Version plus complète de ArRay_](https://github.com/BetaRays/tutoriel-lua/)

Liste à faire:

1. [Hello World](hello_world.md)
2. [Les commentaires](commentaires.md)
3. [Les valeurs](valeurs.md)
4. [Les variables](variables.md)
5. [Les boucles](boucles.md)
6. [If/Else](conditions.md)
7. [Break](break.md)
7. [Les tables](tables.md)
8. [Les fonctions](fonctions.md)
9. [Portée des variables](portee_variables.md)
10. [Fonction à nombre d'arguments variables](variadic.md)
11. [Récupérer les arguments de la ligne de commandes](arg_cli.md)
10. [Les imports](imports.md)
10. [Créer ses propres librairies](creer_lib.md)
10. [La récursivité](recursivite.md)
11. [Lire et écrire un fichier](lecture_ecriture.md)
11. [Les coroutines](coroutines.md)
12. Awesome Lua
13. Remerciements

Les choses à rajouter dans la liste
* Expliquer ce que c'est que nil
* Parler de select (function a(...) for i=1,select('#',...) do print(i,select(i,...)) end end a('c','est','cool'))

exemple: [22:20:21] <nheir> select est une fonction qui prend un premier argument correspondant à l'action que tu veux faire et d'autres arguments ensuite, si le premier est '#', select renvoie le nombre d'arguments qui suit
[22:21:00] <nheir> si c'est un nombre, il renvoie les arguments à partir de l'argument en position ce nombre
[22:21:34] <ChipsterOne> ok
[22:22:03] <nheir> !lua select('#', 4,8,9,1,5,9,7)
[22:22:04] <arch_ange> > 7
[22:22:09] <nheir> !lua select('4', 4,8,9,1,5,9,7)
[22:22:10] <arch_ange> > 1 5 9 7
[22:22:22] <nheir> !lua select('3', 4,8,9,1,5,9,7)

* Récupérer les arguments de la ligne de commandes
* les closures
* sandbox (avec do … end)
* les variables magiques
* pack/unpack (voir ici: https://github.com/BetaRays/tutoriel-lua/blob/master/030-Les_variables.md#les-fonctions-variadiques)
* rajouter sort aux tables (http://wxlua.free.fr/Tutoriel_Lua/Tuto/Tables/tables9.php)
* Les regex