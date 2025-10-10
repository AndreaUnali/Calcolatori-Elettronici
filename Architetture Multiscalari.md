In questo tipo di Architetture abbiamo più processori o piu computer che lavorano in maniera indipendente.
- **CPU multiple**: memoria condivisa
- **Computer multipli**: memoria separata. 


## CPU multiple
Anche in questo caso abbiamo diversi paradigmi applicabili. Il problema principale in questo caso è la gestione della memoria (in realtà anche la gestione dei thread ma non lo vediamo)
- **Memoria condivisa**: Tutte le CPU lavorano nello stesso spazio di memoria, il *BUS fa da collo di bottiglia*.
- **Memoria locale(+ condivisa)**: non ho più il problema del BUS ma la memoria è a 2 livelli quindi *aumenta l'overhead generale*.