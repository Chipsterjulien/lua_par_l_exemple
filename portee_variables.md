# Lua par l'exemple: Portée des variables

Par défaut, les variables sont globales:
```lua
function porte()
  a = 5
end

porte()
print(a)

-- output:
--  5
```

Si l'on souhaite qu'elle soit locale, c'est à dire qu'elle n'existe qu'au niveau du bloc, il faut utiliser le mot clef *local*:
```lua
function porte()
  local a = 5
end

porte()
print(a)

-- output:
--  nil
```

Les variables utilisées en paramètres des fonctions sont locales:
```lua
function plus(a, b)
  local val = a + b
  
  return val
end

resp = plus(6, 6)

print(resp)
print(a)
print(b)

-- output:
--  12
--  nil
--  nil
```

Il est très fortement recommandé d'utiliser des variables locales . Un exemple de comportement problématique:
```lua
a = 5
print(a)

function maFunc()
  a = 6
  print(a)
end

maFunc()
print(a)

-- output:
--  5
--  6
--  6
```

Exemple suivant: [Fonction à nombre d'arguments variables](variadic.md)