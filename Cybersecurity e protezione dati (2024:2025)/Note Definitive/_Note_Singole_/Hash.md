Un **hash** è il risultato di una funzione matematica unidirezionale (nota come **funzione hash**) che converte un input (come una password o un file) in una stringa di lunghezza fissa e apparentemente casuale. Questo processo ha alcune proprietà fondamentali che lo rendono utile per applicazioni di sicurezza informatica, come la protezione delle password.

### Proprietà delle funzioni di Hash

1. **Unidirezionalità**:
	È matematicamente difficile risalire all’input originale partendo dal valore hash.

2. **Deterministico**:
	Lo stesso input produce sempre lo stesso hash.

3. **Sensibile ai cambiamenti (Avalanche Effect)**:
	Anche un piccolo cambiamento nell’input provoca un hash completamente diverso.

4. **Lunghezza fissa**:
	L’hash generato ha una lunghezza predeterminata, indipendentemente dalla dimensione dell’input.

5. **Unicità (praticamente)**:
	È altamente improbabile che due input diversi generino lo stesso hash (collisions).

### Principali utilizzi dell'Hash

**1. Protezione delle Password** in [[Autenticazione per password]]

• Le password non vengono memorizzate in chiaro nei database; invece, il sistema archivia solo il loro hash.

• Durante il login, il sistema genera l’hash della password fornita e lo confronta con quello memorizzato.

**2. Integrità dei Dati**

• Gli hash vengono utilizzati per verificare che i dati non siano stati alterati.

• Esempio: Un file scaricato include un hash pubblicato dal fornitore. L’utente può generare l’hash del file scaricato e confrontarlo per assicurarsi che il file sia integro.


**3. Firma Digitale**

• Gli hash sono utilizzati in crittografia e firme digitali per garantire che il contenuto di un messaggio o documento non sia stato alterato.

### Algoritmi di Hash più comuni

1. **MD5**:
	Molto utilizzato in passato, ma considerato **insicuro** oggi per la presenza di collisioni.

2. **SHA-1**:
	Un tempo uno standard, ora deprecato per motivi di sicurezza (collisioni dimostrate).

3. **SHA-256 (e altre della famiglia SHA-2)**:
	Attualmente considerato **sicuro** ed è uno degli standard più utilizzati.

4. **bcrypt, Argon2**:
	Specificamente progettati per il **password hashing**, includono un fattore di costo per rallentare calcoli e prevenire attacchi brute force.

### Vulnerabilità di Hash

1. **Collisioni**:
	Due input diversi generano lo stesso hash (molto raro con algoritmi moderni come SHA-256).

2. **Rainbow Table Attacks**:
	Tabelle pre-calcolate di hash per password comuni possono velocizzare il cracking.
	**Mitigazione**: Utilizzo di un **salt**, un valore casuale aggiunto alla password prima di calcolare l’hash.
	Esempio: password123 + randomSalt → hash unico.

3. [[Brute force]]
	L’aggressore prova tutte le combinazioni possibili di password finché trova un match.