
La memoria centrale è quella che chiamiamo tipicamente RAM, è dove operano i processi e il sistema operativo stesso.
Difatti contiene sia dati che programmi.

- **Cella**: minima unità di memoria indirizzabile
- **Word**: insieme di celle consecutive (insieme K di Byte)
- **Indirizzo**: nome identificativo della cella
	- **Spazio di indirizzamento**: una volta scelto quanti bit usare per generare indirizzi abbiamo $2^m$  (*m* numero di bit) indirizzi possibili (quindi $2^m$ celle indirizzabili)

### Vari tipi di schede di memoria
- **SIMM (Single Inline Memory Module)**
  - Vecchi moduli di memoria, usati negli anni '90.  
  - Hanno **72 piedini** e un bus di **32 bit**.  
  - Poiché i processori Pentium avevano un bus a 64 bit, servivano **due moduli SIMM in coppia** per funzionare.  
  - Capacità tipica: da pochi MB fino a ~128 MB per modulo.

- **DIMM (Double Inline Memory Module)**
  - Successori dei SIMM, ancora oggi il formato standard nei PC desktop.  
  - Hanno **120 o 240 piedini** e un bus di **64 bit**, quindi **basta un solo modulo** per lavorare con CPU a 64 bit.  
  - Capacità iniziali di poche centinaia di MB, oggi fino a decine di GB per modulo.  
  - Ogni modulo è composto da più chip di memoria (es. 8 chip = 1 word per volta).

- **SO-DIMM (Small Outline DIMM)**
  - Versione compatta dei DIMM.  
  - Usata soprattutto nei **notebook**, mini-PC e dispositivi compatti.  
  - Più corta (67 mm circa) rispetto ai DIMM standard (133 mm).  

- **DDR (Double Data Rate, DDR2, DDR3, DDR4, DDR5)**
  - Tecnologia che permette di **trasferire dati sia sul fronte di salita che di discesa del clock**, raddoppiando la velocità rispetto alla SDRAM classica.  
  - Ogni nuova generazione (DDR → DDR2 → DDR3 → DDR4 → DDR5) aumenta frequenza, banda passante e riduce consumo.  
  - Introdotto anche un sistema di **pipeline** per ottimizzare lettura e scrittura.  

- **Bit di parità / ECC (Error Correction Code)**
  - Alcuni moduli hanno un **bit di parità** o un sistema **ECC**: servono per rilevare (parità) o correggere (ECC) errori di memoria.  
  - Utilizzati soprattutto nei **server** e nei sistemi critici; nei PC consumer spesso assenti.   
  - O ad esempio gli [[Algoritmi di rilevamento dell'errore- Hamming]]

## Gerarchie della memoria

Andando verso il basso:
- **Scende** la **capacità**
- **Aumenta** il **tempo** di accesso
- **Diminuisce** il **costo** per bit


![[Screenshot 2025-08-18 alle 17.46.49.png]]
**I registri sono l'unico livello a diretto contatto con la CPU**


**Esiste un forte [[Performance Gap]] tra processi e memorie creato negli anni**


## Memoria CACHE

Come possiamo vedere dallo schema delle Gerarchie della memoria prima della nostra Memoria centrale troviamo un altro stadio, la Cache, ovviamente i registri non li consideriamo neanche dato che come detto prima sono a diretto contatto con la CPU (oserei dire che ne fanno quasi parte, difatti quando si compra un processore i registri sono gia al suo interno e non è possibile cambiarli o aumentarli).

L'esistenza della cache è dovuta al fatto che **la Memoria centrale è sempre più lenta della [[CPU]]**.
La cache opera alla stessa velocità del processore in modo da compensare i ritardi della memoria centrale, contiene le ultime locazioni di memoria a cui è stato eseguito l'accesso,![[Screenshot 2025-08-18 alle 18.02.24.png]]
In questo modo quando la CPU richiede un indirizzo passa prima per la Cache, se è presente si evita un accesso alla memoria altrimenti si prosegue con il percorso *tradizionale*.

- **Cache hit** = il dato che cerchi è già nella cache → velocissimo 🚀 

- **Cache miss** = il dato non c’è nella cache → tocca prenderlo dalla memoria lenta 🐌  


Quando leggi la **stessa parola k volte di fila**:  

- Solo la prima volta vai in memoria (miss).  

- Le altre k - 1 volte la trovi in cache (hit).  

  

**Formula del cache hit ratio (quanto spesso becco il dato in cache):**  

$$

H = \frac{k-1}{k}

$$

### Tempo medio di accesso

- `m` = tempo per leggere dalla memoria (lento).  

- `c` = tempo per leggere dalla cache (veloce).  

  

Il tempo medio di accesso è:  

$$

A = c + (1 - H)m

$$

Che significa in italiano:  

- Parti dal tempo della cache `c`.  

- Aggiungi una “penalità” per le volte che non trovi il dato (`1 - H`) e devi andare in memoria (`m`).  


  
## Hard Disk
- **Dimensioni**: <10cm (1,8″, 2,5″, 3,5″), densità ~25Gb/cm.
- **Struttura**: 
  - Tracce concentriche divise in settori (dati, preambolo, spazio tra settori, ECC).
  - Velocità di rotazione: 5.400-10.800 RPM.
  - Velocità di trasferimento: 150 MB/sec.
- **Tempi**:
  - `Tseek`: 5-10ms (spostamento testine).
  - `Tlat`: 3-6ms (latenza rotazionale).
  - `Tacc = Tseek + Tlat`.

## Controller per Hard Disk
- **Tipi**: IDE, E-IDE, Serial ATA, SCSI (fino a 640 MB/sec).
- **Evoluzione**:
  - IDE: limite 504 MB, 4MB/sec.
  - E-IDE: LBA a 28 bit (128GB), 17MB/sec.
  - ATA-3/ATAPI-5/6: fino a 100MB/sec, LBA a 48 bit (128PB).
  - SATA: >500MB/sec, tensioni più basse.

## RAID (Redundant Array of Inexpensive Disks)
- **Obiettivi**: Parallelismo, ridondanza, resistenza ai guasti.
- **Livelli**:
  - **RAID 0**: Striping senza ridondanza (migliora velocità, peggiora MTBF).
  - **RAID 1**: Mirroring (duplicazione dati, ottimo per lettura e fault tolerance).
  - **RAID 2/3**: Striping a bit/byte con parità (sincronizzazione dischi, overhead elevato).
  - **RAID 4/5**: Striping a blocchi con parità distribuita (RAID 5 elimina collo di bottiglia del disco di parità).

## Dischi Ottici
- **Struttura**:
  - CD/CD-ROM: traccia a spirale con pit/land, blocchi da 2KB.
  - CD-R: strati di lacca, oro, dye, policarbonato.
  - DVD: doppio lato/doppio strato con semiriflettenti.
- **Tecnologia**: Laser a infrarossi per lettura/scrittura.

## SSD (Solid State Drive)
- **Tecnologia**: Hot-carrier injection (stato transistor fisso).
- **Vantaggi**: 
  - Tempi di accesso nulli (`tseek = 0`), >200MB/sec.
  - Adatti a dispositivi mobili.
- **Svantaggi**: 
  - Costo elevato (~1€/GB vs 1 cent/GB HDD).
  - MTBF limitato (~100.000 cicli di scrittura).

**Prossimo argomento —————————>>** [[Schede IO]]