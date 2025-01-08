## Il problema della privacy nei dataset

Solitamente nelle nostre analisi ==bisogna affidarsi a dataset con informazioni sensibili==. 
Come posso utilizzare questi dataset sfruttando le informazioni ma preservando la privacy degli individui?

![[Pasted image 20241230112910.png]]

Possiamo infatti arrecare danni ai singoli se non ci sforziamo di anonimizzare i dati presenti in caso di intercettazioni da parte di alcuni attaccanti.
![[Pasted image 20241230113310.png]]

### Classificazione degli attributi presenti in un dataset

- #### Explicit identifiers (Identificatori espliciti)
  Sono attributi che ==identificano direttamente l'individuo==.
	  - nome
	  - cognome
	  - numero di passaporto / CI 
	  - codice fiscale
	  - ...
  
- #### Quasi-identifiers (Quasi identificatori)
   Attributi che, presi ==singolarmente==, ==non identificano== un individuo, ma che possono essere ==combinati per rivelare l’identità==.
	  - data di nascita
	  - CAP
	  - numero di telefono
	  - ...
  
- #### Sensitive attributes (Attributi sensibili)
  Attributi che contengono ==informazioni personali critiche==.
  Sono il focus principale di analisi per i ricercatori o le aziende, rappresentando il valore informativo del dataset, devono essere quindi protetti senza compromettere l’utilità del dato.
	  - malattie
	  - salari
	  - opinioni politiche
	  - ...

![[Pasted image 20241230114552.png]]

## Mitigazioni al problema della privacy nei dataset

- Protezione degli Explicit Identifier
	- **Tokenization (Tokenizzazione) :** Genera un token univoco (un identificativo casuale) che sostituisce l’attributo originale.
	  
	- **Substitution (Sostituzione):** Sostituisce un valore di attributo con un altro valore alternativo, spesso preso da un database predefinito.
	  ![[Pasted image 20241230115305.png]]
	
	Solo questo però non può bastare:
	![[Pasted image 20241230115410.png]]![[Pasted image 20241230115421.png]]
- [[K-Anonymity]]
- [[L-Diversity]]
- [[T-Closeness]]

Questi approcci però portano alla conclusione che ==la semplice anonimazione dei dati è comunque insicura==, dato che le informazioni ausiliari e i quasi-identificatori ci possono comunque portare alle informazioni rilevanti. 

Ipotesi di nuova soluzione: invece che utilizzare i dati direttamente si utilizzano risultati di analisi statistica (media, mediana, conteggi, ...).
Sebbene si tenda a pensare che le medie o i conteggi siano **anonimi**, nella pratica:
- **Analisi statistiche** possono rivelare informazioni sensibili individuali se non implementate correttamente.
- Gli attacchi di correlazione e inferenza dimostrano che anche dataset aggregati possono essere vulnerabili.
![[Pasted image 20241230155806.png]]

### Reconstruction Attacks
Mirano a recuperare informazioni sensibili individuali da query aggregate. Le differenze principali sono:
- Query aggregate (es. “Quanti uomini hanno una malattia?”) sono generalmente sicure, ma…
- Query mirate o combinate possono portare a deduzioni precise su individui specifici.
Ad esempio, inserendo un nuovo record nel database, come nella slide, è possibile dedurre l’età e il peso del nuovo record.
![[Pasted image 20241230160042.png]]
![[Pasted image 20241230160059.png]]
Anche limitando le query a quelle aggregate, si può comunque compromettere la privacy degli individui:

- Query troppo specifiche possono ridurre i risultati aggregati a un solo individuo o a un piccolo sottoinsieme, rivelando così informazioni sensibili.
- Questo mette in evidenza come le restrizioni sulle query non siano una soluzione definitiva.

Arriviamo quindi a una possibile soluzione a queste problematiche:
- [[Differential Privacy]]
