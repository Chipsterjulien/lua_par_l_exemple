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

Si vous mettez votre lib dans un répertoire ou plusieurs répertoire(s), il faudra l'appeler comme ceci:
```lua
monModule = require "monRep.unAutreRep.mymodule"
mymodule.foo()

-- output:
--  Hello world!
```

## Exemple complet:
Fichier dans le répertoire fmt: *fmt/printf.lua*
```lua
local fmt = {}

function fmt.printf(str, ...)
  io.write(string.format(str, ...))
end

return fmt
```

Fichier utilisant *fmt/printf.lua*:
```lua
local fmt = require "fmt.printf"

local name = "Julien"
fmt.printf("Bonjour %s", name)

-- output:
--  Bonjour Julien
```


En Lua, le séparateur est un *.* et non un "/" ou un "\"

Exemple suivant: [Les fermetures (closures)](closures.md).
