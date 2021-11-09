export const Color = ({children, color}) => (
  <span
    style={{
      color: color
    }}>
    {children}
  </span>
);

## Descrizione
I fornitori (provider) sono coloro che forniscono i ricambi

Ognuno di essi (ovviamente) fornisce più ricambi

## Composizione colonne
:::caution
I campi segnati in rosso sono univoci e la query restituirà un errore se il vincolo sarà violato
:::
- nome
- email
- address
- <Color color = "red"> piva </Color>
- phone
- ragione_sociale


## API disponibili

### Metodi <Color color = "green"> GET </Color>
- [/allProviders](#allProviders), per cercare uno o più fornitori

### Metodi <Color color = "darkorange"> POST </Color>
- [/createProvider](#createProvider), per creare un fornitore alla volta
- [/updateProviders](#updateProvider), per modificare uno o più dati di un fornitore scelto
- [/deleteProvider](#deleteProvider), per eliminare un fornitore dal db

#### <Color color = "green"> GET </Color> All Providers {#allProviders}
Questo metodo accetta in ingresso i campi del fornitore e stampa i fornitori richiesti, oppure anche nessuno e in questo caso risponde tutti i fornitori presenti nel db

Parametri:

```shell
{
    "id": 1,
    "nome": "Giorgio"
}
```

Risposta:

```shell
{
    "data": [
        {
            "id": 1,
            "created_at": "2021-11-08T19:01:09.986Z",
            "updated_at": "2021-11-08T19:01:09.986Z",
            "nome": "Giorgio",
            "email": "giorgio@ympa.com",
            "address": "1",
            "piva": "12345678900",
            "phone": "123456789",
            "ragione_sociale": "Azienda"
        }
    ]
}
```
#### <Color color = "darkorange"> POST </Color> Create Provider {#createProvider}
Questo metodo crea un fornitore, in input sono passati i parametri del fornitore

```shell
{
    "nome": "antonio"
    "email": "antonio@ympa.com"
    "address": "via ympa"
    "piva": "12345678900"
    "phone": "123456"
    "ragione_sociale": "Azienda"
}
```

Risposta:

```shell
{
    "data": {
        "id": 3,
        "created_at": "2021-11-09T15:39:33.184Z",
        "updated_at": "2021-11-09T15:39:33.184Z",
        "nome": "antonio",
        "email": "antonio@ympa.com",
        "address": "via ympa",
        "piva": "12345678902",
        "phone": "12345",
        "ragione_sociale": "azienda"
    }
}
```

#### <Color color = "darkorange"> POST </Color> Update Provider {#updateProvider}
Questo metodo aggiorna un fornitore, in input sono passati uno o più parametri del fornitore, oltre necessariamente all'id del fornitore da modificare

Parametri:

```shell
{
    "id": 3,
    "nome": Giorgio
}
```

Risposta: 
```shell
{
    "updated": {
        "id": 3,
        "ragione_sociale": "azienda",
        "created_at": "2021-11-09T15:39:33.184Z",
        "updated_at": "2021-11-09T15:39:33.184Z",
        "nome": "antonio",
        "email": "antonio@ympa.com",
        "address": "via ympa",
        "piva": "12345678902",
        "phone": "12345"
    }
}
```
#### <Color color = "darkorange"> POST </Color> Delete Provider {#deleteProvider}
Questo metodo elimina un fornitore sulla base di un id passato

Parametri:

```shell
{
    "id": 3
}
```

Risposta:

```shell
{
    "deleted": [
        {
            "id": 3,
            "created_at": "2021-11-09T15:39:33.184Z",
            "updated_at": "2021-11-09T15:39:33.184Z",
            "nome": "antonio",
            "email": "antonio@ympa.com",
            "address": "via ympa",
            "piva": "12345678902",
            "phone": "12345",
            "ragione_sociale": "azienda"
        }
    ]
}
```