# Lua par l'exemple: Les boucles

## La boucle while

Elle ne s'exécute que si la condition est vraie:
```lua
i = 0
while i < 5 do
  print(i)
  i = i + 1
end

-- output:
--  0
--  1
--  2
--  3
--  4
```

Dans l'exemple précédent, vous pourriez être tentés d'écrire ceci:
```lua
-- Remplacer i = i + 1 par:
i++
```
Cependant, Lua ne supporte pas cette forme de notation dîtes d'*autoincrémentation*


## La boucle until

Elle fonctionne presque comme la boucle while à la différence qu'elle s'exécute au moins 1 fois. Ici on répètera les opérations jusqu'à ce que i soit supérieur à 5:
```lua
i = 0
repeat
  print(i)
  i = i + 1
until i > 5

-- output:
--  0
--  1
--  2
--  3
--  4
--  5
```

Un autre exemple mais cette fois-ci la condition fausse dès le départ. On remarque que la boucle s'effectue au moins 1 fois:
```lua
i = 0
repeat
  print(i)
  i = i + 1
until i < 5

-- output:
--  0
```

## La boucle for

C'est certainement la boucle la plus importante et la plus utilisée. Il est possible de la trouver sous plusieurs formes dont 2 seront aborder dans l'exemple sur *les tables*.
Voici la forme numérique:

```lua
-- Forme numérique
for i=0, 5 do
  print(i)
end
-- output:
--  0
--  1
--  2
--  3
--  4
--  5
```

Il est possible de spécifier le pas d'incrémentation (ou décrémentation selon les besoins)

```lua
-- Forme numérique avec spécification du pas
for i=5, 0, -1 do
  print(i)
end
-- output:
--  5
--  4
--  3
--  2
--  1
--  0
```

Prochain exemple: [If/Else](conditions.md).