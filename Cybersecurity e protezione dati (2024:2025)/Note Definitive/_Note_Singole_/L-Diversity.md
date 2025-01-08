Ogni ==classe di equivalenza== deve contenere almeno l ==valori sensibili diversi==.
L’obiettivo è garantire che un attaccante non possa dedurre il valore sensibile con certezza, anche se conosce la classe di equivalenza di un individuo.

![[Pasted image 20241230141810.png]]

## Storico delle evoluzioni di l-diversity

- **Distinct l-diversity**: 
  Ogni classe di equivalenza deve avere almeno *l* valori sensibili ben rappresentati.
  ⚠️ Non previene attacchi di deduzione probabilistica perché alcuni valori sensibili possono essere molto più rappresentati di altri.![[Pasted image 20241230144026.png]]
  
- **Entropy l-diversity**: 
  Non basta avere valori distinti, ma questi devono essere distribuiti in modo equilibrato. 
  Si utilizza la **entropia** per misurare la distribuzione dei valori sensibili, e questa deve risultare almeno $$log(l)$$![[Pasted image 20241230144145.png]]

## Problemi legati alla L-Diversity

1. **Probabilistic Inference Attack:** Non evita deduzioni probabilistiche quando alcuni valori sensibili sono più rappresentati di altri.

2. **Semantic Similarity Attack:** Non considera la correlazione semantica tra i valori sensibili.![[Pasted image 20241230151027.png]]

3. **Distribuzione Sbilanciata:** Non gestisce bene situazioni in cui i valori sensibili sono estremamente sbilanciati.![[Pasted image 20241230151046.png]]