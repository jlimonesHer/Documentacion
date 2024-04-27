# SYMFONY 6
--------------

[//]: # (version: 1.0)
[//]: # (author: Jose Carlos Limones)
[//]: # (date: 2024-03-04)

# Tabla de contenidos
- [SYMFONY 6](#symfony-6)
- [Tabla de contenidos](#tabla-de-contenidos)
  - [1- Introducción](#1--introducción)
  - [2- Instalación](#2--instalación)
  - [3- Creando mi proyecto de prácticas](#3--creando-mi-proyecto-de-prácticas)
    - [3.1- Contenido del proyecto Symfony](#31--contenido-del-proyecto-symfony)
    - [3.2- Creando la base de datos](#32--creando-la-base-de-datos)
    - [3.3- Que es el composer y apara que sirve](#33--que-es-el-composer-y-apara-que-sirve)
    - [3.4- Entidades y base de datos](#34--entidades-y-base-de-datos)
    - [3.5- Relaciones entre tablas](#35--relaciones-entre-tablas)
    - [3.6- Migraciones a la base de datos](#36--migraciones-a-la-base-de-datos)
  - [4.0- Creando el primer controlador.](#40--creando-el-primer-controlador)
    - [4.1- Controller.php](#41--controllerphp)
  - [5.0 Mostrar datos de la base de datos(READ)](#50-mostrar-datos-de-la-base-de-datosread)
    - [Otra forma de mostrar datos](#otra-forma-de-mostrar-datos)
  - [5.0 Insertar datos de la base de datos(CREATE)](#50-insertar-datos-de-la-base-de-datoscreate)


## 1- Introducción
[Tabla de contenidos](#tabla-de-contenidos)

Symfony es un conjunto de componentes y un marco de desarrollo de software de código abierto utilizado para construir aplicaciones web en el lenguaje de programación PHP. Fue creado por SensioLabs y lanzado por primera vez en 2005. Symfony sigue el paradigma de arquitectura Modelo-Vista-Controlador (MVC) y proporciona un conjunto de herramientas y bibliotecas que facilitan el desarrollo de aplicaciones web robustas, escalables y mantenibles.

1) Reutilización de componentes: Symfony está diseñado en torno a un conjunto de componentes independientes que pueden ser utilizados de forma individual en cualquier proyecto PHP. Esto facilita la reutilización de código y la creación de aplicaciones modulares.

2) Arquitectura MVC: Symfony sigue el patrón de arquitectura Modelo-Vista-Controlador, lo que permite una clara separación de la lógica de negocio, la presentación y la interacción con el usuario.

3) Doctrine ORM: Symfony se integra de manera nativa con Doctrine, un mapeador objeto-relacional (ORM) que simplifica la interacción con bases de datos y permite trabajar con objetos en lugar de consultas SQL directas.

4) Twig: Symfony utiliza Twig como motor de plantillas, lo que facilita la creación de vistas de manera clara y legible.

5) Gestor de dependencias: Symfony cuenta con Composer, un gestor de dependencias de PHP, que facilita la instalación y actualización de bibliotecas y paquetes necesarios para el desarrollo de la aplicación.

6) Testing: Symfony promueve las buenas prácticas de desarrollo y fomenta la escritura de pruebas unitarias y funcionales para garantizar la calidad del código.

7) Symfony es ampliamente utilizado en la comunidad de desarrollo web PHP y ha sido adoptado por numerosos proyectos y empresas para construir aplicaciones web de diversos tamaños y complejidades. Su enfoque modular y su énfasis en la calidad del código han contribuido a su popularidad.

> [!NOTE]
> Para utilizar Symfony 6 necesitaremos conocimientos de php avanzados.

## 2- Instalación
[Tabla de contenidos](#tabla-de-contenidos)
> [!IMPORTANT]
> Para el desarrollo con symfony 6 debemos tener instalado nuestro entorno con la pila LAMP(XAMP ó MANP).

- Necesitaremos instalar un gestor de dependencias llamado composer.
    ```bash
    php -r "copy('https://getcomposer.org/installer', 'composer-setup.php');"
    php -r "if (hash_file('sha384', 'composer-setup.php') === 'c5b9b6d368201a9db6f74e2611495f36999163382a775b6bc45f5f763cc69e49c21a00853a46d053454e5dcf34b965f8') { echo 'Installer verified'; } else { echo 'Installer corrupt'; unlink('composer-setup.php'); } echo PHP_EOL;"
    php composer-setup.php
    php -r "unlink('composer-setup.php');"
    ```
    - Para hacer que Composer sea accesible globalmente, mueve el archivo composer.phar a un directorio que esté en tu PATH:
    ```bash
    mv composer.phar /usr/local/bin/composer
    ```

    - Verifica que Composer se haya instalado correctamente ejecutando:
    ```bash
    composer --version
    ```
- Tambien necesitaremos el CLI de Symfony:
  - MACOS
    ```bash
    curl -sS https://get.symfony.com/cli/installer | bash
    ```
  - Linux:
    ```bash
    wget https://get.symfony.com/cli/installer -O - | bash
    ```
  - Verifica que esta instalado:
    ```bash
    symfony -v
    ```
  - Instalar Dependencias:
```bash
composer require --dev symfony/maker-bundle
composer require twig
composer require symfony/form
```
- En config/services.yaml
```yaml
annotation_reader:
  class: Doctrine\Common\Annotations\AnnotationReader
```
```bash
php bin/console cache:clear
composer update sensio/framework-extra-bundle
composer require symfony/orm-pack
composer require annotations
```


## 3- Creando mi proyecto de prácticas
[Tabla de contenidos](#tabla-de-contenidos)

- Para crear mi crud con symfony empezaremos con:
```bash
symfony new --webapp crud_symfony
```
- Si necesita una version expecifica de Symfony:
```bash
symfony new --webapp crud_symfony --version=^6
```
- Ahora podemos entrar en el directorio creado y levantar el servidor de Symfony:
```bash
cd crud_symfony
symfony serve
```

- Ahora ne la URL **http://127.0.0.1:8000/** podra ver la pagina de inicio de Symfony.

### 3.1- Contenido del proyecto Symfony
[Tabla de contenidos](#tabla-de-contenidos)
- Dentro de nuestro proyecto de Symfony se habran creado algunos directorios de los cuales nos fijaremos en 3 principalmente.
 - public
   - index.php
 - src
   - Controler -> Controladores creados para nuestra plataforma.
   - Entity -> Las entidades para la base de datos.
   - Repository -> Consultas a la base de datos.
   - Kernel.php
 - templates -> aqui iran las plantillas para nuestro proyecto que seran .twig
   - base.html.twig 
  
### 3.2- Creando la base de datos
[Tabla de contenidos](#tabla-de-contenidos)

- Para crear una base de datos y enlazarla con nuestro mysql tendermos que editar nuestro archivo **.env**, tendremos que tener especial cuidado con este archivo ya que contiene informacion sensible sobre nuestra base de datos:

```bash
DATABASE_URL=mysql://usuario:contraseña@127.0.0.1:3306/nombre_de_base_de_datos
```

- El siguiente paso sera crear la base de datos con el comando:
```bash
php bin/console doctrine:database:create
```
> [!NOTE]
> Para ver todos los comandos diponibles:
> ```bash
> php bin/console 
> ``` 


### 3.3- Que es el composer y apara que sirve
[Tabla de contenidos](#tabla-de-contenidos)

Composer es una herramienta que nos ayuda a crear e instalar las dependencias necesarias para nuestro proyecto, estas dependencias se guardan autom,aticamente en archvos como **composer.json** y **composer.lock**, estas dependencias se instalan en el directorio **vendor**(Este directorio no se subira a git ya que lo controlamos con composer).

- Para instalar estas dependencias al descargar nuestro proyecto:
```bash
composer install
```

### 3.4- Entidades y base de datos
[Tabla de contenidos](#tabla-de-contenidos)

- Esta sera la base de datos a crear:
![base_de_datos](img/imgDB.png)

- Empezaremos creando el usuario con la herramienta make:
```bash
php bin/console make:user 
```
> [!IMPORTANT]
> Para ver las opciones introduzca en la respuesta "***?***" y se listara las opciones.
```bash
 Field type (enter ? to see all types) [string]:
 > ?

Main Types
  * string or ascii_string
  * text
  * boolean
  * integer or smallint or bigint
  * float

Relationships/Associations
  * relation a wizard 🧙 will help you build the relation
  * ManyToOne
  * OneToMany
  * ManyToMany
  * OneToOne

Array/Object Types
  * array or simple_array
  * json
  * object
  * binary
  * blob

Date/Time Types
  * datetime or datetime_immutable
  * datetimetz or datetimetz_immutable
  * date or date_immutable
  * time or time_immutable
  * dateinterval

Other Types
  * decimal
  * guid
```

- Esto nos abrira un formulario en la terminal:
```bash
 The name of the security user class (e.g. User) [User]:
> User

 Do you want to store user data in the database (via Doctrine)? (yes/no) [yes]:
 > yes

 Enter a property name that will be the unique "display" name for the user (e.g. email, username, uuid) [email]:
 > 

 Will this app need to hash/check user passwords? Choose No if passwords are not needed or will be checked/hashed by some other system (e.g. a single sign-on server).

 Does this app need to hash/check user passwords? (yes/no) [yes]:
 > yes
 ```
- Como vemos nos hacreado en el directorio Entity u n archivo **User.php** y en Repository **UserReopistory.php**.
- Tambien observamos que nos a creado la clase user pero nos faltan campos, poara agregra estos campos:

```console
php bin/console make:entity
```
- Esto nos llevara a otro formulario en la terminal:
```bash
Class name of the entity to create or update (e.g. OrangeChef):
> user

Your entity already exists! So let is add some new fields!

New property name (press <return> to stop adding fields):
> photo

Field type (enter ? to see all types) [string]:
> string

Field length [255]:
> 255

Can this field be null in the database (nullable) (yes/no) [no]:
> yes

updated: src/Entity/User.php

Add another property? Enter the property name (or press <return> to stop adding fields):
> description

Field type (enter ? to see all types) [string]:
> text

Can this field be null in the database (nullable) (yes/no) [no]:
> yes

updated: src/Entity/User.php

Add another property? Enter the property name (or press <return> to stop adding fields):
> 


           
  Success! 
           

 Next: When you're ready, create a migration with php bin/console make:migration
```

> [!IMPORTANT]
> El "**ID**" lo pondra Symfony de forma automatica.

- Ahora vamos a crear otra entidad:
```console
php bin/console make:entity
```
> [!NOTE]
> Usaremos **make:entity** porque Symfony usa user como entidad principal.

```bash
 created: src/Entity/Post.php
 created: src/Repository/PostRepository.php
 
 Entity generated! Now let is add some fields!
 You can always add more fields later manually or by re-running this command.

 New property name (press <return> to stop adding fields):
 > title

 Field type (enter ? to see all types) [string]:
 > 

 Field length [255]:
 > 

 Can this field be null in the database (nullable) (yes/no) [no]:
 > no

 updated: src/Entity/Post.php

 Add another property? Enter the property name (or press <return> to stop adding fields):
 > type

 Field type (enter ? to see all types) [string]:
 > 

 Field length [255]:
 > 

 Can this field be null in the database (nullable) (yes/no) [no]:
 > no

 updated: src/Entity/Post.php

 Add another property? Enter the property name (or press <return> to stop adding fields):
 > description

 Field type (enter ? to see all types) [string]:
 > text

 Can this field be null in the database (nullable) (yes/no) [no]:
 > no

 updated: src/Entity/Post.php

 Add another property? Enter the property name (or press <return> to stop adding fields):
 > file        

 Field type (enter ? to see all types) [string]:
 > 

 Field length [255]:
 > 

 Can this field be null in the database (nullable) (yes/no) [no]:
 > yes

 updated: src/Entity/Post.php

 Add another property? Enter the property name (or press <return> to stop adding fields):
 > creation_date

 Field type (enter ? to see all types) [string]:
 > datetime

 Can this field be null in the database (nullable) (yes/no) [no]:
 > no

 updated: src/Entity/Post.php

 Add another property? Enter the property name (or press <return> to stop adding fields):
 > url

 Field type (enter ? to see all types) [string]:
 > 

 Field length [255]:
 > 

 Can this field be null in the database (nullable) (yes/no) [no]:
 > no

 updated: src/Entity/Post.php

 Add another property? Enter the property name (or press <return> to stop adding fields):
 > 


           
  Success! 
           

 Next: When you're ready, create a migration with php bin/console make:migration
```
> [!NOTE]
> Puedes hacer los cambios necesarios en los archivos creados por Symfony para ajustarlos a tus necesidades.

### 3.5- Relaciones entre tablas
[Tabla de contenidos](#tabla-de-contenidos)

- Si observamos las tablas del esquema anterior vemos las relaciones entre ellas:
```bash
-------------------------------------------
| Entidad1     | Entidad2   | Relacion    |
-------------------------------------------
| Post         | User       | 1 - muchos  |
-------------------------------------------
| Interaction  | User       | muchos - 1  |         
-------------------------------------------
| Post         | Interaction| 1 - muchos  | 
-------------------------------------------
```
- Volvemos a editar nuestra entidad user(Que en realidad tambien editara la entidad relacionada):
```bash
php bin/console make:entity User
```

- Vamos a crear la primera relacion:
```bash
# La Entidad ya existe
 Your entity already exists! So let is add some new fields!
# Nuevo campo a añadir
 New property name (press <return> to stop adding fields):
 > posts
# Que tipo de campo es?
# Ahora es cuando le indicamos el tipo de relacion
 Field type (enter ? to see all types) [string]:
 > OneToMany
# Con que entidad es la relacion?
 What class should this entity be related to?:
 > Post
# Nombre del campo
 A new property will also be added to the Post class so that you can access and set the related User object from it.
# El nuevo campo como se llamara?
 New field name inside Post [user]:
 > 

 Is the Post.user property allowed to be null (nullable)? (yes/no) [yes]:
 > no
# Si elimina el usuario que desea hacer con el post relacionado?
# Yes para indicarle que lo borre tambien.
# No para indicarle que no lo borre.
 Do you want to activate orphanRemoval on your relationship?
 A Post is "orphaned" when it is removed from its related User.
 e.g. $user->removePost($post)
 
 NOTE: If a Post may *change* from one User to another, answer "no".

 Do you want to automatically delete orphaned App\Entity\Post objects (orphanRemoval)? (yes/no) [no]:
 > yes

 updated: src/Entity/User.php
 updated: src/Entity/Post.php
```

> [!NOTE]
> Haremos lo mismo para la relacion de User con la tabla Iteraction y la de Post con Interaction.

### 3.6- Migraciones a la base de datos 
[Tabla de contenidos](#tabla-de-contenidos)

- Para migrar las entidades:
```bash
php bin/console make:migration
php bin/console doctrine:migrations:migrate
```
> [!NOTE]
> Este comando no creara nuestra base de datos con las tablas y relaciones programadas por Symfony.

## 4.0- Creando el primer controlador.
[Tabla de contenidos](#tabla-de-contenidos)

- El controlador actua como intermediario entre el modelo y la vista.Maneja las solicitudes del usuario, interactúa con el modelo para obtener o actualizar datos y luego selecciona la vista adecuada para mostrar los resultados al usuario.

- En Symfony, los controladores son clases PHP que extienden Symfony\Bundle\FrameworkBundle\Controller\AbstractController (o implementan la interfaz Symfony\Component\DependencyInjection\ContainerAwareInterface en versiones anteriores). Cada método público en un controlador se considera una "acción" y se asocia a una ruta específica a través de anotaciones o configuraciones de enrutamiento.
- El comando para crear nuestro controlador es:
```bash
php bin/console make:controller
```
- Comandos de Symfony:
```bash
 Choose a name for your controller class (e.g. AgreeablePopsicleController):
 > PostController

 created: src/Controller/PostController.php
 created: templates/post/index.html.twig

           
  Success! 
           

 Next: Open your new controller class and add some pages!
```
- Al crear este controlador vemos como, tnto en la carpeta Controller como en la carpeta templates se hacreado archivos que veremos a continuacion.
> [!NOTE]
> El estandar de Symfony nos dice que para crear el controlador debemos añadir el sufijo controller precedido del nombre de nuesgtra entidad.

### 4.1- <Entidad>Controller.php
[Tabla de contenidos](#tabla-de-contenidos)

- Este es nuestro archivo **PostController.php**
```php
<?php

namespace App\Controller;

use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Attribute\Route;

class PostController extends AbstractController
{
    #[Route('/post', name: 'app_post')]
    public function index(): Response
    {
        return $this->render('post/index.html.twig', [
            'controller_name' => 'PostController',
        ]);
    }
}
```
- Como vemos, hay una clase llamada PostController que hereda de AbstractControler.
- Tambien hay una linea que enpieza por #[Route(...)].

- Ahora si entramos en nuestra URL **http://127.0.0.1:8000/post** veremos una pagina renderizada con el nombre de nuestro controlador.

- Los iguiente que debemos hacer es probar nuestra conexion, insertamos un user y 2 post desde PhpMyAdmin o directamente desde MySQL.

## 5.0 Mostrar datos de la base de datos(READ)
[Tabla de contenidos](#tabla-de-contenidos)
- Despues de crear algunos datos.
- PostController.php:
```php
<?php

namespace App\Controller;

use App\Entity\Post;
use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Attribute\Route;

class PostController extends AbstractController
{
    #[Route('/post/{id}', name: 'app_post')]
    public function index(Post $post): Response
    {
        return $this->render('post/index.html.twig', [
            'controller_name' => 'PostController',
            'post' => $post,
        ]);
    }
}
```
- index.html.twig:
```twig
{% extends 'base.html.twig' %}

{% block title %}Hello PostController!{% endblock %}

{% block body %}
    {{ controller_name }}
    {{ dump(post) }}

{% endblock %}
```

### Otra forma de mostrar datos
- PostController.php:
```php
<?php

namespace App\Controller;

use App\Entity\Post;
use Doctrine\ORM\EntityManagerInterface;
use Symfony\Bundle\FrameworkBundle\Controller\AbstractController;
use Symfony\Component\HttpFoundation\Response;
use Symfony\Component\Routing\Attribute\Route;

class PostController extends AbstractController
{
    private $em;

    public function __construct(EntityManagerInterface $em)
    {
        $this->em = $em;
    }

    #[Route('/post/{id}', name: 'app_post')]
    public function index($id): Response
    {
        $post = $this->em->getRepository(Post::class)->find($id);
        return $this->render('post/index.html.twig', [
            'controller_name' => 'PostController',
            'post' => $post,
        ]);
    }
}
```


## 5.0 Insertar datos de la base de datos(CREATE)
[Tabla de contenidos](#tabla-de-contenidos)



[video tutorial](https://www.youtube.com/watch?v=97dHndtgIqE&list=PLDbrnXa6SAzUYxocB3jC81TfvWUynAppf&index=6)

[Tabla de contenidos](#tabla-de-contenidos)






