## Endpoints Utilizados por externos de Garces

### `GET /v1/libraryExternal/filter`

Este endpoint devuelve una lista los grupos de manera unica.

**Ejemplo de solicitud:**

**Parámetros:**

- `clientValue` (opcional): Permite filtrar el cliente por algún criterio específico.

**Ejemplo de repuesta exitosa:**
```json
{
  "groups": [
    {
      "label": "Agricola Membrillar Limitada",
      "value": "Agricola_Membrillar_Limitada"
    },
    {
      "label": "Agroveen Agricultural Spa",
      "value": "Agroveen_Agricultural_Spa"
    }
  ]
}
```

### `GET /v1​/libraryExternal`

Este endpoint devuelve una lista de los group externos de gaces junto al detalle de cada uno.

**Ejemplo de solicitud:**

**Parámetros:**

- `clientValue`: Permite filtrar el cliente por algún criterio específico.

**Ejemplo de repuesta exitosa:**
```json
{
  "groups": [
    {
      "label": "Macaya Y Waak Ltda",
      "value": "Macaya_Y_Waak_Ltda",
      "agroBusiness": [
        {
          "label": "Macaya Y Waak Ltda",
          "value": "Macaya_Y_Waak_Ltda",
          "orchard": [
            {
              "label": "El Huique",
              "value": "El_Huique",
              "variety": [
                {
                  "label": "Santina",
                  "value": "Santina"
                },
                {
                  "label": "Lapins",
                  "value": "Lapins"
                },
                {
                  "label": "Nimba",
                  "value": "Nimba"
                },
                {
                  "label": "Sweet Aryana",
                  "value": "Sweet_Aryana"
                }
              ]
            }
          ]
        }
      ]
    },
  ]
}
```

### `POST /v1/libraryExternal/dahsboard`

Este endpoint devuelve valores del dahsboard según formato requerido.

**Ejemplo de solicitud:**

**Body:**

- `groupValue` (opcional): Permite filtrar Grupo.
- `technicBossValue` (opcional): Permite filtrar por jefe técnico.

**Ejemplo Respuesta exitosa:**
```json
{
  "pieKilos": [
    {
      "y": 34584192,
      "name": "Total"
    },
    {
      "y": 0,
      "name": "Filtrado"
    }
  ],
  "dataVarieties": {
    "data": [
      {
        "kilos": 586000,
        "variety": "Rainier"
      },
      {
        "kilos": 80000,
        "variety": "Cristalina"
      }
    ],
    "total": 34584192
  },
  "dataAgroBusinesss": {
    "data": [
      {
        "date": "2023-11-16",
        "kilos": 75000,
        "agrobusiness": "Maria Ignacia Ramirez Navarro"
      },
      {
        "date": "2023-11-16",
        "kilos": 70000,
        "agrobusiness": "Agricola San Isidro Spa"
      }
    ],
    "total": 34584192
  }
}
```

### `POST /v1/planningHarvest/dashboard`

Este endpoint devuelve valores del dahsboard según formato requerido.

**Ejemplo de solicitud:**

**Body:**

- `orchardValue` (requerido):[] - Permite filtrar los huertos.
- `dateSince` (requerido): Permite filtrar desde una fecha.
- `dateUntil` (requerido): Permite filtrar hasta una fecha.
- `varietyValue` (opcional): Permite filtrar por variedad.

**Ejemplo Body:**

```json
{
    "orchardValue": [
        "Santa_Isabel"
    ],
    "varietyValue": "",
    "dateSince": "2023-12-17",
    "dateUntil": "2024-01-07"
}
```


**Ejemplo Respuesta exitosa:**
```json
{
    "harvestVarieties": {
        "totalHarvest": 67700,
        "varieties": [
            "Kordia",
            "Lapins",
            "Regina",
            "Skeena"
        ],
        "data": [
            800,
            50000,
            16000,
            900
        ]
    },
    "totalKilos": [
        {
            "variety": "Kordia",
            "varietyValue": "Kordia",
            "dailyKilos": [
                {
                    "x": "2023-12-22",
                    "y": 0
                },
                {
                    "x": "2023-12-27",
                    "y": 800
                }
            ]
        },
        {
            "variety": "Lapins",
            "varietyValue": "Lapins",
            "dailyKilos": [
                {
                    "x": "2023-12-18",
                    "y": 0
                },
                {
                    "x": "2023-12-19",
                    "y": 20000
                },
                {
                    "x": "2023-12-20",
                    "y": 20000
                },
                {
                    "x": "2023-12-21",
                    "y": 10000
                }
            ]
        },
        {
            "variety": "Regina",
            "varietyValue": "Regina",
            "dailyKilos": [
                {
                    "x": "2023-12-27",
                    "y": 6000
                },
                {
                    "x": "2023-12-28",
                    "y": 10000
                }
            ]
        },
        {
            "variety": "Skeena",
            "varietyValue": "Skeena",
            "dailyKilos": [
                {
                    "x": "2023-12-22",
                    "y": 0
                },
                {
                    "x": "2023-12-27",
                    "y": 900
                }
            ]
        }
    ]
}
```

### `POST /v1/planningHarvest/list`

Este endpoint devuelve una lista de planificacion de cosecha.

**Ejemplo de solicitud:**

**Body:**

- `orchardValue` (requerido): Permite filtrar los huertos.
- `dateSince` (requerido): Permite filtrar desde una fecha.
- `dateUntil` (requerido): Permite filtrar hasta una fecha.
- `varietyValue` (opcional): Permite filtrar por variedad.
- `limit` (opcional): Permite definir la cantidad de registros.
- `page` (opcional): Permite definir desde que registro traer empezar la lista.
- `sortColumn` (opcional): Permite definir el por que columna se ordenara la información.
- `sortOrder` (opcional): Permite definir el tipo de orden acendente o desendente.

**Ejemplo Body:**

```json
{
    "orchardValue": "Agr._B_Y_P_Ltda._Coltauco",
    "varietyValue": "",
    "dateSince": "2023-12-17",
    "dateUntil": "2024-01-07",
    "page": 1,
    "limit": 10,
    "sortColumn": "varietyValue",
    "sortOrder": "asc"
}
```


**Ejemplo Respuesta exitosa:**
```json
{
    "count": 1,
    "data": [
        {
            "id": "65788b7946486671c8683f23",
            "date": "2023-12-18",
            "kilos": 15000,
            "client": "Garces Fruit 2",
            "orchard": "Agr. B Y P Ltda. Coltauco",
            "variety": "Lapins",
            "version": 1,
            "clientValue": "Garces_Fruit_2",
            "orchardValue": "Agr._B_Y_P_Ltda._Coltauco",
            "varietyValue": "Lapins"
        }
    ]
}
```

### `GET /v1/planningHarvest/calendarization`

Este endpoint devuelve el calendario para planificacion de cosecha.

**Ejemplo de solicitud:**

**Parámetros:**

- `clientValue` (requerido): Permite filtrar por cliente.
- `orchardValue` (requerido): Permite filtrar los huertos.
- `dateSince` (requerido): Permite definir decha de inicio.
- `dateUntil` (requerido): Permite definir decha de termino.
- `varietyValue` (opcional): Permite filtrar por variedad.
- `variety` (opcional): Permite filtrar por variedad.

**Ejemplo Respuesta exitosa:**
```json
{
    "days": [
        {
            "week": "1",
            "days": [
                "2023-12-18",
                "2023-12-19",
                "2023-12-20",
                "2023-12-21",
                "2023-12-22"
            ],
            "weekYear": "51",
            "daysNames": [
                "lunes",
                "martes",
                "miércoles",
                "jueves",
                "viernes"
            ],
            "values": [
                {
                    "day": "2023-12-18",
                    "values": [
                        {
                            "varietyValue": "Lapins",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Regina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Santina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Skeena",
                            "kilos": null
                        }
                    ]
                },
                {
                    "day": "2023-12-19",
                    "values": [
                        {
                            "varietyValue": "Lapins",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Regina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Santina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Skeena",
                            "kilos": null
                        }
                    ]
                },
                {
                    "day": "2023-12-20",
                    "values": [
                        {
                            "varietyValue": "Lapins",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Regina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Santina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Skeena",
                            "kilos": null
                        }
                    ]
                },
                {
                    "day": "2023-12-21",
                    "values": [
                        {
                            "varietyValue": "Lapins",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Regina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Santina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Skeena",
                            "kilos": null
                        }
                    ]
                },
                {
                    "day": "2023-12-22",
                    "values": [
                        {
                            "varietyValue": "Lapins",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Regina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Santina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Skeena",
                            "kilos": null
                        }
                    ]
                }
            ]
        },
        {
            "week": "2",
            "days": [
                "2023-12-25",
                "2023-12-26",
                "2023-12-27",
                "2023-12-28",
                "2023-12-29"
            ],
            "weekYear": "52",
            "daysNames": [
                "lunes",
                "martes",
                "miércoles",
                "jueves",
                "viernes"
            ],
            "values": [
                {
                    "day": "2023-12-25",
                    "values": [
                        {
                            "varietyValue": "Lapins",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Regina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Santina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Skeena",
                            "kilos": null
                        }
                    ]
                },
                {
                    "day": "2023-12-26",
                    "values": [
                        {
                            "varietyValue": "Lapins",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Regina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Santina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Skeena",
                            "kilos": null
                        }
                    ]
                },
                {
                    "day": "2023-12-27",
                    "values": [
                        {
                            "varietyValue": "Lapins",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Regina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Santina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Skeena",
                            "kilos": null
                        }
                    ]
                },
                {
                    "day": "2023-12-28",
                    "values": [
                        {
                            "varietyValue": "Lapins",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Regina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Santina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Skeena",
                            "kilos": null
                        }
                    ]
                },
                {
                    "day": "2023-12-29",
                    "values": [
                        {
                            "varietyValue": "Lapins",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Regina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Santina",
                            "kilos": null
                        },
                        {
                            "varietyValue": "Skeena",
                            "kilos": null
                        }
                    ]
                }
            ]
        }
    ],
    "daysActive": {
        "lunes": true,
        "martes": true,
        "miercoles": true,
        "jueves": true,
        "viernes": true,
        "sabado": false,
        "domingo": false
    },
    "varieties": [
        {
            "variety": "Lapins",
            "varietyValue": "Lapins",
            "yieldTotal": 30000,
            "deliveredYield": 0,
            "availableYield": 30000
        },
        {
            "variety": "Regina",
            "varietyValue": "Regina",
            "yieldTotal": 120000,
            "deliveredYield": 0,
            "availableYield": 120000
        },
        {
            "variety": "Santina",
            "varietyValue": "Santina",
            "yieldTotal": 23000,
            "deliveredYield": 0,
            "availableYield": 23000
        },
        {
            "variety": "Skeena",
            "varietyValue": "Skeena",
            "yieldTotal": 39000,
            "deliveredYield": 0,
            "availableYield": 39000
        }
    ]
}
```
