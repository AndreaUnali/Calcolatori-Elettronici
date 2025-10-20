
La comunicazione tramite BUS viene regolata mediante un **protocollo di BUS**.
Per potersi collegare al BUS tutte le unità possiedono un BUS driver in grado di svolgere le seguenti operazioni:
1.  collegarsi e scollegarsi elettricamente al BUS (tramite collegamento a tre stati o di tipo open collector); 
2. amplificare opportunamente i segnali da trasmettere/ricevere sul/dal BUS.

A questo scopo vengono sfruttati i [[Introduzione alle Memorie|Dispositivi a 3 stati (tri-state-Buffer]]



Come già sappiamo **in qualunque istante una e una sola unità funzionale può avere il controllo del BUS**.

- Chiamiamo l'unità che possiede il controllo **MASTER**
- Tutte le altre unità le chiamiamo **SLAVE**
- Ogni BUS deve avere un MASTER per funzionare

L'unità che possiede il ruolo del MASTER decide quali operazioni fare su quale unità e in quale istante di tempo. **Solitamente il ruolo del MASTER è ricoperto dalla CPU.** 
 ==`Ma non è sempre così, è possibile cedere temporaneamente il ruolo di MASTER tra le varie unità, e questo va gestito tramite qualche meccanismo (arbitraggio)`==

Abbiamo 2 tipi di meccanismi principali:
- Arbitraggio **centralizzato**
- Arbitraggio **distribuito**

## Arbitraggio centralizzato
Per l'arbitraggio centralizzato (o [[daisy chain]]) abbiamo 3 regole fondamentali:

1. È presente un unità funzionale dedita all'arbitraggio (per questo centralizzato)
2. Alcune linee del BUS sono dedite a trasmettere le richieste delle unità funzionali all'arbitro.
3. È l'arbitro che realizza la cessione del controllo del BUS (cessione del ruolo MASTER)


![[Screenshot 2025-08-19 alle 17.35.59.png#invert]]
Come possiamo vedere abbiamo 2 linee per il controllo del BUS, una da destra verso sinistra usata dalle unità funzionali per richiedere il ruolo di MASTER e una da sinistra a destra  che emette l'arbitro per assegnare il ruolo alla prima unità funzionale che incontra che ha fatto richiesta.

==`questo meccanismo avvantaggia le unità funzionali più vicine all'arbitro in questo modo introduce anche una logica di priorità.`==

1. Ingresso `grant` asserito, lo propago agli altri componenti, a meno che abbia intenzione di chiedere il controllo del BUS
2. Solo se ricevo un `grant` asserito sono in grado di effettuare una richiesta
3. Il segnale `busy` ci dice se il BUS è disponibile (questo deve essere non asserito per permettere una richiesta).


### Arbitro centralizzato con richieste

È possibile rendere più flessibile questo meccanismo aumentando il numero di linee request (richiesta del bus) e grant (conferma da parte dell'arbitro). Assegnando una scala di priorità alle varie linee.
![[Screenshot 2025-08-19 alle 17.39.06.png#invert]]

Se abbiamo più linee che chiedono contemporaneamente il BUS, l'arbitro darà il grant alla linea con priorità più alta che ha effettuato la richiesta. (Ha senso se linee di richiesta diverse sono collegate a dispositivi diversi)

### BUS Acknowledge
È possibile migliorare ulteriormente questo meccanismo introducendo i concetto di **accettazione** .

**Flusso operativo**

1. Un’unità chiede all’arbitro il controllo del BUS.
    
2. L’arbitro concede il permesso: l’unità attiva la linea **BUS acknowledge** e disattiva la sua richiesta.
    
3. L’arbitro, vedendo l’acknowledge, disattiva la linea di conferma.
    
4. A questo punto l’unità ha il controllo del BUS; le linee di richiesta e conferma sono libere, quindi un’altra unità può fare richiesta (che rimane in attesa).
    
5. Quando la prima unità rilascia il BUS disattivando l’acknowledge, l’arbitro può confermare la richiesta alla prossima unità.
![[6560A712-ACD5-443F-9F77-E97EB91DB9E1.png#invert]]


## Arbitraggio distribuito 
Anche qui abbiamo delle regole che scandiscono la logica di questo meccanismo.

1. Non abbiamo un arbitro che regola le richieste, ma ogni unità ha la sua linea per emettere la richiesta.
2. Le unità hanno diverse priorità fissate a priori.
3. Ogni unità può attivare **solo la propria linea di richiesta** del BUS.


![[Screenshot 2025-08-19 alle 17.51.46.png#invert]]
**Come funziona:**
Come possiamo vedere tutte le unità possono *parlare* alle altre mediante la propria linea e allo stesso tempo possono *ascoltare* le altre unità

Ogni unità per diventare master si assicura che unità di priorità superiore alla propria abbiamo fatto richiesta.

==`È lampante il problema principale di questo meccanismo, il numero di linee di controllo cresce con il numero di unità funzionali (non va bene)`==

### Arbitraggio distribuito a 3 Linee
Per migliorare l'arbitraggio distribuito è possibile implementarlo usan do solo 3 Linee:
- **Impegno del BUS (BUS busy)**: questa linea viene mantenuta attiva dall’unità che detiene il controllo del BUS. 
-  **Conferma del BUS (BUS grant)**: è la linea di conferma, collegata da un dispositivo all’,altro in *daisy chain.* 
-  **Richiesta del BUS (BUS request)**: l’unità attiva questa linea per richiedere il BUS.

![[Screenshot 2025-08-19 alle 17.58.25.png#invert]]

