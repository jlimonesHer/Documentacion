# BEHAVE
-------------

[//]: # (version: 1.0)
[//]: # (author: Jose Carlos Limones Hernandez)
[//]: # (date: 2023-12-10)

## Tabla de contenidos
- [BEHAVE](#behave)
  - [Tabla de contenidos](#tabla-de-contenidos)
  - [Introducción](#introducción)
  - [Instalación](#instalación)
  - [Desarrollo](#desarrollo)
    - [Estructutra del proyecto](#estructutra-del-proyecto)
    - [Escribir una especficación de comportamiento](#escribir-una-especficación-de-comportamiento)
    - [Implementar los pasos de prueba](#implementar-los-pasos-de-prueba)
  - [Gherkin](#gherkin)
  - [Ejemplo 1: Registros de usuarios con validacion de correo electrónico](#ejemplo-1-registros-de-usuarios-con-validacion-de-correo-electrónico)

## Introducción
[Tabla de contenidos](tabla-de-contenidos)

 Behave es una herramienta que te ayuda a escribir y ejecutar pruebas automatizadas para tu software en Python de una manera muy organizada y fácil de entender.

Piensa en Behave como un asistente que te permite escribir las reglas que tu software debe seguir en un idioma simple y natural, como si estuvieras contando una historia. Luego, este asistente traduce esas reglas en pruebas de software que tu computadora puede entender y ejecutar automáticamente.

Digamos que estás construyendo una aplicación para una tienda en línea. Con Behave, puedes escribir cosas como "Cuando un usuario agrega un artículo al carrito, el número de artículos en el carrito debe aumentar en uno". Behave toma esta descripción y la convierte en una prueba que verifica exactamente eso: que cuando alguien agrega un artículo, el carrito realmente se actualiza correctamente.

## Instalación
[Tabla de contenidos](tabla-de-contenidos)

> [!NOTE]
> Para la instalación usare un entorno virtual de python y lo ddesarrollare usando Visual Studio Code.
1) Instalaremos [vscode](https://code.visualstudio.com/docs).
2) Crearemos nuestro entorno virtual:
   ```bash
   virtualenv env
   ```
3) Behave tiene una instalación simple ya que se trata de un biblioteca de python:
    ```bash
    pip install behave
    ```
## Desarrollo
[Tabla de contenidos](tabla-de-contenidos)

Vamos a empezar con un ejemplo sencillo, imagina que te han pedido que escribas un programa en python que sume dos numeros y usaremos **Behave** para asegurarnos que el programa funciona correctamente.

### Estructutra del proyecto
[Tabla de contenidos](tabla-de-contenidos)

```console
proyecto/
|-- features/
|   -- suma.feature
|-- steps/
|   -- steps.py
```
- Un proyecto tipico de **Beheve** tiene dos carpetas principales: 'features' y 'steps'.
- La carpeta ***features*** contendrá archivos con extension '.feature' donde escribiremos nuestras especificaciones de comportamiento.
- La carpeta ***steps*** contendrá los arcivo Python donde implementaremos los pasos de prueba correspodientes a nuestras especificaciones.

### Escribir una especficación de comportamiento
[Tabla de contenidos](tabla-de-contenidos)

¿Que es un **feature**?

Un **feature** proporciona una descripción de alto nivel de una de las funciones del software y agrupa escenarios que se relacionan entre sí.

¿Que es un **escenario**?

Un **escenario** es un ejemplo concreto de una regla de negocio, generalmente sigue el patron:
  - Given -> Dado un contexto.
  - When -> Cuando yo ejecute una accion.
  - Then -> Resultara o terminara en algo.

¿Que es un **Scenario outline**?

Un **Scenario outline** es para ejecutar un mismo escenario con diferentes parametros o valores.

```
Examples: Amphibians
        | thing         | other things|
        | Red Tree Frog | mush        |
        | apples        | apple juice |
```

Este escenario se ejecutara varias veces con los distintos valores.

¿Que es el **Background**?

El **Background** es una accion qe se va a utilizar en todos los escenarios, por lo que se escribe aqui y no tendremos que reescribir muchas veces la misma acción.

En el archivo ***.feature*** escrbiremos nuestros escenarios an la sintaxis de [Gherkin](#gherkin)
```feature
Feature: Sumar dos números
    Como usuario
    Quiero sumar dos números
    Para obtener el resultado correcto

    Scenario: Sumar números positivos
        Given dos números 5 y 3
        When los sumo
        Then obtengo 8
```

### Implementar los pasos de prueba
[Tabla de contenidos](tabla-de-contenidos)

- Ahora necesitamos implementar los pasos de prueba en Python para que Behave pueda ejecutarlos.
- En el archivo steps.py, escribiremos las funciones Python correspondientes a cada paso de nuestra especificación.
- Por ejemplo:

```python
from behave import given, when, then

@given('dos números {num1:d} y {num2:d}')
def step_given_two_numbers(context, num1, num2):
    context.num1 = num1
    context.num2 = num2

@when('los sumo')
def step_when_sum(context):
    context.result = context.num1 + context.num2

@then('obtengo {result:d}')
def step_then_result(context, result):
    assert context.result == result, f"El resultado fue {context.result}, pero se esperaba {result}"
```

- Ahora que hemos escrito nuestras especificaciones y nuestros pasos de prueba, es hora de ejecutarlas.
- Simplemente abre una terminal en la raíz de tu proyecto y ejecuta el comando behave.
- Behave interpretará tu especificación, ejecutará los pasos de prueba y te dará un informe sobre si las pruebas pasaron o fallaron.

## Gherkin
[Tabla de contenidos](tabla-de-contenidos)

- La sintaxis de Gherkin es un lenguaje específico de dominio (DSL, por sus siglas en inglés) diseñado para escribir especificaciones de comportamiento de una manera legible por humanos. Es el lenguaje utilizado para describir el comportamiento del software en el marco de trabajo de desarrollo conducido por pruebas (BDD, por sus siglas en inglés).

- Gherkin se basa en un conjunto de palabras clave que definen la estructura básica de una especificación de comportamiento. Estas palabras clave incluyen:

- Feature: Describe una característica o funcionalidad del software que se está probando. Por ejemplo: Feature: Iniciar sesión en un sistema de gestión de usuarios.

- Scenario: Describe un escenario específico de uso de la característica que se está probando. Por ejemplo: Scenario: Iniciar sesión con credenciales válidas.

- Given, When, Then, And, But: Estas son palabras clave utilizadas para describir el estado inicial, las acciones que se realizan, y las expectativas en un escenario. Por ejemplo:

```feature
Given un usuario registrado
When inicia sesión con su nombre de usuario y contraseña
Then se redirige a la página de inicio
```
- Background: Describe un contexto común para varios escenarios. Puede ser útil para evitar repetición en tus especificaciones. Por ejemplo:

```feature
Background:
    Given un usuario registrado
    And ha iniciado sesión
```

- Scenario Outline: Permite definir un escenario con parámetros variables. Esto es útil cuando tienes escenarios similares que difieren en datos específicos. Por ejemplo:

```feature
Scenario Outline: Iniciar sesión con diferentes credenciales
    Given un usuario registrado con nombre de usuario "<username>" y contraseña "<password>"
    When inicia sesión
    Then se redirige a la página de inicio

    Examples:
    | username | password |
    | user1    | pass123  |
    | user2    | pass456  |
```

## Ejemplo 1: Registros de usuarios con validacion de correo electrónico
[Tabla de contenidos](tabla-de-contenidos)

Supongamos que estamos desarrollando una aplicación web y queremos escribir especificaciones de comportamiento para el proceso de registro de usuarios, que incluye la validación del correo electrónico.

1) Especificación de comportamiento (.feature):
   ```feature
   Feature: Registro de usuarios
    Como usuario nuevo
    Quiero registrarme en el sitio web
    Para poder acceder a las funciones exclusivas

    Scenario: Registro exitoso con correo electrónico válido
        Given estoy en la página de registro
        When ingreso mi nombre de usuario "usuario123"
        And ingreso mi correo electrónico "usuario@example.com"
        And ingreso mi contraseña "contraseña123"
        And confirmo mi contraseña "contraseña123"
        And hago clic en el botón de registro
        Then veo un mensaje de confirmación "¡Registro exitoso!"

    Scenario: Registro fallido con correo electrónico inválido
        Given estoy en la página de registro
        When ingreso mi nombre de usuario "usuario456"
        And ingreso mi correo electrónico "correo_invalido"
        And ingreso mi contraseña "contraseña456"
        And confirmo mi contraseña "contraseña456"
        And hago clic en el botón de registro
        Then veo un mensaje de error "¡Correo electrónico inválido!"

   ```
2) Pasos de prueba(steps.py):
   ```feature
   from behave import given, when, then
    import re

    # Expresión regular para validar el formato de correo electrónico
    EMAIL_REGEX = re.compile(r"[^@]+@[^@]+\.[^@]+")

    @given('estoy en la página de registro')
    def step_estoy_en_pagina_registro(context):
        # Aquí podrías navegar a la página de registro en tu aplicación web
        pass

    @when('ingreso mi nombre de usuario "{username}"')
    def step_ingreso_nombre_usuario(context, username):
        context.username = username

    @when('ingreso mi correo electrónico "{email}"')
    def step_ingreso_correo_electronico(context, email):
        context.email = email

    @when('ingreso mi contraseña "{password}"')
    def step_ingreso_contrasena(context, password):
        context.password = password

    @when('confirmo mi contraseña "{confirm_password}"')
    def step_confirmo_contrasena(context, confirm_password):
        context.confirm_password = confirm_password

    @when('hago clic en el botón de registro')
    def step_hago_clic_boton_registro(context):
        # Aquí podrías simular el clic en el botón de registro en tu aplicación web
        pass

    @then('veo un mensaje de confirmación "{message}"')
    def step_veo_mensaje_confirmacion(context, message):
        # Aquí podrías verificar en tu aplicación web que se muestra el mensaje de confirmación
        assert message in "¡Registro exitoso!", "Mensaje de confirmación incorrecto"

    @then('veo un mensaje de error "{message}"')
    def step_veo_mensaje_error(context, message):
        # Aquí podrías verificar en tu aplicación web que se muestra el mensaje de error
        assert message in "¡Correo electrónico inválido!", "Mensaje de error incorrecto"

    @then('el correo electrónico ingresado es válido')
    def step_correo_electronico_es_valido(context):
        assert re.match(EMAIL_REGEX, context.email), "El correo electrónico no es válido"
   ```

- En este ejemplo:

  - Utilizamos dos escenarios diferentes (Scenario) para probar el registro de usuarios con un correo electrónico válido y con un correo electrónico inválido.
  - Cada paso (Given, When, Then) describe una acción o una expectativa en el escenario.
  - Los pasos de prueba en Python implementan la lógica necesaria para ejecutar cada paso y verificar que el comportamiento esperado se cumpla.
  - También utilizamos una expresión regular para validar el formato del correo electrónico en el paso correo_electronico_es_valido.