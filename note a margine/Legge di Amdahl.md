
La Legge di Amdahl permette di determinare i potenziali guadagni in termini di prestazioni ottenuti dall’aggiunta di ulteriori core, nel caso di applicazioni che contengano si componenti seriali (quindi non parallelizzabili) sia componenti parallele.

$$
         \textit{speedup} \leq \frac{1}{\textit{S} +\frac{1-\textit{S}}{\textit{N}}} $$
![[LeggeAmdahl copia.png]]

L'immagine illustra la Legge di Amdahl, che descrive il limite massimo di accelerazione ottenibile aumentando il numero di processori per un dato task. I grafici mostrano come il **speedup** (accelerazione del calcolo) cresce con il numero di processori per diverse percentuali di codice parallelizzabile (50%, 75%, 90%, 95%). Si nota che, anche con un elevata *parallelizzabilità*, il guadagno tende ad assestarsi, evidenziando che oltre un certo punto aggiungere più processori non porta benefici significativi. Questo principio è fondamentale nella progettazione di sistemi paralleli e nell'ottimizzazione delle prestazioni computazionali.