# Lua par l'exemple: Les commentaires

Les commentaires permettent de documenter son code. Il permet:
* Une relecture plus facile de son code
* Après un moment sans avoir vu le code, il permet de comprendre plus facilement le cheminement
* Une compréhension plus simple quand on partage son code sur internet
* …

*Il est préférable que les commentaires soient écrits en anglais*

**Ne pas en mettre est une très grosse erreur sur le long terme.**

Ceci est un commentaire:
```lua
-- Je suis un commentaire
```

Un autre commentaire:
```lua
-- print(5) Cette ligne ne sera jamais "lu"
print(10)
```

```shell
$ lua commentaire.lua

10
```

Prochain exemple: [Les valeurs]().