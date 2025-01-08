I buffer sono regioni di memoria che contengono temporaneamente i dati mentre vengono trasferiti da una posizione all'altra. 

Un ==buffer overflow (o buffer overrun)== si verifica quando il volume dei ==dati supera la capacità di memoria del buffer==. Di conseguenza, il programma che tenta di scrivere i dati nel buffer sovrascrive le posizioni di memoria adiacenti.

Questo può essere sfruttato come attacco di [[Exploitation]] :

Gli aggressori sfruttano i problemi di buffer overflow sovrascrivendo la memoria di un'applicazione. Ciò modifica il percorso di esecuzione del programma, innescando una risposta che danneggia i file o espone informazioni private. 

Se gli aggressori conoscono il layout della memoria di un programma, possono inserire intenzionalmente input che il buffer non è in grado di memorizzare e sovrascrivere aree che contengono codice eseguibile, sostituendolo con il proprio codice. Ad esempio, un aggressore può sovrascrivere un puntatore (un oggetto che punta a un'altra area della memoria) e indirizzarlo verso un payload di exploit, per ottenere il controllo del programma.