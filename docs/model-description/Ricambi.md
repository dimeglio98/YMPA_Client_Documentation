export const Color = ({children, color}) => (
  <span
    style={{
      color: color
    }}>
    {children}
  </span>
);

## Descrizione
Questa modello descrive tutti i ricambi reperibili, la loro composizione

## Elenco API a disposizione

- <Color color = "lightgreen"> GET </Color> /allReplacements, ottiene tutti i ricambi
- <Color color = "darkorange"> POST </Color> /createReplacement, crea il ricambio