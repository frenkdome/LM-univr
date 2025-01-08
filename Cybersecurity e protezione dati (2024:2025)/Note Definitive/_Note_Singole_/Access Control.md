![[Pasted image 20241204182252.png]]

L’Access Control è un elemento centrale della sicurezza informatica che si occupa di **prevenire l’uso non autorizzato delle risorse**, incluse le modalità di utilizzo scorrette o non consentite.

Le operazioni principali svolte dall'access control sulle persone e i gruppi sono:
- **Autenticazione al sistema** : L’azione di verificare l’identità degli utenti.
- **Dare i permessi**: Assegnazione di permessi per accedere a specifiche risorse.

### Elementi coinvolti nell'Access Control

- **Soggetto (Subject)**: Un’==entità== (utente o processo) ==che accede== a un oggetto.
- **Oggetto (Object)**: Una ==risorsa controllata== (file, directory, programma, ecc.).
- **Diritto di Accesso (Permission)**: Specifica ==come un soggetto può interagire con un oggetto== (es. lettura, scrittura, esecuzione, cancellazione).

### Componenti principali dell'Access Control

![[Pasted image 20241205142721.png]]

#### **Access Control Policies (Policy di Accesso)**
Le policy di accesso definiscono “chi può fare cosa” all’interno di un sistema. Si tratta di regole scritte che specificano le autorizzazioni per gli utenti, i gruppi o i ruoli e determinano come l’accesso alle risorse deve essere controllato.

**Compiti**:
- Stabiliscono i criteri di accesso.
- Possono essere statiche o dinamiche.

• **Esempi**:
- Una policy può stabilire che solo i membri di un gruppo amministrativo possano accedere ai dati sensibili.
- Un’altra policy può indicare che l’accesso è permesso solo durante specifici orari lavorativi.

#### **Access Control Model (Modello di Accesso)**
Il modello di accesso è una rappresentazione formale che collega le **policy** alle risorse e alle richieste di accesso. Fornisce una struttura per l’applicazione delle policy.

**Compiti**:
- Specifica come le regole vengono tradotte in decisioni operative.
- Funziona come un intermediario tra le policy definite e la loro implementazione tecnica.

**Tipologie di Modelli**
1. [[DAC (Discretionary Access Control)]]:
	Accesso basato sull'==identità== dei soggetti che richiedono il servizio.

2. [[MAC (Mandatory Access Control)]]:
	Accesso basato su ==regole di sicurezza== impostate dall'amministratore di sistema.

3. [[RBAC (Role-Based Access Control)]]:
	Accesso basato sui ==ruoli== per assegnare diritti di accesso.

4. [[ABAC (Attribute-Based Access Control)]]:
	Accesso basato su ==attributi== dinamici legati all’oggetto, al soggetto e al contesto.

#### **Access Control Mechanism (Meccanismo di Accesso)**
Il meccanismo di accesso è la parte tecnica che implementa le decisioni di accesso secondo il modello scelto. Include algoritmi, componenti software e hardware per applicare le policy e gestire le richieste.

**Compiti**:
- Effettua verifiche in tempo reale per garantire che solo gli utenti autorizzati accedano alle risorse.
- Integra componenti specifici del sistema come PEP, PDP, PAP e PIP (vedi sotto).

**Componenti Principali**:

1. **PEP (Policy Enforcement Point)**:
	Punto in cui viene effettivamente applicata la decisione di accesso.
	Esempio: Bloccare o permettere l’accesso a un file.

2. **PDP (Policy Decision Point)**:
	Punto decisionale che determina se l’accesso deve essere consentito o negato.
	Esempio: Valutare una richiesta in base alle policy.

3. **PAP (Policy Administration Point)**:
	Punto di amministrazione per creare e gestire le policy.

4. **PIP (Policy Information Point)**:
	Punto che fornisce informazioni di supporto per le decisioni, come attributi utente o dati di contesto.

Le politiche di controllo vengono solitamente scritte con il linguaggio standardizzato [[XACML]].

### Esempi esercizi fatti in classe 
![[Pasted image 20241205185150.png]]
