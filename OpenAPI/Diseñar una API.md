# Antes de como generar un api, desglosar un Json para modelar algo (modelado de datos)


En el webcast mencionan estos 7 pasos "simples" para el modelado de la API
![image](/HEROKU%20e-commerce/IMG/Pasted%20image%2020220926183120.png)


### 1.- Lista de descripciones semánticas
olvidarnos de los objetos y crear una lista simple de los pasos que queramos en nuestra API, el usa un ejemplo de un laberinto donde dice ok, que tengo - un laberinto - un cuarto del laberinto - un interruptor - la posición de interruptor (abajo o arriba)... a eso se refiere, no estamos programando ni codeando solo hacer la lista de cosas que necesitamos

### 2.- Dibujar diagrama de estado
ahora que sabemos que cosas tiene, intentemos dibujar un diagrama de estado para saber que puedes hacer y como hacerlo, que objeto te lleva al otro y como interactúan, todo eso plasmarlo en el diagrama de estado, Ojo no se estan hablando de absolutos todavía, solo se estan configurando lo que es posible hacer al crear estos descriptores 

### 3.- Encontrar mejores nombres
ya que estemos cómodos con el diagrama y con las descripciones semánticas y ya que tengamos esa noción de lo que es la interacción del estado, necesitamos encontrar mejores nombres, este no creo a verle entendido al 100% pero por lo que dice se trata de que aunque nuestros nombres para las cosas esten padres para nosotros, seria mejor usar los que ya se tienen por convención, ósea los ya definidos, pero si no se puede usar un nombre ya definido ni tampoco uno personal, tenemos la obligación de crear uno unico (como un URI)

### 4.- Escoger un tipo de media
escoger si queremos que los datos los mandemos en Json o XML , aunque dice que hay muchísimos, el tratar de escoger uno de estos para que en futuros cambios se puedan corregir mas fácilmente y para que no se tenga que crear un nuevo cliente por si quieres usar tu propio tipo

### 5.- Diseñar un perfil
El diseñar un perfil consiste en seleccionar un perfil existente para poder aplicar mis descripciones semánticas las cosas que dibujamos en nuestro diagrama de estado a "este medio que elegimos y como lo hacemos" esos e hace con los perfiles, diseñar un perfil es seleccionar un perfil ya existente con un formato de mensaje en particular, En si el quería mostrar como se podía crear un formato legible por la maquina y esto es en realidad el conjunto de descripciones semánticas exactas que acabamos de describir (y le añade una liga a la documentacion de cada objeto)

### 6.- Implementación
Ya tenemos todo lo anterior ahora tenemos que construirlo, incluso pasarlo a personas que ni conoces pero con lo anterior tienen todo para poder construirlo con las descripciones, ya que intentamos crear un patrón de implementación

### 7.- Publicación
El ultimo paso es compartirlo, publicarlo

![image](/HEROKU%20e-commerce/IMG/Pasted%20image%2020220926183059.png)


[https://learning.oreilly.com/videos/api-design-methodology/9781491919224/9781491919224-video209493/](https://learning.oreilly.com/videos/api-design-methodology/9781491919224/9781491919224-video209493/ "https://learning.oreilly.com/videos/api-design-methodology/9781491919224/9781491919224-video209493/")
