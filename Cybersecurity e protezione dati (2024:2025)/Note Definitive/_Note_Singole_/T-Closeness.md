La distribuzione degli attributi sensibili all’interno di ogni classe di equivalenza (ossia, gruppi di record con valori identici per i quasi-identificatori) sia ==“vicina” alla distribuzione globale== di tali attributi nell’intero dataset.

La “vicinanza” viene misurata in termini di distanza tra la distribuzione globale e quella locale (di una specifica classe di equivalenza). Una misura comune è l’[[Earth Mover Distance (EMD)]].

![[Pasted image 20241230151340.png]]

## Passaggi del calcolo

1. **Calcolo della distribuzione globale**:
	Si determina la distribuzione complessiva dei valori dell’attributo sensibile su tutto il dataset.

2. **Calcolo della distribuzione locale**:
	Si calcolano le distribuzioni degli attributi sensibili per ogni classe di equivalenza.

3. **Misurazione della distanza**:
	Si utilizza una metrica come l’**Earth Mover Distance** per quantificare quanto la distribuzione locale di ogni classe di equivalenza si discosta dalla distribuzione globale.

4. **Confronto con la soglia t**:
	Se la distanza calcolata per ogni classe è inferiore o uguale a una soglia definita  t , il dataset soddisfa il criterio di **t-closeness**.

## Esempio di calcolo
![[Pasted image 20241230152619.png]]![[Pasted image 20241230152629.png]]![[Pasted image 20241230152701.png]]![[Pasted image 20241230152714.png]]![[Pasted image 20241230152726.png]]