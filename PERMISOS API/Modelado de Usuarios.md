modelar usarios con roles para la pokemon api
```
{
  "roles": [
    {
      "nombre": "PokeAdministrator",
      "permisos": {
        "perfiles": [
          "crear",
          "editar",
          "borrar"
        ],
        "pokemones": [
          "crear",
          "editar",
          "borrar",
          "consultar"
        ]
      }
    },
    {
      "nombre": "PokeModerador",
      "permisos": {
        "perfiles": [
          "crear",
          "editar",
          "borrar"
        ],
        "pokemones": [
          "consultar"
        ]
      }
    },
    {
      "nombre": "PokeUsuario",
      "permisos": {
        "pokemones": [
          "consultar"
        ]
      }
    }
  ]
}
```