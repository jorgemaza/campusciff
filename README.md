# Crear repositorio y clonarlo en local

Hay varias rutas desde GitHub por las que acceder a la creación de un nuevo repositorio. Una vez dentro de la sección de nuevo repositorio, indicaremos el nombre de éste (campusciff). De igual forma se puede iniciar como público o privado, con archivo readme o sin él... Todas estas opciones es posible configurarlas posteriormente.

Para clonar el repositorio creado se puede optar por copiarlo mediante el protocolo HTTP o SSH. En este caso se ha empleado el protocolo SSH, y se han seguido previamente los pasos para tener nuestra máquina asociada al repositorio por criptografía asimétrica y de esta forma poder trabajar desde el ordenador sin necesidad de introducir la password por cada interacción con el repositorio remoto.

```Shell
$ ssh-keygen -t rsa -b 4096 -C "jorgemaza@campusciff.net"
```
Copiar el archivo id_rsa de nuestra máquina local en nuestra configuración SSH de los ajustes de nuestra cuenta.

Testear la clave por medio del comando 

```Shell
ssh -T git@github.com
```

Aparecerá un mensaje parecido al siguiente:

>Hi jorgemaza! You've successfully authenticated, but GitHub does not provide shell access.

Para clonar el repositorio de nuestro usuario, basta con introducir el comando git clone seguido de la dirección del repositorio al que queremos conectar para descargarlo en la carpeta actual del bash.
```Shell
git clone git@github.com:jorgemaza/campusciff.git
```

# Commit inicial
Para el commit inicial, utilizamos primero el comando add para añadir el archivo README.md al área de staging.

```Shell
git add README.md
```

Tras ello se graban los cambios con commit, utilizando "-m" para incluir el comentario de subida.

```Shell
git commit -m "commit inicial"
```

# Push inicial
Para guardar los cambios del README en GitHub (repositorio remoto), hay que enviar el commit desde el repositorio local utilizando push.

```Shell
git push origin master
```

Siendo "origin" el repositorio del que hemos clonado el proyecto campusciff y "master" el repositorio local de nuestra máquina.

# Ignorar archivos

Se han creado el archivo privado.txt y la carpeta privada. Para ignorar archivos, hay que añadirlos al fichero .gitignore. En este caso se ha usado este comando pero se puede hacer directamente desde cualquier editor. Para tener separadas las líneas entre los dos archivos dentro de .gitignore se han concatenado los saltos de línea "\n" y retorno de carro "\r", y se ha utilizado "-e" para que los pueda interpretar el bash.

```Shell
$ echo -e "privado.txt\r\nprivada/" > .gitignore
```

Quedaría así un fichero "gitignore" conteniendo:
```Folder
privado.txt
privada/
```
# Añadir el fichero 1.txt al repositorio local
Se ha creado un fichero con contenido vacío por medio del comando echo.
```Shell
$ echo "" > 1.txt
```
