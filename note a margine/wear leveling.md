Il **Wear Leveling** (o livellamento dell'usura) è una **tecnica di gestione della memoria** cruciale utilizzata nei dispositivi di archiviazione basati su memorie Flash, come gli SSD (Solid State Drive).

## Cos'è il Wear Leveling e Perché Serve

Il concetto si basa su una limitazione fondamentale delle memorie Flash: la loro **durata è finita**.

1. **Il Problema dell'Usura:** Le memorie Flash non possono essere riscritte all'infinito. La loro durabilità è misurata in **cicli di Programmazione/Cancellazione (P/E cycles)**. Ad esempio, una cella di memoria MLC può sopportare solo circa 3.000 cicli P/E prima di degradarsi.

2. **Operazioni a Blocco:** Inoltre, le operazioni di cancellazione e riscrittura non avvengono a livello di singolo byte, ma su unità più grandi chiamate **blocchi**. Ogni volta che si aggiorna anche solo un piccolo dato all'interno di un blocco, si consuma un intero ciclo P/E per quel blocco specifico.

## La Soluzione del Wear Leveling

Per evitare che alcuni blocchi (quelli che contengono dati che cambiano frequentemente, come i log o le tabelle dei file system) si degradino rapidamente, rendendo inutilizzabile l'intero dispositivo, si ricorre al _wear leveling_.

Il **Wear Leveling** è la **distribuzione uniforme delle scritture sulle celle dell’unità per ridurre l’usura delle singole celle**.

In pratica, un controller interno del dispositivo, che **mantiene una mappa aggiornata dell’uso dei blocchi**, indirizza i nuovi dati in arrivo non sempre allo stesso blocco fisico, ma a un blocco diverso, meno utilizzato (un blocco "fresco"). In questo modo, l'usura dovuta alle scritture viene **spalmata sull'intera capacità** della memoria, prolungando significativamente la vita operativa del componente.