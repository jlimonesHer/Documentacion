# Mi Primer Proyecto Selenium
--------------

[//]: # (version: 1.0)
[//]: # (author: Jose Carlos Limones)
[//]: # (date: 2024-02-22)



# Tabla de contenidos
- [Mi Primer Proyecto Selenium](#mi-primer-proyecto-selenium)
- [Tabla de contenidos](#tabla-de-contenidos)
  - [Introducción](#introducción)
  - [Empiezo el proyecto creando un entorno virtual de python:](#empiezo-el-proyecto-creando-un-entorno-virtual-de-python)
    - [Importe la libreria](#importe-la-libreria)
    - [Inicie la sesion:](#inicie-la-sesion)
    - [URL a la que queremos ir](#url-a-la-que-queremos-ir)
    - [Solicita informacion al navegador](#solicita-informacion-al-navegador)
    - [Imprima resultado](#imprima-resultado)
    - [Cerrar el navegador y finalizar la sesión de WebDriver.](#cerrar-el-navegador-y-finalizar-la-sesión-de-webdriver)
    - [Establecer estrategia de espera](#establecer-estrategia-de-espera)
    - [Encuentra el elemento](#encuentra-el-elemento)
    - [Realice acciones sobre el elemento](#realice-acciones-sobre-el-elemento)
    - [Solicitar infomacion de un elemento](#solicitar-infomacion-de-un-elemento)
    - [Capturas de Pantalla](#capturas-de-pantalla)
  - [Ejercicio 1](#ejercicio-1)
    - [Solucion Ejercicio 1](#solucion-ejercicio-1)
  - [Ejercicio 2](#ejercicio-2)
    - [Solucion Ejercicio 2](#solucion-ejercicio-2)
  - [Ejercicio 3](#ejercicio-3)
    - [Solucion Ejercicio 4](#solucion-ejercicio-4)

## Introducción
[Tabla de contenidos](#tabla-de-contenidos)

[Documentacion de Selenium](https://www.selenium.dev/documentation/)

- Selenium es un proyecto para una variedad de herramientas y bibliotecas que permiten y respaldan la automatización de navegadores web.
- Proporciona extensiones para emular la interaccion del usuario con los navegadores, un servidor de distribucion para escalar la asignacion de navegadores y la infraestructura para implementaciones de la especificación [W3C WebDriver](https://www.w3.org/TR/webdriver/) que le permite escribir código intercambiable para los principales navegadores web.

## Empiezo el proyecto creando un entorno virtual de python:
[Tabla de contenidos](#tabla-de-contenidos)

```bash
# Crea un entorno virtual
python3 -m venv venv

# Activa el entorno virtual (Linux/macOS)
source venv/bin/activate
```

- Creamos nuestro primer script:
```python
from selenium import webdriver


driver = webdriver.Chrome()

driver.get("https://www.selenium.dev/selenium/web/web-form.html")
title = driver.title
print(title)
driver.quit()
```
### Importe la libreria
```python
from selenium import webdriver
```

### Inicie la sesion:
```python
driver = webdriver.Chrome()
```
### URL a la que queremos ir
```python
driver.get("https://github.com/jlimonesHer")
```
### Solicita informacion al navegador
  - Hay muchos tipos de información sobre el navegador que puede solicitar, incluidos identificadores de ventanas, tamaño/posición del navegador, cookies, alertas, etc
```python
title = driver.title
```
### Imprima resultado
```python
print(title)
```
### Cerrar el navegador y finalizar la sesión de WebDriver.
```python
driver.quit()
```

### Establecer estrategia de espera
- La función driver.implicitly_wait(t) en Selenium establece un tiempo de espera implícito para la búsqueda de elementos. Este tiempo de espera se aplica de manera global a todas las búsquedas de elementos realizadas por el WebDriver.

- La función toma un argumento t, que es el tiempo de espera en segundos. En tu ejemplo, driver.implicitly_wait(0.5) significa que Selenium esperará hasta 0.5 segundos antes de lanzar una excepción si no puede encontrar un elemento inmediatamente. Esto es útil para manejar situaciones en las que los elementos tardan un poco en cargarse después de que la página se ha cargado.

```python
driver.implicitly_wait(0.5)
```

### Encuentra el elemento
- La mayoria de las sesiones de Selenium estan relacionados con elementos y debes encontrarlo para ello:
```python
from selenium.webdriver.common.by import By 

text_box = driver.find_element(by=By.NAME, value="my-text")
submit_button = driver.find_element(by=By.CSS_SELECTOR, value="button")
```
- ID:
```python
By.ID
```
- Name:

```python
By.NAME
```
- Class name:

```python
By.CLASS_NAME
```
- Tag name:

```python
By.TAG_NAME
```
- Link text:

```python
By.LINK_TEXT
```
- Partial link text:

```python
By.PARTIAL_LINK_TEXT
```
- CSS selector:

```python
By.CSS_SELECTOR
```
- XPath:

```python
By.XPATH
```
- Estas estrategias se utilizan con el método find_element de la clase WebDriver para localizar elementos en la página web. Por ejemplo, para encontrar un elemento por su ID, puedes usar:

```python
element = driver.find_element(By.ID, "mi_id")
```
- O para encontrar un elemento por su nombre, puedes usar:

```python
element = driver.find_element(By.NAME, "mi_nombre")
```
- 

### Realice acciones sobre el elemento

```python
text_box.send_keys("Selenium")
submit_button.click()
```

### Solicitar infomacion de un elemento
```python
text = message.text
```

### Capturas de Pantalla
[Tabla de contenidos](#tabla-de-contenidos)

- Debemos intalar Pillow para selenium
```python
pip install selenium Pillow
```

- Despues importamos la libreria
```python
from PIL import Image
```
- Ejecutamos la funcion save_screenshot("nombre_captura"):
```python
driver.save_screenshot("pantalla_despues_proceed.png")
```

## Ejercicio 1
[Tabla de contenidos](#tabla-de-contenidos)

> [!NOTE]
> En este ejercicio vamos a practicar con selenium y  la página de practica [GreenKart](https://rahulshettyacademy.com/seleniumPractise/#/). Simularemos la compra de un producto utilizando esta libreria.

### Solucion Ejercicio 1
[Tabla de contenidos](#tabla-de-contenidos)

- Importamos dependencias:
```python
from selenium import webdriver
from selenium.webdriver.common.by import By
```

- Probamos que es la pagina deseada:
```python
driver.get("https://rahulshettyacademy.com/seleniumPractise/#/")
title = driver.title
assert title == "GreenKart - veg and fruits kart"
```
- Asignamos el tiempo de espera
```python
driver.implicitly_wait(0.5)
```
- Guardamos cada elemento encontrandolos por sus atributos:
```python
searchInput = driver.find_element(by=By.XPATH, value='//input[@type="search"]')
increment = driver.find_element(by=By.CSS_SELECTOR, value="a.increment")
quantityInput = driver.find_element(by=By.XPATH, value="//input[@type='number']")
```
- En el buscador insertamos la palabra deseada:
```python
searchInput.send_keys("Broco")
```
- Hacemos click en el boton de incrementar:
```python
increment.click()
```
- Recogemos el valor del contador y lo comprobamos:
```python
quantitySelected = quantityInput.get_attribute("value")

assert quantitySelected == '2'
```
- Guardamos y hacemos click ne el desplegable del carrito
```python
button_add_product = driver.find_element(by=By.CSS_SELECTOR, value=".product-action button")
button_add_product.click()
```
- Guardamos y hacemos click en el boton de proceed
```python
button_proceed = driver.find_element(by=By.XPATH, value='//button[contains(text(), "PROCEED TO CHECKOUT")]')
button_proceed.click()
```
- Comprobamos que el total de la compra es el correcto
```python
totalAmount = driver.find_element(by=By.CLASS_NAME, value='amount').text

assert totalAmount == "240"
```
- Aceptamos la orden:
```python
checkAgree = driver.find_element(by=By.CSS_SELECTOR, value='.chkAgree')

checkAgree.click()
```
- Con la clase Select modificamos el campo select, hay que importar la clase:
```python
from selenium.webdriver.support.ui import Select

selectCountry = driver.find_element(by=By.CSS_SELECTOR, value='#root > div > div > div > div > div > select')
select = Select(selectCountry)
select.select_by_value("Spain")
```
- Mostrar la opcion seleccionada
```python
select_option = select.first_selected_option
select_text = select_option.text
print(select_text)
```
- Pulsamos el boton de realizar compra:
```python
btnProceed = driver.find_element(by=By.XPATH, value='//button[contains(text(), "Proceed")]')
btnProceed.click()
```

## Ejercicio 2
[Tabla de contenidos](#tabla-de-contenidos)

> [!NOTE]
> En este ejercicio vamos a practicar con selenium y  la página de practica [GreenKart](https://rahulshettyacademy.com/seleniumPractise/#/). Simularemos la compra de varios productos utilizando esta libreria y POO(Programacion Orientadada a Objetos).

### Solucion Ejercicio 2
[Tabla de contenidos](#tabla-de-contenidos)

```python
from selenium import webdriver
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import Select
from PIL import Image
import time

class GreenKartTest:
    """Es una clase que testea  como realizar una compra en la web de parctica.
    """
    def __init__(self):
        """
        Constructor de la clase.
        self.driver = webdriver.Chrome() -> inicializa un objeto d la clase webdriver.
        self.open_website() -> Abre el navegador.
        self.searchInput -> Guarda el input del buscador de la web.
        """
        self.driver = webdriver.Chrome()
        self.open_website()
        self.searchInput = self.driver.find_element(by=By.XPATH, value='//input[@type="search"]')       

    def open_website(self):
        """Abre el sitio web para las pruebas.
        Establece el tiempo de espera para la carga de la página.
        """
        self.driver.get("https://rahulshettyacademy.com/seleniumPractise/#/")
        self.driver.implicitly_wait(0.5)

    def delete_text(self):
        """Elimina el texto del input del buscador de productos
        """
        self.searchInput.clear()

    def search_product(self, product):
        """Inserta el nombre del producto deseado en el buscador de productos.

        Args:
            product (string): Recibe el nombre del producto.
        """
        self.searchInput.send_keys(product)

    def add_unit(self, number):
        """Añade una cantidad del producto seleccionado.

        Args:
            number (int): Recibe un entero que determina el numero de unidades del producto
        """
        quantitySelected = 1
        while quantitySelected != number:
            quantityInput = green.driver.find_element(by=By.XPATH, value="//input[@type='number']")
            increment = self.driver.find_element(by=By.CSS_SELECTOR, value="a.increment")
            increment.click()
            quantitySelected = int(quantityInput.get_attribute("value"))
        time.sleep(0.2)
        self.add_cart()
       

    def subtract_unit(self):
        """Resta una unidad del producto al total antyes de añadirlo a la cesta.
        """
        quantityInput = green.driver.find_element(by=By.XPATH, value="//input[@type='number']")
        quantitySelected = int(quantityInput.get_attribute("value"))

        while quantitySelected != 1:
            quantityInput = green.driver.find_element(by=By.XPATH, value="//input[@type='number']")
            quantitySelected = int(quantityInput.get_attribute("value"))
            decrement = self.driver.find_element(by=By.CSS_SELECTOR, value="a.decrement")
            decrement.click()
        time.sleep(0.2)

    def add_cart(self):
        """Añade el total de unidades de un producto a la cesta.
        """
        button_add_product = self.driver.find_element(by=By.CSS_SELECTOR, value=".product-action button")
        button_add_product.click()

    def complet_buy(self):
        """Completa la compra aceptando la lista final de productos.
        Selecciona el pais y acepta terminos y condiciones.
        """
        button_cart = self.driver.find_element(by=By.CSS_SELECTOR, value='[alt="Cart"]')
        button_cart.click()

        button_proceed = self.driver.find_element(by=By.XPATH, value='//button[contains(text(), "PROCEED TO CHECKOUT")]')
        button_proceed.click()

        totalAmount = self.driver.find_element(by=By.CLASS_NAME, value='amount').text

        assert totalAmount != 0
        self.driver.save_screenshot("resumen_cuenta.png")
        placeOrder = self.driver.find_element(by=By.XPATH, value='//button[contains(text(),"Place Order")]')
        placeOrder.click()
        checkAgree = self.driver.find_element(by=By.CSS_SELECTOR, value='.chkAgree')

        checkAgree.click()

        selectBox = self.driver.find_element(by=By.CSS_SELECTOR, value='#root > div > div > div > div > div > select')
        select = Select(selectBox)
        select.select_by_value("Spain")
        btnProceed = self.driver.find_element(by=By.XPATH, value='//button[contains(text(), "Proceed")]')
        btnProceed.click()

        self.driver.save_screenshot("pantalla_despues_proceed.png")

    def complete_process(self, products):
        """Hace el proceso completo de compra.

        Args:
            products (dictionary): recibe un diccionario en el que la clave es
            el numero del producto y el valor la cantidad deseada.
        """
        for product, amount in products.items():
            self.driver.implicitly_wait(0.5)
            self.search_product(product)
            time.sleep(1)
            self.add_unit(amount)
           
            time.sleep(1)
            self.delete_text()
            time.sleep(1)
        self.complet_buy()

# Inicializacion del objeto, declaracion del diccionario y llamada al proceso.

green = GreenKartTest()

products = {
    "Brocolli": 3,
    "Potato": 4, 
    "Tomato": 5, 
    }

green.complete_process(products)

green.driver.quit()
```

## Ejercicio 3
[Tabla de contenidos](#tabla-de-contenidos)

> [!NOTE]
> En este ejercicio seguimos practicando con Selenium y  la página de practica [GreenKart](https://rahulshettyacademy.com/AutomationPractice/) en la que tenemos todos los tipos de input html para ver como se manejan. Crearemos un objeto y un metodo para cada tipo de campo

### Solucion Ejercicio 4
[Tabla de contenidos](#tabla-de-contenidos)

- InputModel.py:
```python
from selenium import webdriver
from selenium.webdriver.support.ui import WebDriverWait
from selenium.webdriver.common.by import By
from selenium.webdriver.support.ui import Select
from PIL import Image
from selenium.webdriver.support import expected_conditions as EC
import time

class InputModel:
    def __init__(self):
        self.driver = webdriver.Chrome()
        self.open_website()
        self.driver.implicitly_wait(0.5)

    def open_website(self):
        self.driver.get("https://rahulshettyacademy.com/AutomationPractice/")
    
    def radio_button(self, option):
        """Este metodo elige un radio_button dependiendo de la opcin pasada

        Args:
            option (int): opcion que va a elegir si existe
        """
        if option == 1:
            radio_button = self.driver.find_element(By.XPATH, '//input[@value="radio1"]')
        elif option == 2:
            radio_button = self.driver.find_element(By.XPATH, '//input[@value="radio2"]')
        elif option == 3:
            radio_button = self.driver.find_element(By.XPATH, '//input[@value="radio3"]')
        else:
            return
        radio_button.click()

    def suggessionClass(self, country):
        inputSugesstion = self.driver.find_element(by=By.ID, value='autocomplete')
        inputSugesstion.send_keys(country)

    def selectExample(self, option):
        inputSelect = self.driver.find_element(by=By.ID, value='dropdown-class-example')
        select = Select(inputSelect)
        if option == 1:
            optionString = "option1"
        elif option == 2:
            optionString = "option2"
        elif option == 3:
            optionString = "option3"
        else:
            return
        select.select_by_value(optionString)

    def checkbox(self, options):
        """Marcara las casillas pasadas por parametros

        Args:
            options (array): Recibe un array de boolenaos.
        """
        checkbox_option1 = self.driver.find_element(By.ID, "checkBoxOption1")
        checkbox_option2 = self.driver.find_element(By.ID, "checkBoxOption2")
        checkbox_option3 = self.driver.find_element(By.ID, "checkBoxOption3")
        checks = (checkbox_option1, checkbox_option2, checkbox_option3)
        for index in range(len(checks)):
            if options[index]:
                checks[index].click()

    def open_window(self):
        """Este método simplemente hace click en el boton, abre la nueva ventana y cambia el foco de una ventana a otra.
        los tiempos de espera los dejamos para ver su funcionamiento.
        """
        button = self.driver.find_element(by=By.ID, value="openwindow")
        button.click()
        time.sleep(1)
        handles = self.driver.window_handles
        time.sleep(1)
        new_window = handles[-1]
        time.sleep(1)
        self.driver.switch_to.window(new_window)
        time.sleep(1)

        # Realizar acciones en la nueva ventana (si es necesario)
        # ...

        # Cerrar ventana actual
        self.driver.close()
        # Regresar a la ventana principal
        self.driver.switch_to.window(handles[0])

    def open_tab(self):
        """Este método simplemente hace click en el boton, abre la nueva pestaña y cambia el foco de una pestaña a otra.
        los tiempos de espera los dejamos para ver su funcionamiento.
        """
        button = self.driver.find_element(by=By.ID, value="opentab")
        button.click()
        time.sleep(1)
        handles = self.driver.window_handles
        time.sleep(1)
        new_tab = handles[-1]
        time.sleep(1)
        self.driver.switch_to.window(new_tab)
        time.sleep(1)

        # Realizar acciones en la nueva pestaña (si es necesario)
        # ...

        # Cerrar pestaña actual
        self.driver.close()

        # Regresar a la pestaña principal
        self.driver.switch_to.window(handles[0])
         
    def read_table(self):
        """Esta función Lee y muestra todos los datos de la primera tabla.
        """
        table = self.driver.find_element(by=By.NAME, value='courses')
        rows = self.driver.find_elements(by=By.XPATH, value='//*[@name="courses"]/tbody/tr')
        for row in rows:
            print(row.text)
```
- main.py

```python
            
form = InputModel()

options = (True, False, True)

form.radio_button(3)

form.suggessionClass("España")

form.selectExample(2)

form.checkbox(options)

form.open_window()

form.open_tab()

form.read_table()

time.sleep(2)
form.driver.quit()
```

> [!NOTE]
> Divierte buscando en los demas elementos de la web para apredender mas sobre selenium.

> [!WARNING]
> Las páginas de práctica no me pertenecen, simplemente las encontre buscando por la red, En la documentación oficial de **Selenium** encontraras las herramientas necesarias para aprender y practicar.