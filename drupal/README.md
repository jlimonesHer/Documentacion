# Drupal


[//]: # (version: 1.0)
[//]: # (author: Jose Carlos Limones)
[//]: # (date: 2020-10-10)



# Tabla de contenidos
- [Drupal](#drupal)
- [Tabla de contenidos](#tabla-de-contenidos)
  - [Guia a seguir](#guia-a-seguir)
  - [1.1 ¿Que es drupal?](#11-que-es-drupal)
    - [1.2 Historia y evolución de Drupal](#12-historia-y-evolución-de-drupal)
    - [1.3 Ventajas y desventajas de Drupal](#13-ventajas-y-desventajas-de-drupal)
    - [1.4 Casos de uso comunes](#14-casos-de-uso-comunes)
  - [Instalación de Drupal.](#instalación-de-drupal)
    - [2.2 Descarga e instalación de Drupal](#22-descarga-e-instalación-de-drupal)
    - [2.3 Configuración inicial del sitio](#23-configuración-inicial-del-sitio)
    - [2.4 Exploración del panel de administración](#24-exploración-del-panel-de-administración)
  - [Estructura de Drupal.](#estructura-de-drupal)
    - [3.1 Nodos, tipos de contenido y campos](#31-nodos-tipos-de-contenido-y-campos)
    - [3.2 Taxonomía y vocabularios](#32-taxonomía-y-vocabularios)
- [3.3 Bloques y regiones](#33-bloques-y-regiones)
  - [3.4 Menús y enlaces de navegación](#34-menús-y-enlaces-de-navegación)
  - [4: Temas en Drupal](#4-temas-en-drupal)
    - [4.1 Instalación y gestión de temas:](#41-instalación-y-gestión-de-temas)
    - [4.2 Creación de subtemas:](#42-creación-de-subtemas)
    - [4.3 Personalización de la apariencia del sitio:](#43-personalización-de-la-apariencia-del-sitio)

## Guia a seguir
Clase 1: Introducción a Drupal
  - 1.1 ¿Qué es Drupal?
  - 1.2 Historia y evolución de Drupal
  - 1.4 Casos de uso comunes
  - 1.3 Ventajas y desventajas de Drupal
- Clase 2: Instalación de Drupal
  - 2.1 Requisitos del sistema
  - 2.2 Descarga e instalación de Drupal
  - 2.3 Configuración inicial del sitio
  - 2.4 Exploración del panel de administración
- Clase 3: Estructura de Drupal
  - 3.1 Nodos, tipos de contenido y campos
  - 3.2 Taxonomía y vocabularios
  - 3.3 Bloques y regiones
  - 3.4 Menús y enlaces de navegación
- Clase 4: Temas en Drupal
  - 4.1 Instalación y gestión de temas
  - 4.2 Creación de subtemas
  - 4.3 Personalización de la apariencia del sitio
- Clase 5: Módulos en Drupal
  - 5.1 Concepto de módulos
  - 5.2 Instalación y activación de módulos
  - 5.3 Módulos populares y su funcionalidad
- Clase 6: Gestión de Usuarios y Permisos
  - 6.1 Creación y gestión de usuarios
  - 6.2 Roles y permisos
  - 6.3 Configuración de la seguridad del sitio
- Clase 7: Desarrollo de Módulos Básicos
  - 7.1 Estructura de un módulo
  - 7.2 Creación de un módulo simple
  - 7.3 Implementación de ganchos (hooks)
- Clase 8: Vistas en Drupal
  - 8.1 Creación y gestión de vistas
  - 8.2 Filtros, campos y exposiciones
  - 8.3 Uso avanzado de Vistas
- Clase 9: Gestión de Contenido Multilingüe
  - 9.1 Configuración de múltiples idiomas
  - 9.2 Traducción de contenido
  - 9.3 Módulos relacionados con la internacionalización
- Clase 10: Optimización del Rendimiento y Seguridad
  - 10.1 Estrategias para mejorar el rendimiento
  - 10.2 Configuración de la seguridad del sitio
  - 10.3 Respaldo y restauración del sitio

## 1.1 ¿Que es drupal?
[Tabla de contenidos](#tabla-de-contenidos)

Drupal es un sistema de gestión de contenidos (CMS) de código abierto que permite a las personas y organizaciones construir sitios web y aplicaciones poderosas. Su flexibilidad y escalabilidad lo convierten en una opción popular para sitios web de todo tipo, desde blogs personales hasta sitios web corporativos y gubernamentales.

### 1.2 Historia y evolución de Drupal
[Tabla de contenidos](#tabla-de-contenidos)

Drupal fue creado por Dries Buytaert en 2001 y ha experimentado un crecimiento significativo desde entonces. La comunidad de Drupal ha contribuido con módulos, temas y mejoras continuas, convirtiéndolo en un CMS robusto y versátil.

### 1.3 Ventajas y desventajas de Drupal
[Tabla de contenidos](#tabla-de-contenidos)

- Ventajas:
    - Flexibilidad y escalabilidad.
    - Gran comunidad de usuarios y desarrolladores.
    - Poderosa gestión de contenido.
    - Extensibilidad mediante módulos.
    - Seguridad robusta.
- Desventajas:
  - Mayor curva de aprendizaje en comparación con algunos otros CMS.
Algunas funciones pueden requerir conocimientos técnicos.

### 1.4 Casos de uso comunes
[Tabla de contenidos](#tabla-de-contenidos)

- Drupal se utiliza en una variedad de escenarios, como:
    - Sitios web corporativos.
    - Portales gubernamentales.
    - Comunidades en línea.
    - Sitios web de medios de comunicación.
    - Plataformas de comercio electrónico.

## Instalación de Drupal.
[Tabla de contenidos](#tabla-de-contenidos)

### 2.1 Requisitos del sistema.
[Tabla de contenidos](#tabla-de-contenidos)

Antes de instalar Drupal, asegúrate de que tu entorno cumple con los requisitos mínimos del sistema. Estos requisitos incluyen un servidor web (como Apache o Nginx), una base de datos (generalmente MySQL o PostgreSQL), y PHP. Asegúrate de tener las versiones compatibles según la documentación oficial de Drupal.

### 2.2 Descarga e instalación de Drupal
[Tabla de contenidos](#tabla-de-contenidos)

- Visita el sitio web oficial de [Drupal](https://www.drupal.org/)
  ```console
  composer create-project drupal/recommended-project drupal 
  cd drupal && php -d memory_limit=256M web/core/scripts/drupal quick-start demo_umami
  ```
- Descarga la última versión estable de Drupal.
- Extrae los archivos descargados en el directorio de tu servidor web.
- Crea una base de datos para Drupal en tu sistema de gestión de bases de datos (por ejemplo, MySQL).

### 2.3 Configuración inicial del sitio
[Tabla de contenidos](#tabla-de-contenidos)

Abre tu navegador y accede a la URL donde instalaste Drupal.
Sigue las instrucciones del instalador web de Drupal.
Configura la conexión a la base de datos, proporcionando el nombre de la base de datos, usuario y contraseña.
Completa la configuración básica del sitio, incluyendo el nombre del sitio y la configuración del administrador.
### 2.4 Exploración del panel de administración
[Tabla de contenidos](#tabla-de-contenidos)

Una vez que hayas instalado Drupal, accede al panel de administración. Aquí podrás gestionar contenido, instalar módulos, cambiar la apariencia y configurar la funcionalidad del sitio.

Ahora, ¿cómo te fue con la instalación? ¿Hay algún paso que necesitas aclarar o algún problema con el que necesitas ayuda?

## Estructura de Drupal.
[Tabla de contenidos](#tabla-de-contenidos)


### 3.1 Nodos, tipos de contenido y campos
[Tabla de contenidos](#tabla-de-contenidos)

En Drupal, el contenido se organiza en **nodos**. Cada nodo puede pertenecer a un "tipo de contenido". Los tipos de contenido definen la estructura y los campos que un nodo puede tener. Por ejemplo, puedes tener un tipo de contenido llamado "Artículo" con campos como título, cuerpo y fecha de publicación.

- Nodos: En Drupal, un nodo es una unidad básica de contenido. Puede representar cualquier tipo de contenido en tu sitio, como un artículo, una página, un evento, etc.

- Tipos de Contenido: Los tipos de contenido definen la estructura y los campos que un nodo puede tener. Por ejemplo, si creas un tipo de contenido llamado "Producto", podrías tener campos como nombre del producto, descripción, precio, etc.

- Ejemplo: Crear un tipo de contenido "Libro" con campos como título, autor, género y fecha de publicación.

- Campos: Los campos son los elementos individuales que componen un tipo de contenido. Pueden ser de diferentes tipos, como texto, fecha, imagen, etc.

- Ejemplo: Dentro del tipo de contenido "Producto", podrías tener un campo "Imagen" para la imagen del producto o un campo "Precio" para el precio del producto.

### 3.2 Taxonomía y vocabularios
[Tabla de contenidos](#tabla-de-contenidos)

La taxonomía en Drupal se utiliza para organizar y clasificar el contenido. Los términos de taxonomía se agrupan en "vocabularios". Por ejemplo, puedes tener un vocabulario llamado "Categorías" con términos como "Tecnología", "Deportes", etc.

- Taxonomía: La taxonomía en Drupal se refiere a la clasificación y organización del contenido mediante términos y vocabularios.

- Vocabularios: Los vocabularios son grupos de términos relacionados. Por ejemplo, podrías tener un vocabulario llamado "Categorías" con términos como "Tecnología", "Deportes", etc.

- Ejemplo: Crear un vocabulario "Etiquetas" con términos como "Drupal", "Tutoriales", "Desarrollo web", y asignar estas etiquetas a tus nodos.

# 3.3 Bloques y regiones
[Tabla de contenidos](#tabla-de-contenidos)

Drupal utiliza un sistema de bloques que te permite organizar y mostrar contenido en diferentes áreas de tu sitio. Las "regiones" son áreas predefinidas en tu diseño donde puedes colocar bloques, como la barra lateral o el pie de página.

- Bloques: Son unidades de contenido que puedes colocar en regiones específicas de tu página. Pueden contener texto, enlaces, formularios, etc.

- Regiones: Son áreas predefinidas en tu diseño donde puedes colocar bloques. Algunas regiones comunes son "Encabezado", "Barra lateral", "Pie de página", etc.

Ejemplo: Colocar un bloque de "Entradas recientes" en la barra lateral para mostrar los últimos artículos en tu sitio.

## 3.4 Menús y enlaces de navegación
[Tabla de contenidos](#tabla-de-contenidos)

Drupal te permite crear menús para organizar la navegación de tu sitio. Puedes agregar enlaces a diferentes partes de tu sitio, como páginas, nodos, o enlaces externos, y luego organizarlos jerárquicamente.

- Menús: En Drupal, puedes crear menús para organizar la navegación de tu sitio.

- Enlaces de Navegación: Puedes agregar enlaces a diferentes partes de tu sitio en tus menús. Pueden ser enlaces a páginas, nodos, o incluso enlaces externos.

- Ejemplo: Crear un menú de navegación principal con enlaces a "Inicio", "Acerca de nosotros", "Servicios", etc.

## 4: Temas en Drupal
[Tabla de contenidos](#tabla-de-contenidos)

### 4.1 Instalación y gestión de temas:
[Tabla de contenidos](#tabla-de-contenidos)

Instalación de Temas: Puedes instalar temas nuevos desde la interfaz de administración de Drupal. Los temas controlan la apariencia visual de tu sitio.

Ejemplo: Descargar un tema desde Drupal.org/themes e instalarlo en tu sitio.

Gestión de Temas: Puedes activar, desactivar y configurar temas desde el panel de administración.

### 4.2 Creación de subtemas:
[Tabla de contenidos](#tabla-de-contenidos)

Subtemas: Puedes crear subtemas para personalizar aún más la apariencia de tu sitio sin modificar directamente el tema principal.

Ejemplo: Crear un subtema basado en un tema existente y personalizar los estilos o las plantillas.

### 4.3 Personalización de la apariencia del sitio:
[Tabla de contenidos](#tabla-de-contenidos)

Personalización de la Apariencia: Puedes personalizar la apariencia de tu sitio a través de la interfaz de administración, ajustando colores, fuentes, y otros elementos visuales.

Ejemplo: Cambiar el color principal del sitio y ajustar el tamaño de la fuente desde la configuración de apariencia.

Clase 5: Módulos en Drupal

5.1 Concepto de Módulos:

Módulos en Drupal: Son extensiones que agregan funcionalidades específicas al sitio. Pueden ser para SEO, formularios, redes sociales, etc.
5.2 Instalación y activación de módulos:

Instalación de Módulos: Se instalan desde la interfaz de administración o manualmente.

Ejemplo: Instalar un módulo de Galería de Imágenes para permitir la creación de galerías en tus nodos.

Activación de Módulos: Después de instalar un módulo, debes activarlo para que comience a funcionar.

5.3 Módulos populares y su funcionalidad:

Ejemplos de Módulos Populares: Views, Pathauto, Token, Webform.

Funcionalidad de Módulos: Views permite crear listas y tablas de contenido, Pathauto automatiza la creación de URL amigables, Token proporciona tokens reutilizables, y Webform facilita la creación de formularios complejos.

