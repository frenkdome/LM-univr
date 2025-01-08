**SAML** (_Security Assertion Markup Language_) è uno standard aperto basato su XML che consente lo ==scambio sicuro di informazioni di autenticazione e autorizzazione tra diverse entità==, tipicamente un **Identity Provider (IdP)** e un **Service Provider (SP)**. È sviluppato dall’organizzazione **OASIS (Organization for the Advancement of Structured Information Standards)**.

SAML è ampiamente utilizzato per implementare **Single Sign-On (SSO)** in ambienti distribuiti, dove gli utenti possono accedere a più applicazioni o servizi con una sola autenticazione.

-> vecchietto 

### Caratteristiche principali

1. **Formato XML**:
	Utilizza il linguaggio XML per rappresentare dati strutturati, come affermazioni di autenticazione e autorizzazione.

2. **Scambio di Affermazioni (Assertions)**:
	SAML scambia _assertions_, che sono pacchetti di informazioni relative a un utente, come:
	- Identità dell’utente (autenticazione).
	- Autorizzazioni o ruoli dell’utente (autorizzazione).

3. **Indipendenza dal Protocollo di Trasporto**:
	SAML può essere implementato su protocolli di trasporto diversi (ad esempio HTTP o SOAP).

4. **Supporto Multi-Dominio**:
	Permette l’interoperabilità tra domini diversi (ad esempio, autenticazione gestita da un dominio, ma accesso fornito in un altro).

### Principali attori nella comunicazione

**Service Provider (SP)**:
Fornisce servizi o risorse e utilizza le _assertions_ inviate dall’IdP per concedere l’accesso all’utente.

**Identity Provider (IdP)**:
Gestisce le identità degli utenti e fornisce _assertions_ sull’utente al Service Provider.

### Flusso di autenticazione

![[Pasted image 20241125214931.png]]![[Pasted image 20241125214939.png]]

#### <AuthnRequest /> 
Un <AuthnRequest /> è un messaggio XML inviato dal Service Provider (SP) all’Identity Provider (IdP) per richiedere l’autenticazione di un utente. È il primo passo di una tipica comunicazione SAML.

![[Pasted image 20241125220704.png]]
1. ID: Identificativo univoco della richiesta generato dal Service Provider per tracciarla.
2. Version: Versione del protocollo SAML, solitamente “2.0”.
3. IssueInstant: Timestamp in formato UTC che specifica quando la richiesta è stata generata.
4. Destination: URL dell’Identity Provider a cui la richiesta è destinata (interfaccia SAML del provider).
5. AssertionConsumerServiceURL: URL del Service Provider dove l’Identity Provider invierà il token SAML (la risposta).
6. <Issuer />:
	• Indica chi ha generato la richiesta (il Service Provider).
	• Serve a identificare la fiducia tra SP e IdP.
7. <Subject /> **(opzionale):** Indica l’utente che deve essere autenticato (può contenere un identificativo dell’utente).
8. <NameIDPolicy /> **(opzionale):** Specifica il livello di sicurezza richiesto per l’identificazione dell’utente.


![[Pasted image 20241125214959.png]]![[Pasted image 20241125215009.png]]

#### < Response />
La <Response/> SAML è il messaggio XML inviato dall’Identity Provider (IdP) al Service Provider (SP) ==contenente l’esito dell’autenticazione e altre informazioni correlate==. È un elemento fondamentale del protocollo SAML ed è critico per stabilire la validità di un’operazione di autenticazione.

![[Pasted image 20241125222219.png]]
1. **ID**: Identificatore unico del messaggio.
2. **Version**: Versione del protocollo SAML (es., 2.0).
3. **IssueInstant**: Timestamp in UTC che specifica quando la risposta è stata emessa.
4. **InResponseTo**: Identifica la richiesta di autenticazione associata (deve corrispondere all’ID della <AuthnRequest/> originale).
5. **Destination**: URL del Service Provider (endpoint dove la risposta deve essere processata).
6. **Status**: Indica lo stato dell’operazione (es., Success o eventuali errori).
7. **Issuer**: Identificativo univoco dell’IdP che emette la risposta.
8. **==Assertion==**: Contiene le informazioni dettagliate sull’utente e il contesto di autenticazione.

#### < Assertion />
L’Assertion è l’elemento contenuto nella <Response/> che fornisce informazioni dettagliate su:
- Chi è l’utente (identità).
- Il contesto in cui è avvenuta l’autenticazione.
- Eventuali attributi dell’utente utili per l’SP.

![[Pasted image 20241125222531.png]]
![[Pasted image 20241125222614.png]]
1. **ID**: Identificativo univoco dell’Assertion.
2. **Version**: Versione del protocollo SAML.
3. **IssueInstant**: Data e ora di emissione.
4. **Issuer**: Identifica l’IdP che ha validato l’utente.
5. **Subject**: Informazioni sull’utente autenticato.
6. **Conditions**: Condizioni temporali o contestuali che specificano la validità dell’asserzione.
	**AudienceRestriction**: Specifica per quali Service Provider è valida l’asserzione.
7. **AttributeStatement**: Elenca gli attributi dell’utente (es., email, ruolo, etc.) certificati dall’IdP.
8. **AuthnStatement**: Fornisce informazioni sul contesto e sul metodo di autenticazione.
	**AuthContext**: Specifica il metodo di autenticazione utilizzato (es., password, certificato).
9. **Signature**: Firma digitale dell’IdP per garantire l’integrità e l’autenticità dell’asserzione.



![[Pasted image 20241125215018.png]]

### E se mi sono già autenticato?

![[Pasted image 20241125215027.png]]
![[Pasted image 20241125215036.png]]![[Pasted image 20241125215045.png]]![[Pasted image 20241125215056.png]]

### Passi del flusso

1. **Richiesta dell’utente**:
	L’utente tenta di accedere a un servizio (Service Provider, SP) protetto.

2. **Controllo dello stato di autenticazione**:
	
	**Caso 1: L’utente non è autenticato**:
	Il Service Provider genera una richiesta di autenticazione (Authentication Request) e reindirizza l’utente verso l’Identity Provider (IdP).
	
	**Caso 2: L’utente è già autenticato (Single Sign-On attivo)**:
	Il Service Provider invia comunque una richiesta al IdP, ma l’IdP rileva che l’utente ha una sessione valida e salta la fase di autenticazione.

3. **Richiesta all’Identity Provider**:
	Il Service Provider inoltra l’utente all’IdP con una richiesta SAML, spesso usando un reindirizzamento tramite il browser dell’utente.

4. **Autenticazione presso l’Identity Provider (se necessario)**:
	
	**Caso 1: L’utente non è autenticato**:
	L’IdP autentica l’utente, ad esempio con username e password, biometria, o altri metodi.
	
	**Caso 2: L’utente è già autenticato**:
	L’IdP verifica lo stato della sessione dell’utente e riconosce che è già autenticato. Non richiede ulteriori credenziali.

5. **Generazione e invio dell’asserzione SAML**:
	L’IdP genera un’asserzione SAML firmata, contenente informazioni sull’utente (ad esempio, ID utente, ruoli e permessi) e la invia al Service Provider tramite il browser dell’utente.

6. **Validazione dell’asserzione SAML da parte del Service Provider**:
	Il Service Provider verifica l’integrità e l’autenticità dell’asserzione ricevuta (es. tramite chiavi pubbliche/chiavi condivise).

7. **Accesso al servizio**:
	L’utente viene autenticato presso il Service Provider e può accedere alle risorse richieste.


### Come facciamo a essere sicuri della validità dell'asserzione?
Riusciamo a essere sicuri della validità di una asserzione grazie a delle caratteristiche:
- La **firma digitale** : l’asserzione viene firmata digitalmente dall’Identity Provider (IdP)
- L'Identity Provider ha un **certificato** per riconoscere e validare l'IpD
- L'asserzione ha una **validità temporale** che aiutano a prevenire attacchi 
- Controlli sull'**Audience**, ovvero ci sono solo uno o più destinatari autorizzati
Queste sono le più importanti, in caso di maggiore dettaglio ci possono essere ulteriori controlli.

### Esempi di sistemi che usano SAML

- [[SPID]]
- [[Shibboleth]]
  
