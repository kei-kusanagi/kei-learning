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

### 3.  Autentificación basada en clave API

### 4.  OAuth 2.0 (Autorización abierta)
