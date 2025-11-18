
## Operazioni fondamentali 
- **Addizione/Sottrazione** si eseguono in 4 passi:
  1. Controllo se uno dei due operandi è nullo.
  2. **Allineamento delle mantisse** (correggendo gli esponenti).
  3. Esecuzione dell’operazione sulle mantisse.
  4. **Normalizzazione** del risultato (se necessario incrementando l’esponente).

- **Moltiplicazione/Divisione**:
  - Sono più semplici: agiscono separatamente su esponenti e mantisse.
  - Esponenti → somma o differenza.
  - Mantisse → moltiplicazione o divisione.

### Esempio di somma Floating Point 
- Dati due numeri FP, se gli esponenti sono diversi si porta il più piccolo al valore del maggiore.
- Le mantisse vengono sommate (includendo il bit implicito).
- Se c’è un **riporto finale**, si incrementa l’esponente e si normalizza la mantissa.

---

## Floating Point Unit (FPU) 
- **Funzione:** eseguire operazioni su numeri in virgola mobile.
- **Struttura:** composta da due unità aritmetiche in virgola fissa:
  - Una per la **mantissa** (somma, sottrazione, moltiplicazione, divisione).
  - Una per l’**esponente** (solo somma algebrica e confronto).
- Il confronto degli esponenti può essere fatto tramite **sottrazione**.
- Per la somma FP:  
  - Si calcola la differenza degli esponenti.  
  - Il numero con esponente minore viene shiftato a destra sulla mantissa.  
  - Un contatore decrementa fino ad annullare la differenza.  
  - Poi si procede all’operazione sulla mantissa.

---

# Tabella riassuntiva

| Operazione          | Passi principali                                                                                                                                               | Note                                                                  |
| ------------------- | -------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------- |
| **Addizione**       | 1. Confronto esponenti<br>2. Allineamento mantisse (shift della più piccola)<br>3. Somma delle mantisse<br>4. Normalizzazione (eventuale incremento esponente) | Operazione più complessa per la necessità di allineare e normalizzare |
| **Sottrazione**     | Stessi passi dell’addizione, ma operazione di differenza tra mantisse                                                                                          | Richiede attenzione ai segni degli operandi                           |
| **Moltiplicazione** | 1. Somma degli esponenti<br>2. Moltiplicazione delle mantisse<br>3. Normalizzazione                                                                            | Più semplice: esponenti e mantisse trattati separatamente             |
| **Divisione**       | 1. Differenza degli esponenti<br>2. Divisione delle mantisse<br>3. Normalizzazione                                                                             | Analogamente più semplice rispetto ad addizione/sottrazione           |