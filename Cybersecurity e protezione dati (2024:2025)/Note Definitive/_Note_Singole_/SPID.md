**SPID** (Sistema Pubblico di Identità Digitale) utilizza [[SAML]] 2.0 come protocollo per gestire l’autenticazione e lo scambio di informazioni di identità tra gli attori coinvolti (Identity Provider e Service Provider).

![[Pasted image 20241126092931.png]]

### Ruoli nel sistema SPID

0. **Agenzia per l'Italia Digitale (AgID):** 
   entità che monitora e accredita le entità che possono contribuire come Identity Provider. 

1. **Identity Provider (IdP):**
   È l’entità che autentica l’utente e fornisce le asserzioni SAML al Service Provider.
   Ad esempio: Poste Italiane, Aruba, TIM, ecc.

2. **Service Provider (SP):**
   È il servizio o l’applicazione che l’utente vuole utilizzare, come l’INPS, il sito dell’Agenzia delle Entrate, o altri portali della Pubblica Amministrazione.

3. **Attribute Provider**
   Certifica che gli attributi degli Identity Provider siano soddisfatti.

4. **Utente finale:**
   La persona fisica che desidera accedere a un servizio utilizzando il proprio account SPID.

### Quali sono i livelli di autenticazione con SPID?
• **Livello 1:** Autenticazione con nome utente e password.
• **Livello 2:** Autenticazione a due fattori.
• **Livello 3:** Autenticazione forte (es., smart card o token hardware).

### Come mai viene utilizzato SAML?

• **Interoperabilità:** SAML 2.0 è uno standard consolidato per la federazione delle identità e permette a diversi fornitori di servizi e identità di comunicare facilmente.

• **Sicurezza:** L’utilizzo di firme digitali e certificati garantisce autenticità e integrità.

• **Controllo centralizzato:** La gestione delle identità e dei livelli di autenticazione (SPID 1, 2 e 3) può essere standardizzata.