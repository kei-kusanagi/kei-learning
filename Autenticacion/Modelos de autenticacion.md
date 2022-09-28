## ¿Qué es la autentificación y que es la autorización?


-   **autentificación (**_**authentication**_**):** La autentificación es el proceso o acción de verificar la identidad de un usuario o proceso.  

-   **autorización (**_**authorization**_**):** La autorización es una función que especifica los privilegios de acceso del usuario a los recursos de tu servicio.

Por lo que entendí la autentificación es como tu INE en un bar, es como quien dice la credencial con la que te identificas como quien dices ser, mayor de edad y te dejan pasar y la autorización es ya que pásate al bar la lana para poder comprar bebidas, si no tienes autorización (lana) no podrás acceder alas bebidas aunque te hayas autenticado.

(las API REST son ASINCRONAS, es un termino que no había entendido hasta que lei lo siguiente)

```
En una API REST, enviar las credenciales una vez para iniciar sesión no es suficiente, las API REST son asíncronas. Al ser asíncrona, la API REST no puede recordar las credenciales ya que no existe ninguna sesión activa HTTP. ¡Así que tienes que indicar quién eres cada vez que hagas una petición!
```

Ahora entiendo, por eso se manda en la petición cada ves el token, por que es cierto al no tener HTTP pues no hay manera de mantener logeada tu cuenta 

Los 4 métodos principales de autentificación API REST son:

### 1.  Autentificación básica
La confiable, el usuario y contraseña, es vulnerable porque aunque la contraseña y usuario estén encriptadas, si alguien intercepta la transmisión de datos puede decodificarlos fácilmente.

### 2.  Autentificación basada en token

la que ya había visto, con un token, con la primera petición le mandas tu INE (tu autenticación) y te regresa un token (autentificación) hecho a partir de tus credenciales (como ya lo vi, que dentro del token viene dividido el token, mensaje y asi) ya con este token (el cual guarda en la base de datos) ya no le pide al usuario vuelva a mandar sus credenciales, solo el token y alli viene lo que s eme dificulto que es ponerle caducidad y refresh y todo eso, pero esta es una vista general namas

### 3. Autentificación basada en clave API

Pues pareciera lo mismititito que la basada en token, le das un acceso a los recursos de la API y la API debe generar una clave y un secret, la cual debe ir en cada petición, según es mas seguro pweo wa mas difícil la escalabilidad de la API (no se a que se refiera)

### 4. OAuth 2.0 (Autorización abierta)
oooooo ok ok, el OAuth es como cuando te dicen, ok quieres registrarte Ó mejor inicia cesión con GitHub o Google o el extinto Passport de Hotmail, ya que le des acceso esta aplicacion de terceros (osea con google, git o pssport) podra acceder a la informacion de la API permitida mediante un token de acceso

el JWToken que manda OAuth luce asi

-   **Encabezado**: metadatos sobre el token como algoritmos criptográficos utilizados para generar el token.
-   **Payload**: la carga útil contiene el Asunto (generalmente identificador del usuario), claims (también conocidos como permisos o concesiones) y otra información como audiencia y tiempo de vencimiento, etc.
-   **Firma**: utilizada para validar el token es confiable y no ha sido alterado.


### 5.- Autenticación basada en cookies

la diferencia es que este si es stateful, osea que aqui si tenemos que tener una plataforma donde el cliente haga inicio de secion y esta mantenga el cookie en correspondencia con el identificador de sesion.

En el lado del cliente una cookie es creada para almacenar el identificador de sesión, mientras que los datos se almacenan en el servidor (y son llamados variables de sesión).

(esto lo copio tal cual)
El flujo que sigue este sistema de autenticación tradicional es el siguiente:

-   Un usuario ingresa sus credenciales (datos que le permiten iniciar sesión)
-   El servidor verifica que las credenciales sean correctas, y crea una sesión (esto puede corresponderse con la creación de un archivo, un registro nuevo en una base de datos, o alguna otra solución server-side)
-   Una cookie con el session ID es puesta en el navegador web del usuario
-   En las peticiones siguientes, el session ID es comparado con las sesiones creadas por el servidor
-   Una vez que el usuario se desconecta, la sesión es destruida en ambos lados (tanto en el cliente como en el servidor)



https://www.itdo.com/blog/cual-es-el-mejor-metodo-de-autentificacion-en-un-api-rest/

https://www.clubdetecnologia.net/blog/2020/buenas-practicas-de-seguridad-para-las-api-rest/


https://programacionymas.com/blog/jwt-vs-cookies-y-sesiones


videos

https://youtu.be/eerHZJuEwJk

https://www.youtube.com/watch?v=nNVlewjKQEQ&t=1523s

https://www.youtube.com/watch?v=9ySvaitF7Lo&t=353s

https://www.youtube.com/watch?v=ycD4_au91eI&t=307s

https://www.youtube.com/watch?v=pMLcAjE5Cso