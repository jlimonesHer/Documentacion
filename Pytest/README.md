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
  - [Parametrización de tests](#parametrización-de-tests)
  - [Uso de Mocks](#uso-de-mocks)
  - [Cobertura de codigo](#cobertura-de-codigo)
  - [Conclusión](#conclusión)
  - [Plugins](#plugins)
  - [Ejemplo](#ejemplo)

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

## Parametrización de tests
[Tabla de contenidos](#tabla-de-contenidos)

Con pytest, puedes parametrizar tus tests para probar diferentes casos de entrada con un sola funcion de test. Esto permite escribir menos codigo y mantener tus test mas limpios.

Ejemplos:

```python
import pytest

@pytest.mark.parametrize("a, b, resultado", [(2, 3, 5), (5, 3, 2), (2, 3, 6)])
def test_operaciones(calculadora, a, b, resultado):
    assert calculadora.suma(a, b) == resultado
```

## Uso de Mocks
[Tabla de contenidos](#tabla-de-contenidos)

Los Mocks son objetos simulados que se utilizan en lugar de objetos reales durante las pruebas. Pytest proprociona un conjunto de herramientas para crear y utilizar mocks facilmente en tus test.

## Cobertura de codigo
[Tabla de contenidos](#tabla-de-contenidos)

Puedes usar pytest junto con herramientas de cobertura como 'coverage.py' para medir la cobertura de tu codigo con test. Esto te ayuda a identificar areas de tu codigo que no estan sienso probadas y a garantizar una cobertura completa.



## Conclusión
[Tabla de contenidos](#tabla-de-contenidos)

Estos son los conceptos básicos de pytest y cómo escribir tests efectivos en Python. Ahora estás listo para empezar a escribir tus propios tests para tus proyectos.

## Plugins
[Tabla de contenidos](#tabla-de-contenidos)

Pytests tiene una amplia gama de plugins disponibles que añaden funcionalidades adicionales, como la integracion con herramientas de calidad de codigo, generacion de informes HTML, patalelizacion de test, entre otros.

## Ejemplo
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