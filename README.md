# Ejercicio práctico sobre la utilización básica de Git, GitHub y Markdown

# Crear repositorio y clonarlo en local

Hay varias rutas desde GitHub por las que acceder a la creación de un nuevo repositorio. Una vez dentro de la sección de nuevo repositorio, indicaremos el nombre de éste (campusciff). De igual forma se puede iniciar como público o privado, con archivo readme o sin él... Todas estas opciones es posible configurarlas posteriormente.

![Crear Nuevo Repositorio](https://github.com/jorgemaza/campusciff/blob/master/img/CrearNuevoRepositorio.PNG)

Para clonar el repositorio creado se puede optar por copiarlo mediante el protocolo HTTP o SSH. En este caso se ha empleado el protocolo SSH, y se han seguido previamente los pasos para tener nuestra máquina asociada al repositorio por criptografía asimétrica y de esta forma poder trabajar desde el ordenador sin necesidad de introducir la password por cada interacción con el repositorio remoto. 

Introducir el comando git clone seguido de la dirección del repositorio al que queremos conectar para descargarlo en la carpeta actual del bash.

![GitClone](https://github.com/jorgemaza/campusciff/blob/master/img/SSH%20github.PNG)

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

Se han creado el archivo "privado.txt" y la carpeta "privada". Para ignorar archivos, hay que añadirlos al fichero ".gitignore". En este caso se ha usado este comando pero se puede hacer directamente desde cualquier editor. Para tener separadas las líneas entre los dos archivos dentro de ".gitignore" se han concatenado los saltos de línea "\n" y retorno de carro "\r", y se ha utilizado "-e" para que los pueda interpretar el bash.

![Archivos](https://github.com/jorgemaza/campusciff/blob/master/img/Crear%20privadotxt.PNG)

```Shell
$ echo -e "privado.txt\r\nprivada/" > .gitignore
```

Quedaría así el archivo ".gitignore" conteniendo:
```File
privado.txt
privada/
```

# Añadir el fichero 1.txt al repositorio local
Se ha creado un fichero con contenido vacío por medio del comando echo.

```Shell
$ echo "" > 1.txt
```

# Crear el tag v1.0 y subir los cambios al repositorio remoto
Estos son los comandos utilizados para el tag v0.1. La imagen seguida es consecuencia del alias "git config --global alias.list 'log --oneline --decorate --graph --all'" que permite ver con mayor facilidad el histórico de git.

```Shell
git tag v0.1
git push origin master
```

![Git list](https://github.com/jorgemaza/campusciff/blob/master/img/Utilizando%20el%20alias.PNG)
![Git list2](https://github.com/jorgemaza/campusciff/blob/master/img/Utilizando%20el%20alias2.PNG)

# Cuenta de GitHub
A continuación se desarrollan los pasos para añadir una imagen al perfil de github, el doble factor de autentificación y la clave pública correspondiente.

## Imagen de perfil 
Para poner una foto en el perfil de GitHub, hay que entrar en las opciones del perfil y añadir una foto menor de 1MB.

![Mi foto](https://avatars0.githubusercontent.com/u/19300313?v=3&s=460)

## Doble factor de autentificación
El doble factor de autentificación permite que nuestra cuenta sea más segura. El procedimiento para realizarlo es sencillo. Entramos en: Perfil/Settings/Security/Two-factor authentication, y entrar al botón Set up two-factor authentication.

![TwoFactorAuth](https://github.com/jorgemaza/campusciff/blob/master/img/TwoFactorAuth.PNG)

Puede optarse por recibir un código desde la aplicación de GitHub o por SMS. En este caso, se ha escogido la opción del SMS.

![TwoFactorAuth2](https://github.com/jorgemaza/campusciff/blob/master/img/TwoFactorAuth2.PNG)

Introducir el código recibido al mensaje del teléfono móvil y finalizar descargando el github-recovery-code.

![RecoveryCode](https://github.com/jorgemaza/campusciff/blob/master/img/RecoveryCode.png)

El recovery code permite que si perdemos los datos de la cuenta podamos recuperarla. 

GitHub enviará otro SMS si la doble autentificación ha funcionado satisfactoriamente.

> You have successfully configured GitHub two-factor authentication. You will receive two-factor codes at this number.

## Añadir la clave pública correspondiente a nuestro ordenador.

Primeramente hay que introducir el siguiente comando en el bash de nuestra consola git.

```Shell
$ ssh-keygen -t rsa -b 4096 -C "jorgemaza@campusciff.net"
```

Copiar el archivo id_rsa de nuestra máquina local en nuestra configuración SSH de los ajustes de nuestra cuenta. Por defecto, se sitúa en "~/.ssh/id_rsa.pub".

```Shell
clip < ~/.ssh/id_rsa.pub
```

Ir a la configuración de GitHub --> SSH and GPG keys --> New SSH key, poner un nombre a nuestra clave del ordenador y pegar en Key la clave copiada con el comando anterior.
![Git list2](https://github.com/jorgemaza/campusciff/blob/master/img/CapturaSSH.PNG)

Probar la clave por medio del comando:

```Shell
ssh -T git@github.com
```

Aparecerá un mensaje parecido al siguiente:

>Hi jorgemaza! You've successfully authenticated, but GitHub does not provide shell access.

# Uso social de GitHub

Seguir los repositorios de los compañeros. :white_check_mark:

Añadir una estrella a los repositorios campusciff del resto de compañeros.
![Estrella](https://github.com/jorgemaza/campusciff/blob/master/img/Estrellita.png)


# Crear una tabla
| Compañer@ | GitHub |
|---|---|
| Alberto Marino  |  https://github.com/amarino5 |
| Enrique Serrano  | https://github.com/eserranom  |
| Araceli Macía | https://github.com/araceliMacia |
| Giovani Mata | https://github.com/giovamata |
| Ainhoa Calvo | https://github.com/AinhoaCE |
| Mark Wellings | https://github.com/Mark-Wellings |
| Fernando Escolano | https://github.com/fescolan |
| Anna Lawrence | https://github.com/annalawrenc |
| Juan García | https://github.com/juangarciaciff |
| Asier Matas | https://github.com/asiermatas |

# Añadir colaborador
![Colaborador](https://github.com/jorgemaza/campusciff/blob/master/img/ColaboradorRepositorio.PNG)