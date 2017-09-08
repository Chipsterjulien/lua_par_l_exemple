# Lua par l'exemple: La récursivité

C'est une fonction qui s'appelle elle-même.
La première chose à faire dans ce type de fonction est une vérification comme l'exemple suivant:

```lua
function fact(n)
  if n == 0 then
    return 1
  end
  
  return n * fact(n-1)
end

print(fact(7))

-- Output:
--  5040
```

Exemple suivant: [Lire et écrire un fichier](lecture_ecriture.md).