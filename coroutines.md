# Lua par l'exemple: Les coroutines

**Attention, les bases du langages doivent être bien maitrisées avant d'attaquer cette partie. N'hésitez pas à la relire plusieurs fois**

Les coroutines sont comme les threads en C mais avec une différence de taille.
Un programme Lua peut avoir plusieurs coroutines de créées mais **seule une** peut fonctionner à la fois **ET** elle arrête le programme principal tant qu'elle n'a pas rendu la main !

## Utilisation

```lua
-- Création d'une fonction qui affichera Bonjour sur la console
function f()
  print("Bonjour")
end

-- Création de la coroutine. Attention, à ce stade, elle est simplement créée !
co = coroutine.create(f)
-- Affichage de l'adresse mémoire de la coroutine
print(co)
-- Exécution de la coroutine
coroutine.resume(co)

-- output:
--  thread: 0x64
--  Bonjour
```

Même code mais en utilisant une fonction anonyme:
```lua
local co = coroutine.create(function()
    print("Bonjour")
end)

print(co)
coroutine.resume(co)

-- output:
--  thread: 0xa8
--  Bonjour
```

Visualisation que seule la coroutine est en fonctionnement. On dit qu'elle est blocante:
```lua
function f()
  print("Début de la coroutine")
  local t0 = os.clock()
  -- On attend 5s
  while os.clock() - t0 <= 5 do
  end
  print("Fin de la coroutine")
end

co = coroutine.create(f)
coroutine.resume(co)
print("Fin du programme")

-- output:
--  Début de la coroutine
--  Fin de la coroutine (après 5s)
--  Fin du programme
```

Il est possible de connaître l'état d'une coroutine avec *coroutine.status()*. Elle peut avoir 3 états:

| État de la coroutine | Signification     |
| -------------------- | ----------------- |
| suspended            | En attente        |
| running              | En fonctionnement |
| dead                 | Morte !           |

Une coroutine qui a l'état *dead* (morte) ne peut être réutilisée !

La vraie puissance des coroutines provient de la fonction **coroutine.yield**. Celui-ci autorise  une reprise ultérieure de son fonctionnement:
```lua
-- Fonction qui sera utilisée pour la coroutine
function f()
  for i=0, 2 do
    print(i)
    -- coroutine.yield() va mettre en "pause" celle-ci et redonner la main au programme principal
    coroutine.yield()
  end
end

co = coroutine.create(f)
-- Appel à la coroutine une 1ère fois
coroutine.resume(co)
-- Appel à la coroutine une 2ème fois
coroutine.resume(co)
-- Appel à la coroutine une 3ème fois
coroutine.resume(co)
-- Attention à la subtilité. La coroutine n'a pas fini la dernière boucle même si tous les chiffres ont été affichés. Regardons:
print(coroutine.status(co))
-- Terminons là !
coroutine.resume(co)
-- Affichage de l'état de la coroutine
print(coroutine.status(co))
-- On essaie de relancer la coroutine (nous allons avoir une erreur)
coroutine.resume(co)

-- output:
--  0
--  1
--  2
--  suspended
--  dead
--  cannot resume dead coroutine
```

## Les générateurs
Passage et retour de paramètres:

```lua
function somme(a, b)
  coroutine.yield(a + b)
end

co = coroutine.create(somme)
print(coroutine.resume(co, 6, 4))

-- output:
--  10
```

## Les itérateurs

Les coroutines étant un mécanisme très puissant, elles permettent de construire, en plus des générateurs, des itérateurs. Nous pourrions utiliser les [closures](closures.md) mais il est parfois plus simple de le faire avec les coroutines:

```lua
-- Déclaration de la coroutine
function f()
  local tab = {1,2,3,4,5}
  for i=1, #tab do
    -- Retour de la valeur et mise en pause de la coroutine
    coroutine.yield(tab[i])
  end
end

-- Création de la coroutine
co = coroutine.create(f)
-- On affiche toutes les valeurs de la coroutine dans une boucle infinie
while true do
  -- On récupère l'état de la coroutine et le paramètre
  local code, res = coroutine.resume(co)
  -- Si la coroutine est terminée, on casse la boucle
  if not code then break end
  -- Sinon on affiche la valeur renvoyée par la coroutine
  print(res)
end

-- output:
--  1
--  2
--  3
--  4
--  5
```

Les exemples sont extrêmements basiques. Les coroutines permettent encore bien des choses qui seront abordés dans les tutos pour utilisateurs intermédiaires/experts

Exemple suivant: [Awesome-lua](awesome.md)























