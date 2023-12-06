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
      - [Intalando *pip*](#intalando-pip)
      - [Instalando el modulo de Django](#instalando-el-modulo-de-django)
    - [Instalar Visual Studio Code](#instalar-visual-studio-code)
  - [Generar nuestro primer proyecto con *Django*](#generar-nuestro-primer-proyecto-con-django)
  - [Fuentes](#fuentes)

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
wget https://www.python.org/ftp/python/3.12.0/Python-3.12.0b3.tgz
tar -xvf Python-3.12.0b3.tgz
```

5) Ahora configuramos el entorno de compilacion. Esto analiza la congiguracion del sistema yestablece opciones especificas para compilar Python de acuerdo con las capacidades y configuraciones de tu maquina.
   - --enable-optimizations: Esta opción indica que se deben incluir optimizaciones durante el proceso de compilación. Esto puede aumentar el rendimiento de la ejecución de Python, ya que el código se compilará con optimizaciones específicas para tu arquitectura.
```
cd Python-3.12.0b3
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

#### Intalando *pip*
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

#### Instalando el modulo de Django
Para instalar este paquete debemos utilizar `pip install Django`, añadiendo laversion que queremos instalar con `==5.0`. En nuestro caso la ultima version disponible actualmente.

```
pip install Django==5.0
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

## Generar nuestro primer proyecto con *Django*
[Tabla de contenidos](#tabla-de-contenidos)



## Fuentes
- [Django projects](https://www.djangoproject.com/)
- [Tutorial Python](https://docs.python.org/es/3/tutorial/)
- [Instalacion de Python](https://python-guide-es.readthedocs.io/es/latest/starting/install3/linux.html)
- [video tutorial intalacion Python 3.12.0](https://www.makeuseof.com/install-python-ubuntu/)
- [InstalacionVSCode](https://alfonsomozkoh.github.io/2020/07/01/como-instalar-visual-studio-code-en-linux.html)

