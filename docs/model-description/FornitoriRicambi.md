export const Color = ({children, color}) => (
  <span
    style={{
      color: color
    }}>
    {children}
  </span>
);

## Descrizione
Questa tabella è usata per collegare la relazione N - N tra ricambi e fornitori, ogni riga contiente la relativa associazione

## Composizione colonne

- replacement_id
- provider_id

## API disponibili

### Metodi <Color color = "green"> GET</Color>
- [/PR/allAssociations](#allAssociations), per cercare tra le associazioni

### Metodi <Color color = "darkorange"> POST </Color>
- [/PR/createAssociation](#createAssociation) per creare un'associazione
- [/PR/deleteAssociation](#deleteAssociation), per eliminare un'associazione

#### <Color color = "green"> GET </Color> All Associations {#allAssociations}
Questo metodo permette di visualizzare tutte le associazioni o di cercarne una o più se inseriti i parametri di ricerca


Parametri:

```shell
{
    "provider_id": 1,
    "replacement_id": 1
}
```

Risposta:

```shell
{
    "data": [
        {
            "replacement_id": 1,
            "provider_id": 1
        }
    ]
}
```

#### <Color color = "darkorange"> POST </Color> Create Association {#createAssociation}
Questo metodo permette di creare un'associazione, passando l'id del ricambio e del fornitore
:::caution AVVISO
Prima della creazione, viene verificata l'esistenza dell'associazione e l'esistenza dei ricambi e fornitori forniti, restituendo:
- **bad_request** se esiste già
- **not_found** se gli id forniti non sono corretti
:::

Parametri:
```shell
{
    "provider_id": 1,
    "replacement_id": 1
}
```
Risposta:
```shell
{
    "data": "Created"
}
```

#### <Color color = "darkorange"> POST </Color> Delete Association {#deleteAssociation}
Questo metodo elimina l'associazione richiesta in base agli id del fornitore e del ricambio forniti
:::info
Prima dell'eliminazione, viene verificata l'esistenza degli id forniti, restituendo **not_found** se non sono corretti
:::

Parametri:
```shell
{
    "provider_id": 1,
    "replacement_id": 1
}
```
Risposta:
```shell
{
    "data": "deleted"
}
```