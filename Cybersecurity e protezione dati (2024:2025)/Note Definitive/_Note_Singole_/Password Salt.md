**Password salting** è una tecnica crittografica utilizzata per aumentare la sicurezza delle password memorizzate nei sistemi. Consiste nell’aggiungere una stringa casuale (chiamata “salt”) a ciascuna password prima che venga sottoposta a una funzione di hash. Questo processo rende più difficile per gli attaccanti utilizzare attacchi basati su dizionari o tabelle arcobaleno (_rainbow tables_), poiché ogni password hash diventa unica, anche se gli utenti scelgono password identiche.

### Definizione Formale
Il salting consiste nell’aggiungere una stringa casuale (salt) univoca a ciascuna password in fase di hashing, producendo hash diversi per password uguali. Questo processo viene eseguito secondo la seguente formula:

$$H = hash(\text{password} + \text{salt})$$

Dove:
• H  è l’hash della password.
• **password** è il valore in chiaro fornito dall’utente.
• **salt** è una stringa casuale univoca associata a ciascun utente o istanza.
• **hash()** è la funzione crittografica utilizzata (es., SHA-256, bcrypt).

### **Benefici del Salting**

1. **Protezione contro attacchi basati su tabelle precomputate (Rainbow Table)**:
	L’aggiunta del salt rende ogni hash unico, impedendo agli attaccanti di utilizzare tabelle precomputate standard.

2. **Unicità degli hash**:
	Due utenti con la stessa password avranno hash diversi grazie ai salt univoci.

3. **Maggiore difficoltà per attacchi brute force**:
	Gli attaccanti devono calcolare un hash specifico per ogni combinazione password + salt, rallentando significativamente il processo.

### Implementazioni

• **Static Salt**: Lo stesso salt per tutte le password. Meno sicuro.
• **Dynamic Salt**: Un salt univoco generato per ciascun utente. Più sicuro.
• **Salt and Pepper**: Oltre al salt, si aggiunge una seconda stringa segreta condivisa, chiamata _pepper_, memorizzata separatamente.

### Considerazioni di Sicurezza

1. **Archiviazione sicura**:
	Il salt non deve essere segreto, ma deve essere salvato insieme all’hash della password.
	Tuttavia, il “pepper” dovrebbe essere mantenuto segreto e archiviato separatamente.

2. **Lunghezza del Salt**:
	Deve essere sufficientemente lungo (almeno 16 byte) per evitare collisioni e garantire unicità.

3. **Funzioni di Hash Sicure**:
	È importante utilizzare funzioni di hashing specifiche per le password, come bcrypt, Argon2 o PBKDF2, che includono anche iterazioni multiple per aumentare la difficoltà.