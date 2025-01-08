Viviamo in un mondo dove gli utenti per accedere a un servizio devono registrarsi, spesso riutilizzando le stesse password oppure inserendole sempre banali. Non si ha la percezione di pericolo, né la voglia di ricercare tool per aiutare il salvataggio di password.
In poche parole, ==si ha difficoltà a gestire le proprie informazioni==.
![[Pasted image 20241123135405.png]]

Una possibile informazione è quella di avere una **soluzione centralizzata**, sfruttando la nostra [[Identità digitale]] per accedere ai servizi.

![[Pasted image 20241123135624.png]]

Per gestire in modo centralizzato questi sistemi vengono usati [[Identity Management System (IDMS)]]

### Chi è coinvolto in questo processo?

- **==User==** 
	- **Definizione**: È l’entità per la quale ==vengono fatte “asserzioni”.==
	- **Ruolo**: L’utente è colui che vuole autenticarsi e accedere a una risorsa o servizio.
	- **Contesto**: L’utente fornisce le credenziali iniziali al sistema di Identity Provider.
	- **Esempio**: un dipendente che accede alla sua email aziendale o un utente che utilizza un servizio web.

- ==**Identity Provider (IdP)**==
	- **Definizione**: È l’entità che ==crea e gestisce asserzioni== sull’identità del soggetto.
	- **Ruolo**:
		- Autentica l’identità dell’utente.
		- Genera “asserzioni” che certificano l’identità e attribuzioni dell’utente (es., nome, ruolo, permessi).
	- **Funzionalità**: Fornisce le asserzioni ai Service Provider (parti affidatarie) affinché possano verificare e autorizzare l’accesso.
	- **Esempio**: Google come Identity Provider, utilizzato per il login su altri servizi web tramite “Accedi con Google”.

- ==**Service Provider (SP)**:==
	- **Definizione**: È l’entità che ==utilizza le asserzioni== dell’Identity Provider ==per autenticare== e autorizzare il soggetto.
	- **Ruolo**:
		- Consuma le asserzioni per verificare se l’utente ha i permessi necessari per accedere al servizio.
		- Affida la gestione dell’identità all’Identity Provider.
	- **Funzionalità**: Decide cosa l’utente può fare in base ai permessi dichiarati dall’asserzione.
	- **Esempio**: Un’applicazione aziendale come Microsoft Teams, che si affida a un Identity Provider per autenticare gli utenti.

### Cosa intendiamo quindi per SSO?
Il Single Sign-On è un **metodo di autenticazione centralizzata** che consente agli utenti di **autenticarsi una sola volta per accedere a tutte le risorse** e applicazioni autorizzate **senza dover inserire nuovamente le credenziali**.

#### Come funziona?

1. **Autenticazione iniziale**:
   L’utente esegue l’accesso tramite il sistema SSO utilizzando le proprie credenziali.
   Una volta autenticato, l’accesso è valido per tutte le risorse associate senza dover reinserire le credenziali.

2. **Identity Provider (IdP)**:
   L’Identity Provider è il sistema che gestisce l’identità dell’utente, archivia le informazioni di autenticazione e autorizzazione, e si occupa di autenticare l’utente quando richiesto da altre risorse.
   Per l’utente, il processo è trasparente: non si accorge che il provider sta autenticando nuovamente la sua identità.

3. **Accesso alle risorse**:
   Quando l’utente tenta di accedere a una nuova risorsa, il sistema SSO invia una richiesta all’Identity Provider, che verifica l’identità e concede l’accesso senza richiedere ulteriori login.

#### Esempio
![[Pasted image 20241123163810.png]]
Dopo questa operazione, se l'utente vuole accedere a un'altro applicativo che supporta google non serve effettuare il login nuovamente.

### Cosa intendiamo per Cross Domain SSO?
Il **Cross-Domain Single Sign-On (SSO)** è una funzionalità di autenticazione che permette a un utente di **accedere a più domini** o servizi web differenti **utilizzando un’unica autenticazione iniziale**.
![[Pasted image 20241123164922.png]]

### Chi gestisce le identità?
La **Federated Identity** è un **modello** in cui diverse organizzazioni ==raggiungono un accordo per condividere un sistema comune di gestione delle identità==. 
Questo consente agli utenti di utilizzare un’unica identità digitale per accedere a più sistemi, servizi o organizzazioni appartenenti alla federazione.

##### Vantaggi della Federated Identity
- Definisce degli standard di autenticazione tra le organizzazioni:
  Le organizzazioni coinvolte stabiliscono un **identificatore condiviso** per ogni utente, che viene riconosciuto da tutti i membri della federazione.
  
- Facilita il Single Sign-On (SSO):
  Gli utenti possono accedere ai servizi di tutti i membri della federazione con una singola autenticazione.
  
- Migliora la sicurezza:
  L’Identity Provider è responsabile della gestione della sicurezza delle credenziali, riducendo i rischi associati alla duplicazione delle informazioni.
  
- Riduce i costi di gestione e di mantenimento:
  Non è necessario che ogni organizzazione mantenga e gestisca separatamente i propri sistemi di gestione delle identità.
  
- Porta scalabilità:
  Ideale per ambienti con numerosi servizi distribuiti su diverse organizzazioni.

##### Protocolli usati nella Federated Identity
- [[SAML]]
- [[OAuth e OpenID Connect (OIDC)]]

