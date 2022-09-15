export const Color = ({children, color}) => (
  <span
    style={{
      color: color
    }}>
    {children}
  </span>
);

## Descrizione
Questa collection contiente tutte le prenotazioni per l'accettazione effettuate dagli utenti

Ogni prenotazione è associata ad un tipo di lavorazione

(in futuro sarà associata anche all'utente e al veicolo dell'utente)
## Composizione colonne
:::info
I campi di colore diverso vengono aggiunti in momenti successivi alla creazione
:::

- accettato
- Codice
- Data
- diagnosta
- lavori_id
- Nome
- Cognome
- Confermato
- NoteCliente
- Ora
- ricambiScelti
- Veicolo (esso può essere una stringa o un oggetto composto da due stringhe Modello e Marca)
- UserID
- <Color color = "blue"> NoteAccettazioneDiagnosta </Color> (quando viene accettata la prenotazione)
- <Color color = "blue"> quotation_id </Color> (quando viene confermato il preventivo)

## API disponibili

### Metodi <Color color = "green"> GET</Color>
- [/viewOneBooking](#viewOneBooking), per cercare tra le prenotazioni con un id

### Metodi <Color color = "darkorange"> POST </Color>
- [/bookingByParameters](#bookingByParameters) per cercare tra le prenotazioni
- [/createBooking](#createBooking), per creare una prenotazione alla volta

### Metodi <Color color = "blue"> PUT </Color>

- [/updateBookings](#updateBooking), per modificare uno o più dati di una prenotazione scelta
- [/updateElementArrayBooking](#updElemArrayBook) per modificare la quantità del ricambio scelto
### Metodi <Color color = "red"> DELETE </Color>

- [/deleteBookings](#deleteBooking), per eliminare una prenotazione dal db
- [/deleteElementArrayBooking](#delElemArrayBook) per eliminare un ricambio scelto

:::note NOTA
Ogni API restituisce anche le relative associazioni per avere una visione totale e di facile accesso a tutto il contenuto associato
:::
#### <Color color = "green"> GET </Color> View One Booking {#viewOneBooking}
Questo metodo permette di visualizzare una prenotazione sulla base di un id fornito

Parametri:

```shell
{
    "id": "61850ad6bf161e0001ffe3b1"
}
```

Risposta:

```shell
{
    "data": {
        "_id": {
            "$oid": "618990391e6eb700016bc5a8"
        },
        "Ora": "9",
        "lavori_id": {
            "$oid": "61790e22157f660001ba6b04"
        },
        "Veicolo": "McLaren - MP4-12C",
        "NoteCliente": "",
        "Data": "2021-11-8",
        "UserID": 48,
        "diagnosta": false,
        "Nome": Giorgio,
        "Cognome": Ympa,
        "Confermato": true,
        "ricambiScelti": [],
        "updated_at": "2021-11-08T21:02:24.885Z",
        "created_at": "2021-11-08T21:01:46.015Z",
        "Codice": "b4d6306d",
        "Lavoro": {
            "_id": {
                "$oid": "61790e22157f660001ba6b04"
            },
            "tipo": "Extra",
            "descrizione": "llorenzo",
            "prezzo_base": 15.0,
            "updated_at": "2021-10-27T08:30:26.312Z",
            "created_at": "2021-10-27T08:30:26.312Z"
        }
    }
}
```

#### <Color color = "darkorange"> POST </Color> Booking By Parameters {#bookingByParameters}

Questo metodo permette di cercare tra tutte le prenotazioni, se non si fornisce nessun parametro restituisce tutte le prenotazioni presenti nel db

:::caution AVVISO
Per cercare tramite id, utilizza [View One Booking](#viewOneBooking)
:::

Parametri:
```shell
{
    "data": {
        "UserID": 46
    }
}
```

OPPURE (per visualizzare tutti gli elementi)

```shell

{
    "data": { }
}
```

Risposta:
```shell

{
    "data": [
        {
            "_id": {
                "$oid": "618977791e6eb700018306d0"
            },
            "Ora": "9",
            "lavori_id": {
                "$oid": "61790e22157f660001ba6b04"
            },
            "Veicolo": "McLaren - MP4-12C",
            "NoteCliente": "",
            "Data": "2021-11-8",
            "UserID": 48,
            "diagnosta": false,
            "Nome": null,
            "Cognome": null,
            "Confermato": true,
            "ricambiScelti": [
                {
                    "id": 1,
                    "label": "123 - Brembo - Freno - nessuna",
                    "quantita": 1,
                    "prezzo": 1
                }
            ],
            "updated_at": "2021-11-08T19:16:45.687Z",
            "created_at": "2021-11-08T19:16:09.230Z",
            "Codice": "f2dfb08c",
            "accettato": true,
            "quotation_id": "618977791e6eb700018306d0",
            "Lavoro": {
                "_id": {
                    "$oid": "61790e22157f660001ba6b04"
                },
                "tipo": "Extra",
                "descrizione": "llorenzo",
                "prezzo_base": 15.0,
                "updated_at": "2021-10-27T08:30:26.312Z",
                "created_at": "2021-10-27T08:30:26.312Z"
            }
        }
    ]
}
```

#### <Color color = "darkorange"> POST </Color> Create Booking {#createBooking}
Questo metodo permette di creare una prenotazione

:::caution AVVISO
Prima della creazione, viene verificato se la data e l'ora scelti sono ancora disponibili e se i dati inseriti sono corretti, restituendo:
- **bad_request** se la data e l'ora scelti non sono più disponibili
- **not_acceptable** se i dati inseriti non sono corretti (es. relazioni con id sbagliati)
:::

Parametri:
```shell
{
        "Confermato": false,
        "Data": "2021-10-25",
        "lavori_id": "618965e71e6eb70001a25008",
        "NoteCliente": "",
        "Ora": "10",
        "UserID": 47,
        "Veicolo": "McLaren MPC",
        "diagnosta": false,
        "ricambiScelti": []
}
```
Risposta:
```shell
{
    "data": {
        "Codice": "145720a6",
        "Confermato": false,
        "Data": "2021-10-25",
        "NoteCliente": "",
        "Ora": "10",
        "UserID": 48,
        "Veicolo": "McLaren MPC",
        "_id": {
            "$oid": "618ba1c41e6eb70001ddfa54"
        },
        "created_at": "2021-11-10T10:41:08.342Z",
        "diagnosta": false,
        "lavori_id": {
            "$oid": "618965e71e6eb70001a25008"
        },
        "ricambiScelti": [],
        "updated_at": "2021-11-10T10:41:08.370Z"
    }
}
```

#### <Color color = "darkorange"> POST </Color> Update Booking {#updateBooking}
Questo metodo aggiorna una prenotazione, in input sono passati uno o più parametri della prenotazione, oltre necessariamente all'id della prenotazione da modificare

:::info
Prima della modifica, viene verificata l'esistenza dell' id fornito, restituendo **not_found** se non è corretto
:::

Parametri:
```shell
{
    "id": "61850ad6bf161e0001ffe3b1",
    "ricambiScelti": []
}
```
Risposta:
```shell
{
    "updated": true
}
```

#### <Color color = "darkorange"> POST </Color> Delete Booking {#deleteBooking}
Questo metodo elimina una prenotazione sulla base dell'id fornito

:::info
Prima dell'eliminazione, viene verificata l'esistenza dell' id fornito, restituendo **not_found** se non è corretto
:::

Parametri:
```shell
{
    "id": "61850ad6bf161e0001ffe3b1",
}
```
Risposta:
```shell
{
    "deleted": true
}
```

#### <Color color = "darkorange"> POST </Color> Update Element Array Booking {#updElemArrayBook}
Questo metodo modifica la quantità del ricambio scelto, nella prenotazione selezionata tramite id

:::info
In caso di errore durante la modifica, viene restituito "updated": false
:::

Parametri:
```shell
{
    "id": "61850ad6bf161e0001ffe3b1",
    "ricambio_id": 1
    "quantita": 2
}
```
Risposta:
```shell
{
    "updated": {
        "_id": {
            "$oid": "618a98281e6eb70001d726ff"
        },
        "Ora": "9",
        "lavori_id": {
            "$oid": "61790e22157f660001ba6b04"
        },
        "Veicolo": "McLaren - MP4-12C",
        "NoteCliente": "",
        "Data": "2021-11-9",
        "UserID": 48,
        "diagnosta": false,
        "Nome": Giorgio,
        "Cognome": Ympa,
        "Confermato": true,
        "ricambiScelti": [
            {
                "id": 3,
                "quantita": 1
            }
        ],
        "updated_at": "2021-11-10T10:57:33.836Z",
        "created_at": "2021-11-09T15:47:52.680Z",
        "Codice": "2e0ad92d",
        "accettato": true,
        "quotation_id": "618a98281e6eb70001d726ff",
    }
}
```

#### <Color color = "darkorange"> POST </Color> Delete Element Array Booking {#delElemArrayBook}
Questo metodo elimina un ricambio (basato sull'id) dalla prenotazione selezionata tramite id

:::caution AVVISO
In caso di errore durante l'eliminazione, viene restituito  **Not found**
:::

Parametri:
```shell
{
    "id": "61850ad6bf161e0001ffe3b1",
    "replacement": 1
}
```
Risposta:
```shell
{
    "data": {
        "_id": {
            "$oid": "618a98281e6eb70001d726ff"
        },
        "Ora": "9",
        "lavori_id": {
            "$oid": "61790e22157f660001ba6b04"
        },
        "Veicolo": "McLaren - MP4-12C",
        "NoteCliente": "",
        "Data": "2021-11-9",
        "UserID": 48,
        "diagnosta": false,
        "Nome": Giorgio,
        "Cognome": Ympa,
        "Confermato": true,
        "ricambiScelti": [],
        "updated_at": "2021-11-10T10:57:33.836Z",
        "created_at": "2021-11-09T15:47:52.680Z",
        "Codice": "2e0ad92d",
        "accettato": true,
        "quotation_id": "618a98281e6eb70001d726ff",
    }
}
```