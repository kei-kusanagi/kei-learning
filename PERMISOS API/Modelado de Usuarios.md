modelar usarios con roles para la pokemon api
```
{
  "role": [
    {
      "displayName": "PokeAdministrator",
      "permissions": {
        "profiles": [
          "create",
          "edit",
          "delete"
        ],
        "pokemon": [
          "create",
          "edit",
          "delete",
          "consult"
        ]
      }
    },
    {
      "displayName": "PokeModerador",
      "permissions": {
        "profiles": [
          "create",
          "edit",
          "delete"
        ],
        "pokemon": [
          "consult"
        ]
      }
    },
    {
      "displayName": "PokeUsuario",
      "permissions": {
        "pokemon": [
          "consult"
        ]
      }
    }
  ]
}
```