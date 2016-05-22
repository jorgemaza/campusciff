# Ejercicio práctico sobre la utilización avanzada de Git, GitHub y Markdown

Se ha querido separar el readme del ejercicio básico, por tanto se ha creado uno nuevo para este otro que es el avanzado:
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

Volver de nuevo a la rama master y hacer un merge con la rama v0.2

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

Para ver las ramas sin conflictos, utilizamos branch --no-meged:
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
De igual forma que se crea un repositorio desde nuestro botón de la esquina superior derecha de la opción del perfil, creamos una nueva organización. Se llamará campusciff-jorgemaza.

![NuevaOrg](https://github.com/jorgemaza/campusciff/blob/master/img/NewSomething.PNG)

# Crear equipos

Se han creado dos equipos en la organización. Habrá administradores y colaboradores, y tres componentes en cada equipo. Los administradores tendrán todos los permisos "Owner" y los colaboradores "Member" algunos como crear repositorios, acceso a éstos y vista de otros miembros.

- Aministradores: [Mark](https://github.com/Mark-Wellings), [Enrique](https://github.com/eserranom) y [Adolfo](https://github.com/asanzdiego).

- Colaboradores: [Asier](https://github.com/asiermatas) y [Héctor](https://github.com/hefaso). **[Adolfo](https://github.com/asanzdiego) se encuentra en administradores por lo que tiene todos los roles (administrador y colaborador) al igual que [Mark](https://github.com/Mark-Wellings) y [Enrique](https://github.com/eserranom)**.

![CuandoCreoProyectoEnOrganizacion](https://github.com/jorgemaza/campusciff/blob/master/img/CuandoCreoProyectoEnOrganizacion.PNG)

A continuación se muestran las opciones escogidas durante la creación de una nueva organización:

Este sería el equipo.

![TeamCc](https://github.com/jorgemaza/campusciff/blob/master/img/TeamCampusCiff.PNG)

Enviamos una solicitud a los compañeros para componer el equipo. 

![CompOwner](https://github.com/jorgemaza/campusciff/blob/master/img/CompiOwner.PNG)

Todavía no hay miembros.

![AunSinMiembros](https://github.com/jorgemaza/campusciff/blob/master/img/SinMiembros.PNG)

# Crear un index.html
Lo que se ha hecho ha sido clonar un repositorio nuevo con el nombre "campusciff-jorgemaza.github.io.git", trabajar en local con un nuevo archivo index.html (se trata de la página de la organización, pero inicialmente hemos dejado una página muy simple).

```Shell
git clone git@github.com:campusciff-jorgemaza/campusciff-jorgemaza.github.io.git
echo "" > index.html
vi index.html
```

```html
<!DOCTYPE html>
<html>
	<body>

	<h1>Mi index</h1>
	<p>Jorge Maza de Julián.</p>
	
	</body>
</html>
```

```Shell
git add -A
git commit -m "Index del repositorio de la organización"
git push origin master
```

# Crear Pull-requests

Primero se han hecho dos forks de dos repositorios de dos organizaciones de compañeros de los que mi usuario no es administrador ni colaborador:
[Juan](https://github.com/juangarciaciff) y [Alberto](https://github.com/amarino5).

![ForkJ](https://github.com/jorgemaza/campusciff/blob/master/img/ForkJuanGarcia.PNG)

Clicando en fork, GitHub pregunta en qué lugar deseamos guardar el proyecto.

![WhereShouldWeForkRepository](https://github.com/jorgemaza/campusciff/blob/master/img/WhereShouldWeForkRepository.PNG)

Se han creado las ramas en cada fork dentro del lugar en el que lo hemos guardado y se ha modificado el fichero index.html añadiendo el nombre.

![ramaJuan2](https://github.com/jorgemaza/campusciff/blob/master/img/ramaJuan2.PNG)

Nos movemos al proyecto copiado en este caso en el perfil y creamos una rama.

![CommiteandoCambiosRamaJuan](https://github.com/jorgemaza/campusciff/blob/master/img/CommiteandoCambiosRamaJuan.PNG)

Hacemos commit del cambio en index.html.

![NuevoPullRequest](https://github.com/jorgemaza/campusciff/blob/master/img/NuevoPullRequest.PNG)

En la página de Juan, se puede observar el cambio en el archivo.

![Mi nombre en la página](https://github.com/jorgemaza/campusciff/blob/master/img/Mi%20nombre%20en%20la%20página.PNG)

Hacemos un Pull Request para solicitar a Juan los cambios en su index desde el fork llevado a cabo previamente.

![NuevoPullRequest2](https://github.com/jorgemaza/campusciff/blob/master/img/NuevoPullRequest2.PNG)

Posteriormente, Juan ha dado su "feedback" y ha mergeado mis cambios con los de su proyecto.

![MergeJuan](https://github.com/jorgemaza/campusciff/blob/master/img/MergeJuan.PNG)

# Aceptar los pull-request que lleguen a los repositorios de mi organización

![pullRequestAmarino5A](https://github.com/jorgemaza/campusciff/blob/master/img/AceptarPullRequest1.PNG)
![pullRequestAmarino5B](https://github.com/jorgemaza/campusciff/blob/master/img/AceptarPullRequest2.PNG)