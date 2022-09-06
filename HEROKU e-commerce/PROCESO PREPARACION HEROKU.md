https://youtu.be/XdZeg3iP5BM

primeramente instalar gunicorn
``pip install gunicorn ``

como utilizaremos postgres, tenemos que usar la siguiente librería

``pip install psycopg2``


para realizar la conexión entre el proyecto y el gestor de base de datos usaremos
``pip install dj-database-url``
ya que heroku nos proveerá de una base de datos que no se encuentra en el mismo servidor

para iniciar el servidor necesitamos ciertas variables de entorno, para eso usaremos
``pip install python-decouple``

instalaremos whitenoise porque Django no soporta subir archivos estáticos en producción
``pip install whitenoise``


ya instalado todo esto tenemos que hacer el requirements.txt
``pip freeze > requirements.txt``


ya instalado esto vamos a nuestro archivo settings y ponemos DEBUG en False
``DEBUG = False``
y 
``ALLOWED_HOST = ['**']``
esto para permitir todos los host (en este proyecto)


ahora vamos con la base de datos
![[Pasted image 20220905165517.png]]
(comente esto por si lo vuelvo a usar) abajo ponemos

```
...

from decouple import config

import dj_database_url

...

DATABASES = {

    'default': dj_database_url.config(

        default=config('DATABASE_URL')

    )

}
```

ahora vamos con los archivos estaticos (que es donde hay mas problema), buscamos donde esta la variable STATIC_URL y ponemos
```
...

STATIC_ROOT = os.path.join(BASE_DIR, 'staticfiles')

STATIC_URL = '/static/'

  

STATICFILES_DIRS = [

    os.path.join(BASE_DIR, "frontend/build"),

    os.path.join(BASE_DIR, 'static'),

]
...
```

Django no soporta subir archivos estáticos en producción, asi que nos apoyaremos en whitenoise que instalamos arriba, vamos a la lista de MIDDLEWARE y ponemos esto hasta abajo

```
'whitenoise.middleware.WhiteNoiseMiddleware',

```
![[Pasted image 20220905171046.png]]
y lo siguiente igual hasta el final de nuestro archivo de settings.py esta nos ayuda a mostrar archivos estaticos imagenes js y css en nuestro proyecto

``STATICFILES_STORAGE = 'whitenoise.storage.CompressedManifestStaticFilesStorage'``

ahora vamos al archivo urls.py e importamos lo siguiente

```
from django.conf import settings

from django.conf.urls.static import static
```

y al final de urlpatterns ponemos
``+ static(settings.STATIC_URL, document_root=settings.STATIC_ROOT)``

lucirá algo así
![[Pasted image 20220905171454.png]]

ahora algo IMPORTANTE, devemos generar una carpeta static al mismo nivel que manage.py y poner un archivo llamado .keep en blanco, esto porque en heroku se ejecutara de forma automática el ``colect statics`` y si no la tiene nos marcara error... yo la cree y aun asi me marcaba un error entonces puse el comando 
``python manage.py collectstatic`` 
y se soluciono
![[Pasted image 20220905171847.png]]

de igual manera algo super importante es crear un archivo llamado ``Procfile`` (asi con mayúscula la primera) y dentro poner lo siguiente
``web: gunicorn ecommerce.wsgi``
con esta linea le estamos indicando a ``gunicorn`` que ejecute el archivo wsgi.py de nuestro proyecto (osease este)
![[Pasted image 20220905172402.png]]

con esto "terminamos" (notese las comillas) la configuración de nuestro proyecto para subirlo a heroku, asi que hacemos un commit
```
$ git add --all
$ git commit -m "Configuraciones Heroku"
```
ahora vamos a heroku.com y le damos en crear app, para esto ya tendremos que aver instalado el cliente de heroku desde su pagina

https://devcenter.heroku.com/articles/heroku-cli
![[Pasted image 20220905173125.png]]
(a mi no me funciono luego luego asi que tube que reiniciar el mounstro)

ya instalado, hacemos login en la terminal con
![[Pasted image 20220905173258.png]]
![[Pasted image 20220905173326.png]]
![[Pasted image 20220905173357.png]]

ahora creamos el proyecto en heroku con el comando
``heroku create velvet-ecommerce``
ahora ligamos nuestro repositorio a la app de heroku
``heroku git:remote -a velvet-ecommerce``

ahora crearemos nuestra base de datos
``heroku addons:create heroku-postgresql:hobby-dev``
esto nos devolvera el mensaje de que ya fue creada la variable ``DATABASE_URL`` que es la que declaramos como variable de entorno.

ahora subiremos nuestro proyecto al repositorio, aqui me dio muchos problemas ya que ahora no se usa master si no main, yo la regué y siguiendo una solución de stack use el comando ``git push heroku multiple-images:main`` porque era la ram que estaba usando y me dejo subirlo pero no corre
![[Pasted image 20220905173939.png]]

entonces para subirlo usamos 
``git push heroku mail``
nos saldra un mensaje que ya hizo DEPLOY

ya que subio ahora nos toca hacer las migraciones ya que creamos una nueva base de datos, asi que ponemos 
``heroku run python ecommerce/manage.py migrate`` 

y listo con esto nos debería de aparecer nuestra app en la pagina de heroku le damos donde dice "open app"
![[Pasted image 20220905180305.png]]