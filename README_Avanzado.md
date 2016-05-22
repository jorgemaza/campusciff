# Ejercicio práctico sobre la utilización avanzada de Git, GitHub y Markdown

Se ha querido separar el readme del ejercicio básico, por tanto se ha creado uno nuevo para este otro:
```
echo "" > README_Avanzado.md
```

# Crear una rama v0.2
Para crear esta rama se ha ejecutad el siguiente comando:
```Shell
git branch v0.2
```

Una vez creada, para posicionarse en ésta se ha ejecutado el comando:
```Shell
git checkout v0.2
```

# Añadir fichero 2.txt
En la rama v0.2, se añade un nuevo fichero con contenido vacío.
```Shell
echo "" > 2.txt
```

# Crear una rama remota v0.2
Se suben los cambios al repositorio remoto:
```Shell
git add -A
git commit -m "Rama remota v0.2"
git push origin v0.2
```

# Merge directo
Posicionarse en rama master y en ella hacer un merge de la rama v0.2:
```Shell
git checkout master
git merge v0.2
```

Git solicitará un mensaje para el merge ya que no incluimos "-m" en el comando.

![MensajeMerge1](https://github.com/jorgemaza/campusciff/blob/master/img/MergeCaptura.PNG)

Introducimos el mensaje con vi.

![MensajeMerge2](https://github.com/jorgemaza/campusciff/blob/master/img/MergeCaptura2.PNG)

Pulsamos ESC y tecleamos :wq para guardar y salir.

Respuesta del último comando:

```Shell
Merge made by the 'recursive' strategy.
 2.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 2.txt
```

Hasta este momento no ha ocurrido nada ya que no hay conflictos. Simplemente existe un nuevo fichero en la rama v0.2.

# Merge con conflicto

A continuación se provoca un conflicto entre las ramas al hacer un merge. En la rama master introducimos "Hola" en el fichero 1.txt y hacemos commit.

```Shell
git checkout master
echo "Hola" >> 1.txt
git add -A
git commit -m "Hola en 1.txt master"
```

Nos posicionamos en la otra rama (v0.2) y ponemos "Adios" en el fichero 1.txt

```Shell
git checkout v0.2
echo "Adios" >> 1.txt
git add -A
git commit -m "Adios en 1.txt v0.2"
```

Posicionarse de nuevo en la rama master y hacer un merge con la rama v0.2

```Shell
git checkout master
git merge v0.2
```

Respuesta: existen conflictos.
```Shell
Auto-merging 1.txt
CONFLICT (content): Merge conflict in 1.txt
Automatic merge failed; fix conflicts and then commit the result.
```

Para ver el listado de ramas con conflictos, se utiliza branch --merged:
```Shell
git branch --merged
```

Aparece entonces la rama master, que es la que da conflicto ya que es desde la que hemos hecho merge:
```Shell
* master
```

Por otro lado, para ver las ramas sin conflictos, utilizamos branch --no-meged:
```Shell
git branch --no-merged
```

Cuyo resultado es la rama v0.2
```Shell
  v0.2
```

## Arreglar conflicto
Para arreglar el conflicto ocasionado al hacer merge desde master con v0.2, abirmos el fichero 1.txt que ahora contiene lo que existe en el master (HEAD) y en v0.2:
```Shell
<<<<<<< HEAD
Hola
=======
Adios
>>>>>>> v0.2
```
Lo resolvemos escribiendo "Hola" en el fichero...
```Shell
Hola
```

...y subimos el conflicto arreglado siguiendo el mismo procedimiento de adición al área de staging y commiteando. También "remergeamos".
```Shell
git add -A
git commit -m "Conflicto resuelto merge"
git merge v0.2
```
El mensaje tras el último merge es:
```Shell
Already up-to-date.
```

# Borrar rama
Crear un tag v0.2.
```Shell
git tag v0.2
```

Eliminar rama v0.2.
```Shell
git branch -d v0.2
```

# Listado de cambios
Utilizando git list (alias creado cuyo comando aparece en el readme del ejercicio básico)...
```Shell
git list
```
...se muestran los distintos commits con sus ramas y sus tags.
```Shell
*   6fb21b1 (HEAD -> master, tag: v0.2) Conflicto resuelto merge
|\
| * e7e9c93 Commit de 1.txt esta vez en rama v0.2
* | 31e8db2 Commit fichero 1.txt
* | bdd1ec5 Commiteando antes de empezar con el merge con conflicto
* |   7cc7f7c Merge branch 'v0.2'
|\ \
| |/
| * 7dc2205 (origin/v0.2) Rama remota v0.2
* |   5a6128e pruebaMerge
|/
* 4dc0def (origin/master, origin/HEAD) Últimos cambios readme ejercicio 1
* f6dd587 Últimos cambios readme ejercicio 1
* 986c1e1 Últimos cambios readme ejercicio 1
* 2b8b51a Subida readme y carpeta imágenes
* 8042179 (tag: v0.1) cambios en readme
* 94d4fb6 commit inicial
```

# Crear una organización
