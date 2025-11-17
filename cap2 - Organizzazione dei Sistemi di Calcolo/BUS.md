Il BUS è una struttura di interconnessione basata sulla condivisione, è composto da **Linee** che collegano 2 o più moduli/dispositivi.

``importante dire LINEE, non sono fili o cavi ne collegamenti magici, sono linee stampate su circuito (se proprio non ti piace linee puoi dire Piste)``

Solo un dispositivo alla volta può essere abilitato a usare il BUS, riguardo ciò abbiamo 2 tipi di trasmissioni a BUS:
- Trasmissioni a Bus Seriali
- Trasmissioni a Bus parallele
!!(dopo vediamo la diferenza)!!

In un moderno calcolatore coesistiono più BUS ma quello figo che si occupa di collegare  i moduli più fohrty ([[CPU]], [[Memorie]],[[Schede IO||Moduli Input Output]] ) si chiama **BUS di Sistema** o se vuoi fare il togo in inglese *System BUS*


In un moderno calcolatore abbiamo:
- **BUS interni**: sono confinati all'interno di un singolo modulo 
- **BUS Esterni**: collegano più moduli


``è ovvio che questa definizione lascia il tempo che trova dato che è molto dipendente dalla definizione di "singolo mudulo", le memorie sono un singolo modulo? anche se composte fisicamente da blocchi diversi? e i bus che collegano le memorie come li consideriamo? non facciamoci troppe seghe mentali e cerchiamo di capire quando stiamo parlando di BUS interni / esterni in base al contesto ``
Vedremo un approfondimento nella nota [[BUS - Approfondimento|BUS - Approfondimento]]

**Come si valutano le prestazioni di un BUS?**
1. Velocità di trasferimento
2. Numero di bit (la larghezza del BUS)

Inoltre sono estremamente dipendenti dal tipo di circuiteria di controllo (generalmente basati sul [[Introduzione alle Memorie|tri-state buffer]])

## Schema Logico di Un BUS

Abbiamo appena descritto il BUS come un insieme di piste, vediamo ora che diverse piste possono essere di tipi diversi in base al tipo di dato che trasmettono.
![[Screenshot 2025-08-17 alle 14.39.43.png#invert]]
Come è possibile vedere nell'immagine un singolo BUS può essere composto da 3 linee principali o sotto-BUS:

### Control BUS:
Si occupa di trasmettere bit di controllo come 
- lo stato di una risorsa (read/write)
- il segnale di clock
- richieste di Interrupt
### Address Bus:
Ci dice la sorgente e la destinazione del dato trasmesso.
La sua ampiezza determina lo spazio di memoria indirizzabile esplicitamente.
- ad esempio con un address BUS di 16 bit sarà possibile indirizzare 64K spazi di memoria, 2^16
### Data BUS:
La linea che si occupa di trasmettere dati o istruzioni, può essere di diverse ampiezze, ad esempio:
- 8 bit
- 16 bit
- 32 bit
- 64 bit


## Tecnologie per un BUS esterni

%% Questa è una nota un po' a margine sui bus esterni. %%


La maggior parte dei **BUS esterni** è realizzata tramite collegamenti elettrici: 
- schede di BUS, con piste di collegamento e connettori montati sulla scheda. 
- cavi elettrici flessibili con connettori.
- Alcuni BUS, ad altissime prestazioni, sono realizzati in fibra ottica (FiberChannel). 
- Alcuni BUS si basano su etere (onde radio,BlueTooth).

**Prossimo Argomento —————————>>** [[CPU]]
