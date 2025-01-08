![[Pasted image 20241228102500.png]]

# Hard Privacy

![[Pasted image 20241228105548.png]]
L’obiettivo della **Hard Privacy** è minimizzare la raccolta di dati personali e ridurre al minimo la necessità di “fidarsi” di altre entità per la gestione di tali dati.

##### Caratteristiche:
- **Data minimization:** Il soggetto fornisce il minor numero possibile di dati personali.
- **Riduzione della fiducia:** Le entità che raccolgono i dati non devono necessariamente essere completamente affidabili perché i dati sono progettati per essere minimamente condivisi.

## Proprietà fondamentali:

- ### Anonymity (Anonimato)
  L’anonimato garantisce che un attaccante non possa identificare il soggetto di un’azione all’interno di un insieme di soggetti ([[Anonymity Set]]). 
  L'anonimato quindi non dipende solamente dal singolo, ma da chi viene coinvolto nella comunicazione.
  ![[Screenshot 2024-12-28 at 11.24.05.png]]
  
  Esempi:
	- Lettore di una pagina web o utente che accede a un servizio.
	- Mittente o destinatario di un’email.
	- Persona a cui si riferisce una voce in un database.
	- Persona presente in una posizione fisica.



- ### Unlinkability (Non Collegabilità)
  La proprietà di **unlinkability** si riferisce all’incapacità di un attaccante di determinare se due o più elementi di interesse (IOI, Items of Interest) siano correlati o meno.
  Si vuole quindi ==nascondere i legami== tra due o più azioni, identità o pezzi di informazione per preservare la privacy.
  
  ![[Screenshot 2024-12-28 at 11.47.48.png]]
  
  Esempi:
	- Due lettere anonime scritte dalla stessa persona.
	- Due visite a una pagina web da parte dello stesso utente.
	- Due voci in database che si riferiscono alla stessa persona.
	- Due persone collegate tramite un link di amicizia.
	- Una persona avvistata in due località diverse in momenti differenti.



- ### Undetectability (Non Rilevabilità)
  La proprietà di **undetectability** significa che un attaccante ==non può distinguere se== un elemento di interesse (es. una comunicazione o un’azione) ==esiste o meno==.
  In questo modo siamo in grado di nascondere l'attività dell'utente.
  ![[Pasted image 20241228124820.png]]
  
  Esempi:
	- Impossibilità di vedere se qualcuno sta accedendo a una pagina web.
	- Impossibilità di sapere se una voce in un database corrisponde a una persona reale.
	- Impossibilità di distinguere se qualcuno si trova in una determinata posizione.



- ### Plausible Deniability (Negazione plausibile)
  La proprietà di **plausible deniability** consente a un utente di negare di aver compiuto una certa azione o possedere certe informazioni.
  Non è quindi possibile dire se un utente sappia, ha fatto o ha detto qualcosa.
  
  ![[Pasted image 20241228125511.png]]
  
  Esempi:
	- Resistenza alla coercizione: impossibile dimostrare che una persona abbia nascosto informazioni in un computer.
	- Negare di possedere la combinazione di una cassaforte.
	- Negare di essere stati in un determinato luogo in un momento specifico.
	- Negare che un record di un database appartenga a una persona.





# Soft Privacy

![[Pasted image 20241228105752.png]]La **Soft Privacy** interviene quando i dati personali sono già stati raccolti. L’obiettivo è garantire che i dati siano gestiti in modo corretto e sicuro.

## Caratteristiche:
- **Perdita di controllo:** Il soggetto dei dati ha perso la capacità di controllare come i suoi dati vengono raccolti e utilizzati.
- **Gestione delle informazioni:** In pratica, è difficile verificare il modo in cui i dati vengono trattati, ma la conformità normativa e le policy aziendali giocano un ruolo chiave.

## Proprietà fondamentali:

- ### Confidentiality (Riservatezza)
  La **riservatezza** implica la protezione delle informazioni da accessi non autorizzati, garantendo che i dati personali e proprietari siano accessibili solo alle persone autorizzate.
  ![[Pasted image 20241228130042.png]]
  
  
- ### Awareness (Consapevolezza)
  La **consapevolezza** si riferisce all’importanza di educare gli utenti sui rischi e sulle conseguenze della condivisione delle informazioni personali.
  Gli utenti devono comprendere l’impatto delle loro azioni e devono essere in grado di prendere decisioni informate riguardo alla condivisione dei propri dati.
  ![[Pasted image 20241228130401.png]]
  
  
  
- ### Compliance (Conformità)
  La **conformità** riguarda l’aderenza a normative e leggi sulla protezione dei dati, come il **GDPR**(General Data Protection Regulation).
  Bisogna controllare che le organizzazioni rispettino le normative sulla protezione dei dati, garantendo che il trattamento sia trasparente e legittimo.
  ![[Pasted image 20241228130535.png]]