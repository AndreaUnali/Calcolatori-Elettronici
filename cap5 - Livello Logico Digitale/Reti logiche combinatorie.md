
## Reti Logiche e Reti combinatorie
Una **rete logica** è un insieme di blocchi funzionali realizzati mediante porte logiche ed elementi di memoria.

Abbiamo 2 tipi di reti Logiche:
- Con memoria : **Reti Sequenziali**
- Senza memoria : **Reti Logiche combinatorie**

Spiegando meglio la rete combinatoria, è caratterizzata dal fatto che in un qualsiasi istante i valori in uscite delle rete combinatoria dipende solo ed esclusivamente dai valori in ingresso (mai da valori precedenti)

D'altra parte una rete sequenziale può assumere uno stato ed esso influenza i valori in uscita della rete. Significa che a parità di ingressi se la rete si trova allo stato S1 o S2 avremo in uscita valori diversi.

## Componenti Elettronici

I circuiti integrati sono chip di silicio che racchiudono al loro interno moltissime porte logiche. A seconda della complessità si parla di SSI, MSI, LSI o VLSI. Oggi i processori moderni sono esempi di VLSI. Questi circuiti sono racchiusi in diversi package, come DIP, PGA e LGA

![[Screenshot 2025-08-23 alle 19.48.43.png]]
- Esistono diversi livelli di integrazione:
    
    - **SSI** (Small Scale): poche porte (1–10)
        
    - **MSI** (Medium Scale): decine di porte (10–100)
        
    - **LSI** (Large Scale): centinaia/migliaia (10²–10⁵)
        
    - **VLSI** (Very Large Scale): centinaia di migliaia o milioni (>10⁵) → processori moderni
        
    
- Hanno tempi di commutazione molto rapidi (nanosecondi).
    
- Si presentano in diversi **contenitori fisici**:
    
    a.  **DIP** (Dual Inline Package, i classici chip rettangolari a piedini)
        
    b.  **PGA** (Pin Grid Array, piedini sul fondo)
        
    c.  **LGA** (Land Grid Array, contatti piatti usati ad esempio nelle CPU moderne).

### Comparatore

Il comparatore è un circuito logico che confronta due stringhe di bit sfruttando l’operatore XOR. Restituisce un’uscita che segnala se i due valori sono uguali o diversi.
![[Screenshot 2025-08-23 alle 19.51.04.png]]
- Si basa sull’operatore **XOR** (esclusivo):
    
    - Se due bit sono uguali → l’uscita è 0.
        
    - Se due bit sono diversi → l’uscita è 1.
    
- In pratica, confronta bit a bit due numeri binari.
    
- L’uscita indica se i due valori sono **uguali** o **diversi**.

### Multiplexer (MUX)

Il multiplexer è un componente Logico che ci permette di scegliere quale segnale ascoltare in base ai bit di controllo.
Facciamo un esempio per capire meglio:
1. Immaginiamo di avere due segnali (A-B) e di voler scegliere se ascoltare uno o l'altro.
2. Tramite il MUX ci basterà un bit di controllo ($S_0$) per scegliere quale segnale ascoltare.
3. Ad esempio $S_0 = 0$ per ascoltare A e $S_0 = 1$ per ascoltare B.

![[Screenshot 2025-08-24 alle 15.38.07.png]]
**Per realizzare un MUX a 1 bit (di controllo) ci basterà:**
1. Scrivere la tabella di verità
2. Trovare la formula Minima tramite le **[[Leggi di Karnaugh]]**
3. Disegnare il circuito della equazione ricavata.


#### Multiplexer a 2 bit
Dati due bit di controllo S0 ed S1 per selezionare l’uscita Y è sufficiente effettuare l’**AND** di ogni ingresso con la configurazione di selezione corrispondente e porre tutte le Multiplexer 4-1 uscite in **OR**.
![[Screenshot 2025-08-24 alle 15.43.44.png]]

#### Utilizzo del Multplexer
Un **multiplexer (MUX)** non serve solo a selezionare quale segnale mandare in uscita tra più sorgenti, ma può anche essere utilizzato per condividere una stessa linea di trasmissione o scegliere un comando/controllo in base a un codice; inoltre, grazie alla sua struttura, con un MUX a _n_ bit è possibile implementare qualsiasi funzione booleana di _n_ variabili, semplicemente cablando i suoi ingressi a 0 o 1 a seconda della presenza dei relativi **mintermini** nella forma canonica della funzione.


### Decoder
Possiamo vederlo un po' come l'inverso del Multiplexer, dato che è caratterizzato da **N ingressi** e $2^n$ **uscite**. Ciò significa che se avremo 2 ingressi troveremo 4 uscite, se invece abbiamo 3 ingressi troveremo 8 uscite.
***Perché ho detto che può essere visto come l'inverso del multiplexer?***
Perché in uscita troveremo alto il segnale corrispondete al valore in binario degli ingressi. 
Vediamo un esempio che rende tutto più chiaro.
![[Screenshot 2025-08-24 alle 15.50.24.png]]
I segnali A sono i 2 ingressi *selettori* mentre i segnali D sono le uscite.
