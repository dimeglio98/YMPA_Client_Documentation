export const Color = ({children, color}) => (
<span
style={{
      color: color
    }}>
{children}
</span>
);

## Descrizione

Questa collection contiene le lavorazioni offerte dall'officina

## Composizione colonne

- tipo
- descrizione
- prezzo_base

## API disponibili

### Metodi <Color color = "green"> GET</Color>

- [/viewOneLavori](#viewOneLavoro), per cercare tra i lavori con un id
- [/allLavori](#allLavori), per mostrare tutti i lavori

### Metodi <Color color = "darkorange"> POST </Color>

- [/createLavoro](#createLavoro), per creare un lavoro alla volta
- [/updateLavoro](#updateLavoro), per modificare uno o più dati di un lavoro scelto
- [/deleteLavoro](#deleteLavoro), per eliminare un lavoro dal db
- [/deleteFieldLavoro](#delFieldLavoro) per eliminare un campo del lavoro scelto

#### <Color color = "green"> GET </Color> View One Lavoro {#viewOneLavoro}

Questo metodo permette di visualizzare un lavoro sulla base di un id fornito

Parametri:

```shell
{
    "id": "619b754cac74e60001ed87f9"
}
```

Risposta:

```shell
{
    "data": {
        "_id": {
            "$oid": "61790e22157f660001ba6b04"
        },
        "created_at": "2021-10-27T08:30:26.312Z",
        "descrizione": "florio",
        "prezzo_base": 15.0,
        "tipo": "Extra",
        "updated_at": "2021-11-22T09:41:15.712Z"
    }
}
```

#### <Color color = "green"> GET </Color> All Lavori {#allLavori}

Questo metodo permette di mostrare tutte le lavorazioni messe a disposizione dall'officina

Parametri: Nessuno

Risposta:

```shell
{
    "data": [
        {
            "_id": {
                "$oid": "61790e22157f660001ba6b04"
            },
            "created_at": "2021-10-27T08:30:26.312Z",
            "descrizione": "florio",
            "prezzo_base": 15.0,
            "tipo": "Extra",
            "updated_at": "2021-11-22T09:41:15.712Z"
        }
    ]
}
```

#### <Color color = "darkorange"> POST </Color> Create Lavoro {#createLavoro}
#### <Color color = "darkorange"> POST </Color> Update Lavoro {#updateLavoro}
#### <Color color = "darkorange"> POST </Color> Delete Lavoro {#deleteLavoro}
#### <Color color = "darkorange"> POST </Color> Delete Field Lavoro {#delfieldLavoro}

Questo metodo permette di eliminare un campo del lavoro scelto

Parametri:

```shell
{
    "id": "61790e22157f660001ba6b04",
    "deletefield": "descrizione"
}
```

Risposta:

```shell
{
    "data": {
        "_id": {
            "$oid": "61790e22157f660001ba6b04"
        },
        "created_at": "2021-10-27T08:30:26.312Z",
        "descrizione": null,
        "prezzo_base": 15.0,
        "tipo": "Extra",
        "updated_at": "2021-11-22T09:41:15.712Z"
    }
}
```