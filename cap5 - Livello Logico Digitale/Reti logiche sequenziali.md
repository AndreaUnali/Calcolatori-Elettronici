## Definizione e Caratteristiche

Le reti sequenziali proprio come le [[Reti logiche combinatorie | reti combinatorie]] sono caratterizzate da **N ingressi** e **M uscite**. A differenza di esse però *i valori dei segnali in uscita dipendono dagli ingressi assunti precedentemente*.
Per far ciò hanno ovviamente bisogno di qualche [[Elementi di memoria in una Rete Logica| elemento di memoria]], e dato che la memoria è ovviamente limitata possono "*ricordare*" sono un numero finito di combinazioni di ingressi precedenti.
**Esempio:**
![[Screenshot 2025-08-24 alle 16.03.19.png]]
Questa rete sequenziale realizza la sua memoria tramite retroazione, cosi è implementato l'elemento di memoria più semplice il **latch**.

**Caratteristiche**
1. Un **insieme degli stati di ingresso**: l’insieme di configurazioni delle variabili booleane d’ingresso.
2. Un i**nsieme degli stati interni**: ogni stato corrisponde ad una possibile configurazione passata della rete.
3. Un **insieme degli stati di uscita**: l’insieme di configurazioni delle variabili booleane di uscita.
4. Un **diagramma degli stati**: descrive, in funzione delle variabili di ingresso e degli stati interni, ad un dato istante, lo stato all’istante successivo e le relative configurazioni degli stati di uscita.

==`Questa definizione coincide con quella di **automa a stati finiti**`==


## Diagramma degli stati: Mealy e Moore a confronto


Entrambi i diagrammi sono grafi orientati, dove i nodi rappresentano lo stato della rete e gli archi la possibilità di passare da uno stato all'altro in funzione degli ingressi.

La differenza sostanziale è che in Moore i valori in uscita della rete sono assegnati in base allo stato mentre nel diagramma di Mealy dipendono dalla combinazione di ingressi e stato.

Facciamo degli esempi per capire meglio:

``Ho implementato una stupidissima rete logica che conta da 0 a 2 finche in ingresso ha 1 e ricomincia, se invece in ingresso ha 0 torna allo step precedente del conteggio (quando è a 0 rimane a zero finche in ingresso ha valore 0)``

Vediamo le differenze tra Mealy e Moore
![[digrammi mealy e mooore.drawio.png]]
Giusto per capire, gli ingressi sono in verde, le uscite in arancione e gli stati i cerchi celesti e la lettera nera per differenziarli.

## Tabella di flusso e Tabella delle transizioni
- La **tabella di flusso** descrive le transizioni della rete sequenziale in forma tabellare:  
  ingresso, stato presente → stato successivo, uscita  
  → È l’equivalente della rappresentazione con **diagramma degli stati**.  

- La **tabella delle transizioni** sostituisce i nomi simbolici degli stati (S0, S1, …) con le **configurazioni binarie** che li rappresentano.  
  - Serve per l’implementazione pratica (per esempio nei circuiti con latch/flip-flop).  

---

### Esempio 

**Tabella di flusso**

| Stato presente | X=0     | X=1     |
|----------------|---------|---------|
| S0             | S0 / 00 | S1 / 10 |
| S1             | S1 / 10 | S2 / 01 |
| S2             | S2 / 01 | S3 / 11 |
| S3             | S3 / 11 | S0 / 00 |

**Tabella delle transizioni** (stati in binario)

| Stato presente | X=0     | X=1     |
| -------------- | ------- | ------- |
| 00             | 00 / 00 | 01 / 10 |
| 01             | 01 / 10 | 10 / 01 |
| 10             | 10 / 01 | 11 / 11 |
| 11             | 11 / 11 | 00 / 00 |
