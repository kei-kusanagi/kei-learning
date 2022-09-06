Bueno ahora lo subiremos gracias al docker file que creo Lecks

primero como lo hicimos antes hacemos el 
``heroku login``
nos logueamos como normalmente y luego le damos
``heroku container:login``
esto me generara algunas credenciales que heroku utilizara despues

el siguiente comando sera generar una app en heroku con el comando 
``heroku create``
esto solo si no tenemos una creada, en mi caso quise seguir el tutorial al 100%

copiamos de la urlk todo lo que esta antes de .herokuap en mi caso el link es https://pure-basin-43866.herokuapp.com 
y ponemos el comando
``heroku container:push web -a pure-basin-43866``

esperamos a que termine el proces (tarda alguiento para generar la imagen segun nuestro dockerfile

ahora ya teniendo nuestra imagen le damos rellease con el comando 

``heroku container:release web -a pure-basin-43866``

esto ejectuara nuestra imagen que se acava de generar dentrod e nuestro servidor, aqui en teoria ya deveria dejarme ver la pagina en heroku pero nop, me da el siguiente error

![[Pasted image 20220906154425.png]]

checando el log me da lo siguiente

```
2022-09-06T19:16:52.916191+00:00 app[web.1]: System check identified some issues:
2022-09-06T19:16:52.916192+00:00 app[web.1]:
2022-09-06T19:16:52.916193+00:00 app[web.1]: WARNINGS:
2022-09-06T19:16:52.916193+00:00 app[web.1]: ?: (staticfiles.W004) The directory '/home/app/webapp/frontend/build' in the STATICFILES_DIRS setting does not exist.
2022-09-06T19:16:52.916193+00:00 app[web.1]:
2022-09-06T19:16:52.916193+00:00 app[web.1]: System check identified 1 issue (0 silenced).
2022-09-06T19:16:52.969309+00:00 app[web.1]: September 06, 2022 - 19:16:52
2022-09-06T19:16:52.969355+00:00 app[web.1]: Django version 4.0.4, using settings 'ecommerce.settings'
2022-09-06T19:16:52.969355+00:00 app[web.1]: Starting development server at http://0.0.0.0:8080/
2022-09-06T19:16:52.969355+00:00 app[web.1]: Quit the server with CONTROL-C.
2022-09-06T19:16:52.971832+00:00 app[web.1]: /usr/local/lib/python3.8/site-packages/whitenoise/base.py:115: UserWarning: No directory at: /home/app/webapp/staticfiles/
2022-09-06T19:16:52.971835+00:00 app[web.1]: warnings.warn(f"No directory at: {root}")
2022-09-06T19:17:50.463931+00:00 heroku[web.1]: Error R10 (Boot timeout) -> Web process failed to bind to $PORT within 60 seconds of launch
2022-09-06T19:17:50.752345+00:00 heroku[web.1]: Stopping process with SIGKILL
2022-09-06T19:17:50.954184+00:00 heroku[web.1]: Process exited with status 137
2022-09-06T19:17:51.010708+00:00 heroku[web.1]: State changed from starting to crashed
```

pense que era tal ves por las variables de entorno que devia ir a heroku a declararlas nuevamente, principalmente la base de datos y nop sigue igual


cambie la estructura del Docker file ya que me aparecia un error relacionado con los ultimos comandos ``CMD`` segune sto solo corre el ultimo entonces pense que podria ser eso, segun stack overflow se deven poner todo en una misma linea como si duera una lista y quedo asi

``CMD [cd frontend, npm install, npm run build, cd .., python manage.py migrate, python manage.py runserver 0.0.0.0:8080]`` 

por lo que veo ne el error noe sta encontrando los archivos de statics, entonces el añadi la instruccion al Dockerfile de collectstatic aver si asi
``python manage.py collectstatic`` 


ok tratamos de no desesperar, subiremos esta imagen de contenedor alque ya teniamso de velvet-ecommerce

``heroku container:push web -a velvet-ecommerce``

cone sto creamos la imagen en velvet y ahora
``heroku container:release web -a velvet-ecommerce``

```
2022-09-06T21:18:59.003757+00:00 app[api]: Release v29 created by user kei_kusanagi@outlook.com
2022-09-06T21:18:59.003757+00:00 app[api]: Deployed web (142013fe2b5c) by user kei_kusanagi@outlook.com
2022-09-06T21:18:59.502993+00:00 heroku[web.1]: State changed from crashed to starting
2022-09-06T21:19:20.702669+00:00 heroku[web.1]: Starting process with command `/bin/sh -c \[cd\ frontend,\ npm\ install,\ npm\ run\ build,\ cd\ ..,\ python\ manage.py\ migrate,\ python\ manage.py\ collectstatic,\ python\ manage.py\ runserver\ 0.0.0.0:8080\]`
2022-09-06T21:19:21.567224+00:00 app[web.1]: /bin/sh: 1: [cd: not found
2022-09-06T21:19:21.677537+00:00 heroku[web.1]: Process exited with status 127
2022-09-06T21:19:21.795330+00:00 heroku[web.1]: State changed from starting to crashed
2022-09-06T21:19:21.801058+00:00 heroku[web.1]: State changed from crashed to starting
2022-09-06T21:19:43.813621+00:00 heroku[web.1]: Starting process with command `/bin/sh -c \[cd\ frontend,\ npm\ install,\ npm\ run\ build,\ cd\ ..,\ python\ manage.py\ migrate,\ python\ manage.py\ collectstatic,\ python\ manage.py\ runserver\ 0.0.0.0:8080\]`
2022-09-06T21:19:44.594538+00:00 app[web.1]: /bin/sh: 1: [cd: not found
2022-09-06T21:19:44.726464+00:00 heroku[web.1]: Process exited with status 127
2022-09-06T21:19:44.884636+00:00 heroku[web.1]: State changed from starting to crashed
2022-09-06T21:19:46.762033+00:00 heroku[router]: at=error code=H10 desc="App crashed" method=GET path="/" host=velvet-ecommerce.herokuapp.com request_id=e9bc44ac-c05f-4090-9122-933069eb192e fwd="189.233.156.13" dyno= connect= service= status=503 bytes= protocol=https
2022-09-06T21:19:46.909712+00:00 heroku[router]: at=error code=H10 desc="App crashed" method=GET path="/favicon.ico" host=velvet-ecommerce.herokuapp.com request_id=9a684c1f-60e9-437d-ad4e-df25ffe4f3ea fwd="189.233.156.13" dyno= connect= service= status=503 bytes= protocol=https
```

ok segune sto al aprecer lo de CMD asi esta mal, asi que segun stack se puede usar mejor el comando RUN asi que lo cambiaremos a run

```
# start server  

RUN cd frontend

RUN npm install

RUN npm run build

RUN cd ..

RUN python manage.py migrate

RUN python manage.py collectstatic

RUN python manage.py runserver 0.0.0.0:8080
```

error al crear al imagen

```
(env) PS C:\Users\admin\Desktop\Proyectos\Ecommerce> heroku container:push web -a velvet-ecommerce
 »   Warning: heroku update available from 7.53.0 to 7.63.0.
=== Building web (C:\Users\admin\Desktop\Proyectos\Ecommerce\Dockerfile)
[+] Building 31.9s (12/17)
 => [internal] load build definition from Dockerfile                                                                                                                                     0.0s 
 => => transferring dockerfile: 804B                                                                                                                                                     0.0s 
 => [internal] load .dockerignore                                                                                                                                                        0.0s 
 => => transferring context: 2B                                                                                                                                                          0.0s 
 => [internal] load metadata for docker.io/library/python:3.8                                                                                                                            1.0s 
 => [internal] load build context                                                                                                                                                        6.5s 
 => => transferring context: 3.62MB                                                                                                                                                      6.4s 
 => [ 1/13] FROM docker.io/library/python:3.8@sha256:7b72fe8ab313d9b48755f1350fa2a42c723a80e6bf7beb5e03b801e5405ecb15                                                                    0.0s 
 => CACHED [ 2/13] RUN mkdir -p /home/app/webapp                                                                                                                                         0.0s 
 => CACHED [ 3/13] WORKDIR /home/app/webapp                                                                                                                                              0.0s 
 => CACHED [ 4/13] RUN pip install --upgrade pip                                                                                                                                         0.0s 
 => [ 5/13] COPY . /home/app/webapp                                                                                                                                                      3.6s 
 => [ 6/13] RUN pip install -r requirements.txt                                                                                                                                         19.6s 
 => [ 7/13] RUN cd frontend                                                                                                                                                              0.5s 
 => ERROR [ 8/13] RUN npm install                                                                                                                                                        0.6s 
------
 > [ 8/13] RUN npm install:
#12 0.628 /bin/sh: 1: npm: not found
------
executor failed running [/bin/sh -c npm install]: exit code: 127
 !    Error: docker build exited with Error: 1
(env) PS C:\Users\admin\Desktop\Proyectos\Ecommerce> 
```
