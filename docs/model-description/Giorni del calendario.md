export const Color = ({children, color}) => (
  <span
    style={{
      color: color
    }}>
    {children}
  </span>
);

## Descrizione

Questa collection permette di tenere traccia dei giorni prenotati e i relativi slot liberi

## Composizione colonne

- day
- schedules_available

## API disponibili

### Metodi <Color color = "green"> GET </Color>
- [/readTimes](#readTimes), per visualizzare gli orari liberi
- [/readDays](#readDays), per visualizzare lo stato dei giorni seguenti

### Metodi <Color color = "darkorange"> POST </Color>

- [/createDay](#createDay), per inserire un giorno occupato

#### <Color color = "green"> GET </Color> Read Times {#readTimes}

Questo metodo mostra lo stato degli orari (slot liberi per ogni singolo orario) nel giorno scelto

Parametri:

```shell
{
    "day": "2021-11-22"
}
```

Risposta:

```shell
{
    "data": {
        "_id": {
            "$oid": "619b6376ac74e60001ed87f3"
        },
        "created_at": "2021-11-22T09:31:34.815Z",
        "day": "2021-11-22",
        "schedules_available": [
            {
                "posti": 2,
                "orario": 9
            },
            {
                "posti": 4,
                "orario": 10
            },
            {
                "posti": 4,
                "orario": 11
            },
            {
                "posti": 4,
                "orario": 12
            },
            {
                "posti": 4,
                "orario": 13
            },
            {
                "posti": 4,
                "orario": 14
            },
            {
                "posti": 4,
                "orario": 15
            },
            {
                "posti": 4,
                "orario": 16
            },
            {
                "posti": 4,
                "orario": 17
            }
        ],
        "updated_at": "2021-11-22T10:47:40.150Z"
    }
}
```

#### <Color color = "green"> GET </Color> Read Days {#readDays}

Questo metodo mostra i giorni (e lo stato dei relativi orari) successivi a una data impostata

Parametri

```shell
{
    "day": "2021-11-22"
}
```

Risposta:

```shell
{
    "data": [
        {
        "_id": {
            "$oid": "619b6376ac74e60001ed87f3"
        },
        "created_at": "2021-11-22T09:31:34.815Z",
        "day": "2021-11-22",
        "schedules_available": [
            {
                "posti": 2,
                "orario": 9
            },
            {
                "posti": 4,
                "orario": 10
            },
            {
                "posti": 4,
                "orario": 11
            },
            {
                "posti": 4,
                "orario": 12
            },
            {
                "posti": 4,
                "orario": 13
            },
            {
                "posti": 4,
                "orario": 14
            },
            {
                "posti": 4,
                "orario": 15
            },
            {
                "posti": 4,
                "orario": 16
            },
            {
                "posti": 4,
                "orario": 17
            }
        ],
        "updated_at": "2021-11-22T10:47:40.150Z"
        }
    ]
}
```

#### <Color color = "darkorange"> POST </Color> Create Day {#createDay}

Questo metodo permette di creare un giorno occupato se è totalmente libero o di modificarne lo stato di occupazione se è stato già occupato precedentemente

Parametri:
```shell
{
    "data": {
        "day": "2021-11-25",
        "schedules_available": [
            {
                "posti": 4,
                "orario": 9
            },
            {
                "posti": 3,
                "orario": 10
            },
            {
                "posti": 4,
                "orario": 11
            },
            {
                "posti": 4,
                "orario": 12
            },
            {
                "posti": 4,
                "orario": 13
            },
            {
                "posti": 4,
                "orario": 14
            },
            {
                "posti": 4,
                "orario": 15
            },
            {
                "posti": 4,
                "orario": 16
            },
            {
                "posti": 4,
                "orario": 17
            }
        ]
    }
}
```

Risposta:

```shell
Se è stato aggiornato:
{
    "data": true
}
```
```shell

Se è stato creato:
{
    "data": {
        "_id": {
            "$oid": "619b8759ac74e60001ed87fc"
        },
        "created_at": "2021-11-22T12:04:41.299Z",
        "day": "2021-11-30",
        "schedules_available": [
            {
                "posti": 4,
                "orario": 9
            },
            {
                "posti": 3,
                "orario": 10
            },
            {
                "posti": 4,
                "orario": 11
            },
            {
                "posti": 4,
                "orario": 12
            },
            {
                "posti": 4,
                "orario": 13
            },
            {
                "posti": 4,
                "orario": 14
            },
            {
                "posti": 4,
                "orario": 15
            },
            {
                "posti": 4,
                "orario": 16
            },
            {
                "posti": 4,
                "orario": 17
            }
        ],
        "updated_at": "2021-11-22T12:04:41.299Z"
    }
}
```