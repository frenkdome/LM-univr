 RBAC è un modello di controllo degli accessi in cui le ==autorizzazioni sono assegnate ai **ruoli**== piuttosto che direttamente agli utenti.

### Famiglia RBAC
È stato definito da Ravi Sandhu nel 1996 ed è diventato standard ANSI nel 2004. 

Versioni di RBAC:

1. **RBAC0 (Core RBAC)**:
	Include i concetti base di utenti, ruoli e permessi.
	Implementa un mapping utente-ruolo e ruolo-permesso.
	![[Pasted image 20241205193522.png]]

2. **RBAC1 (Hierarchical RBAC)**:
	Supporta gerarchie di ruoli, consentendo l’ereditarietà dei permessi.
	Esistono due tipi di gerarchie:
	- **Gerarchie generalizzate**: Supportano sia relazioni di ereditarietà che incroci.
	- **Gerarchie limitate**: Supportano solo un’ereditarietà lineare.
	![[Pasted image 20241211134547.png]]![[Pasted image 20241211134624.png]]
	Non devo associare tutti i permessi a ogni ruolo, posso fare ereditare dei permessi da altri ruoli con l'==ereditarietà==


3. **RBAC2 (Constrained RBAC)**:
	Introduce vincoli per imporre regole specifiche sulle associazioni utente-ruolo o ruolo-permesso.
	Ad esempio, **Separation of Duties (SoD)** per prevenire conflitti di interesse.

4. **RBAC3 (Unified RBAC)**:
	Combina RBAC1 e RBAC2, includendo gerarchie e vincoli.

### Caratteristiche dei ruoli
- Sono basati sui ruoli dei membri dell'azienda
- A ogni ruolo vengono assegnati dei permessi di accesso a delle risorse
- Agli utenti vengono assegnati 1/n ruoli
### Esempi di elementi coinvolti nelle interazioni
![[Pasted image 20241211135116.png]]
![[Pasted image 20241211135129.png]]

### Vantaggi di RBAC
- Efficienza nella gestione dei permessi:
	I permessi sono associati ai ruoli, riducendo la complessità e il rischio di errori.

• **Maggiore sicurezza**:
	I ruoli permettono di limitare gli accessi ai dati e alle risorse solo a chi ha una reale necessità.

• **Facilità di audit e compliance**:
	Le autorizzazioni e i ruoli possono essere documentati facilmente, semplificando il monitoraggio.

### Svantaggi di RBAC
- **Scarsa flessibilità in scenari dinamici**:
	Se i ruoli cambiano frequentemente, il modello diventa difficile da aggiornare.

- **Gestione complessa dei ruoli in grandi organizzazioni**:
	Troppi ruoli possono creare confusione e aumentare i costi amministrativi.

- **Necessità di progettazione accurata**:
	Un’implementazione efficace di RBAC richiede una mappatura ben pianificata dei ruoli e delle autorizzazioni. Potrebbero infatti essere aggiunti dei nuovi ruoli inutili perché ridondanti.

### Utilizzi di RBAC
- Utilizzato in sistemi di gestione delle risorse IT, come:
	- DBMS
	- Prodotti software commerciali
	- Piattaforme cloud (es. Microsoft Azure)

- È il modello preferito per grandi organizzazioni che necessitano di sicurezza e gestione rigorosa degli accessi.
	- Settore **Healthcare** (NHS)
	- Settore **Bancario e Finanziario**
	
