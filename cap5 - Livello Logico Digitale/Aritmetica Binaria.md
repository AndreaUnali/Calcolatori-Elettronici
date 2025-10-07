## Somma binaria 
- La somma segue le regole standard del sistema binario.
- Possibile **overflow** quando servono più bit di quelli disponibili:
  - Il risultato diventa errato.
  - Il segno può risultare discordante da quello degli addendi (se hanno lo stesso segno).
- I numeri negativi sono rappresentati in **complemento a 2**.

## Sottrazione binaria 
- Si effettua sommando il minuendo con il **complemento a 2** del sottraendo.
- Sono necessari solo:
  - Circuiti per l’addizione
  - Circuiti per la complementazione
- Stesse condizioni di **overflow** della somma.

## Schema di un sommatore 
- Può utilizzare registri dedicati per il risultato.
- Segnali di controllo:
  - **OF**: overflow bit
  - **SW**: switch bit (indica addizione/sottrazione)

## Moltiplicazione binaria 
- **Algoritmo base:**
  1. Generare i prodotti parziali (uno per ogni bit del moltiplicatore).
  2. Se il bit del moltiplicatore è `0` → prodotto parziale = `0`.
  3. Se il bit del moltiplicatore è `1` → prodotto parziale = moltiplicando.
  4. Ogni prodotto parziale viene **shiftato a sinistra** di una posizione rispetto al precedente.
  5. Si sommano i prodotti parziali per ottenere il risultato.

- **Problema con numeri negativi:**
  - Algoritmo base non funziona correttamente.
  - Soluzioni:
    1. Convertire i fattori in positivi, applicare algoritmo e negare il risultato se i segni sono discordi.
    2. Usare l’**algoritmo di Booth (1952)**:
       - Più rapido.
       - Non richiede la negazione del risultato.

## Divisione binaria
- Operazione più complessa della moltiplicazione.
- Si può eseguire tramite **sottrazioni ripetute**.
- **Algoritmo base (numeri interi senza segno):**
  1. Allineare a sinistra dividendo e divisore.
  2. Confrontare: se la parte alta del dividendo ≥ divisore:
     - Sottrarre divisore.
     - Inserire `1` nel quoziente.
     - Altrimenti inserire `0`.
  3. Shiftare il divisore di un bit a destra.
  4. Ripetere fino a che il divisore non può più scalare.
  5. La differenza finale è il **resto**.

---
# Confronto operazioni aritmetiche binarie

| Operazione     | Metodo principale | Note operative | Problemi principali |
|----------------|------------------|----------------|---------------------|
| **Somma**      | Addizione bit a bit con propagazione del riporto | Stesse regole dell’aritmetica binaria classica | **Overflow** se servono più bit di quelli disponibili |
| **Sottrazione**| Somma del minuendo con il **complemento a 2** del sottraendo | Richiede solo addizionatore e circuiti per complemento a 2 | Stessi problemi di **overflow** della somma |
| **Moltiplicazione** | Generazione di prodotti parziali e loro somma, con **shift a sinistra** | Se moltiplicatore bit=1 → prodotto parziale = moltiplicando | Con numeri negativi serve conversione o **algoritmo di Booth** |
| **Divisione**  | **Sottrazioni ripetute** con shift del divisore verso destra | Quoziente costruito progressivamente (1 se divisore ≤ parte del dividendo, altrimenti 0) | Operazione più lenta e complessa rispetto alla moltiplicazione |
