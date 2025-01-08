una tecnica di autenticazione basata su crittografia che si utilizza per verificare l’identità senza trasmettere la password o le credenziali in chiaro. Questo metodo si fonda su una **coppia di chiavi crittografiche** (ad esempio, una chiave pubblica e una chiave privata)

### **Funzionamento**

1. **Generazione della challenge**:
	Il sistema o dispositivo invia una **challenge** al client o al token. La challenge è solitamente una stringa casuale (ad esempio, una sequenza di numeri o caratteri).
	
	Questa stringa è generata dinamicamente e cambia ad ogni sessione per evitare attacchi di replay.

2. **Risposta alla challenge**:
	Il dispositivo client o lo smart token utilizza la propria **chiave privata** per generare una risposta, tipicamente cifrando la challenge ricevuta.
	
	Questa risposta cifrata viene inviata al sistema.

3. **Verifica della risposta**:
	Il sistema utilizza la **chiave pubblica** associata al dispositivo o token per decifrare la risposta ricevuta. Se il valore decifrato corrisponde alla challenge originaria, l’autenticazione è confermata.

### **Vantaggi:**

- **Sicurezza elevata**: La password o i dati sensibili non vengono mai trasmessi attraverso la rete, rendendo questo metodo resistente agli attacchi di intercettazione (man-in-the-middle).

- **Protezione contro attacchi di replay**: Poiché la challenge è generata dinamicamente, ogni autenticazione è unica.

### **Esempi d’uso:**

- Sistemi che utilizzano **smart token** (come carte crittografiche o dispositivi USB con chiavi integrate).

- **Autenticazione a due fattori (2FA)**, dove il secondo fattore può utilizzare challenge-response.

- Protocolli come **SSH**, che possono implementare challenge-response per l’autenticazione con chiavi pubbliche e private.