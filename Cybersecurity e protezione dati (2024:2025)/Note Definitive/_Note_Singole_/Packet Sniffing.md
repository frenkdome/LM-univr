Il **Packet Sniffing** è una tecnica utilizzata per c==atturare e analizzare i dati che transitano attraverso una rete==. Fa parte del più ampio concetto di **Network Sniffing**, che comprende tutte le tecniche di monitoraggio del traffico di rete. In sostanza, il Packet Sniffing rappresenta l’aspetto più tecnico e specifico del Network Sniffing, ==focalizzandosi sui singoli pacchetti di dati trasmessi in rete==.

### Come Funziona

1. **Cattura dei Pacchetti**:
	• I dati inviati attraverso una rete sono suddivisi in unità chiamate **pacchetti**.
	
	• Un packet sniffer è uno strumento software o hardware che intercetta e memorizza questi pacchetti.

2. **Analisi dei Dati**:
	• Ogni pacchetto contiene dati come:
		
		• Header (metadati: indirizzo IP, porta, ecc.)
		
		• Payload (contenuto effettivo, es. credenziali o messaggi).
		
	• I pacchetti catturati vengono analizzati per estrarre informazioni utili.

3. **Modalità Operativa**:
   
	• **Promiscuous Mode**: Il dispositivo intercetta tutti i pacchetti trasmessi sulla rete (non solo quelli destinati a sé stesso).

	• **Monitor Mode** (su reti wireless): Consente di catturare pacchetti anche su canali non associati al dispositivo.

### Utilizzi del Packet Sniffing

**1. Scopi Legittimi**

- **Diagnosi e Monitoraggio della Rete**:  
  Gli amministratori di rete utilizzano packet sniffer per risolvere problemi, monitorare le prestazioni o rilevare guasti.
  Esempi di strumenti: **Wireshark**, **tcpdump**.

- **Analisi della Sicurezza**:
  Rilevamento di intrusioni o analisi di attività sospette.  

**2. Scopi Malevoli**

- **Intercettazione di Credenziali**:
  Gli attaccanti possono catturare username, password o token di sessione inviati su connessioni non cifrate.

- **Furto di Informazioni Sensibili**:
  Dati bancari, numeri di carte di credito o contenuti riservati trasmessi in rete.

- **Preparazione di Altri Attacchi**:
  Raccolta di informazioni per attacchi più mirati, come il **Man-in-the-Middle (MITM)**.

### Tecniche Utilizzate negli Attacchi di Packet Sniffing

1. **Eavesdropping su Reti Non Cifrate**:
   In reti non cifrate (es. HTTP), tutti i pacchetti possono essere intercettati facilmente.

2. **Intercettazione in Reti Wi-Fi Pubbliche**:
   Le reti aperte o con crittografia debole (come WEP) sono particolarmente vulnerabili.

3. **Spoofing per Deviare il Traffico**:
   Utilizzo di tecniche come l’**ARP Spoofing** per deviare il traffico attraverso il dispositivo dell’attaccante.

4. **Intercettazione di Sessioni (Session Hijacking)**:
   Gli attaccanti possono catturare i cookie o il Session ID per impersonare un utente.

### Strumenti Comuni di Packet Sniffing

1. **Wireshark**:
	Strumento avanzato per catturare e analizzare pacchetti.

2. **tcpdump**:
	Utility da riga di comando per catturare il traffico di rete.

3. **Ettercap**:
	Specifico per attacchi di MITM e sniffing su reti locali.

4. **Cain & Abel**:
	Usato per intercettare pacchetti e decifrare password.