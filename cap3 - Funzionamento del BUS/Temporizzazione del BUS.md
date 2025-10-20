
Le attività di un calcolatore si scandiscono in **cicli di BUS**, un'operazione per ciclo.
I MASTER governano le operazioni, ricordiamo che gli SLAVE non possono dare inizio a un'operazione autonomamente.

Abbiamo sostanzalmente 2 tipi di operazioni:
- **Lettura**:  un dato viene trasferito da uno SLAVE al MASTER. 
- **Scrittura**: un dato viene trasferito dal MASTER a uno SLAVE.

==`Sottolineo che la direzionoe del dato è sempre decisa dal MASTER`==

Il susseguirsi di questi eventi sopra descritti va coordinato e per farlo abbiamo 2 metodi:
- **Temporizzazione Sincrona**
- **Temporizzazione Asincrona**

## Temporizzazione Sincrona

Questa modalità è la più semplice e anche la più usata, a discapito di ciò è però meno flessibile.

Vediamo cosa la caratterizza:
- Eventi determinati da un clock. BUS cycle corrispondono a Clock Cycle.
- Tutti gli eventi sono sincronizzati sui fronti del clock.
- Molti eventi durano più cicli di clock.

![[Screenshot 2025-08-20 alle 11.23.51.png#invert]]

``Questa immagine ci mostra chiaramente come tutti gli eventi siano guidati dal tempo imposto dai colpi di clock. In un caso di lettura di un dato.``


## Temporizzazione Asincrona

Questa modalità consente a dispositivi di diversa velocità di condividere efficacemente il BUS, è quindi più flessibile. Un evento dipende dagli eventi precedenti.

Vediamo da cosa è caratterizzata:
- Non esiste un segnale di clock comune tra tutti.
- Le transizioni si sincronizzano in base agli eventi.
- Il BUS include dei segnali di controllo che insieme formano il **protocollo di sincronizzazione del BUS**.
- Lo stato delle operazioni avanza in corrispondenza degli eventi

### Lettura asincrona di una Parola 
![[Screenshot 2025-08-20 alle 11.35.21.png#invert]]

1. Il **Master invia l’indirizzo** sul BUS indirizzi, attiva **MREQ**, **RD** e, dopo averli stabilizzati, attiva **MSYN**. 
2. Lo **Slave (memoria) esegue l’operazione** nel minor tempo possibile e fornisce la parola sul BUS dati; poi attiva **SSYN**.
3. Il **Master legge la parola** dal BUS dati, toglie l’indirizzo e disattiva MREQ e RD; poi disattiva anche MSYN. 
4. Infine, lo Slave disattiva SSYN.

```
Tutte le operazioni sono scandite dall'attivazione e la disattivazione di MSYN e SSYN
```


## Lettura Sincrona con ritardi 
Questo meccanismo serve a sincronizzare un Master veloce (come la CPU) con uno Slave più lento (come la memoria). Dato che la memoria è troppo lenta per fornire i dati in un ciclo di clock standard, il sistema introduce un "Ciclo di stato di attesa" (*Wait State*), in questo caso il ciclo T2.
![[Screenshot 2025-10-20 alle 15.11.39.png#invert]]
### I 3 cicli

1. **Ciclo T1 (Selezione):**

	- Il Master (CPU) avvia l'operazione.
	    
	- Mette l'indirizzo della memoria che vuole leggere sul bus `ADDRESS`.
	    
	- Dopo che l'indirizzo si è stabilizzato, sul _fronte di discesa_ del clock (metà ciclo T1), il Master attiva (abbassa) i segnali $\overline{MREQ}$ (richiesta di memoria) e $\overline{RD}$ (richiesta di lettura)5.

2. **Ciclo T2 (attesa, *wait*)** :
	-  Lo Slave (memoria) ha rilevato la richiesta ($\overline{MREQ}$ e $\overline{RD}$ bassi) ma sa di non essere abbastanza veloce per fornire il dato (richiede 40 ns6, più del tempo disponibile).
    
	- Per guadagnare tempo, sul _fronte di salita_ del clock (inizio ciclo T2), lo Slave attiva (abbassa) il segnale $\overline{WAIT}$ .
    
	- Il Master rileva $\overline{WAIT}$ attivo e capisce che deve attendere. Invece di leggere i dati alla fine di T2, estende l'operazione di un altro ciclo. Questo T2 diventa un "ciclo di attesa".
	
3. **Ciclo T3 (Trasferimento dati e Conclusione):**

	- All'inizio di T3, lo Slave ha finalmente il dato pronto.
    
	- Sul _fronte di salita_ del clock (inizio ciclo T3), lo Slave disattiva (alza) il segnale $\overline{WAIT}$ (per dire "OK, sono pronto") e contemporaneamente mette il dato richiesto sul bus `DATA`.
    
	- Sul _fronte di discesa_ del clock (metà ciclo T3), il Master (che stava aspettando) legge il dato presente sul bus `DATA`.
    
	- Subito dopo aver letto, il Master conclude l'operazione: disattiva (alza) $\overline{MREQ}$ e $\overline{RD}$ e rimuove l'indirizzo dal bus.

### Flusso operativo

1. **Inizio T1:** Il Master (CPU) impone l'indirizzo sul bus `ADDRESS`.
    
2. **Metà T1 (Fronte di discesa):** Il Master attiva $\overline{MREQ}$ e $\overline{RD}$ per avviare la lettura.
    
3. **Inizio T2 (Fronte di salita):** Lo Slave (Memoria) rileva la richiesta, sa di essere lento e attiva $\overline{WAIT}$ per chiedere un ciclo di attesa.
    
4. **Metà T2 (Fronte di discesa):** Il Master campiona il segnale $\overline{WAIT}$, lo trova attivo (basso) e si mette in attesa, estendendo il ciclo di lettura.
    
5. **Inizio T3 (Fronte di salita):** Lo Slave ha il dato pronto. Disattiva $\overline{WAIT}$ (lo alza) e mette i dati sul bus `DATA`.
    
6. **Metà T3 (Fronte di discesa):** Il Master campiona il bus `DATA` e legge il valore.
    
7. **Fine T3:** Avendo letto il dato, il Master conclude l'operazione disattivando $\overline{MREQ}$ e $\overline{RD}$ .


## Tipi di ritardi possibili
![[Screenshot 2025-10-20 alle 15.18.18.png#invert]]



## Lettura Sincrona a Blocchi

Più parole vengono fornite in parallelo, nello specifico siamo in grado di trasferire lungo il BUS una parola per ciclo. Nella lettura tradizionale necessitiamo sempre di 3 cicli per parola.
![[Screenshot 2025-10-20 alle 16.21.30.png#invert]]
Grazie a questo paradigma necessitiamo dei primi 2 cicli preparatori e successivamente un ciclo per parola.
```
molto vantaggioso al crescere delle parole
```

Trasferimento di 4 parole:
- **Lettura a blocchi**: 6 cicli = 2 + 4
- **Lettura tradizionale**: 12 cicli = 3 x 4

# Ricapitolando 

Il BUS sincrono è più semplice da implementare e da gestire. Introduce *sprechi di tempo* (operazioni che richiederebbero meno di un ciclo o un numero frazionato di essi.)

Il BUS asincrono è più efficiente ma ha in generale una complessità più alta.

Si usano principalmente bus con temporizzazione sincrona, nonostante  sia più lenta. Questo perché la maggior parte dei dispositivi (CPU, memorie, etc..) sono nativamente sincroni, ciò significa che per permettere l'utilizzo con bus asincroni necessiterebbe una rete sequenziale ad hoc usata come interfaccia tra il bus e il dispositivo. Aumentando particolarmente  la complessità del sistema (in particolare la progettazione di esso). 


**Prossimo Argomento —————————>> [[Algebra e Logica Binaria|Capitolo 4 Algebra e Logica Binaria]]**

