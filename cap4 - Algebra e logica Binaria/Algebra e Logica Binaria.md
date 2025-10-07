
## 1. Sistemi Numerici

### Definizione

Un sistema numerico è definito da:

- Un insieme di simboli (cifre)

- Un insieme di regole per costruire i numeri

I sistemi possono essere **posizionali** o **non posizionali** (come il sistema romano).

  

### Formula Generale dei Sistemi Posizionali

```

V(n) = Σ(i=-m to n-1) di × r^i

```

Dove:

- `di` è il simbolo in posizione i-esima

- `r` è la base del sistema

- `m` = numero di cifre della parte frazionaria

- `n` = numero di cifre della parte intera

- `0 ≤ di < r`

  

### Principali Sistemi Numerici

- **Sistema binario**: `di = 0,1`, `r = 2`

- **Sistema ottale**: `di = 0,1,2,3,4,5,6,7`, `r = 8`

- **Sistema esadecimale**: `di = 0,1,2,3,4,5,6,7,8,9,A,B,C,D,E,F`, `r = 16`

  

## 2. Alfabeto Binario

  

### Terminologia Base

- **BIT** (binary digit): una cifra binaria (0 o 1)

- **BYTE**: insieme di 8 bit

- **WORD** (parola): insieme di più byte

- Un numero binario è una **sequenza di bit**

  

## 3. Rappresentazione di Numeri con Segno

  

Per rappresentare interi relativi con n bit, si dimezza l'intervallo dei valori assoluti. Esistono diverse rappresentazioni:

  

### 3.1 Modulo e Segno

- 1 bit per il segno (0: positivo, 1: negativo)

- n-1 bit per il modulo

- Intervallo: `[-(2^(n-1) - 1), +(2^(n-1) - 1)]`

- **Svantaggio**: doppia rappresentazione dello zero

  

### 3.2 Complemento a 1

- Numeri positivi: rappresentazione posizionale normale

- Numeri negativi: complemento bit a bit del corrispondente positivo

- Positivi iniziano per 0, negativi per 1

- Intervallo: `[-(2^(n-1) - 1), +(2^(n-1) - 1)]`

- **Svantaggio**: doppia rappresentazione dello zero

  

### 3.3 Complemento a 2

- Numeri positivi: stessa rappresentazione del complemento a 1

- Numeri negativi: complemento a 1 + 1

- **Metodo pratico**: da destra, lasciare invariati tutti i bit fino al primo 1 compreso, poi complementare

- Intervallo: `[-2^(n-1), +2^(n-1) - 1]`

- **Vantaggi**: intervallo più esteso, una sola rappresentazione dello zero

  

### 3.4 Eccesso 2^(n-1)

- I numeri sono rappresentati come somma tra il numero dato e 2^(n-1)

- Positivi iniziano per 1, negativi per 0

- Si ottiene da CP2 complementando il bit più significativo

- Intervallo: `[-2^(n-1), +2^(n-1) - 1]`

  

## 4. Rappresentazione in Virgola Mobile (IEEE 754)

  

### Standard IEEE 754 (1985)

  

#### Singola Precisione (32 bit)

```

S | WWWWWWWW | YYYYYYYYYYYYYYYYYYYYYYY

1 8 bit 23 bit

```

- **S**: segno (1 bit)

- **W**: esponente (8 bit)

- **Y**: mantissa/significando (23 bit)

  

#### Doppia Precisione (64 bit)

- 1 bit segno + 11 bit esponente + 52 bit mantissa

  

### Numeri Normalizzati

- Esponente rappresentato in **eccesso 127** (singola precisione)

- Range esponente: -126 ≤ e ≤ 127

- Mantissa: solo parte frazionaria (bit 1 prima della virgola è implicito)

- Condizione: `1 ≤ m < 2`

- Intervallo: `[2^(-126), ~2^128]`

  

### Casi Speciali

- **Zero**: mantissa ed esponente tutti 0

- **Overflow**: mantissa tutti 0, esponente tutti 1

- **Not a Number (NaN)**: mantissa ≠ 0, esponente tutti 1

- **Numero denormalizzato**: mantissa ≠ 0, esponente tutti 0

  

### Numeri Denormalizzati

- Gestiscono situazioni di **underflow**

- Esponente = 0, bit implicito = 0

- Intervallo: `[2^(-149), ~2^(-126)]` (singola precisione)

  

### Operazioni in Virgola Mobile

Per la **moltiplicazione**:

1. Moltiplicare le mantisse

2. Sommare algebricamente gli esponenti

3. Normalizzare la mantissa se necessario

4. Riaggiustare l'esponente

  

### Errori di Rappresentazione

- **Errore assoluto**: `eA = n - n'`

- **Errore relativo**: `eR = eA / n = (n - n') / n`

- Con mantissa normalizzata, l'errore relativo massimo è costante

- La **densità** dei numeri rappresentabili non è uniforme (maggiore vicino all'origine)

  

## 5. Algebra Booleana

  

### Definizione (George Boole, 1854)

Sistema algebrico definito da:

1. Variabili binarie (true/false, 1/0)

2. Operatori logici

3. Tabelle di verità

4. Relazione di equivalenza "=" tra espressioni

  

### Operatori Logici di Base

  

#### Operatori Fondamentali

- **AND**: `P • Q` (vale 1 quando entrambi gli operandi sono 1)

- **OR**: `P + Q` (vale 1 quando almeno un operando è 1)

- **NOT**: `P̄` o `P'` (inverte il valore dell'operando)

  

#### Operatori Aggiuntivi

- **XOR**: `P ⊕ Q` (vale 1 quando gli operandi sono diversi)

- **NAND**: `P̄•Q̄` = `P̄ + Q̄` (complemento dell'AND)

- **NOR**: `P̄+Q̄` = `P̄ • Q̄` (complemento dell'OR)

  

### Espressioni Booleane

- **Letterale**: ogni presenza di una variabile (diretta o negata)

- **Livelli**: numero di operatori che agiscono in cascata

- Due espressioni sono **equivalenti** se assumono lo stesso valore per ogni assegnazione delle variabili

  

### Forme Canoniche

  

#### Somma di Prodotti (SoP)

- Configurazioni che producono uscita = 1 sono chiamate **mintermini**

- Esempio: `F = A'BC' + A'BC + ABC'`

  

#### Prodotto di Somme (PoS)

- Configurazioni che producono uscita = 0 sono chiamate **maxtermini**

- Esempio: `F = (A + B) • (A + B') • (A' + B)`

  

Si passa da una forma all'altra applicando il **teorema di De Morgan**.

  

### Completezza Funzionale

- **AND, OR, NOT** sono sufficienti per rappresentare tutte le funzioni booleane

- Anche **solo NAND** è sufficiente (o solo NOR)

- Per De Morgan: `A • B = Ā + B̄` e `A + B = Ā • B̄`

  

## 6. Porte Logiche e Reti Combinatorie

  

### Porte Logiche

- Circuiti elettronici che implementano operatori booleani

- Ingressi e uscite sono segnali elettrici digitali binari

- Realizzate tramite **transistor**

- Più facile realizzare porte NAND e NOR che AND e OR

  

### Reti Logiche

Caratterizzate da:

- n variabili di ingresso

- m variabili di uscita

  

#### Tipologie

- **[[Reti logiche combinatorie|Reti Combinatorie]]**: senza memoria, uscita dipende solo dagli ingressi attuali

- **[[Reti logiche sequenziali|Reti Sequenziali]]**: con memoria

  

### Reti Combinatorie

  

#### Caratteristiche

- Per ogni combinazione dei 2^n ingressi è fissato il valore delle uscite

- L'uscita dipende solo dal valore attuale degli ingressi

  

#### Livelli di una Rete

- **Livello**: porte i cui ingressi ricevono segnali nello stesso istante

- Il numero di livelli determina il **ritardo di elaborazione**

- Ritardo totale = L × Δt (dove L è il numero di livelli)

- Conviene minimizzare i livelli per ridurre il ritardo

  

### Analisi e Sintesi

  

#### Analisi

Dall'esame delle porte logiche si determina la funzione implementata.

  

#### Sintesi

Dai requisiti e dalle corrispondenze ingresso-uscita si implementa la funzione con il minimo numero di porte logiche.

  

**Obiettivi della sintesi minima**:

- Ridurre il numero di porte/ingressi

- Minimizzare spazio sul chip

- Ridurre i costi

  

### Metodi di Sintesi Minima

  

1. **Semplificazione algebrica**: uso delle relazioni notevoli dell'algebra booleana

2. **Mappe di Karnaugh**: rappresentazione su mappa di 2^n celle

3. **Metodo di Quine-McKluskey**: confronto sistematico dei termini

  

L'obiettivo è ottenere il minor numero possibile di termini (porte) e letterali (ingressi) mantenendo la funzionalità equivalente.


**Prossimo Argomento —————————>> [[Architettura dei calcolatori e livello logico|Capitolo 5 Livello Logico Digitale]]**
