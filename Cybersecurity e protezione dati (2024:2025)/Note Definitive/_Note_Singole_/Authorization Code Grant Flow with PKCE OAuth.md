Variante del flusso Authorization Code, progettata per **applicazioni native (es. app mobile)**.

PKCE (Proof Key for Code Exchange) introduce una **chiave pubblica** per proteggere l’ottenimento del token anche su canali non sicuri .
- **Code Verifier**: token segreto in formato stringa lunga dai 43-128 caratteri.
- **Code Challenge**: ricavato dal code verifier -> BASE64URL(SHA256(Code Verifier))

![[Pasted image 20241126103634.png]]![[Pasted image 20241126103656.png]]![[Pasted image 20241126103713.png]]![[Pasted image 20241126104327.png]]![[Pasted image 20241126104454.png]]![[Pasted image 20241126104511.png]]![[Pasted image 20241126104530.png]]


### Differenze tra PKCE e il flusso standard

| **Caratteristica**                    | **OAuth 2.0 Authorization Code Grant** | **OAuth 2.0 con PKCE**               |
|---------------------------------------|----------------------------------------|---------------------------------------|
| **Sicurezza del codice di autorizzazione** | Non garantisce protezione contro intercettazioni | Aggiunge un controllo con Code Verifier e Challenge |
| **Richiede un client secret**         | Sì                                      | No (pensato per app pubbliche)        |
| **Code Verifier/Challenge**           | Non presente                           | Presente                              

### Utilizzi di PKCE

Il meccanismo di **Code Verifier** e **Code Challenge** si trova esclusivamente nel flusso PKCE ed è utilizzato principalmente nei seguenti scenari:

1. **App mobili (Native Apps):** Non possono mantenere un segreto client sicuro, quindi PKCE protegge il flusso.

2. **Single Page Applications (SPA):** Sono vulnerabili perché operano interamente sul browser dell’utente.

3. **Contesti di applicazioni pubbliche:** Dove non esiste un backend sicuro.
