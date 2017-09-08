# Lua par l'exemple: Lire et écrire un fichier

Lire et écrire un fichier sont des tâches basiques nécessaires pour beaucoup de programmes Lua

## Lecture d'un fichier

Avec cette forme, nous lisons le fichier dans son intégralité en une seule fois:

```lua
function readFile(path)
  -- Ouverture du fichier en lecture seule
  local file = io.open(path, "r")
  -- On vérifie que le fichier est bien ouvert en lecture
  if not file then
    return
  end
  
  -- slurp contient l'intégralité du fichier
  local slurp = file:read("*a")
  -- On ferme le fichier
  file:close()
  
  -- On affiche le fichier en console
  print(content)
end

readFile("/tmp/dat")
```

Dans l'exemple suivant, le fichier sera lu ligne par ligne:
```lua
function readFile(path)
  -- Ouverture du fichier en lecture seule
  local file = io.open(path, "r")
  -- On vérifie que le fichier est bien ouvert en lecture
  if not file then
    return
  end
  
  for line in io.lines(file) do
    -- On affiche le fichier en console, ligne par ligne
    print(line)
  end
  
  -- On ferme le fichier
  file:close()
end

readFile("/tmp/dat")
```

## Écriture dans un fichier
L'écriture dans un fichier ressemble beaucoup à ce qui a été mis précédemment:
```lua
function writeStringInFile(path, str)
  -- Ouverture du fichier en écriture seul
  -- Attention, si un fichier existe déjà avec ce nom, il sera écrasé !
  file = io.open(path, "w")
  if not file then
    return
  end
  
  -- On écrit dans le fichier
  file:write(str)
  file:close()
end

writeStringInFile("/tmp/dat", "Hello world!\n")
```

## Seek
Seek permet de se déplacer dans le fichier. Par exemple, lors de l'ouverture d'un fichier en lecture seule, le curseur est placé automatiquement au début à savoir 0, 0:
* ligne 0
* colonne 0

Voici un exemple d'utilisation:
```lua
-- Ouverture en lecture seule
file = io.open("test.lua", "r")
-- On ne s'occupe pas de vérifier que le fichier est bien ouvert
-- On se place à la fin du fichier et on recule de 25 caractères
file:seek("end", -25)
-- On affiche tout le fichier, du curseur jusqu'à la fin
print(file:read("*a"))
file:close()
```

seek() attend 2 paramètres optionnels **whence** et **offset**.
* whence peut prendre comme valeur *set*, *cur* ou *end*
* offset est un entier (voir l'exemple ci-dessus)

seek() peut être utilisé dans n'importe quel mode d'ouverture (voir suite)

## Les modes
### Modes d'ouvertures d'un fichier
Il en existe plurieurs. Nous avons vu la lecture et l'écriture mais il en existe d'autres:

| Mode | Description                                                                                                          |
| ---- | -------------------------------------------------------------------------------------------------------------------- |
| "r"  | Mode en lecture seule. C'est le mode par défaut si rien n'est indiqué                                                |
| "w"  | Mode en écriture seule. Écrase les fichiers existants ou crée un nouveau fichier                                     |
| "a"  | Mode ajout. Ouvre un fichier existant et se place à la fin ou crée un nouveau fichier en mode écriture               |
| "r+" | Mode en lecture et écriture pour un fichier existant                                                                 |
| "w+" | Si le fichier existe, toutes les données sont supprimées autrement il en crée un nouveau en mode lecture et écriture |
| "a+" | Mode ajout avec le mode lecture d'activé qui ouvre un fichier existant ou en crée un nouveau                         |

### Modes de lecture d'un fichier
Au début de cet exemple, nous avons lu l'intégralité d'un fichier avec la commande suivante:
```lua
slurp = file:read("*a")
```

Cependant, la fonction *read()* peut prendre d'autres paramètres:

| Mode   | Description                                                                                                                |
| ------ | -------------------------------------------------------------------------------------------------------------------------- |
| "*n"   | Lit à partir de la position actuelle du fichier et renvoie un numéro, s'il existe, à la position du fichier ou renvoie nil |
| "*a"   | Lit l'intégralité du fichier à partir de la position du curseur                                                            |
| "*l"   | Lit la ligne à partir de la position du curseur et le place à la prochaine ligne                                           |
| nombre | Lit le nombre de bytes                                                                                                     |

## Autres commandes intéressantes

* **io.tmpfile():** Retourne un fichier temporaire en lecture et écriture qui sera supprimer une fois que le programme sera terminé
* **io.type(nomDuFichier):** Renvoie le fichier, le fichier fermé ou nil en fonction du fichier d'entrée.
* **io.flush():** Efface le tampon de sortie par défaut
* **io.lines(nomDuFichierFacultatif):** Fournit un générique pour l'itérateur de boucle qui boucle le fichier et le ferme à la fin, au cas où le nom du fichier est fourni ou le fichier par défaut est utilisé et n'est pas fermé à la fin de la boucle (voir exemple en début de chapitre).

Prochain exemple: [Les coroutines](coroutines.md).