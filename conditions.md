# Lua par l'exemple: If/Else

Les conditions avec *if* et *else* est très simple à mettre en œuvre.
Voici un exemple basique:
```lua
if 7%2 == 0 then
  print("7 est pair")
else
  print("7 est impair")
end

-- output:
--  7 est impair
```

Il est possible d'avoir une condition avec un *if* sans *else*:

```lua
if 8%4 == 0 then
  print("8 est divisible par 4")
end

-- output:
--  8 est divisible par 4
```

Il est aussi possible d'embrancher les conditions:
```lua
num = 9
if num < 0 then
  print(num .. " est négatif")
elseif num < 10 then
  print(num .. " a un chiffre")
else
  print(num .. " a plusieurs chiffres")
end

-- output:
--  9 a un chiffre
```

Prochain exemple: [Break](break.md).