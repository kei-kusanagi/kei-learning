modelar usarios con roles para la pokemon api

"roles": [
{
    "displayName": "PokeAdministrator",
    "permisos": "perfiles" [
        "crear",
        "editar",
        "borrar",
    ],
    "pokemones" [
        "crear",
        "editar",
        "borrar",
        "consultar",
    ]
},
{
    "displayName": "PokeModerador",
    "permisos": "perfiles" [
        "crear",
        "editar",
        "borrar",
     ],
    "pokemones" [
        "consultar",
    ]
}
{
    "displayName": "PokeUsuario",
    "permisos": "pokemones" [
        "consultar",
    ]
}
]
