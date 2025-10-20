Ricordiamo che parliamo di Hardwere e non softwere. *La pipeline stessa è un insieme di componenti hardwere*. (ne abbiamo una per core)

Questo tipo di approccio permette di eseguire più operazioni contemporaneamente, vediamo i punti chiave.
1. Ogni istruzione deve essere spezzettata in più *parti* (nello specifico 5)
2. Per ogni  *parte* dell'istruzione abbiamo un supporto Hardware, quindi un modulo dedicato per svolgere solo quello specifico compito 
3. L'obbiettivo è tenere occupati più moduli possibili contemporaneamente, appene se ne libera uno deve essere richiesto dall'istruzione successiva.

Vediamo uno schema:
![[Screenshot 2025-08-18 alle 16.51.57.png#invert]]

L'istruzione (o i bit di essa) non passa da un componente all'altro, viene divisa nei moduli della pipeline che si attivano in maniera sequenziale (gestiti da un controllo) solo perchè la *fase n necessita della fase n-1*. 

- S1,S2,...,S5 sono i moduli sopracitati ma possiamo anche interpretarli come stati in cui si possono trovare le istruzioni in un certo istante al fine di comprendere meglio questo schema.
- Come possiamo vedere all'istante di tempo 1 abbiamo una sola istruzione (chiamata 1 essendo la prima) e si trova nello stato 1.
- Notiamo che fino allo stato 5 l'istruzione uno è passata per tutti gli stati, liberando dietro di se spazio per le istruzioni successive.
- All'istante di tempo 6 l'istruzione 1 abbandona il nostro schema dato che ha terminato il suo ciclo di vita.
- Fanno la stessa cosa le istruzioni successive negli istanti che seguono.

**Vantaggi**
1. Notiamo che dall'istante 5 in poi abbiamo un'istruzione portata a termine per ogni colpo di clock (OTTIMO!)
2. Il fattore di guadagno è pari al numero di stati della pipeline

**Svantaggi**
1. Le istruzioni che richiedono salti, possono complicare molto la pipeline o rallentarla dato che non si può più garantire la sequenzialità degli stadi delle istruzioni ed è complesso prevederla
2. Le istruzioni devono ovviamente essere indipendenti, in caso contrario si genera uno stallo. (sarà necessario attendere il termine di un istruzione prima di eseguirne un altra, *contro il concetto stesso della pipeline*)

### Tempi
- ciclo di clock : T \* nsec
- Frequenza: 10<sup>9</sup> / T
- Latenza: n \* T
- Larghezza di banda: Numero di istruzioni eseguite al secondo.
n = numero di stadi.