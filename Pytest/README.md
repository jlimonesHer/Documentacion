# TUTORIAL PYTEST
------------------

[//]: # (version: 1.0)
[//]: # (author: Jose Carlos Limones)
[//]: # (date: 2024-02-22)



# Tabla de contenidos
- [TUTORIAL PYTEST](#tutorial-pytest)
- [Tabla de contenidos](#tabla-de-contenidos)
  - [Introducción](#introducción)
  - [Instalación](#instalación)
  - [Estructura de los test](#estructura-de-los-test)
  - [Ejecutar test](#ejecutar-test)
  - [Asserts](#asserts)
  - [Fixtures](#fixtures)
    - [Fixtures avanzadas](#fixtures-avanzadas)
  - [Parametrización de tests](#parametrización-de-tests)
  - [Uso de Marcadores](#uso-de-marcadores)
  - [Uso de Mocks](#uso-de-mocks)
  - [Cobertura de codigo](#cobertura-de-codigo)
    - [Coverage.py](#coveragepy)
  - [Plugins](#plugins)
  - [Ejemplo Pytest](#ejemplo-pytest)
  - [Ejemplo Coverage](#ejemplo-coverage)
  - [Conclusión:](#conclusión)

------------------

## Introducción
[Tabla de contenidos](#tabla-de-contenidos)

- Pytest es un framework de testing en python que hace que escribir y ejecutar test sea mas sencillo y legible.

[Documentacion oficial pytest](https://docs.pytest.org/en/7.1.x/contents.html)

## Instalación
[Tabla de contenidos](#tabla-de-contenidos)

- Yo siempre trabajo con entornos virtuales para no saturar el equipo.
```bash
python3 -m venv venv
```
- Instalamos la libreria:
```bash
pip install pytest
```

## Estructura de los test
[Tabla de contenidos](#tabla-de-contenidos)

Los test en pytest se escriben en funciones python normales. Cada funcion de test debe empezar con el prefijo test_ o terminar con el sufijo _test.
Por ejemplo:
```python
def test_suma():
    assert suma(1,2) == 3
```

## Ejecutar test
[Tabla de contenidos](#tabla-de-contenidos)
Para ejecutar los test simplemente navega hasta el directorio que contene tus archivos y ejecuta:
```bash
pytest
```

> [!NOTE]
Pytest buscara automaticamente archivos  con nombres que coincidan con el patron(_test, _test).

## Asserts
[Tabla de contenidos](#tabla-de-contenidos)

En los test, usamos afirmaciones(assertions) para verificar si el resultado esperado coincide con el resultado real.
```python
def test_suma():
    assert suma(1,2) == 3
```
Si la afirmacion es verdadera, el test pasa, de lo contrario falla.


## Fixtures
[Tabla de contenidos](#tabla-de-contenidos)

Las fixtures en pytest son funciones que se ejecutan antes de cada test y que pueden proporcionar datos de prueba o realizar configuraciones necesarias.

Por ejemplo:
```bash
import pytest

@pytest.fixture
def setup():
    # realizar la configuración necesaria
    yield
    # limpiar después de cada test si es necesario
```

### Fixtures avanzadas
[Tabla de contenidos](#tabla-de-contenidos)

Las fixtures en pytest pueden ser mas complejas y pueden tener un alcance mas amplio. Por ejemplo, puedes definir fixtures que dependan de otras fixtures, utilizar parametros en las fixtures y controlar el alcance de las fixtures.

Por ejemplo:

```python
import pytest

@pytest.fixture
def setup():
    # Setup inicial
    yield
    # Teardown final

@pytest.fixture
def usuario(setup):
    usuario = crear_usuario()
    yield usuario
    eliminar_usuario(usuario)

def test_usuario_creado(usuario):
    assert usuario.estado == 'activo'
```

## Parametrización de tests
[Tabla de contenidos](#tabla-de-contenidos)

- Con pytest, puedes parametrizar tus tests para probar diferentes casos de entrada con un sola funcion de test. Esto permite escribir menos codigo y mantener tus test mas limpios.

Ejemplos:

```python
import pytest

@pytest.mark.parametrize("a, b, resultado", [(2, 3, 5), (5, 3, 2), (2, 3, 6)])
def test_operaciones(calculadora, a, b, resultado):
    assert calculadora.suma(a, b) == resultado
```

- Pytest te permite ejecutar tus tests en paralelo, lo que puede reducir significativamente el tiempo de ejecucion de tus suites de tests, especialmente en proyectos grandes.

```bash
pytest -n auto
```

## Uso de Marcadores
[Tabla de contenidos](#tabla-de-contenidos)

Los marcadores son una forma de etiquetar tus test para controlar su ejecucion y aplicar configuraciones adicionales.

```python
import pytest

@pytest.mark.slow
def test_calculo_lento():
    # Test de una operación lenta
    pass
```

## Uso de Mocks
[Tabla de contenidos](#tabla-de-contenidos)

Los Mocks son objetos simulados que se utilizan en lugar de objetos reales durante las pruebas. Pytest proprociona un conjunto de herramientas para crear y utilizar mocks facilmente en tus test.

Ejemplo:

Supongamos que tienes una fucion 'enviar_correo' que utiliza una clase 'Servidor_correo' para enviar correos electronicos. Queremos probar 'enviar_correo', pero no queremos depender del servidor de correo real durante nuestras pruebas.

Primero, necesitaremos instalar el paquete 'pytest-mock', que proporciona funcionalidades de mocks integradas con pytest:
```bash
pip install pytest-mock
```

> [!IMPORTANT]
> Este modulo de pytest suele dar problemas, la solucion es recargar el entorno virtual.

Luego, podemos escribir nuestro test utilizando mocks:

```bash
# Código de la función enviar_correo
class ServidorCorreo:
    def enviar(self, destinatario, mensaje):
        # Código para enviar el correo
        pass

def enviar_correo(destinatario, mensaje):
    servidor_correo = ServidorCorreo()
    servidor_correo.enviar(destinatario, mensaje)
```
```bash
# Test utilizando mocks
import pytest
from pytest_mock import mocker
from mi_modulo import enviar_correo, ServidorCorreo

def test_enviar_correo(mocker):
    mocker.patch.object(ServidorCorreo, 'enviar')  # Mockeamos el método 'enviar' de la clase ServidorCorreo
    enviar_correo('destinatario@example.com', 'Hola, esto es un correo de prueba')
    ServidorCorreo.enviar.assert_called_once_with('destinatario@example.com', 'Hola, esto es un correo de prueba')
```

## Cobertura de codigo
[Tabla de contenidos](#tabla-de-contenidos)

Puedes usar pytest junto con herramientas de cobertura como 'coverage.py' para medir la cobertura de tu codigo con test. Esto te ayuda a identificar areas de tu codigo que no estan sienso probadas y a garantizar una cobertura completa.

### Coverage.py

1) Instalat coverage.py:
    ```bash
    pip install coverage
    ```
2) Ejecutar tus pruebas con cobertura:
   1) Una vez tengas instalada la herramienta de cobertura, puedes ejecutar tus pruebas con la opcion:
        ```bash
        coverage run -m pytest
        ```
3) Generar un informe de cobertura
   1) Despues de ejecutar tus pruebas, puedes generar un informe de cobertura utilizando el comando:

        ```bash
        coverage report
        ```
    2) Esto te mostrara un resumen de la cobertura de tu codigo.

4) Visualizar el informe de cobertura:
   1) Ademas del informe de texto puedes  generar un informe  HTML mas detallado.
        ```bash
        coverage html
        ```

5) Integracion con herramientas de CI/CD:
   1) Puedes integrar la ejecucion de la cobertyra de codigo en tus pipelines de integracion continua(CI) para asegurarte de que siempre estas evaluando la cobertura de tus pruebas.
   2) Esto te ayuda a mantenesr un codigo probado y a detectar posibles areas de mejora en tus pruebas.
   
6) Ajustar la configuracion de cobertura:
   1) Puedes ajustar la configuracion de cobertura segun tus necesidades, como excluir ciertos directorios o archivos de ser incluidos en el analisis de cobertura.


## Plugins
[Tabla de contenidos](#tabla-de-contenidos)

Pytests tiene una amplia gama de plugins disponibles que añaden funcionalidades adicionales, como la integracion con herramientas de calidad de codigo, generacion de informes HTML, patalelizacion de test, entre otros.

[Plugins pytest](https://docs.pytest.org/en/7.1.x/reference/plugin_list.html)


## Ejemplo Pytest
[Tabla de contenidos](#tabla-de-contenidos)

- Creamos una carpeta llamada mytest.
- Dentro de ella creamos los archivos calculadora.py y test_calculadora.py

calculadora.py:
```python
class Calculadora:
    def suma(self, a, b):
        return a + b

    def resta(self, a, b):
        return a - b

    def multiplicacion(self, a, b):
        return a * b

    def division(self, a, b):
        if b == 0:
            raise ValueError("No se puede dividir por cero.")
        return a / b
```

test_calculadora.py
```bash
import pytest
from calculadora import Calculadora

@pytest.fixture
def calculadora():
    return Calculadora()

def test_suma(calculadora):
    assert calculadora.suma(2, 3) == 5

def test_resta(calculadora):
    assert calculadora.resta(5, 3) == 2

def test_multiplicacion(calculadora):
    assert calculadora.multiplicacion(2, 3) == 6

def test_division(calculadora):
    assert calculadora.division(6, 3) == 2
```

Y ejecutamos:
```bash
pytest
```

Ahora veras la salida de los test realizados.

## Ejemplo Coverage
[Tabla de contenidos](#tabla-de-contenidos)

correo.py:

```bash
# Código de la función enviar_correo
class ServidorCorreo:
    def enviar(self, destinatario, mensaje):
        # Código para enviar el correo
        pass

def enviar_correo(destinatario, mensaje):
    servidor_correo = ServidorCorreo()
    servidor_correo.enviar(destinatario, mensaje)
```

test_correo.py

```bash
# Test utilizando mocks
import pytest
from pytest_mock import mocker
from correo import enviar_correo, ServidorCorreo

def test_enviar_correo(mocker):
    mocker.patch.object(ServidorCorreo, 'enviar')  # Mockeamos el método 'enviar' de la clase ServidorCorreo
    enviar_correo('destinatario@example.com', 'Hola, esto es un correo de prueba')
    ServidorCorreo.enviar.assert_called_once_with('destinatario@example.com', 'Hola, esto es un correo de prueba')
```

## Conclusión:
[Tabla de contenidos](#tabla-de-contenidos)

- pytest es una herramienta de prueba potente y flexible para Python que ofrece una sintaxis simple y clara, lo que facilita la escritura y lectura de pruebas. Sus características como fixtures y parametrización permiten una configuración flexible de las pruebas, mientras que los plugins proporcionan funcionalidades adicionales según las necesidades del proyecto.

- La comunidad activa y el soporte de una amplia gama de plugins hacen de pytest una opción popular para proyectos de cualquier tamaño. Además, su integración con otros frameworks de prueba y su capacidad para generar informes detallados de cobertura hacen que sea una herramienta completa para el desarrollo de software en Python.

- En resumen, pytest es una opción sólida para escribir pruebas en Python, que ayuda a garantizar la calidad del código y facilita el proceso de desarrollo de software al proporcionar una infraestructura de prueba confiable y fácil de usar.