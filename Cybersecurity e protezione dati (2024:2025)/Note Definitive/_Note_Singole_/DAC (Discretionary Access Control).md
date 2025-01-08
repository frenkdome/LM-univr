L'accesso alle risorse con modello viene permesso ==basandosi sull'identità degli utenti==.

Viene gestito tramite delle ==regole esplicite== : chi può / non può eseguire azioni su una certa risorsa.

**Discrezionalità**:
Gli utenti possono concedere o revocare i privilegi di accesso ad altri utenti.
Questo approccio rende il modello più flessibile ma, al tempo stesso, più vulnerabile ad errori o abusi da parte degli utenti.

I permessi vengono dati tramite una ==Access Control Matrix==
![[Pasted image 20241205145733.png]]

### Access Control Structures legate a DAC
- [[Access Control Matrix]]
- [[Access Control List]]
- [[Capability List]]

### Limitazioni 

1. **Gestione complessa in sistemi di grandi dimensioni**:
   - Gruppi dove ci sono tanti soggetti o oggetti
   - Gruppi dove i soggetti e gli oggetti vengono cambiati spesso

2. **Limitazioni legate alle rappresentazioni**
   - [[Access Control List]] : è difficile avere una overview dei permessi dati per un oggetto (soggetto)
   - [[Capability List]] : è difficile avere una overview dei permessi dati a un utente
