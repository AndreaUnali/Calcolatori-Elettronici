
## Temporizzazione delle memorie

Adesso andiamo a vedere la *temporizzazione delle memorie*, in particolare quali sono i parametri (tempi) che caratterizzano il lavoro delle memorie. Sono aspetti che incidono significativamente la velocità delle memorie, da cui possiamo ricavare i tempi di risposta di esse.

![[Screenshot 2025-11-19 alle 19.54.03.png]]

1. **Imposizione dell'indirizzo del dato**: all'istante 1 incontriamo per la prima volta l'indirizzo del dato richiesto, in questo momento **iniziano** i seguenti tempi:
	- **TCW**: tempo minimo di scrittura, ossia il tempo minimo che deve passare tra due operazioni di scrittura
	- **TSU(a)**: tempo di set-up, rappresenta il tempo minimo in cui il segnale deve rimanere stabile per essere considerato valido. a sta per *address*

2. **Fornisco il dato**: all'istante 2 viene fornito il dato da scrivere in memoria, in questo istante **iniziano** i seguenti tempi:
	- **TSU(d)**: tempo di set-up, rappresenta il tempo minimo in cui il segnale deve rimanere stabile per essere considerato valido. d sta per *data*

3.  **Impulso di scrittura**: in questo istante si presente il primo segnale che avvia la fase di scrittura in memoria, a questo punto **terminano i tempi TSU**, e **iniziano** i tempi:
	- **TW(w)**: anche questo è un tempo di set-up, rappresenta la durata minima dell'impulso, w sta per *write*

4. **Abbasso comando di scrittura**: in questo istante termina l'impulso di scrittura, e con esso **termina il tempo TW(w)**, in questo istante **iniziano** i seguenti tempi:
	- **TH(a)**: tempo di hold,  rappresenta il tempo in cui il segnale deve rimanere stabile a seguito dell'operazione, anche in questo caso a indica *address*
	- **TH(a)**: tempo di hold,  rappresenta il tempo in cui il segnale deve rimanere stabile a seguito dell'operazione. Anche in questo caso d indica *data*

5. **Variazione del dato**: in questo istante termina la possibilità di variare il dato scritto (in questo ciclo di scrittura), **termina il tempo TH(d)**

6. **Cambio di Indirizzo**: questo istante rappresenta la fine del ciclo di scrittura e con esso **termina il tempo TH(d)**, con un conseguente cambio di indirizzo.
