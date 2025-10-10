Attualmente possiamo distinguere 5 diversi tipi di paradigmi da perseguire in fase di progettazione
1. **Eseguire tutte le istruzioni direttamente dall’hardware** 
	- Esecuzione diretta per le istruzioni più comuni. 
	-  Interpretazione solo per le istruzioni più complesse e meno comuni.
	  
2. **Massimizzare la frequenza di emissione delle istruzioni** 
	- Determina il valore dei MIPS (Millions Instructions per Second). 
	-  Ruolo importante del parallelismo. 

3. **Semplificare la decodifica delle istruzioni** 
	-  Rendere le istruzioni regolari, di lunghezza fissa, pochi campi.
	     - in questo modo la decodifica avrà meno variabili, ergo più semplice

4. **Limitare i riferimenti alla memoria (solo LOAD e STORE)** 
	- L’accesso alla memoria richiede tempo.
	- Tutte le operazioni dovrebbero operare su registri.
	- Operazioni sovrapponibili agli accessi alla memoria.

5. **Aumentare il numero di registri disponibili** 
	- Limitare l’accesso alla memoria richiesta dalle operazioni. 
	- Disporre sempre di registri liberi per le operazioni

## Parallelismo
Ad oggi il paradigma migliore (e più diffuso) per massimizzare le prestazioni è il parallelismo nel nostro caso ne abbiamo di 2 tipi.
1. **Parallelismo a livello di Istruzione**
	- Diverse istruzioni o porzioni di esse vengono eseguite contemporaneamente
2. **Parallelismo a livello di processore**
	- Diversi processori lavorano congiuntamente sullo stesso problema.
	- Fattori di parallelismo molto elevati. 
	- Diversi tipi di interconnessione e cooperazione.

Uno dei più importanti metodi per implementare il parallelismo è la [[Pipeling]] (anche quello che vediamo meglio), vediamo adesso altri tipi di parallelismo, meno importanti rispetto alla pipeline ma pur sempre degni di nota.

- [*] Un altro paradigma molto utilizzato sono le [[Architetture Multiscalari]]

### Architetture Superscalari

In queste architetture si avviano più istruzioni (4-6 contemporaneamente). Ognuna di esse con una propria [[Pipeling|Pipeline]].
![[Screenshot 2025-08-17 alle 18.38.59.png]]
Ovviamente abbiamo dei problemi a fronte di questo paradigma, principalmente 2:
- **Interdipendenza tra istruzioni**: diverse istruzioni possono richiedere stesse risorse
- **Nessuna istruzione può dipendere da una eseguita in parallelo**: ad esempio gli operandi di un istruzione non possono essere il risultato di un altra.


È possibile avere una versione della stessa architettura ma con singola pipeline, dotate di unità funzionali multiple
![[Screenshot 2025-08-17 alle 18.40.44.png]]
Viene duplicato solo lo stadio più lento.
- Lo stadio S3 deve poter lanciare istruzioni ad una frequenza superiore all’esecuzione dello stadio S4.
- La CPU contiene diverse unità funzionali indipendenti. 
- Architettura adottata nei processori Intel Core.

### Parallelismo mediante Multithreading
Più Processi vengono eseguiti in maniera concorrente.
Ho 2 opzioni:
- [>]  **Grana fina**: Ogni processo ha a disposizione un quanto di tempo fisso per poi cedere il posto al Thread successivo
	- In questo modo non ho stalli ma effettuo molti *context switch*, che è un operazione pesante per il sistema 
- [>] **Grana grossa**: Cambio processo quando quest'ultimo si interrompe (perchè ha finito o ha una fase di stallo), o se raggiunge un quanto di tempo massimo.
	- Effettuo pochi context switch ma presenta *stalli* dato che devo attendere un operazione *nop* per sapere quando passare al prossimo processo

Il Thread che è attualmente in esecuzione esegue 2 istruzioni per ciclo fino a quando non raggiunge uno stallo, in quel caso si passa al Thread successivo.


![[Screenshot 2025-08-17 alle 18.46.29.png]]

**L'obbiettivo è quello di tenere la CPU perennemente impegnata** 

### Parallelismo a livello della [[CPU]]
Per avere guadagni fino a 2 ordini di grandezza è necessario utilizzare più processori simultaneamente, anche in questo caso abbiamo 2 vie:

**Parallelismo dei dati** (SIMD)
Le stesse istruzioni vengono eseguite contemporaneamente da due processori distinti ma su dati diversi.
--->> Breve approfondimento [[SIMD]]

**Parallelismo dei task** (MIMD)
Diversi processori eseguono diversi task


**Prossimo argomento —————————>>** [[Memorie]]


