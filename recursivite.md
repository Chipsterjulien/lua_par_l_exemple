# Lua par l'exemple: La récursivité

C'est une fonction qui s'appelle elle-même. Dans notre cas, la fonction *fact* s'appelle jusqu'à ce que le cas fact(0) apparraisse:

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
