Se ha querido separar el readme, por tanto:
```
echo "" > README_Avanzado.md
```

# Crear una rama v0.2
```Shell
git branch v0.2
git checkout v0.2
```
# Añadir fichero 2.txt
```Shell
echo "" > 2.txt
```

# Crear una rama remota v0.2
```Shell
git add -A
git commit -m "Rama remota v0.2"
git push origin v0.2
```

# Merge directo
Posicionarse en rama master:
```Shell
git checkout master
```

Hacer un merge de la rama v0.2 en la rama master:
```Shell
git merge v0.2
```
Respuesta
```
Merge made by the 'recursive' strategy.
 2.txt | 1 +
 1 file changed, 1 insertion(+)
 create mode 100644 2.txt
```Shell

```Shell
git merge v0.2
```
Respuesta
```Shell
Auto-merging 1.txt
CONFLICT (content): Merge conflict in 1.txt
Automatic merge failed; fix conflicts and then commit the result.
```

```Shell
$ git branch --merged
```
Aparece
```Shell
* master
```

```Shell
git branch --no-merged
```

```
  v0.2
```
  
```Shell
<<<<<<< HEAD
Hola
=======
Adios
>>>>>>> v0.2
```

```Shell
Hola
```

Arreglando conflicto
```Shell
$ git add -A
```

```Shell
$ git commit -m "Conflicto resuelto merge"
[master 6fb21b1] Conflicto resuelto merge
 Committer: Jorge M <Jorge M>
Your name and email address were configured automatically based
on your username and hostname. Please check that they are accurate.
You can suppress this message by setting them explicitly:

    git config --global user.name "Your Name"
    git config --global user.email you@example.com

After doing this, you may fix the identity used for this commit with:

    git commit --amend --reset-author
```

```Shell
$ git merge v0.2
Already up-to-date.
```

$ git branch -d v0.2
Deleted branch v0.2 (was e7e9c93).

```Shell
$ git list
*   6fb21b1 (HEAD -> master) Conflicto resuelto merge
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