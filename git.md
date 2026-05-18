# BREVE TUTORIAL DE GIT

## ¿Qué es Git?

Git es un sistema de control de versiones, creado originalmente por Linus
Torvalds para gestionar las contribuciones de código al núcleo de Linux.

Está diseñado para ser fácil de usar, y a la vez, se puede personalizar tanto
como se desee. Para un ingeniero de sistemas, el manejo de Git es esencial para
el desarrollo colaborativo de software, y para poder llevar un control
organizado y metódico de los cambios al código fuente.

Git está disponible para todas las plataformas principales (Linux, Windows y
Mac OS), su última versión puede descargarse desde https://git-scm.com

Una vez descargado e instalado, debe accederse a un shell (BASH/ZSH en Linux
y Mac OS, Powershell/Git BASH en Windows) y digitar el comando `git --version`
para comprobar la instalación. Un resultado similar a éste:

```
$ git --version
git version 2.24.3 (Apple Git-128)
```
...indica una instalación exitosa.

## ¿Qué es Github?

Github es un sitio público para alojar repositorios Git. Permite tener una
copia en línea de los repositorios propios, posibililtando también el desarrollo
colaborativo de software.

Un repositorio Github bien ordenado y gestionado puede considerarse como la
carta de presentación y portafolio de productos de un ingeniero de sistemas
o de un profesional de la computación.

## Comandos básicos para creación de un repositorio

Para crear un repositorio, primero debe crearse un directorio nuevo en el
disco duro local, y cambiarse a él.

Luego se ejecutan los siguientes tres comandos:
```
git init
git config user.name "Tu nombre"
git config user.email tu-email@algunsitio.com
```
El primer comando inicializa el repositorio, creando un directorio oculto `.git`
donde quedan almacenada toda la información que Git necesita para efectuar el
control de versiones. Los dos comandos siguientes permiten especificar el nombre
y la dirección de correo de quien está configurando el repositorio. Git emplea
esta información para identificar a quiénes hagan aportes de código al
repositorio.

## Cómo decirle a Git que controle los archivos del repositorio

Los archivos nuevos que se creen en el repositorio no estarán controlados inicialmente por Git.
Se puede verificar si hay archivos sin controlar mediante el comando `git status`:
```
$ git status
On branch main
Untracked files:
  (use "git add <file>..." to include in what will be committed)
	nuevo.txt

nothing added to commit but untracked files present (use "git add" to track)
```
En este ejemplo, Git informa que estamos en la rama *main* del repositorio, y que existe un
archivo llamado `nuevo.txt` que aún no es controlado por Git. Para indicarle a Git que
controle el archivo, debe emplearse el comando `git add`:
```
git add nuevo.txt
```
Se puede emplear `git add .` para adicionar todos los archivos del directorio al repositorio,
o se pueden emplear comodines para especificar un determinado tipo de archivos, por ejemplo,
`git add *html`.

Si se hacen cambios a algún archivo que ya esté controlado por Git, debe volverse a ejecutar
el `git add` sobre dicho archivo, para que los cambios sean tenidos en cuenta por Git.

## Haciendo commit de los cambios

Una vez hecho el `git add`, los cambios quedan en lo que se conoce como *área de preparación*
(staging area). Para confirmar dichos cambios, se emplea el comando `git commit`:
```
$ git commit -m "Se agregó el archivo nuevo.txt`
[main 8c35293] Se agregó el archivo nuevo.txt
 1 file changed, 1 insertion(+)
 create mode 100644 nuevo.txt
```
Siempre es necesario acompañar el commit de un comentario, mediante el parámetro -m. La idea
es que el comentario refleje los cambios que se hicieron al repositorio, ya que cada
commit puede considerarse como un hito, o un punto de referencia al que nos podemos devolver
si es necesario.

## Verificando el estado del repositorio

En cualquier momento, puedes verificar el estado del repositorio mediante el comando `git status`.
Este comando te dirá si existen archivos cambiados o sin controlar, si los cambios están en el
área de preparación a la espera de un commit, o si todos los cambios han sido confirmados.

## Cambios a un archivo: Viendo las diferencias

Si se hacen cambios a un archivo o archivos del repositorio, se puede emplear el comando
`git diff` para ver los cambios que se han hecho sobre los archivos, antes de ejecutar un nuevo
`git add`.

## Descartando cambios a un archivo

Si se desea descartar todos los cambios hechos a un determinado archivo antes de hacer
un `git add`, se puede emplear el comando `git restore`, por ejemplo:

```
git restore nuevo.txt
```
...descartaría todos los cambio hechos a `nuevo.txt` desde el último commit.

## Revisión de la historia de commits

Se puede revisar la historia de commits con `git log --oneline`:
```
$ git log --oneline
8c35293 (HEAD -> main) Se agregó el archivo nuevo.txt
1ef437a (origin/main) Creado git.md
4752737 Primera versión de los materiales de estudio
071eaf8 Se agregan temas a expodidacticas.md
0d1a3eb expodidacticas.md creado
```
Cada commit va identificado con su hash único.

## Apertura y fusión de ramas

La creación de una *rama* nueva permite hacer modificaciones al software respetando
lo que se ha hecho hasta ahora. Más adelante, el desarrollador puede optar por incorporar
los cambios a la rama principal, o descartar los cambios.

Creación de una rama nueva:
```
git branch nueva_rama
```
Pasarse a la rama nueva:
```
git checkout rama_nueva
```
Pasarse a la rama principal (**master** o **main**, dependiendo de la configuración de Git):
```
git checkout master
- ó -
git checkout main
```
Incorporar los cambios de la rama nueva a la principal (requiere pasarse primero a la rama principal):
```
git merge rama_nueva
```
Git incorpora automáticamente todos los cambios. Si existen conflictos entre archivos, Git los indicará.
Debes solucionarlos manualmente editando el archivo, y luego hacer `git add` y `git commit` para concluir
la fusión.

## Crear una asociación con un repositorio remoto

Para hacerlo, primero debe crearse un repositorio remoto en Github, y copiar la URL de actualización
(que Github muestra terminada siempre en `.git`). Es recomendable que el repositorio remoto tenga el
mismo nombre del repositorio local.

Luego se le informa a Github de la existencia del repositorio remoto:
```
git remote add origin https://github.com/jm3-cyber/abc.git
```
La palabra **origin** es el alias con el que Git identifica al repositorio remoto.

Una vez hecho esto, se puede proceder a "empujar" (push) el repositorio local hacia
el remoto:
```
git push origin main
- ó -
git push origin master
```

Si se hacen cambios al repositorio remoto, se pueden traer los cambios al repositorio local, "halándolos" (pull):
```
git pull origin main
- ó -
git pull origin master
```
El pull hace una fusión (merge) automática de los cambios. Si existen conflictos, deben resolverse manualmente.

## Regresando a commits anteriores del código

Se emplean los siguientes comandos:
```
git checkout HEAD^            ... para regresar al commit anterior
git checkout HEAD^^           ... para retroceder dos commits
git checkout HEAD^^^          ... para retroceder tres commits, y así sucesivamente
git checkout master (ó main)  ... para regresar al commit más reciente.
```
