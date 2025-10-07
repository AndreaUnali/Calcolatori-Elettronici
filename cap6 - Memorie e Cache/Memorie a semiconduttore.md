

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

La **RAM** è una memoria volatile, significa che una volta terminato il suo compito non conserva i dati al suo interno. A compenso di ciò però è molto veloce, la sua velocità è fondamentale per le prestazioni del sistema.

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



![[Screenshot 2025-09-15 alle 11.54.07.png]]

### EEPROM
Le **EEPROM** (Electrically Erasable Programmable Read-Only Memory) sono memorie non volatili che mantengono i dati anche senza alimentazione. Si possono cancellare e riscrivere elettricamente, byte per byte, a differenza delle EPROM che richiedono luce UV. Sono usate per memorizzare dati persistenti come configurazioni o firmware.


### Memorie Flash

- Sono memorie **non volatili** a semiconduttore (mantengono i dati senza alimentazione).  
- Derivano dalle **EEPROM**, ma sono più veloci e convenienti.  
- Ampiamente usate in sistemi embedded, memorie di massa (SSD, USB, schede SD).  
![[Screenshot 2025-09-15 alle 11.58.10.png]]
---

#### Caratteristiche principali
- **Lettura:** veloce (simile a DRAM).  
- **Scrittura:** più lenta, richiede la cancellazione preventiva di un intero **blocco**.  
- **Cancellazione:** avviene per blocchi (molto più grande della singola cella → limite rispetto alle EEPROM).  
- **Durata:** numero limitato di cicli di scrittura/cancellazione (usura delle celle).  

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

#### Prestazioni
- Tempo di accesso in lettura: **10–50 ns**.  
- Tempo di scrittura: **200–500 µs** (molto più lento).  
- Tempo di cancellazione blocco: anche **millisecondi**.  

---

#### Utilizzi
- **NOR Flash:** memorizzazione di programmi, BIOS, firmware.  
- **NAND Flash:** archiviazione dati (SSD, telefoni, fotocamere, dispositivi portatili).  
