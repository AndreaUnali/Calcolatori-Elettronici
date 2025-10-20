
## Introduzione
È il componente che si occupa di eseguire le operazioni aritmetiche all'interno del nostro calcolatore.
Per essere tale ha bisogno dei seguenti requisiti:
1. **Registri** : per conservare gli operandi e risultati parziali 
2. **Bit di controllo** : per indicare il tipo di operazione voluta
3. **MUX** : per interpretare i bit di controllo
4. **Rete combinatoria**  : per effettuare le operazioni

![[Screenshot 2025-09-01 alle 18.25.01.png#invert]]

È inoltre indispensabile avere un blocco in grado di eseguire [[Aritmetica in virgola Mobile|operazioni in virgola Mobile]], una **Floating Poin Unit**. (è possibile vedere come è fatta dalla pagina sopra linkata).

## Sommatori di un modulo ALU

Il tipo di sommatore più elementare è l'**Half-Adder**, 
``Dati 2 bit in ingresso restituisce la loro somma e l'eventuale riporto``

![[Screenshot 2025-09-11 alle 11.02.45.png#invert]]


- **Ingressi** : 2 bit (i 2 operandi da sommare)
- **Uscite** : 2 bit (somma dei due operandi e eventuale riporto)
- **Somma**: Ottenuta mediante XOR dei due ingressi (A-B)
- **Riporto**: Ottenuto mediante AND dei due ingressi (A-B) 

Il passo subito successivo a livello di implementazione per i sommatori è il **Full-Adder**
``Dati 3 bit in ingresso (operandi sa sommare e eventuale riporto) restituisce la somma degli operandi e un eventuale riporto.``
![[Screenshot 2025-09-11 alle 11.09.51.png#invert]]
Come possiamo vedere dall'immagine è sostanzialmente composto da 2 Half-Adder, il primo (da sinistra) esegua la somma dei due operandi in ingresso e restituisce somma (per adesso parziale) e riporto. 
Il secondo somma il risultato del primo Half-Adder e l'eventuale riporto in ingresso (derivante da operazioni precedenti), da qua escono la somma totale in uscita e l'eventuale riporto.

Notare che i due riporti vengono poi messi in OR, questo perchè basta uno dei due Half adder abbia overflow per generare un riporto. Sopratutto teniamo a mente che per la natura dello XOR non potremmo avere riporto in entrambi gli Half-Adder.

## ALU a 1 Bit

![[Screenshot 2025-09-11 alle 11.17.02.png#invert]]

Questa rappresenta il blocco fondamentale per costruire ALU più complesse a 32 o 64 bit.
### 1. Unità Logica (in alto a sinistra)

- **Funzione**: Esegue operazioni logiche tra i bit A e B
- **Operazioni disponibili**:
    - AND (A ∧ B)
    - OR (A + B)
    - NOT B (¬B)
- **Controllo**: Le linee INVA, A, ENA, B, ENB determinano quale operazione viene eseguita

### 2. Decodificatore (in basso a sinistra - area blu)

- **Funzione**: Interpreta i segnali di controllo F₀ e F₁
- **Scopo**: Determina quale operazione deve essere eseguita dalla ALU
- **Output**: Genera i segnali per abilitare le diverse unità funzionali

### 3. Sommatore Full-Adder (in basso a destra - area gialla)

- **Funzione**: Esegue operazioni aritmetiche (addizione/sottrazione)
- **Componenti**: Circuito di somma completo con riporto in ingresso e in uscita
- **Riporti**:
    - **Riporto in ingresso**: Collegato al bit precedente
    - **Riporto in uscita**: Collegato al bit successivo

### 4. Multiplexer di Output

- **Funzione**: Seleziona quale risultato inviare in output
- **Scelta**: Tra il risultato dell'unità logica o del sommatore
- **Controllo**: Basato sui segnali del decodificatore

### Linee di Abilitazione

Le **linee di abilitazione** collegano il decodificatore alle varie unità, permettendo di:

- Attivare/disattivare specifiche operazioni
- Controllare il flusso dei dati attraverso il circuito
- Coordinare il funzionamento delle diverse unità

### Funzionamento

1. I bit A e B vengono inseriti come input
2. I segnali F₀ e F₁ specificano l'operazione da eseguire
3. Il decodificatore attiva l'unità appropriata (logica o aritmetica)
4. Il risultato viene selezionato e inviato all'output
5. Il riporto viene gestito per operazioni multi-bit

Questa struttura modulare permette di collegare più ALU a 1 bit in serie per creare processori capaci di operare su numeri di dimensioni maggiori.


## ALU a N Bit

![[Screenshot 2025-09-11 alle 11.23.30.png#invert]]

Per ottenere ALU a N Bit ci basterà mettere in sequenza tante ALU a 1 Bit.
Passando da una all'altra gli eventuali riporti delle operazioni.

- [!]  Ciò significa che ogni stadio deve aspettare che lo stadio precedente termini l'operazione e gli fornisca il riporto prima di poter eseguire le sue.
- [d] Generando un ritardo in base al numero di bit della ALU. Un ritardo che cresce al crescere di n (*O(n)*) terribile per un modulo Hardware 

- [p] La soluzione è inserire delle **Ottimizzazioni nei sommatori**

## Ottimizzazioni nei Sommatori


### Carry Look-Ahead Adder (CLA) 
- [!]    Problema del **Parallel Adder (Ripple Carry Adder)**: il tempo di somma cresce linearmente con il numero di bit `n`, poiché ogni stadio deve attendere il riporto dal precedente.
- [I] **Soluzione**: calcolare i riporti in **parallelo** usando le relazioni tra bit di ingresso.

#### Definizioni
- **gᵢ (generate):** `Aᵢ · Bᵢ` → il bit genera sempre un riporto.
- **pᵢ (propagate):** `Aᵢ ⊕ Bᵢ` → il riporto viene propagato.
- Formula ricorsiva del riporto:
  - `Cᵢ₊₁ = gᵢ + (pᵢ · Cᵢ)`

#### Vantaggi
- I riporti non dipendono più dalla propagazione sequenziale ma vengono calcolati da una **rete combinatoria**.
- Ritardo complessivo = ritardo della rete CLA + singolo Full Adder.
- Svantaggio: **circuito più complesso** all’aumentare dei bit.

---

### Carry Save Adder (CSA) 
- Utilizzato quando si devono sommare **più di due operandi**.
- Idea: evitare la propagazione dei riporti a ogni somma parziale.
![[Screenshot 2025-09-11 alle 11.58.49.png#invert]]
#### Principio
- Dati 3 addendi X, Y, Z:
  - La somma produce due uscite:
    - **pre-somma (S*)**: somma parziale senza riporti.
    - **pre-riporto (C*)**: riporti generati, shiftati di un bit a sinistra.
  - La somma finale è `S = S* + (C* << 1)`.

#### Caratteristiche
- Ogni CSA è formato da `n` **Full Adder in parallelo**, ciascuno con 3 ingressi.
- Il risultato finale si ottiene con un **Parallel Adder** solo all’ultimo stadio.
- Vantaggio: riduzione del ritardo complessivo (nessuna attesa del riporto in cascata).
- Svantaggio: non riduce il ritardo se gli operandi sono meno di tre.

---

### Confronto rapido
| Sommatore              | Caratteristica principale                                      | Vantaggio                                        | Svantaggio                              |
| ---------------------- | -------------------------------------------------------------- | ------------------------------------------------ | --------------------------------------- |
| Ripple Carry Adder     | Propagazione sequenziale del riporto                           | Circuito semplice                                | Ritardo proporzionale a `n`             |
| Carry Look-Ahead Adder | Calcolo dei riporti in parallelo                               | Molto più veloce                                 | Circuito complesso                      |
| Carry Save Adder       | Somma di più operandi senza propagazione immediata dei riporti | Ideale per moltiplicazioni e operazioni multiple | Serve comunque un Parallel Adder finale |
