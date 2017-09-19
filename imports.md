# Lua par l'exemple: les imports

Le langage Lua est riche en possibilités mais il est impossible de tout mettre en son sein (noyau). Par exemple, si vous souhaitez faire du réseau, de base, Lua ne sait pas faire.
Au lieu de réinventer systématiquement la roue, il est possible de récupérer du code déjà écrit par quelqu'un d'autre:

```lua
-- Affichage de la variable http qui est vide actuellement
print(http)
-- Chargement de la lib dans la variable locale http
local http = require("socket")
-- Affichage de la variable http qui contient une table
print(http)
-- Utilisation d'une variable dite magique pour obtenir la version de la lib
print(http._VERSION)

-- output:
--  nil
--  table: 0x7c5280
--  LuaSocket 3.0-rc1
```

Un exemple complet:

```lua
-- On charge la lib dans la variable locale http
local http = require("socket.http")
local body, code = http.request("https://www.lua.org/pil/contents.html")
if not body then
  -- si on a rien récupérer
end

local f = io.open("Contents.html", "w")
-- On sauvegarde ce que nous avons téléchargé
f:write(body)
f:close()
```

Il existe un multitude de modules sur le net qui peuvent être trouvé et installé via [*luarocks*](https://luarocks.org/) (entre autre)

Exemple suivant: [Créer ses propres librairies](creer_lib.md)