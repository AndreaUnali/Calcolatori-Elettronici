In questo capitolo 6 andremo a studiare [[Reti logiche sequenziali]] note.
## Dispositivi a 3 Stati (tri-state-Buffer)

È un dispositivo di controllo usato per la connessione al BUS e in generale per tutte le comunicazioni Bidirezionali. 
Ha un segnale in input che rappresenta il dato e un secondo segnale in input che rappresenta invece il segnale di controllo. In base al segnale di controllo permette o meno il passaggio del dato.![[Screenshot 2025-09-12 alle 11.40.33.png]]

## Chip di Memoria
Un **chip di memoria** è visto come una **matrice di celle** organizzate in **righe e colonne**.
Per selezionare l'operazione da eseguire e le celle interessate usiamo 3 **segnali di controllo**:

1. **CS (Chip Select)** → abilita/disabilita il chip.
2. **OE (Output Enable)** → abilita l’uscita dei dati.
3. **WE (Write Enable)** → stabilisce se scrivere o leggere.

![[Screenshot 2025-09-12 alle 11.46.31.png]]

Nelle **memorie dinamiche (DRAM)**, per ridurre il numero di piedini, l’indirizzo viene fornito in due parti:

- **RAS (Row Address Strobe)** → seleziona la riga.

- **CAS (Column Address Strobe)** → seleziona la colonna.

In questo modo con **n linee di indirizzo** si possono indirizzare **2ⁿ celle**, ma usando RAS/CAS lo stesso bus indirizzi può essere sfruttato due volte (prima per la riga, poi per la colonna), riducendo i pin necessari.

## Banchi di memoria

Se vogliamo ottenere memorie più grandi sarà necessario avere **più chip in parallelo**, formando così un **banco di memoria**.
Ogni chip fornisce solo **una parte della parola**:
- ["]  Es. se un chip è largo **1 bit**, servono **n chip in parallelo** per memorizzare una parola di _n_ bit.

==Gli **indirizzi** sono condivisi da tutti i chip del banco → in questo modo la stessa posizione viene selezionata in ogni chip.==
![[Screenshot 2025-09-12 alle 11.57.39.png]]

I **segnali di controllo** possono invece essere sia **unificati** (in modo da attivare tutti i chip insieme), o **differenziati** (in modo da dividere il banco di memoria in più blocchi)


Con più chip si possono realizzare:
- **Memorie più larghe** (aumentando i bit per parola).
	
- **Memorie più grandi** (aumentando il numero di parole).
