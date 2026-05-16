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
indica una instalación exitosa.

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

