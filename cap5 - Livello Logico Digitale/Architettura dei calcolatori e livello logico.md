
## Architettura a livelli dei Calcolatori

Per semplificare la progettazione e rendere più facile la manutenzione scegliamo di costruire i calcolatori in maniera modulare, *a strati*, in questo modo abbiamo diversi *livelli* dal *livello 0* (Hardware), *Livello n* interfaccia con cui interagisce l'utente.
![[Screenshot 2025-08-23 alle 18.39.14.png#invert]]
- Più siamo in basso di Livello più è facile la realizzazione Hardware e più è complesso programmare
- Più siamo in alto di Livello più è facile programmare ma da un certo punto in poi diventa impossibile la realizzazione Hardware.
- Il livello 2 è il più basso al quale un utente può arrivare.
- Tipicamente di programma al livello 5

## Livello 0 Circuiti Logici Digitali

In questo livello troviamo Circuiti elettronici i cui ingressi e uscite assumono solo 2 valori (0-1)
![[Screenshot 2025-08-23 alle 18.42.41.png#invert]]
Unendo tanti di questi blocchi generiamo **[[Reti logiche combinatorie]]**
