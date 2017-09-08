# Lua par l'exemple: Les variables

En Lua, les variables se définissent à l'aide du signe égal (=):

```lua
-- Une chaîne
a = "Hello World"
print(a)

-- output:
--  Hello World
```

Déclaration multiple:
```lua
a, b = "Hello", "World"
print(a .. b)

-- output:
-- HelloWorld
```

Des entiers:
```lua
a = 6
print(a)

-- output:
-- 6
```

Des booléens:
```lua
a = true
print(a)

-- output
--  true
```

Des décimaux:
```lua
a = 3.1415927
print(a)

-- output:
--  3.1415927
```

Comme d'autres langages de programmation, Lua n'a pas de typage fort, c'est à dire que les variables ne sont pas spécialisées pour contenir un type spécifique de données (entier, chaîne …). Elles peuvent à tout instant contenir un entier, puis, quelques lignes de code plus bas, une chaîne ….
```lua
a = "Une chaîne"
a = 4
print(a)

-- output:
--  4
```

Affectation multiple:
```lua
a, b = 1, 2
print(a, b)

-- output:
--  1   2
```

Prochain exemple: [Les boucles]()