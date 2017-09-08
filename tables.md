# Lua par l'exemple: Les tables

Un des plus gros intérêt de Lua réside dans l'utilisation des tables. Attention tout de même, il existe quelques pièges.

## Première partie

Création basique d'une table:
```Lua
a = {}
print(a)

-- Attention, la sortie variera très certainement chez vous.
-- Le résultat est donc une simple information.
-- Il représente l'adresse mémoire où est rangé le début de la table
-- La sortie n'a aucune utilité si ce n'est de vous indiquer que la table existe quelque part en mémoire.

-- output:
--  table: 0x380
```

Récupération du nombre d'éléments que contient une table:
```lua
a = {}
print(#a)

-- output:
--  0
```

Ajout d'un ou plusieurs éléments:
```lua
a = {}
-- Première méthode pour ajouter un élément quand on connait l'indice
a[1] = 5
-- Deuxième méthode pour ajouter un élément à la suite
table.insert(a, 8)
print(a[1])
print(a[2])
print("Taille de la table: " .. #a)

-- output:
--  5
--  8
--  Taille de la table: 2
```

Ajout d'éléments et parcourt de la table avec une boucle for:
```lua
maTable = {}
-- Remplissage de la table
for i=1, 5 do
  table.insert(maTable, i+1)
end

print("Taille de la table: " .. #maTable)

-- Affichage de la table:
for i=1, #maTable do
  print(maTable[i])
end

-- output:
--  Taille de la table: 5
--  2
--  3
--  4
--  5
--  6
```

Création d'une table avec des éléments pré-existants:
```lua
a = {6, "cinq", 5}
print(#a)
for i=1, #a do
  print(a[i])
end

-- output
--  3
--  6
--  cinq
--  5
```

Une autre méthode de parcourt avec ipairs:
```lua
maTable = {}
for i=1, 5 do
  table.insert(maTable, i+1)
end

for i, val in ipairs(maTable) do
  print("Indice: " .. i)
  print("Valeur: " .. val)
end

-- output:
--  Indice: 1
--  Valeur: 2

--  Indice: 2
--  Valeur: 3

--  Indice: 3
--  Valeur: 4

--  Indice: 4
--  Valeur: 5

--  Indice: 5
--  Valeur: 6
```

Une autre variante avec ipairs. La variable i ne nous intéresse pas donc nous la remplaçons par _:
```lua
maTable = {}
for i=1, 5 do
  table.insert(maTable, i+1)
end

for _, val in ipairs(maTable) do
  print(val)
end

-- output
--  2
--  3
--  4
--  5
--  6
```

Suppression d'un élément d'une liste:
```lua
a = {"un", "deux", "deux", "quatre", "quatre", "cinq"}
-- suppression du premier élément
val = table.remove(a, 1)
print("Valeur supprimée: " .. val)
-- Suppression du dernier élément
table.remove(a, #a)

for i=1, #a do
  print(a[i])
end

-- output:
--   Valeur supprimée: un

--   deux
--   deux
--   quatre
--   quatre

```

Fusion d'une liste:
```lua
a = {"Hello", "world", "!"}
chaine = table.concat(a, " ")
print(chaine)

a = {1, 2, 3, 4, 5}
print(table.concat(a, " "))

-- output:
--  Hello world !
--  1 2 3 4 5
```

## Deuxième partie

Au lieu d'utiliser des indiques numériques, il est possible d'utiliser une chaîne. Dans d'autres langages, d'autres noms lui sont donné: hash, map, dict …

Voici un exemple basique:
```lua
maTable = {}
maTable["var"] = 1
maTable["autreChaine"] = "texte"

-- Affichage de la table
-- Attention, j'utilise bien pairs() et non ipairs()
for key, value in pairs(maTable) do
  print("Clef: " .. key)
  print("Valeur: " .. value)
end

-- output:
--  Clef: var
--  Valeur: 1
--  Clef: autreChaine
--  Valeur: texte
```

Comme vous pouvez le remarquer, la seule manière de parcourir cette table est d'utiliser *pairs()*. Nous y reviendrons dans les pièges.

Un autre exemple avec une table contenant des valeurs à la création:
```lua
-- Attention de ne pas mettre de "" autour des clefs
a = {var = 1, autreChaine = "texte"}

for key, value in pairs(maTable) do
  print("Clef: " .. key)
  print("Valeur: " .. value)
end

-- output:
--  Clef: var
--  Valeur: 1
--  Clef: autreChaine
--  Valeur: texte
```

Il existe une autre méthode d'accès aux valeurs:
```lua
maTable = {}
maTable["var"] = 1
maTable["autreChaine"] = "texte"

print(maTable["var"])
print(maTable.var)
print(maTable["autreChaine"])
print(maTable.autreChaine)

-- output:
--  1
--  1
--  texte
--  texte
```

Pour résumer la différence entre pairs() et ipairs():
* pairs() est utile pour les clefs valeurs
* ipairs() est utile pour les index valeurs

## Les pièges

* La première entrée d'une table commence à **1** et non à 0:
```lua
-- Création d'une table vide
a = {}
-- Ajout d'un premier élément
table.insert(a, 6)
-- Affichage de l'indice 0
print(a[0])
-- Affichage de l'indice 1
print(a[1])

-- output:
--  nil
--  6
```

* Un autre exemple que vous seriez tenté de faire mais qui ne fonctionne pas :
```lua
maTable = {}
maTable["var"] = 1
maTable["autreChaine"] = "texte"

for k, v in pairs(maTable) do
  print(maTable.k)
end

-- output:
--  nil
--  nil
```

* Taille d'une table avec des clefs valeurs:
```lua
maTable = {}
maTable["var"] = 1
maTable["autreChaine"] = "texte"

print("Taille de la table: " .. #maTable)

-- output
--  Taille de la table: 0
```
Pour connaître la taille de la table, il faut la parcourir avec pairs().

* Taille d'une table avec des valeurs non consécutives:
```lua
a = {}
a[1] = 5
a[2] = 5
a[4] = 5

print("Taille de la table: " .. #a)
for i=1, #a do
  print(a[i])
end

-- output:
--  Taille de la table: 4
--  5
--  5
--  nil
--  5
```

* Comme précédemment mais séparé d'au moins 2 "trous":
```lua
a = {}
a[1] = 5
a[2] = 5
-- Sale !
a[5] = 5

print("Taille de la table: " .. #a)
for i=1, #a do
  print(a[i])
end

-- output:
--  Taille de la table: 2
--  5
--  5
```

Exemple suivant: [Les fonctions](fonctions.md).