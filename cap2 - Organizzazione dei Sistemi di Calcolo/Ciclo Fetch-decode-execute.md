Per eseguire ogni singola istruzione la CPU deve seguire una serie di precisi STEP l'insieme di questi è appunto chiamato **ciclo fetch decode execute**.
Vediamoli:
1. (**FETCH**) Carica l'istruzione dalla memoria al registro *istruction register* (IR).
2. Incrementa il *program counter* (PC).
3. (**DECODE**) Decodifica l'istruzione.
4. Se l'operazione usa un dato in memoria ne calcola l'indirizzo.
5. Carica l'operando in un registro (qualsiasi).
6. (**EXECUTE**) Esegue l'istruzione.
7. (**STORE**) Memorizza il risultato.
8. Siamo pronti a eseguire la prossima istruzione e torniamo allo step 1.

``Accessi alla memoria sono effettuati sempre al passo 1, e non sempre ai passi 4, 5 e 7.``

 
![[Screenshot 2025-08-17 alle 16.51.30.png]]