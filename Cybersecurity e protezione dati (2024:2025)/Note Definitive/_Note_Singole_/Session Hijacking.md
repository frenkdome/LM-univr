Il **Session Hijacking** è un attacco informatico in cui un ==attaccante prende il controllo di una sessione attiva di comunicazione tra un utente e un’applicazione web==, simulando l’identità della vittima. Questo consente all’attaccante di accedere a risorse protette senza conoscere le credenziali originali dell’utente.

### Come Funziona il Session Hijacking

1. **Sessione Web**:
	Una sessione è una connessione temporanea tra un client (utente) e un server (applicazione web) che consente all’utente autenticato di accedere a servizi o dati.

	È identificata da un **Session ID** (un valore unico generato dal server).

2. **Session Hijacking**:
	L’attaccante intercetta o ruba il **Session ID** e lo utilizza per impersonare l’utente legittimo, ottenendo accesso alle stesse risorse e privilegi.

### Tipologie di Session Hijacking

1. **Active Session Hijacking**:
	L’attaccante interagisce direttamente con la sessione, interrompendola o manipolandola.

2. **Passive Session Hijacking**:
	L’attaccante si limita a monitorare il traffico della sessione senza interagire direttamente.

3. **Cross-site Scripting (XSS)**:
	Gli attaccanti iniettano codice malevolo per catturare il Session ID attraverso l’interfaccia dell’utente.

4. **Session Fixation**:
	L’attaccante forza la vittima a utilizzare un Session ID predeterminato, che poi viene riutilizzato per accedere al sistema.

5. **Network Sniffing**:
	Utilizzo di strumenti per intercettare i dati non cifrati durante il transito in rete, inclusi i Session ID.