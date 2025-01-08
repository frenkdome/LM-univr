Le OTP (One-Time Password) sono password uniche valide per una singola sessione o transazione. Migliorano la sicurezza riducendo il rischio di riutilizzo o intercettazione delle password.

### Caratteristiche OTP

1. **Generate Dinamicamente**: Le password vengono create periodicamente o su richiesta, a seconda dell’implementazione.

2. **Valide Una Sola Volta**: Ogni OTP è valida per una sola sessione o transazione.

3. **Richiedono Sincronizzazione**: I sistemi e i dispositivi che generano e validano le OTP devono essere sincronizzati.

4. **Maggiore Sicurezza**: Elimina rischi come il riutilizzo delle password o attacchi brute force.

### **Metodi di Invio delle OTP:**

1. **Basate su SMS**:
	Le OTP vengono inviate via messaggio di testo al numero di telefono registrato dell’utente.
	
	**Vulnerabilità**:
	- Esposizione ad attacchi di SIM swapping o intercettazione.

2. **TOTP (Time-Based OTP)**:
	Generate utilizzando un segreto condiviso e il timestamp Unix corrente.
	Applicazioni come Google Authenticator generano continuamente OTP.
	Richiedono generalmente di inquadrare un QR code per iniziare a generare token su un'app di Authentication.
	
	**Vantaggi**:
	- Non richiede connessione di rete.
	- Sicuro contro l’intercettazione.
	  
	**Formula**:
	$$TOTP(K, T) = \text{HMAC-SHA256}(K, T)$$
		K: Chiave segreta
		T: Tempo Unix corrente

### Algoritmi su cui si basa OTP

1. **HOTP (HMAC-Based One-Time Password)**:
	La generazione della OTP si basa su un contatore (C) incrementato dopo ogni tentativo di autenticazione.
	
	**Passaggi**:
	1. L'utente abilita l'autenticazione a due fattori.
	2. Il backend crea una chiave segreta per l'utente.
	3. Il server condivide una chiave segreta (K) con l’applicazione dell’utente.
	4. L’applicazione inizializza un contatore (C).
	5. L'applicazione incrementa prima di tutto il valore del contatore di uno e poi genera una una password unica utilizzando la chiave segreta e il contatore come segue
	$$\text{HOTP}(K, C) = Truncate ({HMAC-SHA1}(K, C))$$
	6. Se il valore inviato dall'applicazione combacia con quello generato dal server, il server incrementa il contatore di 1.
	
	**Limitazione**:
	- Richiede la sincronizzazione del contatore tra client e server.

2. **TOTP (Time-Based One-Time Password)**:
	Simile a HOTP, ma utilizza il tempo al posto del contatore. Elimina così la necessità di sincronizzazione del contatore, dato che sia il server sia l'applicazione hanno accesso al tempo (currentUnixTime).
	
	**Calcolo valore:**
	$$\text{TOTP}(K, C)= {HMAC-SHA256}(K, T)$$
	dove T -> Unix Time
	
	**Caratteristica Chiave**:
	Si basa sul tempo Unix per generare OTP sensibili al tempo.

Riassumendo:

| **Caratteristica**   | **HOTP**                                      | **TOTP**                                         |
| -------------------- | --------------------------------------------- | ------------------------------------------------ |
| **Base**             | Contatore (`C`)                               | Tempo Unix (`T`)                                 |
| **Sincronizzazione** | Richiesta tra server e client                 | Non richiesta                                    |
| **Generazione OTP**  | Ogni volta che viene richiesto e incrementato | Automaticamente basato sull'orario               |
| **Validità OTP**     | Fino al prossimo utilizzo                     | Limitata a una finestra temporale (es. 30s)      |
| **Uso Tipico**       | Sistemi con autenticazioni meno frequenti     | Autenticazioni frequenti (es. 2FA su app)        |
| **Vantaggio**        | Non dipende dal tempo                         | Non richiede sincronizzazione del contatore      |
| **Limite**           | Rischio di desincronizzazione del contatore   | Richiede sincronizzazione oraria tra dispositivi |


