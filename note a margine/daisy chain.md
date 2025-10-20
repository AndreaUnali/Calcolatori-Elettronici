 È una configurazione in cui più dispositivi sono collegati in **serie lungo la stessa linea di comunicazione**. In pratica, ogni dispositivo è connesso al successivo, formando una catena in cui i segnali del bus passano da un’unità all’altra. Questo metodo consente di **ridurre il cablaggio** e **semplificare la connessione** di più periferiche, ma presenta anche alcuni svantaggi: un guasto in un dispositivo o in un collegamento può interrompere la comunicazione per tutta la catena, e la **latenza** può aumentare con il numero di dispositivi collegati.

Grazie al daisy chain implementiamo le priorità all'interno del BUS, posizionando i moduli in ordine il modulo di priorità *n* non trasmette il segnale al dispositivo con priorità *n+1* (priorità più bassa) se vuole prendere controllo del BUS o fare richieste.

![[Screenshot 2025-08-19 alle 17.35.59.png#invert]]
