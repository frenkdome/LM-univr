L’**autenticazione** è il processo di ==verifica dell’identità di un utente o di un’entità che tenta di accedere a un sistema==, applicazione o risorsa. 
In altre parole, è il meccanismo attraverso il quale un sistema conferma che l’utente è effettivamente chi dichiara di essere.

### **Componenti e Metodi di Autenticazione:**
La determinazione di un'entità consiste nella combinazione dei metodi di autenticazione basati su:

**Qualcosa che l’utente conosce**:
![[Pasted image 20241117185449.png]]
- **Password**: Combinazioni di caratteri segreti.
- **PIN**: Numeri identificativi personali.

**Qualcosa che l’utente possiede**:
![[Pasted image 20241117185510.png]]
- **Token di Sicurezza**: Dispositivi fisici che generano codici temporanei.
  Esistono due tipologie di token
	- **Hardware token**
		- **Smart Card**: Carte con chip incorporato che contengono certificati digitali.
		- **Usb Key**: Token dove è possibile utilizzare dei dati biometrici per accedere al computer
		![[Pasted image 20241204150054.png]]
		  
	- **Software token**
		- **Mobile App Authenticator** (Es. Google, Microsoft)![[Pasted image 20241204150112.png]]

**Qualcosa che l’utente è**:
![[Pasted image 20241117185429.png]]
- [[Biometria]]: Impronte digitali, riconoscimento facciale, scansione dell’iride, riconoscimento vocale.

### **Tipologie di Autenticazione:**

**Autenticazione a Fattore Singolo (SFA)**:
Utilizza un solo metodo di autenticazione, solitamente una password.

**Autenticazione a Due Fattori (2FA)**:
Combina ==due metodi di autenticazione==, ad esempio una password (qualcosa che conosci) e un codice inviato via SMS (qualcosa che possiedi).

**Autenticazione Multifattore (MFA)**:
Integra tre o più fattori di autenticazione, aumentando la sicurezza.

### Protocolli di autenticazione
- [[One-time Password]]
- [[Challenge-response]]

### Attacchi principali svolti sull'identità
![[Pasted image 20241117185707.png]]

### **Best Practice per l’Autenticazione:**

• **Politiche di Password Forti**:
	Richiedere password complesse e lunghe, con scadenze periodiche.

• **MFA**:
	Implementare l’autenticazione multifattore per ridurre il rischio di accessi non autorizzati.

• **Monitoraggio delle Autenticazioni**:
	Tenere traccia dei tentativi di accesso e rilevare attività sospette.

• **Educazione degli Utenti**:
	Formare gli utenti sull’importanza di proteggere le proprie credenziali e di riconoscere tentativi di phishing.

### **Importanza dell’Autenticazione:**

• **Prima Linea di Difesa**:
	Impedisce a utenti non autorizzati di accedere ai sistemi.

• **Protezione delle Identità Digitali**:
	Salvaguarda le informazioni personali e aziendali.

### **Problemi e soluzioni legati all'autenticazione**

PROBLEMI
- Il token può essere **perso**
- Il token può essere **clonato**

SOLUZIONI
- Bloccare l'account per l'utente
- Associare un ulteriore segreto -> aggiunta di ulteriori gesture biometriche per assicurarci che sia l'utente ad accedere

# Aree specifiche di autenticazione
[[User Authentication]]
[[Autenticazione per password]]
[[Single Sign On Protocols (SSO)]]
