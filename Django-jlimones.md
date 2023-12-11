# Python y Django
--------------

[//]: # (version: 1.0)
[//]: # (author: Jose Carlos Limones Hernandez)
[//]: # (date: 2020-12-8)


# Tabla de contenidos
- [Python y Django](#python-y-django)
- [Tabla de contenidos](#tabla-de-contenidos)
  - [Introducción](#introducción)
  - [Instalación](#instalación)
    - [Instalacion de Python en linux](#instalacion-de-python-en-linux)
    - [Instalación de *Django* en linux](#instalación-de-django-en-linux)
      - [Instalando el modulo de Django](#instalando-el-modulo-de-django)
    - [Instalar Visual Studio Code](#instalar-visual-studio-code)
  - [Comandos Django](#comandos-django)
  - [Generar nuestro primer proyecto con *Django*](#generar-nuestro-primer-proyecto-con-django)
    - [manage.py](#managepy)
      - [Lista de comandos de manage.py](#lista-de-comandos-de-managepy)
  - [Borradores](#borradores)
      - [Intalando *pip*](#intalando-pip)

<div style="page-break-after: always;"></div>




## Introducción
[Tabla de contenidos](#tabla-de-contenidos)

¿Que es **Python**?

- **Python** es un lenguaje de programación interpretado cuya filosofía hace hincapié en una sintaxis muy limpia y un código legible.

- **Python** puede ser una buena alternativa para empezar a programar puesto que es un lenguaje muy sencillo, fácil y con una curva de aprendizaje buena.

- La sintaxis es fácil de entender puesto que es cercana al lenguaje natural.

¿Que es **Django**?

- **Django** es un framework web de python gratuito y de codigo abierto que fomenta un desarrollo rapido y un diseño limpio y pragmatico.
- **Django** Django fue diseñado para ayudar a los desarrolladores a llevar las aplicaciones desde el concepto hasta su finalización lo más rápido posible.
- Ayuda a los desarrolladores a evitar muchos errores de seguridade comunes.
- Es muy escalable, algunos de los sitios más concurridos de la web aprovechan la capacidad de Django para escalar de forma rápida y flexible.
- Su version actual es  **Django 5.0** aunque su version mas estable y con errores menores solucionados es **Django 4.2.8**.
- **Django** es un framework que respeta y utiliza el modelo MVC [(Modelo Vista Controlador)](https://es.wikipedia.org/wiki/Modelo%E2%80%93vista%E2%80%93controlador), que basicamente es un patron de diseño arquitectònico que nos permite separar la logica de negocio de la interfaz de usuario.

<div style="page-break-after: always;"></div>

## Instalación
[Tabla de contenidos](#tabla-de-contenidos)

### Instalacion de Python en linux

> En este apartado veremos como instalar Python por terminal en linux.

1) Para ver si tenemos instalado Python y en el caso de que este instalado ver que version tenemos:
```
python --version
```
> Si tenemos instalada a partir de la version 3 no es necesario seguir los siguientes pasos a no ser que deseemos instalar la ultima version de Python.

2) Lo siguiente que tendemos que hacer es actualizar la lista de paquetes con:
```
sudo apt-get update
```

3) para descargar la ultima versiòn de python:
     - Primero debemos descargar el PPA(Personal Package Archive) llamado "deadsnake", que proporciona versiones actualizadas de python para tu sistema y volveremos a actualizar la lista de paquetes:
```
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
```
4) Descargamos la version que deseemos con wget y la descomprimimos:
```
wget https://www.python.org/ftp/python/3.x.y/Python-3.x.y.tgz
tar -xvf Python-3.x.y.tgz
```

5) Ahora configuramos el entorno de compilacion. Esto analiza la congiguracion del sistema yestablece opciones especificas para compilar Python de acuerdo con las capacidades y configuraciones de tu maquina.
   - --enable-optimizations: Esta opción indica que se deben incluir optimizaciones durante el proceso de compilación. Esto puede aumentar el rendimiento de la ejecución de Python, ya que el código se compilará con optimizaciones específicas para tu arquitectura.
```
cd Python-3.x.y
./configure --enable-optimizations
```
6) Ahora compilaremos los archivos necesarios con el comando:(Esto llevara unos minutos)
```
sudo make install
```
Ahora ejecute el comando:
```
python3
```
y podra usar Python en la terminal.

### Instalación de *Django* en linux
[Tabla de contenidos](#tabla-de-contenidos)

Lo primero que debemos hacer es saber si tenemos instalado el gestor de paquetes de Python.
```
pip --version
```

> En caso de que este instalado nos dira la version del gestor de paquetes.

#### Instalando el modulo de Django
Para instalar este paquete debemos utilizar

```
sudo apt install python3-django
```
Ahora con el siguiente comando comprobamos que Django esta instalado y su version:
```
pip list | grep Django
```

<div style="page-break-after: always;"></div>

### Instalar Visual Studio Code
[Tabla de contenidos](#tabla-de-contenidos)

Empezamos Actualizando paquetes:
```
sudo apt-get update
```
Lo siguiente sera descargar el repositorio de Visual Studio Code:
```
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
```
Ahora actualizamos el sistema de nuevo y e instalamos VSCode.
```
sudo apt update
sudo apt install code
```
Veremos la version instalada con:
```
code -v
```
Ahora podemos abrir VSCode desde la terminal.
```
code
```

## Comandos Django

- django-admin startproject <name_project>

## Generar nuestro primer proyecto con *Django*
[Tabla de contenidos](#tabla-de-contenidos)

Crearemos un directorio donde trabajaremos con Django.
```
mkdir AprendiendoDjango
```
> Deberas usar camelCase, UpperCamelCase o snake_case.
> Es buena práctica crear un archivo requeriments.txt para indicar la librerias y versiones utilizadas en el proyecto.
```
pip freeze > requeriments.txt
```

Para iniciar un proyecto con django nos vamos a la carpeta creada y utilizamos.

```
django-admin startproject aprendiendoDjango`
```
Esto nos creara un directorio con el nombre del proyecto con varios ficheros que veremos mas adelante entre ellos esta manage.py.

### manage.py

El fichero creado manage.py es un script de line de comandos que se utiliza para realizar tareas administrativas realacionadas con un proyecto Django y se encuentra en el directorio raiz del proyecto.

Con el siguiente comando veremos todos los comandos y que poodemos hacer con ellos:

```
python3 manage.py help
```
#### Lista de comandos de manage.py
- [auth]
  - **changepassword**: permite cambiar la contraseña de un usuario.
  - **createsuperuser**: Interactivamente crea un nuevo superusuario para el panel de administracion.
- [contenttypes]
  - **remove_stale_contenttypes**: Elimina los tipos de contenido obsoletos de la base de datos.
- [django]
  - **check**: verifica la configuracion de Django en busca de problemas.
  - **compilemessages**: compila archivos de mensajes(.po) a archivos binarios(.mo).
  - **createcachetable**: Crea la tabla de cache en la base de datos.
  - **dbshell**: Accede a la shell de la base de datos.
  - **diffsettinng**: Muestra las diferencias entre la configuración actual y la configuración por defecto.
  - dumpdata: Exporta datos de la base de datos enformato JSON.
  - **flush**: Borra todos los datos de lña base de datos  sin afectar a la estructura.
  - **inspectdb**: Genera modelos de Django  basados en una base de datos existente.
  - **loaddata**: Carga datos desde archivos fixtures.
  - **makemessages**: Crea archivos de mensajes(.po) a partir del codigo fuente.
  - **makemigrations**: crea nuevas migraciones.
  - **migrate**: Aplica migraciones a la base de datos.
  - **optimizemigration**: Optimiza las migraciones existentes.
  - **sendtestemail**: Envía un correo electrónico de prueba.
  - **shell**: Inicia la consola interactiva de Django.
  - **showmigrations**: Muestra todas las migraciones y su estado.
  - **sqlflush**: Muestra las declaraciones SQL para realizar un flush de la base de datos.
  - **sqlmigrate**: Muestra las declaraciones SQL para una migración específica.
  - **sqlsequencereset**: Muestra las declaraciones SQL para reiniciar secuencias de la base de datos.
  - **squashmigrations**: Combina migraciones antiguas en una sola.
  - **startapp**: Crea una nueva aplicación Django.
  - **startproject**: Crea un nuevo proyecto Django.
  - **test**: Ejecuta las pruebas definidas en la aplicación.
  - **testserver**: Inicia un servidor para pruebas.
- [sessions]
  - **clearsessions**: Elimina las sesiones de usuarios expiradas.
- [staticfiles]
  - **collectstatic**: Recopila archivos estáticos en una ubicación central.
  - **findstatic**: Muestra la ubicación de un archivo estático.
  - **runserver**: Inicia el servidor de desarrollo de Django.




## Borradores


#### Intalando *pip*
Para instalar este paquete debemos utilizar `pip install Django`, añadiendo laversion que queremos instalar con `==5.0`. En nuestro caso la ultima version disponible actualmente.

1) Actualizamos los paquetes.
```
sudo apt-get update
```
```
sudo apt-get upgrade
```
2) Instalamos pip.
```
sudo apt install python3-pip
```
3) Comprobamos que se a instalado correctamente.
```
pip --V
```
> Esta es otra forma de ver la version del gestor de paquetes de python instalada.
