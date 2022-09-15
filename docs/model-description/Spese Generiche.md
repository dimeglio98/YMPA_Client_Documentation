export const Color = ({children, color}) => (
<span
style={{
      color: color
    }}>
{children}
</span>
);

## Descrizione

Questa collection contiene le spese effettuate una volta, che non si ripetono nel tempo

## Composizione colonne

- nome
- costo
- datapagamento
- descrizione

## API disponibili

### Metodi <Color color = "green"> GET</Color>

- [/viewOneSpesaGenerica](#viewOneSpesaGenerica), per cercare tra le spese generiche con un id
- [/allSpeseGeneriche](#allSpeseGeneriche), per mostrare tutti le spese generiche

### Metodi <Color color = "darkorange"> POST </Color>

- [/createSpesaGenerica](#createSpesaGenerica), per creare una spesa generica alla volta

### Metodi <Color color = "blue"> PUT </Color>

- [/updateSpesaGenerica](#updateSpesaGenerica), per modificare uno o più dati di una spesa generica scelto

### Metodi <Color color = "red"> DELETE </Color>

- [/deleteSpesaGenerica](#deleteSpesaGenerica), per eliminare un spesa generica dal db

#### <Color color = "green"> GET </Color> View One SpesaGenerica {#viewOneSpesaGenerica}

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
        "nome": "ord. 654147",
        "costo": 15.0,
        "datapagamento": "2022-2-10",
        "descrizione": "nessuna",
        "updated_at": "2021-11-22T09:41:15.712Z"
    }
}
```

#### <Color color = "green"> GET </Color> All Spese Generiche {#allSpeseGeneriche}
#### <Color color = "darkorange"> POST </Color> Create Spesa Generica {#createSpesaGnerica}
#### <Color color = "blue"> PUT </Color> Update Spesa Generica {#createSpesaGnerica}
#### <Color color = "red"> DELETE </Color> Delete Spesa Generica {#createSpesaGnerica}
