## Dispositivi Input/Output

Iniziano a definire cosa sono i dispositivi Input Output, sono tutti i dispositivi che possiamo vedere/toccare/usare concretamente quando abbiamo a che fare con un calcolatore.
Ad esempio le tastiere, lo schermo, il mouse e tanto altro.

Vengono connesse al BUS tramite una circuiteria chiamata **device controller**, non possono essere direttamente collegate al BUS di sistema per diversi motivi ma i 2 principali sono:
1. Sono di diversi ordini di grandezza più lente rispetto a tutti gli altri apparecchi che usufruiscono del bus (potrebbero rallentare drasticamente l'intero sistema)
2. Ogni Dispositivo potrebbere richiedere un tipo di dato di verso, non è detto che sia facilmente compatibile con il nostro BUS.

### Moduli Input/output

Si occupano di fare da ponte tra le interfacce e il BUS di sistema, credo siano quelli che abbiamo precedentemente chiamato *device controller*.
![[Screenshot 2025-08-18 alle 19.08.06.png#invert]]
#### Struttura Logica
![[Screenshot 2025-08-19 alle 15.46.51.png#invert]]

## Modalità di I/O

### 1. I/O programmato
In questo caso la CPU si occupa di controllare la totalità delle operazioni, mediante l'esecuzione diretta di istruzioni di I/O.

| In questa immagine possiamo vedere il flusso di lavoro nel caso di I/O programmato.<br><br>Tutte le istruzioni del flusso vengono eseguite dalla CPU, e devono essere incluse esplicitamente nelle istruzioni del programma.<br><br>si puo notare che abbiamo al termine abbiamo un ciclo di polling per verificare se abbiamo o no terminato l'esecuzione del programma. | ![[Screenshot 2025-10-15 alle 11.25.53.png#invert]] |
| ------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------- |

### 2. I/O pilotato da Interrupt

La CPU in questo caso non necessita di Polling, quindi non ho più cicli di attesa, verifica se è stato emesso un interrupt al termine di ogni istruzione (lo fa all'interno del ciclo stesso, questo non genera quindi sovraccarichi inutili di lavoro), in caso positivo dovrà effettuare in **context switch**

1. La CPU sta eseguendo un processo e si trova all'istruzione *x*
2. **arriva un interrupt**
3. La CPU emette un Acknowledge per segnalare la corretta rilevazione dell'interrupt e dell'imminente gestione di esso.
4. Esegue le Istruzioni contenute nel **IV** (Interrupt vector, contenente le istruzioni richieste dall' interrupt).
5. Terminate le istruzioni del IV riprende con l'esecuzione del processo interrotto dall'istruzione *x+1*

### 3. Accesso diretto alla memoria - DMA

I moderni dispositivi sono dotati di moduli DMA che "bypassano" la CPU in fase di esecuzione delle istruzioni.

1. Il DMA invia un interrupt alla CPU per richiedere *scrittura* o *letura*
2. La CPU interrompe il suo flusso di lavoro per inviare **dei segnali di controllo** al DMA
3. La CPU riprendere il suo flusso e intanto il DMA si occupa del trasferimento in maniera indipendente
4. Al termine del trasferimento il DMA invia nuovamente un interrupt per segnalare il fine lavoro.

#### Segnali di controllo
- **Locazione Iniziale**: cella in memoria da cui partire per ricevere/trasferire dati
- **Numero di parole**: quante parole trasferire (immagino che in alcuni casi *pensa a una keyboard* sia indefinito)
- **Indirizzo**: indirizzo che identifica il modulo I/O

### Interfacce I/O

1. **Parallela**: Trasmissione di più `bit` alla volta

2. **Seriale**: Trasmissione di un singolo `bit` alla volta

a. **Point-To-Point**: due dispositivi che hanno un loro canale dedicato per la comunicazione
	e il trasferimento dati 

b. **Multipoint**: Canali condivisi tra più dispositivi


## USB 
Bus Universale di I/O
```
Permette il trasferimento tra moduli a diverse velocità di trasmissione
```

Il trasferimento avviene mediante **frame**, ne possiamo avere di 4 tipi:

1. **Controllo**: Per configurare e interrogare dispositivi
2. **Isocrono**: Per interrogazione sincrona di dispositivi *real-time*, hanno  un ritardo prevedibile
3. **Bulk**: trasferimento massiccio di dati (grandi dimensioni)
4. **Interrupt**: Simula Interrupt includendo tutti le richieste emesse in un intervallo di tempo

Quattro tipi di **pacchetti**:

1. **Token**: Inviato dal Root Hub al dispositivo : **SOF** (Start of Frame);**IN/OUT** (richiesta di lettura/scrittura dati); **SetUp** (configurazione). 
2. **Dati**: 8bit sync; 8bit packet type(id); payload fino a 64 byte; 16bit CRC. 
3. **Handshake**: ACK/NACK (acknowledge o errore)
4. **Speciali**: vedi foto

![[Screenshot 2025-10-15 alle 12.14.40.png#invert]]