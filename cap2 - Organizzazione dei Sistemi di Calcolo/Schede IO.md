## Dispositivi Input/Output

Iniziano a definire cosa sono i dispositivi Input Output, sono tutti i dispositivi che possiamo vedere/toccare/usare concretamente quando abbiamo a che fare con un calcolatore.
Ad esempio le tastiere, lo schermo, il mouse e tanto altro.

Vengono connesse al BUS tramite una circuiteria chiamata **device controller**, non possono essere direttamente collegate al BUS di sistema per diversi motivi ma i 2 principali sono:
1. Sono di diversi ordini di grandezza più lente rispetto a tutti gli altri apparecchi che usufruiscono del bus (potrebbero rallentare drasticamente l'intero sistema)
2. Ogni Dispositivo potrebbere richiedere un tipo di dato di verso, non è detto che sia facilmente compatibile con il nostro BUS.

### Moduli Input/output

Si occupano di fare da ponte tra le interfacce e il BUS di sistema, credo siano quelli che abbiamo precedentemente chiamato *device controller*.
![[Screenshot 2025-08-18 alle 19.08.06.png]]
#### Struttura Logica
![[Screenshot 2025-08-19 alle 15.46.51.png]]
