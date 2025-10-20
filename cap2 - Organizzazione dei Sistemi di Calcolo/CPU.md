La CPU è colei che si occupa di gestire l'intera struttura del sistema ed è responsabile di tutte le operazioni aritmetiche e logiche sui dati contenuti nei registri.
![[Screenshot 2025-08-17 alle 15.14.46.png#invert]]
Un **ciclo elementare** da prendere come esempio può essere:
- due operandi sono inviati alla ALU
- la ALU li somma
- il risultato viene memorizzato nella memoria

Perchè parliamo di ciclo? Nello specifico ci stiamo riferendo al [[Ciclo Fetch-decode-execute]]

## Differenza tra Esecuzione e Interpretazione

### Esecuzione 
In questo caso abbiamo un **Set prestabilito di istruzioni** e vengono direttamente eseguite dall'hardware.
- È un approccio complesso 
- Le istruzioni possibili sono limitate
- L'esecuzione è molto più efficiente

### Interpretazione
In questo caso l'hardware esegue poche istruzioni elementari dette **micro-istruzioni**. Le istruzioni che usiamo nel nostro progetto vengono scomposte da un **decoder** in tante microistruzioni.
Questo paradigma permette
- repertorio di istruzioni più esteso 
- Hardware più compatto (meno dispendio economico)
- Più flessibilità di progetto 

Possiamo vedere 2 tipi diversi di architetture nella nota [[Architetture CISC e RISC]]

## Microprogrammazione
L’hardware può eseguire microistruzioni:
- **Trasferimenti** **tra** registri. 
- **Trasferimenti** **da** e **per** la memoria. 
- **Operazioni** della ALU **su** registri. 

Ciascuna istruzione viene scomposta in una sequenza di microistruzioni. L’unità di controllo della CPU esegue un microprogramma per effettuare l’interpretazione delle istruzioni macchina.

Il microprogramma è contenuto in una memoria ROM sul chip del processore.
Vantaggi:
- Progetto strutturato;
- Semplice correggere errori;
- Facile aggiungere nuove istruzioni


**Prossimo Argomento —————————>>** [[Principi di progettazione, Focus sul Parallelismo]] 