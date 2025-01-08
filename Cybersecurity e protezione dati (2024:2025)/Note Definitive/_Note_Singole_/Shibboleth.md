Shibboleth è un progetto del consorzio Internet2 che **facilita la condivisione di risorse e ricerche tra università e istituzioni**.
L'obiettivo è quello di consentire agli studenti, docenti e personale di accedere alle risorse di partner istituzionali senza creare ID e password separati per ciascuna organizzazione.

### Esempio di federazione

![[Pasted image 20241126095057.png]]
### Flusso di autenticazione

![[Pasted image 20241126095114.png]]

1. L’utente (**User Agent**) tenta di accedere a una risorsa offerta da un Service Provider (SP).
2. L’SP emette una richiesta di autenticazione Shibboleth e la inoltra al servizio WAYF o direttamente a un Identity Provider (IdP).
3. Se viene usato il servizio WAYF, l’utente seleziona il proprio IdP affiliato.
4. L’IdP identifica il principale (Principal) attraverso i metodi configurati.
5. Un messaggio di risposta (**SAML Response**) viene emesso dall’IdP e inviato all’SP.
6. L’SP può inviare una richiesta di attributi (**SAML AttributeQuery**) all’IdP per ottenere informazioni aggiuntive sull’utente (es. ruoli o permessi).
7. L’IdP risponde con un’asserzione SAML (**SAML Assertion**) contenente gli attributi richiesti.
8. In base alle informazioni ricevute, l’SP fornisce accesso alle risorse o restituisce un errore.

### Differenze con SAML puro?

• **WAYF (Where Are You From)**:
	Servizio aggiuntivo che semplifica la selezione dell’IdP da parte dell’utente, migliorando l’esperienza utente in contesti con più organizzazioni.

• **Focus accademico**:
	Principalmente usato in contesti educativi e di ricerca per facilitare la collaborazione tra istituzioni.