
Le attività di un calcolatore si scandiscono in **cicli di BUS**, un'operazione per ciclo.
I MASTER governano le operazioni, ricordiamo che gli SLAVE non possono dare inizio a un'operazione autonomamente.

Abbiamo sostanzalmente 2 tipi di operazioni:
- **Lettura**:  un dato viene trasferito da uno SLAVE al MASTER. 
- **Scrittura**: un dato viene trasferito dal MASTER a uno SLAVE.

==`Sottoliineo che la direzionoe del dato è sempre decisa dal MASTER`==

Il susseguirsi di questi eventi sopra descritti va coordinato e per farlo abbiamo 2 metodi:
- **Temporizzazione Sincrona**
- **Temporizzazione Asincrona**

## Temporizzazione Sincrona

Questa modalità è la più semplice e anche la più usata, a discapito di ciò è però meno flessibile.

Vediamo cosa la caratterizza:
- Eventi determinati da un clock. BUS cycle corrispondono a Clock Cycle.
- Tutti gli eventi sono sincronizzati sui fronti del clock.
- Molti eventi durano più cicli di clock.

![[Screenshot 2025-08-20 alle 11.23.51.png]]

``Questa immagine ci mostra chiaramente come tutti gli eventi siano guidati dal tempo imposto dai colpi di clock. In un caso di lettura di un dato.``


## Temporizzazione Asincrona

Questa modalità consente a dispositivi di diversa velocità di condividere efficacemente il BUS, è quindi più flessibile.

Vediamo da cosa è caratterizzata:
- Non esiste un segnale di clock comune tra tutti.
- Le transizioni si sincronizzano in base agli eventi.
- Il BUS include dei segnali di controllo che insieme formano il **protocollo di sincronizzazione del BUS**.
- Lo stato delle operazioni avanza in corrispondenza degli eventi

### Lettura asincrona di una Parola 
![[Screenshot 2025-08-20 alle 11.35.21.png]]

1. Il **Master (CPU) invia l’indirizzo** sul BUS indirizzi, attiva **MREQ**, **RD** e, dopo averli stabilizzati, attiva **MSYN**. 
2. Lo **Slave (memoria) esegue l’operazione** nel minor tempo possibile e fornisce la parola sul BUS dati; poi attiva **SSYN**.
3. Il **Master legge la parola** dal BUS dati, toglie l’indirizzo e disattiva MREQ e RD; poi disattiva anche MSYN. 
4. Infine, lo Slave disattiva SSYN.



## Ricapitolando 

Il BUS sincrono è più semplice da implementare e da gestire. Introduce *sprechi di tempo* (operazioni che richiederebbero meno di un ciclo o un numero frazionato di essi.)

Il BUS asincrono è più efficiente ma ha in generale una complessità più alta.


**Prossimo Argomento —————————>> [[Algebra e Logica Binaria|Capitolo 4 Algebra e Logica Binaria]]**

