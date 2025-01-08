Un **Man-in-the-Middle (MITM) attack** è una tipologia di attacco informatico in cui un ==attaccante intercetta, manipola o monitora la comunicazione tra due parti== (ad esempio, un client e un server) senza che queste siano a conoscenza della sua presenza. L’attaccante si posiziona tra le due parti e agisce come un intermediario, compromettendo la riservatezza, l’integrità o l’autenticità dei dati scambiati.

### Caratteristiche Fondamentali

1. **Intercettazione**:
	L’attaccante cattura i dati trasmessi tra le due parti, che possono includere credenziali, dati personali o altre informazioni sensibili.

2. **Manipolazione**:
	L’attaccante può alterare il contenuto dei messaggi trasmessi, inducendo una o entrambe le parti a prendere decisioni basate su dati falsificati.

3. **Impostura**:
	L’attaccante si maschera da una delle due parti legittime, ingannando l’altra e acquisendo fiducia per continuare l’attacco.

### Obiettivi degli Attacchi MITM

• **Furto di Credenziali**:
	L’attaccante cattura username, password o token di sessione.

• **Accesso ai Dati Sensibili**:
	Ad esempio, informazioni bancarie, numeri di carte di credito, o dati aziendali riservati.

• **Manipolazione di Transazioni**:
	Modificare transazioni in corso, come ordini online o bonifici bancari.

• **Installazione di Malware**:
	Alterare i contenuti trasmessi per iniettare malware o reindirizzare l’utente verso siti dannosi.

### Tipologie di Attacchi MITM

1. **Network-based MITM**:
	L’attaccante compromette il traffico in una rete locale (LAN/Wi-Fi).
	
	Tecniche comuni:
	- **ARP Spoofing**: Manipolazione delle tabelle ARP per reindirizzare il traffico al dispositivo dell’attaccante.
	- **DNS Spoofing**: Alterazione delle risposte DNS per reindirizzare le richieste a siti dannosi.

2. **Browser-based MITM**:
	L’attaccante utilizza tecniche come script dannosi o vulnerabilità nei browser per intercettare o modificare il traffico web.
	
	Esempio: [[Session Hijacking]].

3. **HTTPS Spoofing**:

• Installazione di certificati SSL falsificati per intercettare il traffico HTTPS, convincendo il client che la connessione è sicura.

4. **Email MITM**:

• Intercettazione o manipolazione di email per reindirizzare transazioni o diffondere malware.