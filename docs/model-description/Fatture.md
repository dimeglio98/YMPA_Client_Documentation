export const Color = ({children, color}) => (
  <span
    style={{
      color: color
    }}>
    {children}
  </span>
);

## Descrizione

Questa collection colleziona le fatture nel formato richiesto dalla fattura elettronica italiana

## Composizione colonne

Vedere il documento alla seguente [pagina](https://www.fatturapa.gov.it/export/documenti/Specifiche_tecniche_del_formato_FatturaPA_v1.3.1.pdf)

## API disponibili

### Metodi <Color color = "green"> GET </Color>
- [/allInvoices](#allInvoices), per tutte le fatture
- [/viewOneInvoice](#oneInvoive), per visualizzare una fattura

### Metodi <Color color = "darkorange"> POST </Color>

- [/createInvoice](#createInvoice), per creare una fattura