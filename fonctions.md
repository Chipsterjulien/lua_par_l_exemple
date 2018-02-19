# Lua par l'exemple: Les fonctions

Les fonctions sont très importantes.
Voici un exemple simple:

```lua
function bonjour()
  print("Bonjour")
end

bonjour()

-- output:
--  Bonjour
```

Un exemple avec passage de paramètres
```lua
function plus(a, b)
  print(a + b)
end

plus(5, 5)

-- output:
--  10
```

Fonction avec une valeur de retour:
```lua
function plus(a, b)
  return a + b
end

z = plus(5, 5))
print(z)
-- On aurait pu écrire directement: print(plus(5, 5))

-- output:
--  10
```

Fonction avec plusieurs valeurs de retour:
```lua
function vals()
  return 3, 7
end

function main()
  a, b = vals()
  print(a)
  print(b)
  
  -- Si nous ne voulons pas utiliser la première variable, il faut utiliser _
  _, c = vals()
  print(c)
end

-- output:
--  3
--  7
--  7
```

Lorsque nous avions vu le mot clef *break* je vous avais dit qu'il existait une autre solution. Nous y voilà:
```lua
-- Avec le mot clef break
function maFunc()
  for i=0, 10 do
    if i == 5 then
      break
    end
    print(i)
  end
  print("Fin")
end

maFunc()

-- output:
--  0
--  1
--  2
--  3
--  4
--  Fin

-- Avec le mot clef return
function otherFunc()
  for i=0, 10 do
    if i == 5 then
      return
    end
    print(i)
  end
  print("Fin")
end

otherFunc()

-- output:
--  0
--  1
--  2
--  3
--  4
```

Vous remarquerez que *print("Fin")* n'est pas lu dans notre cas. Le mot clef return permet de "sortir" de la fonction.

Avant dernière précision, une fonction peut appeler une autre fonction.

Dernière précision. Il existe 2 autres possibilités pour appeler une fonction:
```lua
local function test(str)
  print(str)
end

test "5"
test{ "4" }
test{ "4", "5"}

-- output:
--  5
--  table: 0x16aad60
--  table: 0x16abad0
```


Exemple suivant: [Portée des variables](portee_variables.md).
