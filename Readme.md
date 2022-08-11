# Creación de proyecto Django.

### 1- Crear proyecto.
Para la creación del proyecto genérico de Django, se deberá ejecutar 
el comando de consola siguiente:
``django-admin startproject nombre_proyecto``.

Este comando crea en nuestro directorio del proyecto la estructura del proyecto Django a desarrollar.

Dentro de dicho directorio, se encuentra una subcarpeta con el mismo nombre del proyecto donde
se encuentra los archivos de configuración del proyecto Django. Donde encontramos:
- __ *init* __*.py*: Python package.
- *asgi.py**: Configurar el despliegue en servidor.
- *setings.py*: Configuración de características. Agregar aplicaciones en proyecto Django. Configurar conexion a BBDD...
- *urls.py*: Añadir urls del proyecto
- *wsgi.py*: Despliegue de la applicacion en servidor

Adicionalmente, el archivo *manage.py* en la carpeta superior
nos permitirá ejecutar los comandos para el proyecto.

### 2- Ejecutar aplicación.
Para poder ejecutar nuestra aplicación, se debe acceder al directorio de nuestro proyecto
donde se encuentra el archivo *manage.py* mencionado ya que es el encargado de ejecutar
el comando para empezar: ``python manage.py runserver``

***Nota:*** *Tras ejecutar el servicio de nuestra aplicación, Django crea de forma automática
un archivo *db.sqlite3* pues es el que emplea para base de datos. Aunque se puede añadir 
otra base de datos para trabajar.*

# Creación de Views
Para agregar el contenido web a nuestra aplicación, primero saber qué es el concepto de **App**.

El concepto App ayuda a organizar mas eficientemente la aplicación Django. Un proyecto, puede contener
varias App para diferentes funcionalidades cada una (Organizar páginas de la aplicación, 
gestionar datos...)

Para lanzar una App, desde el directorio de nuestro proyecto, se ejecutará ``python manage.py startapp nombre_app``.
Una vez ejecutado el comando, al mismo nivel que nuestra subcarpeta del proyecto Django, se creará otro directorio
con el nimbre de nuestra App.

Dentro de dicho directorio, se crea una serie de archivos *.py* para la gestión de nuestra App, entre ellos, 
*views.py*.

### PASOS CREACIÓN VIEW
### 1- Agregar App
Para que cualquier App que deseemos emplear en nuestro proyecto esté disponible, es necesario
registrar la misma. Para ello, desde el fichero *settings.py* en nuestro directorio del proyecto 
Django creado, se añadirá en la lista *INSTALLED_APPS* el nombre de nuestra app.

***Nota:*** *Esta lista, deberá terminar con coma ','.*

### 2- Agregar URL
Para poder visualizar nuestra app, se deberá crear el *url* necesario. Para ello, en el 
archivo *urls.py* del directorio del proyecto, se añadirá un path deseado, seguido de la función que 
se ejecutará en el mismo. Dicha función, se debe definir en el archivo *views.py* del directorio de la 
app deseada.

Por lo tanto, en la lista *urlpatterns* se deberá añadir el siguiente path (a modo ejemplo):
``path('cualquier_url/', funcion),``. Si queremos que sin necesidad de insertar url se ejecute una pagina, 
el path deberemos dejarlo vacio tal que ``path('', funcion)``.

Para poder emplear la función deseada, se deberá importar desde la ruta del archivo *views.py* del
directorio de la app ``from nombre_proyecto.nombre_app.views import nombre_funcion``

***Nota:*** *Esta lista, deberá terminar con coma ','.*

***Nota:*** *Por defecto, existe el url admin/ para gestionar los usuarios de la aplicación.*

### 3- Crear Funcion
Desde el archivo *views.py* de nuestra App, se definirá la función deseada. Esta función, ha de recibir el 
parámetro *request*. Este parámetro request, de modo automático proporciona la información desde el navegador
a nuestra aplicación Django.

Como parámetro return de la función, se le indica a Django un *HttpResponse* con la información necesaria.

***Nota:*** *HttpResponse, debe ser importado para poder emplearlo desde django.http*

### IMPORTANTE
En el caso que exista algun fallo *ModuleNotFoundError* en la importación de la función de view de nuestra app,
se debe indicar en el editor (en este caso Pycharm) que nuestro directorio del proyecto Django es nuestro "Source Root"