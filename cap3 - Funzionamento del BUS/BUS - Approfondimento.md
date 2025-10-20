
In questo capitolo 3 andiamo ad approfondire il BUS, in particolare vediamo come funziona, e come va gestito, quindi quali sono i problemi da sopperire e quali sono le strategie utilizzate.
Purtroppo in questa prima nota introduttiva (*si introduttiva anche se si tratta di un capitolo di approfondimento*) dovrò un po ripetermi al fine di aggiungere dettagli e smussare qualche definizione data frettolosamente nella nota [[BUS]].

Iniziando dalle basi, come già detto tale quale in precedenza possiamo constatare che:

- **Un calcolatore elettronico può essere sinteticamente visto come un insieme di unità funzionali interconnesse tra loro mediante un BUS**
![[Screenshot 2025-08-19 alle 16.45.10.png#invert]]

Tutti i BUS hanno una propria velocità, quelli sincroni sono scanditi dal clock.  Quelli asincroni dipendono dalla frequenza della corrente che li attraversa, che viene a sua volta influenzata dalla circuiteria a monte e a valle del BUS.

- **In un moderno calcolatore esistono:**
	- **BUS interni (data path)**, confinati all’interno di una singola unità funzionale, e che collegano i blocchi funzionali contenuti nell’unità.
	- **BUS esterni,** che si estendono all’esterno dell’unità funzionale, e che la collegano alle altre unità funzionali. I BUS esterni del calcolatore sono solitamente standardizzati![[Screenshot 2025-08-19 alle 16.47.49.png]]
``Qua sembrerebbe la stessa definizione discussa nella nota precedente in cui parlavo del BUS ma c'è un dettaglio che cambia le cose ossia nominare i BUS interni come datapath, in elettronica come già sappiamo il datapath è l'insieme di tutti i componenti che svolgono calcoli ma non mutiano il comportamento del sistema.``


- Larghezza del BUS = numero di linee. 
- Linee indirizzo: dimensione dello spazio (di memoria) indirizzabile: 
	- con n bit di indirizzo 2n locazioni.
- Ampliando le linee dati aumenta la velocità di trasmissione: banda di trasferimento. 
- **Condivisione** di più segnali sulla stessa linea (*multiplexing*) per diminuire i costi.
	- Il **Multiplexing** consiste nell'utilizzo delle stesse linee per diversi tipi di segnali a seconda della situazione, questo permette un grosso risparmio.
	- ==Problema==: al crescere della velocità del bus aumenta il 
		**BUS skew** (differenza nella velocità di propagazione dei segnali su linee diverse).

``Da adesso in poi quanto dirò 
	Segnale basso = 0
	Segnale alto. = 1  ``


## Terminologia
Per evitare confusione si parla di:
- *Segnale asserito:* quando assume il valore (alto o basso) che provoca l’azione. 
- *Segnale negato:* altrimenti.

**Si adotta la seguente notazione:**
S : segnale che è asserito alto.
$\overline S$: segnale che è asserito basso. 
S# : segnale che è asserito basso in contesto Intel.


Passiamo alle cose interessanti andando a parlare dell' [[Arbitraggio del BUS]], per vedere come viene gestito il suo utilizzo e la [[Temporizzazione del BUS]] per vederne il suo funzionamento

