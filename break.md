# Lua par l'exemple: Break

Dans les boucles (for, until, while) il est possible d'arrêter la boucle avant:

```lua
for i=0, 5 do
  if i == 2 then
    print("On arrête la boucle ici")
    break
  end
  
  print(i)
end

-- output:
--  0
--  1
--  On arrête la boucle ici
```

Il existe une autre possibilité de "casser" une boucle avec le mot clef *return* que nous aborderons dans les fonctions.

Prochain exemple: [Les tables](tables.md).