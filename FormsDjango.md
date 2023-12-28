# Formularios en Django

--------------

[//]: # (version: 1.0)
[//]: # (author: Jose Carlos Limones Hernandez)
[//]: # (date: 2020-12-8)

## Tabla de contenidos

- [Formularios en Django](#formularios-en-django)
  - [Tabla de contenidos](#tabla-de-contenidos)
  - [1- Introducción](#1--introducción)
  - [Formularios generados por Django](#formularios-generados-por-django)
    - [Validacion de formularios "Validators"](#validacion-de-formularios-validators)
    - [Mensajes/Sesiones Flash](#mensajessesiones-flash)
  - [Fuentes](#fuentes)

## 1- Introducción

[Tabla de contenidos](#tabla-de-contenidos)

En este manual vamos a ver ejemplos de como se pueden generar formularios desde Django:

## Formularios generados por Django

[Tabla de contenidos](#tabla-de-contenidos)

- Ejemplo views.py
  ```python
  from myapp.forms import FormEmpleado # Importamos el forms.py que crearemos a continuación

  def create_full_empleado(request):
    if request.method == 'POST':
        formulario = FormEmpleado(request.POST)

        if formulario.is_valid():
            data_form = formulario.cleaned_data

            nombre = data_form['nombre']
            apellidos = data_form['apellidos']
            edad = data_form['edad']
            autorizado = data_form['autorizado']
            carta = data_form['carta']
            print('Esta entrando')
            empleado = Empleado.objects.create(
                nombre = nombre,
                apellidos = apellidos ,
                edad = edad,
                autorizado = autorizado,
                carta_presentacion = carta,
            )
            return redirect('empleados')
    else:
        formulario = FormEmpleado()
        print('No esta entrando')
    
    return render(request, 'create_full_empleado.html', {
        'form': formulario
    })
  ```

  - Método HTTP:

    - Verifica si la solicitud es una solicitud POST.
    - Si es POST, significa que el formulario ha sido enviado.

  - Creación del formulario:

    - Crea una instancia del formulario FormEmpleado utilizando los datos de la solicitud POST (si está presente). Si no hay datos POST, se crea un formulario vacío.
    - FormEmpleado es un formulario basado en una clase, presumiblemente definido en algún lugar de tu aplicación, y contiene campos para los atributos de un Empleado, como nombre, apellidos, edad, etc.

  - Validación del formulario:

    - Verifica si el formulario es válido llamando al método is_valid(). Este método realiza validaciones en los datos ingresados y devuelve True si el formulario es válido, o False en caso contrario.

  - Acceso a los datos del formulario:

    - Si el formulario es válido, se accede a los datos limpios (cleaned_data) del formulario. Estos son los datos que han pasado las validaciones del formulario.
    - Se extraen los valores específicos del formulario, como nombre, apellidos, edad, etc.

  - Creación del objeto Empleado:

    - Se utiliza la función Empleado.objects.create() para crear un nuevo objeto Empleado en la base de datos utilizando los valores extraídos del formulario.

  - Redirección:

    - Después de crear el objeto Empleado, redirige al usuario a la vista 'empleados'. Puedes ajustar esto según tus rutas y nombres de vistas específicos.

  - Formulario no válido o solicitud GET:

    - Si la solicitud no es POST (es decir, una solicitud GET) o si el formulario no es válido, se renderiza la plantilla 'create_full_empleado.html' con el formulario para que el usuario pueda completar los datos.

- Ejemplo urls.py
  ```python
  path('create_full_empleado/', views.create_full_empleado, name="create_full_empleado")
  ```

- A continuacion crearemos un archivo en el directorio de nuestra aplicacion ***myapp*** llamado forms.py
  - Ejemplo forms.py
    ```python
    from django import forms

    class FormEmpleado(forms.Form):
        nombre = forms.CharField(
            label = 'Nombre'
        )
        apellidos = forms.CharField(
            label = 'Apellidos'
        )
        edad = forms.IntegerField(
            label = 'Edad'
        )
        opciones = [
            (1, 'Si'),
            (0, 'No'),
        ]
        autorizado = forms.TypedChoiceField(
            label = '¿Autorizado?',
            choices=opciones,
            widget=forms.Select
        )
        carta = forms.CharField(
            label = 'Carta de presentacion',
            widget=forms.Textarea
        )
    ```

- Ahora cargaremos nuestro formulario en la template:

  - Ejemplo template, create_full_empleado.html
    ```python
    {% extends "layout.html" %}

    {% block title %}
    Formularios en Django
    {% endblock title %}


    {% block content %}
    <h1 class="title">Formularios en Django</h1>
    <form action="" method="POST">
        {% csrf_token %}
        {{ form }}
        <input type="submit" value="Guardar">
    </form>

    {% endblock content %}
    ```


### Validacion de formularios "Validators"

[Tabla de contenidos](#tabla-de-contenidos)

- Los "validators" son funciones o clases que se utilizan para validar los datos ingresados en los campos de un modelo. Estos validators permiten establecer reglas específicas sobre qué datos son aceptables y cuáles no en un campo determinado.

- En la template debemos insertar una condicion para mostrar el error:
  ```django
  {% if form.errors %}
    <strong>Hay Errores en el formulario</strong>
  {% endif %}
  ```

- Ejemplo forms.py
  ```python
  from django import forms
  from django.core import validators

  class FormEmpleado(forms.Form):
      nombre = forms.CharField(
          label = 'Nombre',
          required=True,
          validators=[
              validators.MaxLengthValidator(20, 'El nombre es demasiado largo'), # El número máximo de carácteres es de 20.
              validators.RegexValidator('^[A-Za-z0-9ñ ]*$', 'Caracteres no validos', 'Invalid_name') # Solo se puede utilizar los carácteres especificados.
          ]
      )
  ```
> Esto es solo un ejemplo, para mas detalles visite [Django validators](https://docs.djangoproject.com/en/5.0/ref/validators/#maxlengthvalidator) .


### Mensajes/Sesiones Flash

[Tabla de contenidos](#tabla-de-contenidos)

Las sesiones flash son un mecanismo utilizado en muchos frameworks web, incluyendo Django, para enviar mensajes temporales entre las solicitudes del usuario. Estos mensajes generalmente se utilizan para mostrar notificaciones o mensajes informativos después de realizar una acción, como enviar un formulario.

- Ejemplo viwes.py
  ```python
  from django.contrib import messages

  def create_full_empleado(request):
      if request.method == 'POST':
          formulario = FormEmpleado(request.POST)

          if formulario.is_valid():
              data_form = formulario.cleaned_data

              nombre = data_form['nombre']
              apellidos = data_form['apellidos']
              edad = data_form['edad']
              autorizado = data_form['autorizado']
              carta = data_form['carta']
              empleado = Empleado.objects.create(
                  nombre = nombre,
                  apellidos = apellidos ,
                  edad = edad,
                  autorizado = autorizado,
                  carta_presentacion = carta,
              )

              messages.success(request, f'El empleado: {empleado.id} llamado {empleado.nombre} se ha creado correctamente')

              return redirect('empleados')
      else:
          formulario = FormEmpleado()
      
      return render(request, 'create_full_empleado.html', {
          'form': formulario
      })
  ```

- Ejemplo template:
  ```python
  {% if messages %}
    {% for message in messages %}
        <div class="message">
            {{ message }}
        </div>
    {% endfor %}
  {% endif %}
  ```


## Fuentes

[Tabla de contenidos](#tabla-de-contenidos)

- [Django projects](https://www.djangoproject.com/)
- [Tutorial Python](https://docs.python.org/es/3/tutorial/)
- [Instalacion VSCode](https://alfonsomozkoh.github.io/2020/07/01/como-instalar-visual-studio-code-en-linux.html)
