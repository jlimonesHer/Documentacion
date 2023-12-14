# Python y Django
--------------

[//]: # (version: 1.0)
[//]: # (author: Jose Carlos Limones Hernandez)
[//]: # (date: 2020-12-8)


# Tabla de contenidos
- [Python y Django](#python-y-django)
- [Tabla de contenidos](#tabla-de-contenidos)
  - [1- Introducción](#1--introducción)
  - [2.Instalación](#2instalación)
    - [2.1.Instalacion de Python en linux](#21instalacion-de-python-en-linux)
    - [Instalación de *Django* en linux](#instalación-de-django-en-linux)
      - [Instalando el modulo de Django](#instalando-el-modulo-de-django)
    - [Instalar Visual Studio Code](#instalar-visual-studio-code)
  - [Generar nuestro primer proyecto con *Django*](#generar-nuestro-primer-proyecto-con-django)
    - [manage.py](#managepy)
      - [Lista de comandos de manage.py](#lista-de-comandos-de-managepy)
  - [Principales componentes de Django](#principales-componentes-de-django)
  - [Cómo funciona Django](#cómo-funciona-django)
  - [Django Avanzado](#django-avanzado)
    - [Migraciones en Django](#migraciones-en-django)
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
  - [Fuentes](#fuentes)

<div style="page-break-after: always;"></div>




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

<div style="page-break-after: always;"></div>

## 2.Instalación
[Tabla de contenidos](#tabla-de-contenidos)

### 2.1.Instalacion de Python en linux

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
django-admin startproject aprendiendoDjango
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

## Django Avanzado

### Migraciones en Django 
Las migraciones son una forma de realizar cambios en la estructura de la base de datos de maneara controlada y evolutiva.

1) Despues de [Generar nuestro proyecto con *Django*](#generar-nuestro-primer-proyecto-con-django).
2) Debemos migrarlo.

```
python3 manage.py migrate
```
Este paso generara una base de datos con las funcionalidades de las aplicaciones que vienen por defecto dentro de Django.

3) El siguiente paso sera arrancar nuestro servidor local:
```
python manage.py runserver
```
  > Al arrancarlo nos da informacion como la fecha y hora de arranque, la version de Django, la configuracion utilizada y la URL.

  > Si copiamos la URL en nuestro navegador veremos la pagina por defecto de Django.

### Creando una app

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
```
python3 manage.py startapp
```
> Esto generara un directorio con varios archivos que iremos viendo.


### Vistas
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
1) Debemos arrancar el servidor de Django:
```
python3 manage.py runserver
```
2) Introducimos la URL que nos da el servidor en el navegador o pulsamos ctrl y hacemos click en ella.
3) En esta ocasión en vez de mostrar la pagina por defecto de Django nos devuelve un error 404. Esto sucede porque la primera ruta(path) que tenemos en *urls.py* es "hola-mundo/", asi que debemos añadirle esto a la URL.

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
```
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
```
http://127.0.0.1:8000/contacto/Jose%20Carlos/Limones
```

### Parámetros opcionales
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
Django viene con una aplicación de redirecciones opcional. Te permite almacenar una redireccion en una base de datos y maneja la redirección por ti.

- En este ejemplo vamos a dirigir la pagina de contacto con los parametros necesarios:

  1) importar el *shortcut* ***redirect***.
  ```python
  from django.shortcuts import redirect
  ```
  2) Metemos una redireccion en nuestro metodo o función.
  ```python
  def pagina(request, redirigir = 0):
      if redirigir == 1:
          return redirect('contacto', nombre="Jose Carlos", apellido="Limones")

      return HttpResponse(layout+"""
          <h1>Esta es la Pagina 1!!</h1>
          """)
  ``` 
  3) Escribimos el nuevo path:
  ```python
      path('pagina/<int:redirigir>', views.pagina, name="pagina"),
  ```
  4) Ahora nos redirigira a contacto con los paramtros pasados escribiendo en el navegador:
   ```
   http://127.0.0.1:8000/pagina/1
   ```
  
> Recuerda que debemos mantener el path anterior.


### Vistas Base
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
-  La lista de métodos permitidos:
> ["get", "post", "put", "patch", "delete", "head", "options", "trace"]

### Templates en Django
Hasta ahora hemos trabajado con el codigo html directamente en las vista, pero esa no es la forma correcta de utilizar Django.

En Django, los templates son archivos de texto que contienen marcadores o placeholders que luego son reemplazados por valores específicos cuando la página se renderiza dinámicamente. Estos marcadores están rodeados por doble llave y siguen la sintaxis del lenguaje de plantillas de Django

#### ¿Como se utlizan?
- Los templates hacen que nustras app esten mejor estructuradas y organizadas para ello hay que crear nuestra carpeta de templates dentro de el directorio de la app.
```
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
> Usamos la funcion **render()** cuando queremos que nos devuelva un template, pasandole como argumento la avariable **request** y el **nombre del template** como minimo.

De esta forma nos mostrara nuestro primer template.

#### Layout, bloques y herencia de plantillas
- Como vemos el codigo no es limpio ¿como soluciona esto Django?
- Django utiliza un sistema de bloques y herencia que nos deja un proyecto estructurado y codigo limpio.
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

- En la primera linea le indicamos a Django el template de donde tiene que heredar.
- Como vemos los bloques son como etiquetas deben abrirse y cerrarse.
- A las etiquetas de bloques se le añadira el nombre del bloque donde debe ir.

<div style="page-break-after: always;"></div>

## Fuentes
- [Django projects](https://www.djangoproject.com/)
- [Tutorial Python](https://docs.python.org/es/3/tutorial/)
- [Instalacion de Python](https://python-guide-es.readthedocs.io/es/latest/starting/install3/linux.html)
- [video tutorial intalacion Python 3.12.0](https://www.makeuseof.com/install-python-ubuntu/)
- [InstalacionVSCode](https://alfonsomozkoh.github.io/2020/07/01/como-instalar-visual-studio-code-en-linux.html)

