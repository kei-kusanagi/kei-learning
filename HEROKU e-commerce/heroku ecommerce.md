primero se configuro todo segun este video

https://youtu.be/XdZeg3iP5BM

primero es meter todos los secrets y key a variables de entorno mediante la función decouple
en settings declaramos la base de datos como bariable de entorno URL y la dejanmos asi

instalamos unicorn para la base de datos

configuramos el debug en false, cambiamos static_url con la diagonal

instalamos whitenoise y lo declaramos en settings junto su middleware

creamos una carpeta llamada static y ponemos un archivo .keep dentro

hacemos un collect statics 

cremoas el archivo Procfile a la altura de manage*******

refrescamos erequeriments.txt

creamos la app en el portal, nos logueamos en terminal con ``heroku login`` 

luego hacemos un ``heroku git add .`` 

luego hacemos un push pero usando la rama ``git push heroku multiple-images:main`` 

si ya hiso deploy entonces tenemos que ir a los secretos dentro de heroku a dar de alta las variabels dentorno y yo aproveche pa sacar la url de la base de datos y tambien ponerla como variable de entorno dentro de mi local

en teeoria con todo esto deveria de correr pero nooooooooooooooo no todo peude ser asi de sensillo

quite el tailwind y lo remplas epor el CDN proque no valla a ser 

y de alli me la pase haciendo cambieos en el procfile

le quite el ``--log-file -`` del final

le puse `` --pythonpath ecommerce.wsgi``

borre algunos paths en urls para ver si era eso y nop

como tengo dos urls.py le agregue 
```
from django.conf import settings  
from django.conf.urls.static import static
urlpatterns = [  
      
    path('', frontpage, name='frontpage'),
    ...
    ...
] + static(settings.STATIC_URL, document_root=settings.STATIC_ROOT)
```

quite la configuracion que recomendaban en herocu docs y deje ``ALLOWED_HOST = ["*"]``

le quite los paths de mas en urls.py que habia puesto

en stac overflow dicen que puede ser borrando el proc, haciendo commit, luego lo creo y hago commit and push y nada

en stack comentan que puede ser si tienes el archivo anidado en otra carpeta y nada
![image](/HEROKU%20e-commerce/IMG/Pasted%20image%2020220902193440.png)


en casi todo stack mencionan que es sobre los dinos y con esto queda

```
$ heroku ps:scale web=1
```

y nop



