# Lua par l'exemple: Les fermetures (closures)

Lua prend en charge les [fonctions anonymes](https://fr.wikipedia.org/wiki/Fonction_anonyme). Elles permettent notamment de former [des fermertures (closures)](https://fr.wikipedia.org/wiki/Fermeture_(informatique)). Les fonctions anonymes sont utiles lorsque l'on souhaite définir une fonction sans avoir à la nommer.
```lua
function intSeq()
  i = 0
  -- Début de la fonction anonyme
  return function()
    i = i + 1
    return i
  end
end

nextInt = intSeq()
print(nextInt())
print(nextInt())
print(nextInt())

-- output:
--  1
--  2
--  3
```

La fonction intSeq renvoie une autre fonction que nous définissons anonymement dans le corps de intSeq. La fonction retournée se ferme sur la variable i pour former une fermeture.
Nous appelons intSeq en attribuant le résultat (une fonction) à nextInt. Cette valeur de fonction capture sa propre valeur de i qui sera mise à jour chaque fois que nous appelons nextInt

Pour confirmer que l'état est unique à cette fonction particulière, regardez l'exemple suivant:
```lua
function intSeq()
  i = 0
  return function()
    i = i + 1
    return i
  end
end

nextInt = intSeq()
print(nextInt())
print(nextInt())
print(nextInt())
print()

newInts = intSeq()
print(newInts())

-- output:
--  1
--  2
--  3
--
--  1
```

Exemple suivant: [La récursivité](recursivite.md).