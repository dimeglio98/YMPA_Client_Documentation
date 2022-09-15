export const Color = ({children, color}) => (
<span
style={{
      color: color
    }}>
{children}
</span>
);

## Descrizione

Questa collection contiente i preventivi effettuati, inclusi quelli creati dal diagnosta direttamente

Ogni preventivo è associato ad una sola prenotazione e alle relative associazioni di quest'ultima

## Composizione colonne

:::info
I campi di colore diverso vengono aggiunti in momenti successivi alla creazione
:::

- booking_id
- sconti_id
- lavori_id
- Consegnato
- accettato
- Completato
- _id (viene passato per allinearsi alla prenotazione corrispondente)
- CostoPreventivoNoIva
- ricambiScelti (se sono selezionati in fase di preventivo)

Quando la scheda lavoro viene terminata:

- <Color color = "blue"> OreLavoro </Color>
- <Color color = "blue"> NoteOperatore </Color>

Quando il veicolo viene consegnato:

- <Color color = "blue"> Pagato </Color>
- <Color color = "blue"> PrezzoFinale </Color>

## API disponibili

### Metodi <Color color = "green"> GET</Color>

- [/viewOneQuotation](#viewOneQuotation), per cercare tra i preventivi con un id

### Metodi <Color color = "darkorange"> POST </Color>

- [/quotationByParameters](#quotationByParameters) per cercare tra le prenotazioni
- [/createQuotation](#createQuotation), per creare un preventivo alla volta

### Metodi <Color color = "blue"> PUT </Color>

- [/updateQuotations](#updateQuotation), per modificare uno o più dati di un preventivo scelto
- [/updateElementArrayQuotation](#updElemArrayQuot) per modificare la quantità del ricambio scelto

### Metodi <Color color = "red"> DELETE </Color>

- [/deleteQuotations](#deleteQuotation), per eliminare un preventivo dal db
- [/deleteElementArrayQuotation](#delElemArrayQuot) per eliminare un ricambio scelto

<!-- - [/viewOneQuotationSelect](#quotationSelect) per il modulo react-select (al momento non usato) -->

:::note NOTA
Ogni API restituisce anche le relative associazioni per avere una visione totale e di facile accesso a tutto il contenuto associato
:::

#### <Color color = "green"> GET </Color> View One Quotation {#viewOneQuotation}

Questo metodo permette di visualizzare una prenotazione sulla base di un id fornito

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
      {
            "_id": {
                "$oid": "619b754cac74e60001ed87f9"
            },
            "booking_id": {
                "$oid": "619b754cac74e60001ed87f9"
            },
            "accettato": true,
            "Consegnato": false,
            "sconti_id": {
                "$oid": "617a7d24157f660001c3cdda"
            },
            "Completato": false,
            "CostoPreventivoNoIva": "16.00",
            "lavori_id": {
                "$oid": "61790e22157f660001ba6b04"
            },
            "updated_at": "2021-11-22T10:48:23.965Z",
            "created_at": "2021-11-22T10:48:23.953Z",
            "ricambiScelti": [
                {
                    "id": 1,
                    "label": "123 - Brembo - Freno - nessuna",
                    "quantita": 1,
                    "prezzo": 1
                }
            ],
            "Datiprenotazione": {
                "_id": {
                    "$oid": "619b754cac74e60001ed87f9"
                },
                "Ora": "9",
                "lavori_id": {
                    "$oid": "61790e22157f660001ba6b04"
                },
                "Veicolo": "McLaren - MP4-12C",
                "NoteCliente": "",
                "Data": "2021-11-22",
                "UserID": 48,
                "diagnosta": false,
                "Nome": G,
                "Cognome": DM,
                "Confermato": true,
                "ricambiScelti": [
                    {
                        "id": 1,
                        "label": "123 - Brembo - Freno - nessuna",
                        "quantita": 1,
                        "prezzo": 1
                    }
                ],
                "updated_at": "2021-11-22T10:48:23.851Z",
                "created_at": "2021-11-22T10:47:40.017Z",
                "Codice": "045d87ba",
                "NoteAccettazioneDiagnosta": "",
                "accettato": true,
                "quotation_id": "619b754cac74e60001ed87f9"
            },
            "Lavoro": {
                "_id": {
                    "$oid": "61790e22157f660001ba6b04"
                },
                "tipo": "Extra",
                "prezzo_base": 15.0,
                "updated_at": "2021-11-22T09:41:15.712Z",
                "created_at": "2021-10-27T08:30:26.312Z",
                "descrizione": "florio"
            },
            "Sconto": {
                "_id": {
                    "$oid": "617a7d24157f660001c3cdda"
                },
                "percentuale": 0,
                "termini": "nessuno",
                "updated_at": "2021-10-28T10:36:20.569Z",
                "created_at": "2021-10-28T10:36:20.569Z"
            }
        }
    }
}
```

<!-- #### <Color color = "darkorange"> GET </Color> View One Quotation Select  {#quotationSelect}
Questo metodo cerca uno specifico preventivo sulla base di un id fornito e ne formatta l'output nel modo richiesto dal plugin react-select

Parametri: -->





#### <Color color = "darkorange"> POST </Color> Quotation By Parameters {#quotationByParameters}

Questo metodo permette di cercare tra tutte i preventivi, se non si fornisce nessun parametro restituisce tutti quelli presenti nel db

:::caution AVVISO
Per cercare tramite id, utilizza [View One Quotation](#viewOneQuotation)
:::

Parametri:

```shell
{
    "data": {
        "Consegnato": false
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
                "$oid": "619b754cac74e60001ed87f9"
            },
            "booking_id": {
                "$oid": "619b754cac74e60001ed87f9"
            },
            "accettato": true,
            "Consegnato": false,
            "sconti_id": {
                "$oid": "617a7d24157f660001c3cdda"
            },
            "Completato": false,
            "CostoPreventivoNoIva": "16.00",
            "lavori_id": {
                "$oid": "61790e22157f660001ba6b04"
            },
            "updated_at": "2021-11-22T10:48:23.965Z",
            "created_at": "2021-11-22T10:48:23.953Z",
            "ricambiScelti": [
                {
                    "id": 1,
                    "label": "123 - Brembo - Freno - nessuna",
                    "quantita": 1,
                    "prezzo": 1
                }
            ],
            "Datiprenotazione": {
                "_id": {
                    "$oid": "619b754cac74e60001ed87f9"
                },
                "Ora": "9",
                "lavori_id": {
                    "$oid": "61790e22157f660001ba6b04"
                },
                "Veicolo": "McLaren - MP4-12C",
                "NoteCliente": "",
                "Data": "2021-11-22",
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
                "updated_at": "2021-11-22T10:48:23.851Z",
                "created_at": "2021-11-22T10:47:40.017Z",
                "Codice": "045d87ba",
                "NoteAccettazioneDiagnosta": "",
                "accettato": true,
                "quotation_id": "619b754cac74e60001ed87f9"
            },
            "Lavoro": {
                "_id": {
                    "$oid": "61790e22157f660001ba6b04"
                },
                "tipo": "Extra",
                "prezzo_base": 15.0,
                "updated_at": "2021-11-22T09:41:15.712Z",
                "created_at": "2021-10-27T08:30:26.312Z",
                "descrizione": "florio"
            },
            "Sconto": {
                "_id": {
                    "$oid": "617a7d24157f660001c3cdda"
                },
                "percentuale": 0,
                "termini": "nessuno",
                "updated_at": "2021-10-28T10:36:20.569Z",
                "created_at": "2021-10-28T10:36:20.569Z"
            }
        }
    ]
}
```

#### <Color color = "darkorange"> POST </Color> Create Quotation {#createQuotation}
Questo metodo crea un preventivo

:::caution AVVISO
Se i dati inseriti non dovessero essere corretti, restituisce come status **not_acceptable** e come testo *invalid data*
:::

Parametri:

```shell
{
        "_id": "61995f39ac74e60001505709",
        "sconti_id": "617a7d24157f660001c3cdda",
        "booking_id": "61995f39ac74e60001505709",
        "lavori_id": "6185040ff00bf80001751264",
        "CostoPreventivoNoIva": 17.0,
        "Completato": false,
        "Consegnato": false,
        "accettato": true,
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

#### <Color color = "darkorange"> POST </Color> Update Quotation {#updateQuotation}

Questo metodo aggiorna un preventivo, in input sono passati uno o più parametri del preventivo, oltre necessariamente all'id

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

#### <Color color = "darkorange"> POST </Color> Delete Quotation {#deleteQuotation}

Questo metodo elimina un preventivo sulla base dell'id fornito

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

#### <Color color = "darkorange"> POST </Color> Update Element Array Quotation {#updElemArrayQuot}

Questo metodo modifica la quantità del ricambio scelto, nel preventivo selezionata tramite id

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
    "updated": [
        {
            "Completato": false,
            "Consegnato": false,
            "CostoPreventivoNoIva": "16.00",
            "_id": {
                "$oid": "619b754cac74e60001ed87f9"
            },
            "accettato": true,
            "booking_id": {
                "$oid": "619b754cac74e60001ed87f9"
            },
            "created_at": "2021-11-22T10:48:23.953Z",
            "lavori_id": {
                "$oid": "61790e22157f660001ba6b04"
            },
            "ricambiScelti": [
                {
                    "id": 1,
                    "label": "123 - Brembo - Freno - nessuna",
                    "quantita": 2,
                    "prezzo": 1
                }
            ],
            "sconti_id": {
                "$oid": "617a7d24157f660001c3cdda"
            },
            "updated_at": "2021-11-22T10:48:23.965Z"
        }
    ]
}
```

#### <Color color = "darkorange"> POST </Color> Delete Element Array Quotation {#delElemArrayQuot}

Questo metodo elimina un ricambio (basato sull'id) dal preventivo selezionata tramite id

:::caution AVVISO
In caso di errore durante l'eliminazione, viene restituito **Not found**
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
        "Completato": false,
        "Consegnato": false,
        "CostoPreventivoNoIva": "16.00",
        "_id": {
            "$oid": "619b754cac74e60001ed87f9"
        },
        "accettato": true,
        "booking_id": {
            "$oid": "619b754cac74e60001ed87f9"
        },
        "created_at": "2021-11-22T10:48:23.953Z",
        "lavori_id": {
            "$oid": "61790e22157f660001ba6b04"
        },
        "ricambiScelti": [],
        "sconti_id": {
            "$oid": "617a7d24157f660001c3cdda"
        },
        "updated_at": "2021-11-22T11:09:35.831Z"
    }
}
```

