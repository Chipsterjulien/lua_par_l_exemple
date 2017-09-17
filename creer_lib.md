# Lua par l'exemple: Créer ses propres librairies

Créez un fichier nommé *mymodule.lua* puis mettez-y le code suivant:
```lua
local mymodule = {}

function mymodule.foo()
  print("Hello world!")
end

return mymodule
```

Maintenant, pour pouvoir utiliser notre nouvelle lib dans un autre fichier, il suffit de l'appeler comme ceci:
```lua
monModule = require "mymodule"
mymodule.foo()

-- output:
--  Hello world!
```

Si vous mettez votre lib dans un répertoire ou plusieurs répertoire, il faudra l'appeler comme ceci:
```lua
monModule = require "monRep.unAutreRep.mymodule"
mymodule.foo()

-- output:
--  Hello world!
```

En Lua, le séparateur est un *.* et non un "/" ou un "\"

Exemple suivant: [Les fermetures (closures)](closures.md).