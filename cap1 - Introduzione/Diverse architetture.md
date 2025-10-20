Tanto per iniziare vediamo sbrigativamente una serie di tipologie di calcolatori che possiamo trovare ai giorni nostri:
- **RFID**:
	Appartengono alla categoria **usa e getta** sono tipicamente senza batteria.
	Nel concreto stiamo parlando di quei miniscoli processori che troviamo sulle carte di credito o all'interno dei libri della biblioteca.
	
	Di fatto vengono utilizzati per il *riconoscimento di qualcosa*
	
	Contengono al loro interno un **numero a 128 bit** e quando **ricevono un segnale radio trasmettono il proprio numero**.

- **Microcontrollori**:
	Piccoli computer inclusi in vari dispositivi tipicamente connessi alla rete, li troviamo all'interno delle automobili, elettrodomestici,...etc. etc.

	Sono tipicamente dotati di :
	- una **CPU** 
	- una piccola **Memoria**
	- qualche **dispositivo di I/O**

- **Game computers**
	Sono normali computer ma con le seguenti caratteristiche:
	- Software Limitato
	- Sbilanciati verso il calcolo grafico (GPU)
	- sistemi chiusi (non estendibili)

- **Smartphone**
	Sono normali computer, con interfaccia (ormai quasi tutti) touchscreen, e possiado tipicamente un sistema di riconoscimento biometrico. Un sistema operativo diverso, studiato a doc per l'uso mobile e le limitate risorse Hardware

- **Tablet** 
	Quasi considerabili dei computer portatili sono però caraterrizzati da:
	- Sistema operativo mobile
	- CPU potenti
	- Memorie ridotte
	- interfaccia touchscreen

- **Workstation**:
	- Diversi TB di disco
	- Diversi GB di memorie
	- Rete locale o web server

- **COW (cluster of workstation)**
	- Sistema multiprocessore ad [[accoppiamento lasco]]
	- in sostanza tante work station che comunicano tra loro

- **Mainframe**
	- Centinaia di terminali connessi
	- costi di parecchi milioni di euro


## Differenza tra CPU e GPU

- La **CPU**: è un processore di tipo generale, utilizzabile per usi più comuni e in grado di far girare qualunque tipo di software ( tralasciando problemi di compatibilità)
- La **GPU**: è un processore specializzato, nasce per un uso specifico, in particolare è orientato al calcolo ai fini grafici, quindi immagini e video, mediante operazioni tra matrici . Non è specializzata (e quindi limitata) quanto un ASIC o un FPGA. 


## Architetture multilivello

![[Screenshot 2025-08-11 alle 18.23.59.png#invert]]
Vedremo poi nel dettaglio la [[Struttura di un computer]] per analizzare le sue componenti interne e il loro funzionamento 

Per progettare una macchina/[[CPU]] non posso mettere insieme i componenti necessari, raggruppare dei transistor e collegarli tra loro. È *necessario astrarre il problema in più livelli, nello specifico ogni livello può usufruire di strumenti e risorse messi a disposizione dai lielli sottostanti.*

Adesso quando si progetta un Architettura multilivello si tiene anche conto dell'importante uso di parallelismo, sia di task che di componenti. Per evitare sprechi (livelli di parallelismo inutilmente alti) si fa affidamento alla [[Legge di Amdahl]]





## Come si sono evolute le architetture?

### 8 Grandi idee che hanno permesso di Inseguire le prestazioni

1. Legge di Moore
2. Astrazione per semplificare i design
3. Rendere l’utilizzo comune veloce
4. Aumento il Parallelismo dei task e dell’hardware
5. Aumento Prediction (prevedere le prossime istruzioni, i tempi di esecuzione,)
6. Aumento Pipeling (catena di montaggio)
7. Gerarchia delle memorie cache(più livelli)->ram->rom
8. Rindondanza

Queste idee e non solo hanno contrassegnato l'andamento dell'[[Evoluzione delle architetture|evoluzione delle architetture]] nel tempo
 
**Prossimo Argomento —————————>>** [[Leggi di Moore e Nathan]]