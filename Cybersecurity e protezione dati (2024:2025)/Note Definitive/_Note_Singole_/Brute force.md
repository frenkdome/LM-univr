Un attacco **brute force** è una tecnica in cui un ==aggressore tenta di indovinare password, PIN, o chiavi crittografiche provando sistematicamente tutte le combinazioni possibili== fino a trovare quella corretta. Questo tipo di attacco è basato sulla “forza bruta”, utilizzando calcolo ripetitivo e automatizzato, piuttosto che strategie più complesse.

### Caratteristiche di un attacco brute force

1. **Metodologia**:
	Prova tutte le possibili combinazioni di caratteri (lettere, numeri, simboli) fino a trovare una corrispondenza.
	
	Ad esempio, per una password di 4 caratteri con solo lettere minuscole (a-z), si proverebbero tutte le combinazioni da “aaaa” a “zzzz”.

2. **Obiettivo**:
	Indovinare credenziali per ottenere l’accesso a un sistema o un file.
	Decriptare un hash per risalire al testo originale della password.

3. **Esecuzione**:
	Utilizza strumenti automatizzati come **John the Ripper**, **Hashcat**, o **Hydra**.
	
	Può sfruttare hardware avanzato come **GPU**, che accelerano enormemente il processo rispetto alle CPU tradizionali.

### Tipologie di attacco brute force

1. **Attacco Classico**:
	Prova ogni combinazione possibile.
	Molto lento ma garantito per password deboli, se viene concesso abbastanza tempo.

2. **Dictionary Attack**:
	L’attaccante utilizza un elenco predefinito di password comuni o plausibili (ad esempio, “123456”, “password”, “qwerty”) oppure sfrutta un dizionario.
	
	Più veloce del brute force puro, ma inefficace contro password non comuni (potrebbe non trovare la password).

3. **Online Dictionary Attack**:
	Un tipo di attacco che utilizza una **ricerca intelligente** per individuare password associate a un determinato utente o sistema. Si basa su un dizionario predefinito di password comuni e plausibili per ottimizzare il tempo necessario a violare le credenziali, aggiungendo però informazioni personali legate all'utente per perfezionare le password.

5. **Hybrid Attack**:
	Combina le tecniche brute force e dizionario, cercando di sfruttare le euristiche comuni agli utenti.
	Ad esempio, modifica password del dizionario aggiungendo numeri o simboli (es., “password” diventa “Password1!”).

5. **Reverse Brute Force**:
	Parte da una password conosciuta e tenta di applicarla a un ampio set di account.
	Esempio: Provare “123456” su milioni di account.

6. **Credential Stuffing**:
	Riutilizza credenziali rubate in precedenti data breach per tentare accessi su altri sistemi.
	Sfrutta la pratica comune di riutilizzare la stessa password su più account.
	![[Pasted image 20241123120249.png]]

7. **Rainbow Table attack**:
	L’attaccante utilizza una tabella precomputata che associa password in chiaro ai rispettivi hash. Questo metodo elimina la necessità di calcolare l’hash durante l’attacco, rendendolo più veloce rispetto a brute force o dictionary attacks. Tuttavia, richiede una quantità significativa di memoria per memorizzare le tabelle precomputate.


Attacco che inverte l'approccio, non focalizzandosi solo su un individuo ma provando tutti e vedendo chi usa password comuni: **Password Spraying**
![[Pasted image 20241123120826.png]]

### Strumenti utilizzati dagli attaccanti

• **John the Ripper**: Software open source per il cracking di password.

• **Hashcat**: Ottimizzato per GPU, supporta numerosi tipi di hash.

• **Hydra**: Specializzato per tentativi su protocolli di rete (ad esempio, FTP, SSH).