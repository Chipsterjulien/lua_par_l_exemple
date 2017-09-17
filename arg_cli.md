# Lua par l'exemple: Récupérer les arguments de la ligne de commandes

En Lua, il est très facile de récupérer les arguments de la ligne de commandes. Ils sont tous stockés dans la table arg:
```lua
print("Nombre d'argument(s): " .. #arg)
```

Il suffit ensuite de lancer le programme comme suit:
```shell
$ lua mon_programme.lua coin

Nombre d'argument(s): 1
```

Pour parcourir tous les arguments, rien de plus simple:
```lua
-- Exemple avec ipairs()
for position, v in ipairs(arg) do
  print(position, v)
end
```

Exemple suivant: [Les imports](imports.md).