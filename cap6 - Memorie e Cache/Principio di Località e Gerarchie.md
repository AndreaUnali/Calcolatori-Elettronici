#cap6 

**Definizione:** Si è osservato che, in un breve lasso di tempo, la CPU dovrà accedere a determinati gruppi (cluster) di dati ed istruzioni.

Il concetto si distingue in due tipologie:
- **Località spaziale** : I prossimi dati e istruzioni da utilizzare probabilmente si troveranno in locazioni contigue a quelli attualmente in uso (cluster di locazioni). Ciò avviene perché i programmi hanno un flusso di esecuzione tipicamente sequenziale e spesso usano strutture dati sequenziali (come vettori o matrici

- **Località temporale**: Dati e istruzioni usati di recente è probabile che vengano riutilizzati entro breve tempo. Ad esempio, istruzioni ripetute all'interno di cicli (loop)

	
**Osservazioni fondamentali:** Il principio di località si basa quindi su questi fatti:

1. I programmi hanno un flusso di esecuzione tipicamente sequenziale.
    
2. Si hanno tante chiamate a procedure nidificate in sequenza, una dietro l'altra.
    
3. Nei programmi si hanno spesso gruppi di istruzioni che vengono ripetuti per un certo tempo (loop).
    
4. Nei programmi si utilizzano spesso strutture dati sequenziali.


## Esempio gerarchie a 2 Livelli M1 e M2

- **Livello M1 (Cache):** Più veloce e costoso. Ha una capacità di 1.000 parole e un **tempo di accesso (T1) di 0,1 μsec**.

- **Livello M2 (Memoria Principale/DRAM):** Più lento ed economico. Ha una capacità di 100.000 parole e un **tempo di accesso (T2​) di 1 μsec**.

Tutte le informazioni presenti in M1 sono anche in M2, ma non viceversa. Quando i dati non vengono trovati in M1 (*Cache Miss*), si accede a M2, ma si copia in M1 un intero **blocco di dati** contenente anche le locazioni contigue, sfruttando la Località Spaziale.

È possibile calcolare il **tempo medio di accesso**:

1. ipotizziamo che il 95% delle volte troviamo il dato richiesto nella cache (*cache hit*), il restante 5% avremo un *cache miss*.
2. Quindi *H = 0.95*
3. Calcoliamo...

$$
	Ts​=H×T1​+(1−H)×(T1​+T2​)
$$

Dove: 
- $H×T1$ : è il tempo speso quando l'accesso è un successo (Cache Hit).
- $1-H$ : è la probabilità che l'accesso fallisca (Cache Miss).
- $(T1+T2)$ : è il tempo speso per cercare in M1 e poi accedere a M2, copiando il dato.

sostituendo i valori dell'esempio:
$$
	Ts​=(0.95×0,1 μs)+(0.05×(0,1 μs+1 μs))
$$
$$
	Ts​=0.095 μs+(0.05×1.1 μs)
$$
$$
	Ts​=0.095 μs+0.055 μs=0.15 μs
$$


Il tempo medio effettivo di accesso (0,15 μs) si avvicina molto al tempo di accesso della memoria più veloce (0,1 μs), dimostrando l'efficacia della gerarchia

> [!NOTE] Conclusione
> Sfruttando questo principio, la gerarchia di memoria organizza i dati in modo che i _cluster_ che servono in un dato momento si trovino ai livelli più alti e veloci della gerarchia

