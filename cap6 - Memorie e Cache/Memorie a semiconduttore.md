

|              ==Tipo di Memoria==              |         ==Categoria==         |        ==Cancellabilità==        | ==Meccanismo di scrittura== | ==Permanenza dei Dati== |
| :---------------------------------------: | :-----------------------: | :--------------------------: | :---------------------: | :-----------------: |
|     **RAM**<br>(Random acces memory)      |   <br>Scrittura/lettura   |  Elettrica, Livello di Byte  |      <br>Elettrico      |    <br>Volatile     |
|       **ROM**<br>(Read only memory)       |     <br>Sola Lettura      |      <br>Non Possibile       |      <br>Maschere       |  <br>Non Volatile   |
|      **PROM**<br>(Programmable ROM)       |     <br>Sola Lettura      |      <br>Non Possibile       |      <br>Elettrico      |  <br>Non Volatile   |
|       **EPROM**<br>(Eresable PROM)        | Principalmente di Lettura |    Luce UV, livello CHIP     |        Elettrico        |    Non Volatile     |
|              *memoria flash*              | Principalmente di Lettura | Elettrica, livello di Blocco |        Elettrico        |    Non Volatile     |
| **EEPROM**<br>(Eletrically Eresable PROM) | Principalmente di Lettura |  Elettrica, Livello di Byte  |        Elettrico        |    Non Volatile     |


## RAM (Random access Memory)

Quando parliamo della `memoria del computer` ci riferiamo spesso alla sua memoria RAM, ai nostri giorni i computer hanno dai 4GB (a partire da una fascia bassa) fino a 64 al massimo 128 GB per quelli di fascia alta.  Specifichiamo però che non abbiamo un limite massimo da rispettare, con i soldi e lo spazio (in particolare spazio all'interno dell'hardware) è possibile aumentare di molto questi numeri.

La **RAM** è una *memoria volatile*, significa che una volta terminato il suo compito non conserva i dati al suo interno. A compenso di ciò però è molto veloce, la sua velocità è fondamentale per le prestazioni del sistema.

- La lettura e la scrittura avvengo mediante segnali elettrici.

### DRAM (RAM Dinamica)

I dati sono memorizzati tramite l’iniezione di cariche elettriche; la lettura avviene rilevando la presenza di cariche.

- Richiede un’operazione periodica di ripristino delle cariche (*refresh*)

### SRAM (RAM Statica)

È realizzata mediante Flip Flop tradizionali, per questo è più costosa della DRAM. Ma a suo vantaggio ha che mantiene il contenuto al suo interno fino a che viene alimentata.

## ROM (read only memory)

La memoria ROM è quella che rappresenta lo spazio di archiviazione del nostro sistema, nasce come una memoria in **sola lettura**, **non riscrivibile** e ha come grosso vantaggio che i contenuti al suo interno sono persistenti (rimangono invariati nel tempo).

- [p] **Vantaggi**: 
	- I dati contenuti nella ROM sono reperibili direttamente nello spazio di indirizzamento della memoria principale

- [c] **Svantaggi**:
	-  Costo fisso elevato per la fabbricazione di ogni chip. La scrittura avviene tramite maschere litografiche. 
	- Non sono ammessi errori, altrimenti la ROM è da cambiare


### PROM (Programable ROM)

È una ROM riprogrammabile (riscrivibile) anche in fasi successive alla fabbricazione, nonostante ciò rimane di tipo **non volatile**. È più flessibile di una normale ROM ma per essere scritta necessita di Hardware dedicati (*programmatore di ROM*).

La cancellazione può avvenire solo dopo la cancellazione della memoria
- [!]  diversi tipi di PROM possono avere modalità diverse di cancellazione. (quindi immagino anche parziali) 

## Memorie Read Mostly

Sono sempre memorie **non volatili riprogrammabili** ma con un importante squilibro nell'utilizzo verso la lettura
### EPROM (Erasable PROM)

È una PROM cancellabile.
Ad ogni scrittura si devono riportare tutte le celle allo stato iniziale mediante esposizione a raggi ultravioletti. Ogni cancellazione dura circa 20 min.



![[Screenshot 2025-09-15 alle 11.54.07.png#invert]]

### EEPROM
Le **EEPROM** (Electrically Erasable Programmable Read-Only Memory) sono memorie non volatili che mantengono i dati anche senza alimentazione. Si possono cancellare e riscrivere elettricamente, byte per byte, a differenza delle EPROM che richiedono luce UV. Sono usate per memorizzare dati persistenti come configurazioni o firmware.


### Memorie Flash

- Sono memorie **non volatili** a semiconduttore (mantengono i dati senza alimentazione).  
- Derivano dalle **EEPROM**, ma sono più veloci e convenienti.  
- Ampiamente usate in sistemi embedded, memorie di massa (SSD, USB, schede SD).  
- Organizzata a blocchi
![[Screenshot 2025-09-15 alle 11.58.10.png#invert]]
---

#### Caratteristiche principali
- **Lettura:** veloce (simile a DRAM), posso indirizzare o interi blocchi o una specifica riga di un blocco.  
- **Scrittura:** più lenta, richiede la cancellazione preventiva di un intero **blocco**.  
- **Cancellazione:** avviene per blocchi (molto più grande della singola cella → limite rispetto alle EEPROM).  
- **Durata:** numero limitato di *cicli di scrittura/cancellazione*, possiamo trovarlo anche come "cicli di P/E" (usura delle celle).  

---

#### Tipi di Flash
- **NOR Flash**
  - Accesso diretto a livello di byte.  
  - Maggiore velocità in lettura → usata per codice eseguibile (firmware).  
  - Più costosa e meno densa.  

- **NAND Flash**
  - Organizzata a blocchi, con accesso sequenziale.  
  - Maggiore densità, più economica.  
  - Usata per archiviazione di massa (SSD, penne USB, SD card).  

---
#### Ciclo di vita delle memorie Flash
A differenza di altre memorie (come le EEPROM, che possono essere aggiornate a livello di byte), nelle memorie flash:

   - La *cancellazione avviene tramite segnali elettrici*.
   
   - Non è possibile aggiornare solo una parte della memoria a livello di byte o word. L'aggiornamento deve avvenire a un livello superiore (blocco o pagina).
   
   - L'operazione di scrittura è **molto più veloce** rispetto a una EPROM

• **Operazioni su Blocco (Block-Based):** Nelle memorie flash, la cancellazione (erase) è tipicamente un'operazione su **blocco**. Sebbene il contenuto possa essere aggiornato solo in parte, non si può scendere al livello del byte o della word. Per aggiornare un dato, è spesso necessario cancellare l'intero blocco prima di riscrivere le pagine aggiornate (questo è implicito nel modello Flash, che limita gli aggiornamenti a parti più grandi di un byte o una word).

• **Operazioni su Pagina (Page-Based):** La **pagina** rappresenta l'unità logica più piccola per l'operazione di programmazione (scrittura). Dopo che un blocco è stato cancellato, la scrittura (o "programmazione") può avvenire a livello di pagina.

L'influenza della scelta tra operazioni **page-based** e **block-based** sulla vita della memoria (durabilità) è **critica** e deriva dal meccanismo fisico di cancellazione delle memorie Flash:

1. **Unità Operative:** Nelle memorie Flash, l'unità logica più piccola per la scrittura (programmazione) è la **pagina** (page-based), ma la cancellazione (_erase_) deve avvenire sull'unità più grande, il **blocco** (block-based). Ogni blocco è suddiviso in N pagine.

2. **Consumo del Ciclo di Vita:** La durabilità è misurata in **cicli di Programmazione/Cancellazione (P/E cycles)**, dove un ciclo è consumato ogni volta che un blocco viene cancellato e riscritto.

3. **L'Impatto:** Poiché non è possibile aggiornare i dati a un livello granulare (byte o word), anche se un utente modifica solo un dato all'interno di una singola pagina, il dispositivo deve cancellare l'intero **blocco** che contiene quella pagina prima di poter riscrivere la pagina aggiornata (programmazione). Questo fa sì che **ogni piccolo aggiornamento consumi un intero ciclo P/E del blocco**.

4. **Dipendenza:** Pertanto, la **durata del componente dipende direttamente dalla dimensione del blocco di lettura/scrittura**. Più grande è il blocco, e più piccola è la modifica richiesta, meno efficiente è l'operazione in termini di usura, costringendo il sistema a implementare il **[[wear leveling]]** (distribuzione uniforme delle scritture) per prolungare la vita della memoria.

---
#### Prestazioni
- Tempo di accesso in lettura: **10–50 ns**.  
- Tempo di scrittura: **200–500 µs** (molto più lento).  
- Tempo di cancellazione blocco: anche **millisecondi**.  

---

#### Utilizzi
- **NOR Flash:** memorizzazione di programmi, BIOS, firmware.  
- **NAND Flash:** archiviazione dati (SSD, telefoni, fotocamere, dispositivi portatili).  

