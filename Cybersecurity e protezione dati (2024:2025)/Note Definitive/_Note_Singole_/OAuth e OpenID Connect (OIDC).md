
# Autori coinvolti in OAuth e OpenID

0. **Protected Resources**: sono le informazioni presenti nel servizio personali dell'utente.

1. **Resource Owner:** L’utente che possiede le risorse protette e concede l’accesso.

2. **Client (Third-party Application):** Applicazione che richiede accesso alle risorse per conto dell’utente.

3. **Authorization Server:** Server che autentica il Resource Owner e rilascia il token di accesso.

4. **Resource Server:** Server che ospita le risorse protette e verifica il token per fornire l’accesso.

![[Pasted image 20241126101818.png]]

# OpenID Connect (OIDC)

OpenID Connect è un **livello di IDENTITÀ** costruito sopra il protocollo OAuth 2.0. 
Si occupa dell’**AUTENTICAZIONE DEGLI UTENTI** e **permette alle applicazioni di VERIFICARE L'IDENTITÀ DEGLI UTENTI e ottenere informazioni** basilari del profilo.

### Caratteristiche generiche

- **Riutilizzo delle credenziali:** Permette a un servizio di sfruttare le credenziali di un altro per autenticare un utente.
- **Autenticazione semplice, sicura e decentralizzata:** Offre un metodo standardizzato per verificare l’identità dell’utente, migliorando l’interoperabilità tra servizi.

### Vantaggi

- **SSO (Single Sign-On):** Un’unica autenticazione permette l’accesso a più applicazioni.
- **User-Centric:** Gli utenti possono decidere quali dati condividere con le applicazioni, migliorando la privacy.
- **Interoperabilità:** Ampio supporto da provider come Google, Microsoft, ecc.
- **Sicurezza:** Si basa sulle solide meccaniche di OAuth 2.0.

### Caratteristiche implementative
OpenID Connect viene tipicamente implementato nei flussi di autorizzazione di OAuth 2.0, in particolare nel [[Authorization Code Grant Flow OAuth]] e nel [[Authorization Code Grant Flow with PKCE OAuth]], per fornire autenticazione utente sicura.


1. **ID Token**: Un token specifico che contiene informazioni sull’utente autenticato. Questo token è firmato digitalmente per garantire la sua integrità e autenticità.
   
   L’**ID Token** è un **JSON Web Token (JWT)** che contiene informazioni codificate sull’**utente**
   
   **Campi principali dell’ID Token**:![[Pasted image 20241126121551.png]]
	   1. **sub**: Identificativo unico del soggetto autenticato.
	   2. **iss**: Indica il provider OpenID che ha rilasciato il token (es. https://provider.com).
	   3. **aud**: Indica il client (applicazione) autorizzato a ricevere il token.
	   4. **auth_time**: Momento in cui l’utente si è autenticato.
	   5. **iat**: Data e ora di emissione del token (issued at).
	   6. **exp**: Data e ora di scadenza del token (expiration).
	   7. **Signature**: Firma crittografica del token per garantirne l’autenticità.

3. **UserInfo Endpoint**: Un endpoint dedicato che permette di recuperare ulteriori informazioni sul profilo dell’utente autenticato.

4. **Standard Set of Scopes**: Definizione di ambiti standard per accedere a specifiche informazioni sull’identità, come openid, email, o profile.

5. **Standardized Implementation**: OpenID Connect garantisce interoperabilità tra diversi provider (ad esempio, Google, Microsoft, ecc.).

### Flusso di OpenID Connect
![[Pasted image 20241126121851.png]]![[Pasted image 20241126121904.png]]![[Pasted image 20241126121919.png]]![[Pasted image 20241126121933.png]]![[Pasted image 20241126121949.png]]![[Pasted image 20241126122003.png]]


# OAuth 2.0

OAuth è un **protocollo di AUTORIZZAZIONE** che **consente** alle applicazioni di terze parti di **accedere a RISORSE protette senza dover condividere le credenziali** dell’utente.

### Flusso di autenticazione

1. L’utente (Resource Owner) concede il permesso a un’applicazione (Client Application).
2. L’applicazione invia una richiesta di autorizzazione al server di autorizzazione.
3. Il server di autorizzazione rilascia un **Access Token** che l’applicazione può usare per accedere alle risorse protette.
4. Il Resource Server verifica il token e concede l’accesso.

### Flussi di autenticazione

- [[Authorization Code Grant Flow OAuth]] : usato per applicazioni web con front-end e back-end.
- [[Authorization Code Grant Flow with PKCE OAuth]] : usato per native mobile app.
- [[Resource Owner Password Grant OAuth]] : Client application e Authorization Server sono della stessa compagnia, perciò le informazioni sono mandate direttamente.
- [[Client Credential Grant OAuth]] : usato dove il client accede alle proprie risorse salvate in locale, non coinvolgendo l'utente.
- [[Device Flow OAuth]] : usato per dispositivi senza browser e con input limitati.

### Esercizi svolti in classe
![[Pasted image 20241126120621.png]]![[Pasted image 20241126122042.png]]

# Differenze tra OpenID Connect e OAuth
| **Caratteristica**           | **OAuth**                                                              | **OpenID Connect (OIDC)**                                                                |
| ---------------------------- | ---------------------------------------------------------------------- | ---------------------------------------------------------------------------------------- |
| **Scopo**                    | Autorizzare l'accesso a risorse protette                               | Autenticare l'identità dell'utente                                                       |
| **Tipo di token**            | Access Token                                                           | ID Token (in aggiunta all'Access Token)                                                  |
| **Focus**                    | Permettere a terze parti di accedere a dati o API                      | Verificare chi è l'utente (autenticazione)                                               |
| **Informazioni sull'utente** | Non fornisce informazioni sull'utente                                  | Fornisce informazioni sull'utente (es. nome, email)                                      |
| **Implementazione**          | Usato per accedere a risorse specifiche (es. API)                      | Usato per Single Sign-On (SSO) e per rendere disponibili account utente su altri sistemi |
| **Esempio d'uso**            | Un'app come Spotify accede ai tuoi dati su Facebook (es. elenco amici) | Accedi a un sito (es. Medium) con il tuo account Google                                  |
| **Estensione**               | Protocollo di autorizzazione standard                                  | Basato su OAuth 2.0 con un livello aggiuntivo di autenticazione                          |
| **Sicurezza**                | Garantisce l'accesso sicuro alle risorse senza condividere la password | Verifica l'identità dell'utente e protegge i dati personali                              |