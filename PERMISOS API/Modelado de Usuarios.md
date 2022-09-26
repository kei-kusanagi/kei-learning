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
          "view"
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
          "view"
        ]
      }
    },
    {
      "displayName": "PokeUsuario",
      "permissions": {
        "pokemon": [
          "view"
        ]
      }
    }
  ]
}
```