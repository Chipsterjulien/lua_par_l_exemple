# Lua par l'exemple: Fonction à nombre d'arguments variables

Des fonctions en Lua peuvent recevoir un nombre d'arguments variables comme *print()*:
```lua
a = 2
b = 4
c = 6
-- On passe 3 paramètres
print(a, b, c)
-- On passe 1 seul paramètre
print(6)

-- output:
--  2    4    6
--  6
```

Pour récupérer ses arguments, il faut utiliser **...** :
```lua
function variadic(...)
  print(...)
end
variadic(1, 2, 3)
variadic("a", 2, "b")

-- output
--  a
--  2
--  b
```

Attention, *...* aspire toutes les données restantes donc, il doit être mis en dernier paramètre lors de la déclaration de la fonction:
```lua
function variadic(a, ...)
  print("variable a: " .. a)
  for _, v in ipairs{...} do
    print(v)
  end
end

variadic("b", "c", 2, 6, 4)

-- output:
--  variable a: b
--  c
--  2
--  6
--  4
```

Exemple suivant: [Récupérer les arguments de la ligne de commandes](arg_cli.md).