# Python y Django

--------------

[//]: # (version: 1.0)
[//]: # (author: Jose Carlos Limones Hernandez)
[//]: # (date: 2020-12-8)

## Tabla de contenidos

- [Python y Django](#python-y-django)
  - [Tabla de contenidos](#tabla-de-contenidos)
  - [1- Introducción](#1--introducción)
  - [2.Instalación](#2instalación)
    - [2.1.Instalacion de Python en linux](#21instalacion-de-python-en-linux)
    - [Instalación de *Django* en linux](#instalación-de-django-en-linux)
      - [Instalando el modulo de Django](#instalando-el-modulo-de-django)
    - [Instalar Visual Studio Code](#instalar-visual-studio-code)
  - [Generar nuestro primer proyecto con *Django*](#generar-nuestro-primer-proyecto-con-django)
    - [¿Que es un entorno virtual?](#que-es-un-entorno-virtual)
    - [Cómo usar un entorno virtual en Django](#cómo-usar-un-entorno-virtual-en-django)
    - [Crea tu proyecto](#crea-tu-proyecto)
    - [manage.py](#managepy)
      - [Lista de comandos de manage.py](#lista-de-comandos-de-managepy)
  - [Principales componentes de Django](#principales-componentes-de-django)
  - [Cómo funciona Django](#cómo-funciona-django)
  - [Primer contacto con Django](#primer-contacto-con-django)
    - [Creando una app](#creando-una-app)
      - [¿Que es una *app*?](#que-es-una-app)
      - [Como crear una app](#como-crear-una-app)
    - [Vistas](#vistas)
      - [Creando una vista(Ejemplo)](#creando-una-vistaejemplo)
      - [Utilizar el metodo en una URL](#utilizar-el-metodo-en-una-url)
      - [Hello World](#hello-world)
      - [Multiples vistas y URLs](#multiples-vistas-y-urls)
    - [Navegación entre rutas](#navegación-entre-rutas)
    - [parámetros en ruta](#parámetros-en-ruta)
    - [Parámetros opcionales](#parámetros-opcionales)
    - [Redirecciones](#redirecciones)
    - [Vistas Base](#vistas-base)
    - [Templates en Django](#templates-en-django)
      - [¿Como se utlizan?](#como-se-utlizan)
      - [Layout, bloques y herencia de plantillas](#layout-bloques-y-herencia-de-plantillas)
      - [Vistas, Templates y Variables](#vistas-templates-y-variables)
      - [URLs en las templates](#urls-en-las-templates)
      - [Fechas](#fechas)
      - [Condicionales -if templates Django](#condicionales--if-templates-django)
      - [Bucle -for template Django](#bucle--for-template-django)
        - [Funcionalidades extras de bucle -for](#funcionalidades-extras-de-bucle--for)
      - [Filtros](#filtros)
        - [Crear filtros personalizados](#crear-filtros-personalizados)
      - [Includes en Django](#includes-en-django)
        - [{% include %}](#-include-)
        - [{% include with %}](#-include-with-)
      - [Comentarios](#comentarios)
    - [Archivos estáticos](#archivos-estáticos)
      - [Estilos y apariencia visual con Django](#estilos-y-apariencia-visual-con-django)
  - [Modelos](#modelos)
    - [Migraciones en Django](#migraciones-en-django)
    - [Ejemplos para entender los modelos y migraciones](#ejemplos-para-entender-los-modelos-y-migraciones)
    - [Crear y aplicar el primer modelo](#crear-y-aplicar-el-primer-modelo)
    - [Consultas básicas](#consultas-básicas)
  - [Fuentes](#fuentes)

## 1- Introducción

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

## 2.Instalación

[Tabla de contenidos](#tabla-de-contenidos)

### 2.1.Instalacion de Python en linux

> En este apartado veremos como instalar Python por terminal en linux.

- Para ver si tenemos instalado Python y en el caso de que este instalado ver que version tenemos:

```bash
python --version
```

> Si tenemos instalada a partir de la version 3 no es necesario seguir los siguientes pasos a no ser que deseemos instalar la ultima version de Python.

- Lo siguiente que tendemos que hacer es actualizar la lista de paquetes con:

```bash
sudo apt-get update
```

- para descargar la ultima versiòn de python:
  - Primero debemos descargar el PPA(Personal Package Archive) llamado "deadsnake", que proporciona versiones actualizadas de python para tu sistema y volveremos a actualizar la lista de paquetes:

```bash
sudo add-apt-repository ppa:deadsnakes/ppa
sudo apt-get update
```

- Descargamos la version que deseemos con wget y la descomprimimos:

```bash
wget https://www.python.org/ftp/python/3.x.y/Python-3.x.y.tgz
tar -xvf Python-3.x.y.tgz
```

- Ahora configuramos el entorno de compilacion. Esto analiza la congiguracion del sistema yestablece opciones especificas para compilar Python de acuerdo con las capacidades y configuraciones de tu maquina.
  - --enable-optimizations: Esta opción indica que se deben incluir optimizaciones durante el proceso de compilación. Esto puede aumentar el rendimiento de la ejecución de Python, ya que el código se compilará con optimizaciones específicas para tu arquitectura.

```bash
cd Python-3.x.y
./configure --enable-optimizations
```

- Ahora compilaremos los archivos necesarios con el comando:(Esto llevara unos minutos)

```bash
sudo make install
```

Ahora ejecute el comando:

```bash
python3
```

y podra usar Python en la terminal.

### Instalación de *Django* en linux

[Tabla de contenidos](#tabla-de-contenidos)

Lo primero que debemos hacer es saber si tenemos instalado el gestor de paquetes de Python.

```bash
pip --version
```

> En caso de que este instalado nos dira la version del gestor de paquetes.

#### Instalando el modulo de Django

Para instalar este paquete debemos utilizar

```bash
sudo apt install python3-django
```

Ahora con el siguiente comando comprobamos que Django esta instalado y su version:

```bash
pip list | grep Django
```

### Instalar Visual Studio Code

[Tabla de contenidos](#tabla-de-contenidos)

Empezamos Actualizando paquetes:

```bash
sudo apt-get update
```

Lo siguiente sera descargar el repositorio de Visual Studio Code:

```bash
sudo add-apt-repository "deb [arch=amd64] https://packages.microsoft.com/repos/vscode stable main"
```

Ahora actualizamos el sistema de nuevo y e instalamos VSCode.

```bash
sudo apt update
sudo apt install code
```

Veremos la version instalada con:

```bash
code -v
```

Ahora podemos abrir VSCode desde la terminal.

```bash
code
```

## Generar nuestro primer proyecto con *Django*

[Tabla de contenidos](#tabla-de-contenidos)

Crearemos un directorio donde trabajaremos con Django.

```bash
mkdir AprendiendoDjango
```

> Deberas usar camelCase, UpperCamelCase o snake_case.
>
### ¿Que es un entorno virtual?

Un entorno virtual (también conocido como virtualenv) es una herramienta que ayuda a gestionar las dependencias de un proyecto de software de manera aislada del sistema operativo y de otros proyectos. En el caso de Django (un marco de desarrollo web para Python), el uso de un entorno virtual es común y recomendado por varias razones:

1. Aislamiento de Dependencias:

Un entorno virtual permite tener una copia independiente de Python y las bibliotecas específicas que tu proyecto necesita. Esto asegura que las dependencias de un proyecto no interfieran con las de otro.
2. Versiones de Python:

Permite utilizar diferentes versiones de Python para diferentes proyectos. Esto es útil cuando tienes proyectos que requieren versiones específicas de Python.
3. Facilita la Reproducibilidad:

Al especificar las dependencias de tu proyecto en un archivo requirements.txt, puedes fácilmente recrear el entorno virtual en otro lugar o compartirlo con otros desarrolladores, asegurando que todos estén utilizando las mismas versiones de las bibliotecas.
4. Evita Conflictos con el Sistema Operativo:

Evita conflictos entre las bibliotecas del sistema operativo y las bibliotecas del proyecto. Un entorno virtual proporciona un espacio aislado donde las bibliotecas pueden instalarse sin afectar al sistema global.
5. Facilita la Mantenibilidad:

Hace que la gestión de dependencias sea más fácil y mantenible. Puedes tener diferentes versiones de bibliotecas para diferentes proyectos sin afectar el sistema principal.
6. Mejora la Seguridad:

Al tener un entorno virtual específico para cada proyecto, limitas el acceso a las bibliotecas y dependencias específicas de ese proyecto, reduciendo el riesgo de conflictos y mejorando la seguridad.

### Cómo usar un entorno virtual en Django

Crear un Entorno Virtual:

Ejecuta el siguiente comando para crear un entorno virtual en la carpeta de tu proyecto:

```bash
python -m venv venv
```

Activar el Entorno Virtual:

```bash
source venv/bin/activate
```

Desactivar el Entorno Virtual:

```bash
deactivate
```

Instalar Dependencias:

Una vez que el entorno virtual está activado, puedes instalar las dependencias del proyecto utilizando pip install -r requirements.txt.
Usar un entorno virtual es una buena práctica en el desarrollo de software en Python y es especialmente útil en proyectos web como Django, donde la gestión de dependencias es crucial.

> Es buena práctica crear un archivo requeriments.txt para indicar la librerias y versiones utilizadas en el proyecto.

```bash
pip freeze > requeriments.txt
```

De este modo podemos instalar todos las dependencias necesarias para nuestro proyecto.

Para iniciar un proyecto con django nos vamos a la carpeta creada y utilizamos.

### Crea tu proyecto

```bash
django-admin startproject aprendiendoDjango
```

Esto nos creara un directorio con el nombre del proyecto con varios ficheros que veremos mas adelante entre ellos esta manage.py.

### manage.py

El fichero creado manage.py es un script de line de comandos que se utiliza para realizar tareas administrativas realacionadas con un proyecto Django y se encuentra en el directorio raiz del proyecto.

Con el siguiente comando veremos todos los comandos y que poodemos hacer con ellos:

```bash
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

## Principales componentes de Django

[Tabla de contenidos](#tabla-de-contenidos)

1) **ORM(Object-Relational-Mapping)**
    > Django incluye un ORM que facilita la interacción con bases de datos relacionales. Los modelos de Django definen en Python y se mapean a tablas de base de datos,permitiendo a los desarrolladores realizar operaciones de base de datos de manera más intuitiva.
2) **MVC(Model-View-Controller)**
    > Django sigue el patrón de diseño Modelo-Vista-Controlador, aunque a menudo se le llama Modelo-Vista-Plantilla (MVT) en el contexto de Django. Los modelos representan la estructura de datos, las vistas gestionan la lógica de presentación y las plantillas definen la presentación de los datos.
3) **Sistema de plantillas**
    > Django proporciona un sistema de plantillas que permite separar la logica de presentacion del codigo Python, facilitando la ceracion de páginas web dinámicas.
4) **Enrutamiento y Vistas**
    > El enrutador de Django dirige las solicitudes HTTP a las vistas correspondientes. Las vistas correspondientes son funciones de Python que toman solicitudes y devuelven respuestas, y son responsables de procesar la lógica de la aplicación.
5) **Admin Site**
    > Django incluye un panel de administración automático que facilita la gestión de modelos y datos de la base de datos sin tener que crear una interfaz de administración personalizada.
6) **Sistema de formularios**
    > Django proporciona herramientas para crear y procesar formularios de manera sencilla, facilitando la interaccion con los usuarios.
7) **Manejo de URL**
    > Django utiliza un sistema de enrutamiento basados en patrones de URL para dirigir lsa solicitudes a las vistas correspondientes.

## Cómo funciona Django

[Tabla de contenidos](#tabla-de-contenidos)

1) **Solicitud y enrutamiento**
    > Cuando se recibe una solicitud HTTP, el sistema de enrutsamiento de Django(definido en el archivo "urls.py") dirige la solicitud a ubna vista especifica.
2) **Vistas y lógica de Aplicación**
    > La vista es una funcion de python que maneja la logica de la aplicación. Puede acceder a la base de datos procesar datos y devolver una respuesta.
3) **Modelo y Base de Datos**
    > Los modelos de Django definen la estructura de la base de datos. El ORM se encarga de traducir las operaciones de la base de datos a operaciones en objetos Python.
4) **Platillas y Presentación**
    > Las plantillas de Django se utilizan para definir la presentación de los datos generados por las vistas. Estas plantillas son procesadas y enviadas al cliente.
5) **Respuesta HTTP**
    > Django genera una respuesta HTTP que se envia de vuelta al navegador del usuario.

- Django facilita la creación de aplicaciones web robustas al proporcionar una estructura organizada y herramientas poderosas, permitiendo a los desarrolladores construir aplicaciones de manera eficiente y mantenible. Además, su énfasis en la seguridad y las mejores prácticas lo convierten en una opción popular para el desarrollo web en Python.

## Primer contacto con Django

[Tabla de contenidos](#tabla-de-contenidos)

### Creando una app

[Tabla de contenidos](#tabla-de-contenidos)

#### ¿Que es una *app*?

- Si miramos el directorio creado en el capitulo anterior dentro veremos una serie de archivos y una carpeta con el nombre de nuestro proyecto, esto es un paquete donde tenemos el archivo ***settings.py***.
- Empezaremos a configurarlo por ***INSTALLED_APPS***.

```python
INSTALLED_APPS = [
    'django.contrib.admin',
    'django.contrib.auth',
    'django.contrib.contenttypes',
    'django.contrib.sessions',
    'django.contrib.messages',
    'django.contrib.staticfiles',
]
```

> Esto es una lista con con varias aplicaciones que generan distintas funcionalidades.

- **admin**: Proporciona la interfaz de administracion de Django que te permite gestinar modelos y datos directamente desde el navegador.
- **auth**: Gestiona la autentificación y autorización de usuarios.
- **contenttypes**: Permite la asociación de modelos con tipos de contenido.
- **sessions**: Proporciona soporte para sesiones de usuario.
- **messages**: Maneja mensajes de un lado a otro entre vistas.
- **staticfiles**: Gestiona archivos estaticos como CSS, JavaScript e imágenes para tu aplicación.

> Puedes agregar tanatas aplicaciones como desees.

- En resumen, una aplicación es un paquete dentro de Django y todas estas aplicaciones forman nuestro proyecto.

#### Como crear una app

1) abre la terminal en el directorio creado para el proyecto(AprendiendoDjango).
2) Para crear una app:

```bash
python3 manage.py startapp
```

> Esto generara un directorio con varios archivos que iremos viendo.

### Vistas

[Tabla de contenidos](#tabla-de-contenidos)

- Las **vistas** se refieren a las funciones o clases que manejan las solicitudes HTTP y devuelven respuestas. Las vistas son responsables de procesar la entrada del usuario (la solicitud) y producir la salida (la respuesta).

- En Django las vistas se crean o modifican desde el fichero *views.py* que esta en el directorio de nuestra app.

> En este fichero vemos como se importan los ***shortcuts***,

- los "shortcuts" (atajos) son funciones y clases proporcionadas por el módulo django.shortcuts que facilitan y simplifican tareas comunes en el desarrollo de aplicaciones web. Estos atajos son una manera conveniente de realizar operaciones que se realizan frecuentemente sin tener que escribir una cantidad extensa de código.

> Para mas informacion sobre -> [SHORTCUTS](https://docs.djangoproject.com/en/5.0/topics/http/shortcuts/).
>> Para continuar a partir de este punto deberia tener unas nociones basicas de fundamentos de la programacion y una base de programacopn y sintaxis de [Python](https://docs.python.org/es/3.12/tutorial/index.html).

#### Creando una vista(Ejemplo)

- En el fichero views.py, debemos importar HttpResponse, que es un objeto que representa la respuesta HTTP que sera enviada al navegador de lusuario cuando se realiza una solicitud a la vista.

```python
from django.shortcuts import render, HttpResponse

def hola_mundo(request):
    return HttpResponse("hola mundo con Django!!")
```

> Por convención los métodos y funciones en python seran con camelCase.
***Contructor de HttpResponse:***

```python
HttpResponse(content=b'', status=200, content_type='text/html', charset=None)
```

- Si nos fijamos esta vista es una simple función de Python que recibe un parametro llamado *request*, que es un parametro que me permite recibir datos de peticiones que haga a esta URL y devuelve una cadena de texto.

Para ver el funcionamiento de nuestra vista necesitamos cargar el metodo o utilizarlo en una URL.

#### Utilizar el metodo en una URL

Para utilizar el metodo en una URL debemos abrir el fichero llamado *urls.py* del directorio con el mismo nombre creado dentro de nuestro proyecto.

- Primero importaremos la funcion:

```python
from myapp import views
```

- Despues modificaremos la lista urlpatterns:

```python
urlpatterns = [
    path('admin/', admin.site.urls),
    path('hola-mundo/', views.hola_mundo, name="hola_mundo")
]
```

- Desglosamos el objeto *path*:
  - path('hola-mundo/', ...) -> define la URL que activara la vista.
  - views.hola_mundo -> especifica la funcion que se ejecutara cuando la URL coincida.
  - name="hola_mundo" -> Asigna un nombre a la URL. Este nombre puede ser utilizado en otras partes del código para referenciar esta URL de manera más fácil. Por ejemplo, en las plantillas o en la generación de URLs dentro de las vistas.

#### Hello World

Ya tenemos nuestra primera vista preparada para verla en el navegador.

***¿Como lo hacemos?***

- Debemos arrancar el servidor de Django:

```bash
python3 manage.py runserver
```

- Introducimos la URL que nos da el servidor en el navegador o pulsamos ctrl y hacemos click en ella.
- En esta ocasión en vez de mostrar la pagina por defecto de Django nos devuelve un error 404. Esto sucede porque la primera ruta(path) que tenemos en *urls.py* es "hola-mundo/", asi que debemos añadirle esto a la URL.

**Ya tenemos El hola mundo!**

#### Multiples vistas y URLs

Ahora crearemos otro método en *views.py*, por ejemplo una pagina de inicio:

```python
def index(request):
    return HttpResponse("""
        <h1>Inicio</h1>
    """)
```

Ya tenemos nuestro segundo método, solo nos queda asignarle una ruta, para ello volvemos al fichero *urls.py*:

```python
urlpatterns = [
    path('admin/', admin.site.urls),
    path('', views.index, name="index"),
    path('index', views.index, name="inicio"),
    path('hola-mundo/', views.hola_mundo, name="hola_mundo")
]
```

En este ejemplo dejamos vacia la cadena que recoge como primer argumento para que al abrir la raiz de la URL nos muestre nuestra pagina de inicio.

### Navegación entre rutas

[Tabla de contenidos](#tabla-de-contenidos)

- Para entender como funciona lo haremos con un ejemplo:
En el fichero views.py declararemos la siguiente variable:

```python
layout = """
<h1>Sitio web con Django | Jose Carlos Limones</h1>
<hr/>
<ul>
    <li>
    <a href="/">Inicio</a>
    </li>
    <li>
    <a href="/hola-mundo">Hola mundo</a>
    </li>
    <li>
    <a href="/pagina">Pagina 1</a>
    </li>
</ul>
<hr/>
"""
```

- Y modificamnos las funciones ya creadas:

```python
def index(request):
    return HttpResponse(layout+"""
        <h1>Inicio</h1>
    """)

def hola_mundo(request):
    return HttpResponse(layout+"""
        <h1">hola mundo con Django!!</h1>
        <h3>Soy Jose Carlos Limones</h3>
        """)

def pagina(request):
    return HttpResponse(layout+"""
        <h1>Esta es la Pagina 1!!</h1>
        """)
```

> *Recuerda modificar el fichero urls.py*.

### parámetros en ruta

[Tabla de contenidos](#tabla-de-contenidos)

Como sabemos en la URL podemos pasar parametros, en este apartado veremos como se tratan.

Creamos una supuesta pagina llamada "contacto":

```python
def contacto(request, nombre):
  return HttpResponse(layout+f"<h1>Contacto {nombre} </h1>")
```

- Para poder tratar estos parametros debemos indicarle al path que tipo de parametro es y su nombre de esta forma:

```python
 path('contacto/<str:nombre>', views.contacto, name="contacto")
```

Ahora probamos en nuestro navegador:

```bash
http://127.0.0.1:8000/contacto/jose%20Carlos
```

> el "%20" el navegador lo tratara como un espacio.

Si queremos añadir mas parametros simplemente lo haremos asi:

- En views.py:

```python
def contacto(request, nombre, apellido):
  return HttpResponse(layout + f"<h1>Contacto {nombre} </h1>")
```

- En urls.py:

```python
    path('contacto/<str:nombre>/<str:apellido>', views.contacto, name="contacto")
```

- En el navegador:

```bash
http://127.0.0.1:8000/contacto/Jose%20Carlos/Limones
```

### Parámetros opcionales

[Tabla de contenidos](#tabla-de-contenidos)

- Podemos hacer que los parámetros sean opcionales inicializandolos a null o vacío de esta forma:

```python
def contacto(request, nombre="", apellido=""):
    html = ""

    if nombre and apellido:
        html = f"<h3>{nombre} {apellido}"
    elif nombre:
        html = f"<h3>{nombre}"
    
    return HttpResponse(layout + f"<h2>Contacto </h2>" + html)
```

- Despues en urls.py debemos darle las opciones de cada path:

```python
path('contacto/', views.contacto, name="contacto"),
path('contacto/<str:nombre>', views.contacto, name="contacto"),
path('contacto/<str:nombre>/<str:apellido>', views.contacto, name="contacto")
```

### Redirecciones

[Tabla de contenidos](#tabla-de-contenidos)

Django viene con una aplicación de redirecciones opcional. Te permite almacenar una redireccion en una base de datos y maneja la redirección por ti.

- En este ejemplo vamos a dirigir la pagina de contacto con los parametros necesarios:

  - importar el *shortcut* ***redirect***.

  ```python
  from django.shortcuts import redirect
  ```

  - Metemos una redireccion en nuestro metodo o función.

  ```python
  def pagina(request, redirigir = 0):
      if redirigir == 1:
          return redirect('contacto', nombre="Jose Carlos", apellido="Limones")

      return HttpResponse(layout+"""
          <h1>Esta es la Pagina 1!!</h1>
          """)
  ```

  - Escribimos el nuevo path:

  ```python
      path('pagina/<int:redirigir>', views.pagina, name="pagina"),
  ```

  - Ahora nos redirigira a contacto con los paramtros pasados escribiendo en el navegador:

   ```bash
   http://127.0.0.1:8000/pagina/1
   ```
  
> Recuerda que debemos mantener el path anterior.

### Vistas Base

[Tabla de contenidos](#tabla-de-contenidos)

- Django proporciona una serie de vista(objetos) ya creadas. Estas vistas han sido creadas para usarlas como plantilla, es decir crear clases que hereden de de esta base.

- Todas las demás vistas basadas en clases heredan de esta base. clase. No es estrictamente una vista genérica y, por lo tanto, también se puede importar desde *django.views*.
- El diagrama de flujo del metodo es:
  - setup() -> Se llama al inicio de cada solcitud par realizar cualquier configuracion necesaria.
  - dispatch() -> Se llama para maneja la solicitud HTTP. Determina qué método HTTP se está utilizando y llama al método correspondiente (por ejemplo, get(), post(), etc.).
  - http_method_not_allowed() -> Este metodo se invoca si el metodo de la solicitud HTTP no esta permitido.
  - options() -> Este método se invoca cuando se recibe una solicitud OPTIONS en la vista. La implementación predeterminada devuelve una respuesta HTTP con los métodos permitidos en el encabezado "Allow".

Ejemplo views.py:

```python
from django.http import HttpResponse
from django.views import View


class MyView(View):
    def get(self, request, *args, **kwargs):
        return HttpResponse("Hello, World!")
```

Ejemplo urls.py

```python
from django.urls import path

from myapp.views import MyView

urlpatterns = [
    path("mine/", MyView.as_view(), name="my-view"),
]
```

- La lista de métodos permitidos:

> ["get", "post", "put", "patch", "delete", "head", "options", "trace"]

### Templates en Django

[Tabla de contenidos](#tabla-de-contenidos)

Hasta ahora hemos trabajado con el codigo html directamente en las vista, pero esa no es la forma correcta de utilizar Django.

En Django, los templates son archivos de texto que contienen marcadores o placeholders que luego son reemplazados por valores específicos cuando la página se renderiza dinámicamente. Estos marcadores están rodeados por doble llave y siguen la sintaxis del lenguaje de plantillas de Django

#### ¿Como se utlizan?
>
> Si estas utilizando Visual Studio Code puedes descargarte su extension, pichando en la pestaña de la barra de navegacion izquierda y poniendo en el buscador *Django*. Te aparecera la primera.

- Los templates hacen que nustras app esten mejor estructuradas y organizadas para ello hay que crear nuestra carpeta de templates dentro de el directorio de la app.

```bash
cd myapp
mkdir templates
```

- En esta carpeta crearemos todas nuestras plantillas siempre organizandola de la mejor manera y la mas intuitiva para cuando llegue el mantenimiento de nuestro proyecto. En este caso practico las crearemos directamente en el directorio.
- Creamos un fichero por template.
Ejemplo myapp/templates/pagina.html:

```python
<h1>inicio</h1>
<p>Esta es la pagina de inicio</p>
```

- Ahora tenemosque modificar views.py:

```python
def pagina(request, redirigir = 0):
    if redirigir == 1:
        return redirect('contacto', nombre="Jose Carlos", apellido="Limones")

    return render(request, 'pagina.html')
```

> Usamos la funcion **[render()](#vistas-templates-y-variables)** cuando queremos que nos devuelva un template, pasandole como argumento la avariable **request** y el **nombre del template** como minimo.

De esta forma nos mostrara nuestro primer template.

#### Layout, bloques y herencia de plantillas

- Como vemos el codigo no es limpio ¿como soluciona esto Django?
- Django utiliza un sistema de bloques y herencia que nos deja un proyecto estructurado y codigo limpio.
-

Ejemplo:

1) Creamos *layout.html* en nuestro directorio de templates y le añadimos una estructura basica de html.
2) En la etiqueta title creamos un bloque con el nobre title
3) Dentro del body crearemos un *div* que nos servira de ontenedor con el atributo *id* y el valor de *content*.
4) Dentro del div crearemos nuestro bloque.
  
Ejemplo layout.html

```django
<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>
        {% block title %}
        
        {% endblock title %}
        | Jose Carlos Limones
    </title>
</head>
<body>
    <h1>Sitio web con Django | Jose Carlos Limones</h1>
    <hr/>
    <ul>
        <li>
            <a href="/">Inicio</a>
        </li>
        <li>
            <a href="/hola-mundo">Hola mundo</a>
        </li>
        <li>
            <a href="/pagina">Pagina 1</a>
        </li>
        <li>
            <a href="/contacto">contacto</a>
        </li>
    </ul>
    <hr/>
    <div id ="content">
        {% block content %}

        {% endblock content %}
    </div>
    <footer>
        Master en Python &copy Jose Carlos Limones
    </footer>
</body>
</html>
```

Ejemplo index.html

```django
{% extends "layout.html" %}

{% block title %}
index
{% endblock title %}

{% block content %}
<h1>inicio</h1>
<p>Esta es la pagina de inicio</p>
{% endblock content %}
```

- En la primera linea le indicamos a Django el template de donde tiene que heredar, esto herda la estructura html.
- Como vemos los bloques son como etiquetas deben abrirse y cerrarse.
- A las etiquetas de bloques se le añadira el nombre del bloque donde debe ir.
  
> Si en nuestro contenedor tenemos algun contenido este se machacara al cargar el bloque.

Para solucinar esto debemos indicar a nuestro template que debe heredar el contenido insertando en el bloque lo siguiente:

```django
{{ block.super }}
```

#### Vistas, Templates y Variables

Django nos da la posibilidad de enviar variables de nuestras vistas a los templates.

La forma de hacerlo es añador un tercer argumento al método **render()**:

Ejemplo views.py:

```python
def index(request):
  return render(request, 'index.html', {
    'title': 'Inicio',
    'nombre': 'JC Limones',
    'mi_variable': 'Soy un dato en la vista'
    })
```

Ahora nos vamos a nuestro template y con la doble llave podemos insertar nuestra variable en el codigo.

Ejemplo index.html:

```Django
{% extends "layout.html" %}

{% block title %}

{{title}}

{% endblock title %}

{% block content %}

  <h1 class="title" >{{title}}</h1>
  <p>mi variable: {{mi_variable}}</p>
  <p>nombre: {{nombre}}</p>
  <p>Esta es la pagina de inicio</p>

{% endblock content %}
```

#### URLs en las templates

Si nos observamos el fichero *layout.html*, en los atributos href de los enlaces tenemos las direcciones [*hardcodeadas*](https://es.wikipedia.org/wiki/Codificaci%C3%B3n_r%C3%ADgida), es decir si tenemos que cambiar alguna url tambien la tendremos que cambiar en este fichero.

Podemos utilizar una instruccion de una template pasandole el nombre(name) de nuestra path en urls.py.

```django
<li>
    <a href="{% url 'index' %}">Inicio</a>
</li>
<li>
    <a href="{% url  'hola_mundo'%}">Hola mundo</a>
</li>
<li>
    <a href="{% url 'pagina' %}">Pagina 1</a>
</li>
<li>
    <a href="{% url 'contacto' %}">contacto</a>
</li>
```

Desde esta instrucción podemos enviar los valores de las variables que necesitamos en orden de declaración.

```django
 <a href="{% url 'contacto' 'Jose Carlos' 'Limones'%}">contacto</a>
```

o asi:

```django
 <a href="{% url 'contacto' nombre='Jose Carlos' apellido='Limones'%}">contacto</a>
```

> Ya podemos cambiar la url del path en el fichero urls.py sin tener que cambiar los enlaces a esa pagina.

#### Fechas

Podemos mostrar la fecha de mnuestro servidor de la siguiente forma:

```django
{% now "Y:M:D h:m:s" %}
```

#### Condicionales -if templates Django

Los condicionales if funcionan exactamente como en python, solo cambia su sintaxis. Si borramos la variable "nombre" pasada en el diccionario de la funcion render() veremos como funciona.

Ejemplo index.html:

```django
{% if nombre %}
    <p>nombre: {{nombre}}</p>
{% else %}
        <strong>El nombre no existe</strong>
{% endif %}
```

#### Bucle -for template Django

Los bucles for al igual que los if solo cambia su sintaxis, veamos un ejemplo.

Ejemplo views.py:

```python
def index(request):
    lenguajes = ['C', 'C++', 'Python', 'PHP', 'JavaScript']
    return render(request, 'index.html', {
        'title': 'Inicio',
        'nombre': 'JC Limones',
        'mi_variable': 'Soy un dato en la vista',
        'lenguajes': lenguajes
    })
```

Ejemplo index.html:

```django
<h3>Listado de lenguajes</h3>
<ul>
    {% for lenguaje in lenguajes %}
    <li>{{lenguaje}}</li>
    {% endfor %}
</ul>
```

##### Funcionalidades extras de bucle -for

- for...empty:
  - Puedes utilizar **empty** para manejar el caso de que la secuencia este vacia

```django
{% for item in my_list %}
    {{ item }}
{% empty %}
    La lista está vacía.
{% endfor %}

```

- for...if:
  - puedes usar la etiqueta if para filtrar los elementos que cumplen ciertas condiciones

```django
{% for item in my_list %}
    {{ item }}
{% empty %}
    La lista está vacía.
{% endfor %}

```

- forloop:
  - La variable forloop proporciona informacionadicional sobre el bucle actual.

```django
{% for item in my_list %}
    {{ forloop.counter }}: {{ item }}
    {% if forloop.last %}(Último elemento){% endif %}
{% endfor %}
```

- forloop.counter: Número de la iteración actual (comienza en 1).
- forloop.counter0: Número de la iteración actual, indexado desde 0.
- forloop.revcounter: Número de iteraciones desde el final (comienza en 1).
- forloop.revcounter0: Número de iteraciones desde el final, indexado desde 0.
- forloop.first: True si es la primera iteración.
- forloop.last: True si es la última iteración.

#### Filtros

En Django, los filtros son funciones que se aplican a las variables en las plantillas para modificar su contenido o formato. Los filtros permiten realizar diversas operaciones, desde el formateo de cadenas hasta la manipulación de datos en las plantillas. Los filtros se aplican a las variables utilizando el siguiente formato:

```django
{{ variable|filtro }}
```

> Estos son unos ejemplos de filtros:

1) **date:**
   - **Descripción:** Formatea una fecha según el formato especificado.
   - **Ejemplo:** `{{ my_date|date:"F j, Y" }}`

2) **default:**
   - **Descripción:** Establece un valor predeterminado si la variable es nula.
   - **Ejemplo:** `{{ my_variable|default:"No disponible" }}`

3) **length:**
   - **Descripción:** Obtiene la longitud de una lista o cadena.
   - **Ejemplo:** `{{ my_list|length }}`

4) **lower y upper:**
   - **Descripción:** Convierte una cadena a minúsculas o mayúsculas.
   - **Ejemplo:** `{{ my_string|lower }}` / `{{ my_string|upper }}`

5) **default_if_none:**
   - **Descripción:** Establece un valor predeterminado solo si la variable es `None`.
   - **Ejemplo:** `{{ my_variable|default_if_none:"No disponible" }}`

6) **floatformat:**
   - **Descripción:** Formatea un número de punto flotante según la cantidad de decimales especificada.
   - **Ejemplo:** `{{ my_float|floatformat:2 }}`

7) **slice:**
   - **Descripción:** Obtiene una porción de una lista o cadena.
   - **Ejemplo:** `{{ my_list|slice:":2" }}`

8) **yesno:**
   - **Descripción:** Retorna un valor específico según si la variable es True, False o None.
   - **Ejemplo:** `{{ my_bool|yesno:"Sí,No" }}`

9) **linebreaks:**
   - **Descripción:** Convierte saltos de línea en etiquetas de párrafo HTML.
   - **Ejemplo:** `{{ my_text|linebreaks }}`

10) **pluralize:**
    - **Descripción:** Añade una "s" al final de una palabra según el valor numérico proporcionado.
    - **Ejemplo:** `Hay {{ count }} mensaje{{ count|pluralize }}.`

Encuentra una lista completa de filtros en la [documentación oficial de Django](https://docs.djangoproject.com/en/stable/ref/templates/builtins/#built-in-filter-reference).

##### Crear filtros personalizados

Vamos a ver un ejemplo de como  crear un filtro personalizado.

1) En el directorio de nuestra app creamos un subdirectorio llamado templatetags.
2) Dantro de este directorio creamos un fichero llamado **init**.py para que se convierta en un paquete.
3) Creamos el fichero donde iran nuestros filtros, ***filters.py***.
4) En el fichero lo primero que tenemos que hacer es importar las templates.
5) El siguiente paso e crear la función que ejecutara el filtro.
6) Ahora debemos cargar los filtros en la template para poder usarlos.
Ejemplo filters.py:

```python
from django import template

register = template.Library()

@register.filter(name='saludo')

def saludo(value):
    return f"<h1 style='background:green;'>Bienvenido, {value}.</h1>"
```

Ejemplo pagina.html (template):

```python
{% load filters %}
{{ "jclimones" | saludo | safe }}
```

> ***safe*** convierte el html. Si no lo ejecutamos nos mjuestra el codigo como tal.

#### Includes en Django

##### {% include %}

En Django, el tag {% include %} se utiliza para incluir el contenido de otro archivo de plantilla dentro de la plantilla actual. Esto es útil para dividir grandes plantillas en partes más pequeñas y manejables, o para reutilizar bloques de contenido en varias plantillas.

La sintaxis basica es:

```django
{% include '/ruta/nombre_de_archivo.html' %}
```

Ejemplo:

- Creamos una nueva template, por ejemplo **contenido_template.html**.

```django
<p>Este es el contenido de la nueva template</p>
```

- Despues nos vamos a nuestro **index.html** y colocamos en la posicion que deseemos los siguiente:

```django
{% include "contenido_template.html" %}
```

> Esto nos mostrara el contenido de la nueva template en el index.

Veamos que pasaria si le quisiera pasar en la nueva template una de las variables existente en la vista.

Ejemplo contenido_template.html:

```django
<p>Este es el contenido de la nueva template y mi nombre es {{nombre}}</p>
```

Y si, respeta el valor de las variables de la vista.

##### {% include with %}

En Django, el {% include %} con la opción with permite pasar variables adicionales al archivo de plantilla incluido. Esto es útil cuando necesitas proporcionar datos específicos para el contenido que estás incluyendo.

La sintaxis básica es la siguiente:

```django
{% include 'nombre_de_archivo.html' with variable1=valor1 variable2=valor2 %}
```

Ejemplo:

- En el archivo index.html modificamos el include de esta forma:

```django
{% include 'contenido_template.html' with edad=", mi edad es de 38 años" %}
```

- El archivo contenido_template.html lo modificamos asi:

```django
<p>Este es el contenido de la nueva template y mi nombre es {{nombre}} {{edad}}</p>
```

Esta tipo de includes te permite varias opciones como **only** que indica que solo debe utilizar las variables pasadas en el include.

Ejemplo de **only** en index.html:

```django
{% include 'contenido_template.html' with edad=", mi edad es de 38 años" only %}

```

> Vemos como la variable nombre ya no aparece.

Las opciones son:

- **parsed**: La opción parsed se utiliza para indicar que el contenido de la plantilla incluida ya ha sido analizado. Esto es útil cuando se incluyen fragmentos de HTML preprocesados.

```django
{% include 'nombre_de_archivo.html' with variable_html=mi_contenido_html parsed %}
```

- **language**: La opción language se utiliza para establecer el idioma en el que se debe procesar la plantilla incluida. Por ejemplo:

```django
{% include 'nombre_de_archivo.html' with variable1=valor1 variable2=valor2 language='es' %}
```

> Estas opciones proporcionan flexibilidad al utilizar el tag include y permiten adaptar su comportamiento según las necesidades específicas de tu aplicación.

#### Comentarios

- Los comentarios en nuestras templates se pueden hacer como  en html. El problema de esto es que si le damos al inspector nos aparecera entre el codigo html.
- Pero si lo hacemos con Django sera un comentario que queda para el codigo fuente.
- Se pueden hacer de dos formas:

1) ```django
    {% comment "" %}
    Esto es un comentario.
    {% endcomment %}
    ```

2) ```django
    {% comment "Esto es un comentario." %}
    
    {% endcomment %}
    ```

### Archivos estáticos

[Tabla de contenidos](#tabla-de-contenidos)

Los archivos estáticos en el contexto del desarrollo web se refieren a recursos como archivos CSS, JavaScript e imagenes. Son aquellos que no cambian dinámicamente según la solicitud del usuario. A diferencia de los archivos dinámicos que son generados y servidos por el servidor en tiempo real.

#### Estilos y apariencia visual con Django

Para incluir nuestro css en el proyecto debemos seguir los siguientes pasos:

- Creamos en nuestra app un directorio llamado static y dentro de esta otro llamado css.

```bash
mkdir static
cd static
mkdir css
```

- Ahora crearemos nuestro archivo **styles.css**.
- En ete Archivo daremos los estilos.

Ejemplo styles.css

```css
body {
    font-family: Verdana, Geneva, Tahoma, sans-serif;
    background-color: aquamarine;
}
```

- El siguiente paso es cargar y linkear nuestro archivo.css. En la primera linea, antes de la linea de ***< !DOCTYPE html >*** cargamos los archivo estáticos.

Ejemplo layout.html:

```django
{% load static %}
```

- En el  ***< head >***

```html
<link rel="stylesheet" href="{% static 'css/styles.css' %}">
```

## Modelos

[Tabla de contenidos](#tabla-de-contenidos)

En Django, un "modelo" es una representación de una tabla en una base de datos relacional. Los modelos son utilizados para definir la estructura de la base de datos y para interactuar con ella mediante consultas. Los modelos en Django son parte del sistema de Object-Relational Mapping (ORM), que permite interactuar con la base de datos utilizando objetos de Python en lugar de consultas SQL directas.

Aquí hay algunas características clave de los modelos en Django y para qué sirven.

### Migraciones en Django

[Tabla de contenidos](#tabla-de-contenidos)

Las migraciones son una forma de realizar cambios en la estructura de la base de datos de manera controlada y evolutiva. Django utiliza un sistema de migraciones para llevar a cabo estas modificaciones.

Pasos Comunes:

- **Crear una Migración:**

  - Cuando realizas cambios en tus modelos, como agregar un nuevo campo o modificar una relación, necesitas crear una nueva migración para reflejar esos cambios.

```bash
python manage.py makemigrations
```

- **Aplicar Migraciones:**

  - Luego de crear una migración, debes aplicarla para actualizar la base de datos.

```bash
python manage.py migrate
```

- **Desplegar Migraciones Específicas:**

  - Puedes especificar el nombre de una migración para aplicar solo hasta cierto punto.

```bash
python manage.py migrate myapp 0003_migration_name
```

- **Desplegar Todas las Migraciones:**

  - Para aplicar todas las migraciones pendientes.

```bash
python manage.py migrate
```

- **Estado de Migraciones:**

  - Puedes verificar el estado actual de las migraciones.

```bash
python manage.py showmigrations
```

**Rollback y Deshacer Migraciones:**
    - Para revertir la última migración:

```bash
python manage.py migrate myapp zero
```

- Para deshacer todas las migraciones y volver a un estado vacío:

```bash
python manage.py migrate myapp zero
```

### Ejemplos para entender los modelos y migraciones

[Tabla de contenidos](#tabla-de-contenidos)

Recomendacion
> Es aconsejable utilizar el paquete de python llamado pylint.

- Pylint es una herramienta de análisis estático para código Python. Su objetivo principal es detectar errores y problemas en el código fuente, así como aplicar convenciones de estilo definidas en las PEP (Python Enhancement Proposals), como PEP 8.

Para más información -> [pylint]("https://pypi.org/project/pylint/").

```bash
pip install pylint-django
```

Para usarlo solo debemos hacer esto:

```bash
pylint mi_archivo.py
```

> Para los ejemplos vamos a utilizar la base de datos que viene por defecto SQLite que esta almacenada en el fichero ***db.sqlite3***.

Si observamos el archivo de configuración de Django(*settings.py*) vemos que hay declarado un diccionario llamado ***DATABASES***. A continuacion te doy una explicacion con detalle:

1) **default**:
    - Esto indica que estamos configurando la base de datos predeterminada para nuestra aplicación. Puedes tener múltiples bases de datos en una aplicación Django y asignar nombres distintos a cada una.
2) **ENGINE**:
    - Aquí especificamos el motor de la base de datos que Django utilizará. En este caso, 'django.db.backends.sqlite3' indica que estamos usando SQLite como motor de base de datos. SQLite es una base de datos ligera que se almacena en un archivo local y es una opción común para el desarrollo.
3) **NAME**:
    - Esto especifica la ruta al archivo de la base de datos.
        - *BASE_DIR* es una variable que apunta al directorio base de tu proyecto Django. Con la expresión BASE_DIR / 'db.sqlite3', estamos construyendo la ruta completa al archivo db.sqlite3 dentro del directorio base (Que en el caso de nuestra aplicación esta en la raiz).

### Crear y aplicar el primer modelo

[Tabla de contenidos](#tabla-de-contenidos)

- Localizamos y abrimnos el archivo **models.py**
- Creamos 2 clases, **Empleado** y **Categoria** con los siguientes atributos:

```python
from django.db import models

class Empleado(models.Model):
    nombre = models.CharField(max_length=100)
    apellidos = models.CharField(max_length=100)
    edad = models.models.IntegerField()
    autorizado = models.BooleanField()
    carta_presentacion = models.TextField()
    fecha_alta = models.DateTimeField(auto_now_add=True)


class Categoria(models.Model):
    nombre = models.CharField(max_length=100)
    nivel = models.CharField(max_length=150)
    antiguedad = models.DateField()

```

> Para informacion sobre los tipos de campos -> [models]("https://docs.djangoproject.com/en/5.0/ref/models/fields/#field-types)

- Tenemos que crear las migraciones, vamos al directorio donde se encuentra el archivo manage.py y ejecutamos:

```bash
python manage.py makemigrations
```

Esto generara una salida parecida a esta:

```bash
Migrations for 'myapp':
  myapp/migrations/0001_initial.py
    - Create model Categoria
    - Create model Empleado
```

- Aplicamos las migraciones:

```bash
python3 manage.py migrate
```

Salida:

```bash
Operations to perform:
  Apply all migrations: admin, auth, contenttypes, myapp, sessions
Running migrations:
  Applying myapp.0001_initial... OK
```

Para poder ver si todo se ha creado correctamente necesitamos una aplicación como ***DB Browser for SQLite***.

- Instalacion *SQLite*
Debian/Ubuntu:

```bash
sudo apt-get update
sudo apt install sqlite3
```

- Instalacion *DB Browser for SQLite*

```bash
sudo apt-get update
```

- Con el siguiente comando se abrira la interfaz grafica de esta aplicacion.

```bash
sqlitebrowser
```

- En la pestaña file, pinchamos en abrir base de datos y buscamos en el directorio de nuestra aplicación, ahora en la barra de navegación izquierda deberia aparecernos nuestros modelos en forma de tabla SQL.

### Consultas básicas
Django proporciona una API para realizar consultas a la base de datos de manera sencilla.

- **Obtener todos los objetos de un modelo**
  ```python
  all_books = Book.objects.all()
  ```
- **Filtrar resultados:**
  ```python
  recent_books = Book.objects.filter(publication_date__gte='2022-01-01')
  ```

- **Ordenar resultados:**
  ```python
  ordered_books = Book.objects.order_by('-publication_date')
  ```

- **Limitar resultados:**

  ```python
  first_two_books = Book.objects.all()[:2]
  ```

- **Obtener un solo objeto:**

  ```python
  specific_book = Book.objects.get(title='The Great Gatsby')
  ```

## Fuentes

[Tabla de contenidos](#tabla-de-contenidos)

- [Django projects](https://www.djangoproject.com/)
- [Tutorial Python](https://docs.python.org/es/3/tutorial/)
- [Instalacion de Python](https://python-guide-es.readthedocs.io/es/latest/starting/install3/linux.html)
- [Instalacion VSCode](https://alfonsomozkoh.github.io/2020/07/01/como-instalar-visual-studio-code-en-linux.html)
