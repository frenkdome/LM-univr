La **crittografia** è la scienza e l’arte di ==proteggere le informazioni trasformandole in un formato illeggibile per chiunque non sia autorizzato ad accedervi==. Questo processo di trasformazione, chiamato **cifratura**, utilizza algoritmi matematici per convertire il testo in chiaro (informazioni leggibili) in testo cifrato (informazioni illeggibili senza la chiave appropriata). 

L’obiettivo principale della crittografia è garantire la **confidenzialità**, l’**integrità**, l’**autenticazione** e la **non ripudiabilità** delle informazioni durante la trasmissione o l’archiviazione.

-> Studio e pratica di tecniche per la ==creazione di canali di comunicazione sicuri== (ragionevolmente parlando).

### Principi Fondamentali della Crittografia

1. **Confidenzialità**: Garantire che le informazioni siano accessibili solo a chi è autorizzato.

2. **Integrità**: Assicurare che le informazioni non siano state alterate o modificate durante la trasmissione o l’archiviazione.

3. **Autenticazione**: Verificare l’identità delle parti coinvolte nella comunicazione.

4. **Non Ripudiabilità**: Impedire che una delle parti possa negare di aver effettuato una certa operazione o comunicazione.

### Tipi di Crittografia

1. **Crittografia Simmetrica (a Chiave Simmetrica)**
	**Descrizione**: Utilizza la stessa chiave sia per cifrare che per decifrare il messaggio.
	
	**Vantaggi**: Velocità ed efficienza nel processo di cifratura e decifratura.
	
	**Svantaggi**: Distribuzione sicura delle chiavi; se la chiave viene compromessa, l’intera comunicazione è a rischio.
	
	**Esempi di Algoritmi**:
	- **AES (Advanced Encryption Standard)**
	- **DES (Data Encryption Standard)**
	- **3DES (Triple DES)**
	- **RC4, RC5, RC6**

2. **Crittografia Asimmetrica (a Chiave Pubblica)**
	**Descrizione**: Utilizza una coppia di chiavi correlate matematicamente: una chiave pubblica (disponibile a tutti) e una chiave privata (segreta). La chiave pubblica cifra il messaggio, mentre la chiave privata lo decifra.
	
	**Vantaggi**: Risolve il problema della distribuzione delle chiavi; consente autenticazione e scambio sicuro di chiavi.
	
	**Svantaggi**: Processi di cifratura e decifratura più lenti rispetto alla crittografia simmetrica.
	
	**Esempi di Algoritmi**:
	- **RSA (Rivest-Shamir-Adleman)**
	- **ECC (Elliptic Curve Cryptography)**
	- **DSA (Digital Signature Algorithm)**

3. **Funzioni Hash e Crittografia a Senso Unico**
	**Descrizione**: Trasformano un input di lunghezza variabile in un output di lunghezza fissa (hash). Sono progettate per essere funzioni a senso unico, rendendo impraticabile risalire all’input originale dall’hash.
	
	**Utilizzi**: Verifica dell’integrità dei dati, memorizzazione sicura delle password.
	
	**Esempi di Algoritmi**:
	- **MD5 (Message Digest Algorithm 5)**
	- **SHA-1, SHA-2, SHA-3 (Secure Hash Algorithm)**
	- **Bcrypt, Scrypt (utilizzati per la protezione delle password)**


### Componenti Chiave della Crittografia

1. **Algoritmi Crittografici**
	Serie di passaggi matematici utilizzati per cifrare e decifrare i dati.
	
	**Proprietà Importanti**:
	- **Sicurezza**: Difficoltà nel rompere l’algoritmo senza conoscere la chiave.
	- **Efficienza**: Capacità di cifrare e decifrare rapidamente.

2. **Chiavi Crittografiche**
	Informazioni segrete utilizzate in combinazione con l’algoritmo per cifrare e decifrare i dati.
	
	**Gestione delle Chiavi**: Processo critico che include la generazione, distribuzione, archiviazione, rotazione e revoca delle chiavi.


Solitamente per spiegare il problema si usa l’esempio di Alice e Bob:
![[Pasted image 20241012144807.png]]![[Pasted image 20241125211714.png]]