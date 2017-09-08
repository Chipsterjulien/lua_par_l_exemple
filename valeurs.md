# Lua par l'exemple: Les valeurs

Lua dispose d'une variété de valeurs comme les chaines, les nombres décimaux, les booléens …. Voici quelques exemples de base:

Les chaînes peuvent être concaténée avec le signe ..

```lua
print("Lu" .. "a")

-- output (sortie de ce que vous devez obtenir):
--  Lua
```

Addition avec des entiers:
```lua
print("1+1=" .. 1+1)

-- output:
--  1+1=2
```

Division avec des décimaux:
```lua
print("7.0/3.0=" .. 7.0/3.0)

-- output:
--  7.0/3.0=2.3333333333333
```

Division avec des décimaux qui donnera un entier:
```lua
print("7.0//3.0=" .. 7.0//3.0)

-- output:
--  2
```

Les booléens avec les opérateurs booléens:
```lua
print(true and false)
print(true or false)
print(not true)

-- output:
--  false
--  true
--  false
```

Même si les sorties sont déjà mises en dessous de chaque exemple, vous pouvez mettre le tout dans un fichier et l'exécuter comme suit:

```shell
$ lua values.lua
Lua
1+1=2
7.0/3.0=2.3333333333333
false
true
false
```

Prochain exemple: [Les variables](variables.md).