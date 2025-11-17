Gli Elementi di memoria servono a memorizzare gli stati passati della rete, più elementi di memoria abbiamo (a 1 bit) piu stati è possibile memorizzare combinandoli.
Abbiamo 2 tipi di elementi di memoria:
1. Elementi di memoria di tipo **Sincroni** o **Asincroni** (i **Latch**)
2. Elementi di memoria di tipo **Master-Slave**

## Latch
Il principio base che accomuna tutti i tipi di Latch è quello della retroazione, ossia *usare un precedente risultato come operando per calcolare il prossimo valore in uscita*.
Adesso vediamo diversi tipi di Latch in ordine di complessità.

### Latch Set-Reset (SR)
È un latch asincrono (privo di clock) ed è il lath più semplice che possiamo implementare

![[Screenshot 2025-08-25 alle 14.50.17.png#invert]]
![[Screenshot 2025-08-25 alle 14.50.40.png#invert]]
Il modo più facile per capire la logica secondo me è:
1. Se R = 0 abbiamo S in uscita
2. Se R = 1 abbiamo sempre 0 in uscita
3. Se R = S = 0 abbiamo Q(t) che sarebbe l'uscita all'istante precedente (ricorda che questa tabella di verità non ci dice niente sugli istanti di tempo passati/presenti/futuri non ha senso guardare l'ordine in cui sono disposti i segnali qui)
4. Non posso mai avere S = R = 1.

## Latch SR Sincrono

Vediamo adesso cosa succede se proviamo a rendere sincrono il circuito appena visto, collegando quindi un clock alla logica.
![[Screenshot 2025-08-25 alle 14.54.42.png#invert]]
La logica rimane identica l'unica differenza è che le uscite cambiano solo in corrispondenza di fronti di salita (o di discesa) del clock.

## Implementazione Pratica

 Per implementare un Latch di tipo SR necessito di:
 - 2 transistor 
 - 2 interruttori -> non possono mai essere entrambi aperti.

## Latch JK

Per quanto riguarda la logica, è identico a un latch SR con la differenza che permette in entrata due valori uguali a 1.
In questo caso particolare (con i due ingressi uguali a 1) avremo in uscita il risultato dell'istante precedente invertito.

Vediamo che per realizzare il circuito ci basta collegare alle 2 AND iniziali l'uscita del LATCH.
![[Screenshot 2025-08-25 alle 14.57.37.png#invert]]
![[Screenshot 2025-08-25 alle 15.01.20.png#invert]]


## Altri tipi di Latch

Abbiamo ovviamente altri tipi di Latch, per vederne 2 in più lascio questo contributo da cui è possibile volendo ricavare l circuito.
![[Screenshot 2025-08-25 alle 15.06.58.png#invert]]

## Generatore di Impulsi

Un generatore di impulsi è un piccolo circuito logico utile a simulare un clock.
Il concetto di base è quello di generare un ritardo (nello specifico sfruttiamo il ritardo di un **inverter**) per creare dei segnali intermittenti.
![[Screenshot 2025-08-25 alle 15.15.40.png#invert]]
 Nel diagramma in figura l’inverter induce un ritardo  $\Delta$ che permette alla rete di cambiare il proprio stato. 
 La durata $\Delta$ dell’impulso equivale al ritardo dell’inverter.


### Come rappresentiamo i Latch all'interno dei nostri circuiti

![[Screenshot 2025-11-17 alle 14.42.38.png#invert]]

## Elementi di Memoria Master-Slave (Flip-Flop)
1. **Cosa sono gli elementi di memoria?**

	- Gli **elementi di memoria** sono circuiti che **salvano 1 bit** (0 oppure 1).  

	- A differenza della **logica combinatoria** (uscita dipende solo dagli ingressi in quel momento),  qui l’uscita **dipende anche dal passato** → cioè mantengono informazione.

  2. **Il problema del “latch trasparente”**
	- Un **latch** è un circuito semplice che memorizza un bit.  
	- Ma è **trasparente**: quando l’ingresso cambia, l’uscita può cambiare subito.  
	- Questo può creare errori (perché non c’è un momento preciso in cui “bloccare” il valore).


3. **La soluzione: il Master–Slave**
	
	Un **flip-flop master–slave** è formato da **due latch** messi in cascata:
	
	- **Master** = primo latch  
	
	- **Slave** = secondo latch  

Funzionano alternati, grazie alla negazione del segnale di **clock**:

- Quando il **clock è alto** → il master legge l’ingresso, lo slave è bloccato.  

- Quando il **clock è basso** → il master si blocca e lo slave prende il valore dal master.  
![[Screenshot 2025-08-25 alle 15.24.32.png#invert]]
  
**Risultato:** l’uscita cambia **solo in corrispondenza del fronte di clock**, non in modo “sporco”.


4. **Vantaggi**

	- Uscita stabile e sincronizzata col **clock**.  

	- Niente più effetto “trasparenza” del latch.  

	- È la base di **registri, contatori, memorie digitali**.


### Come rappresentiamo i Flip Flop all'interno dei nostri circuiti


![[Screenshot 2025-11-17 alle 14.45.15.png#invert]]


# Analisi e sintesi di una rete sequenziale 

- [i] **Analisi**: Consiste nel passaggio dal circuito alla sua descrizione.
	- si descrive mediante tabelle e diagrammi

- [!] **Sintesi**: Consiste nel passaggio dalla descrizione delle funzionalità alla realizzazione del circuito.
	- Tipicamente questa fase ha in ingresso una descrizione (anche qualitativa) del comportamento che il circuito deve avere, e si progetta a step la circuiteria
	- si passa per diagrammi -> tabelle -> equazioni
