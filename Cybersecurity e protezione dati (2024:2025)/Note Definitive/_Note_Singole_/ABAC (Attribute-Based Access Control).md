**Attribute-Based Access Control (ABAC)** è un approccio avanzato al controllo degli accessi che si basa su ==attributi== e ==politiche specifiche== per determinare i permessi di accesso alle risorse.

![[Screenshot 2024-12-11 at 14.25.12.png]]

Gli attributi rappresentano **informazioni contestuali** o proprietà relative a:

1. **Utente** (User): Identità, ruolo, dipartimento, ecc.
2. **Ambiente** (Environment): Contesto come posizione, ora del giorno, rete utilizzata.
3. **Risorsa** (Resource): Tipo di documento, classificazione, proprietà specifiche della risorsa.

Dopo aver raccolto gli attributi da varie fonti, vengono scritte le **==Policy==**

**Policy**:
	Le regole di accesso sono definite come **politiche** che combinano attributi legati all'ambiente per determinare se l’accesso deve essere **permesso** o **negato**.

Esempio di policy:
![[Pasted image 20241211143015.png]]

### Funzionamento ABAC

- Gli attributi del soggetto, dell’ambiente e della risorsa vengono considerati da un motore di autorizzazione (Authorization Engine).

- Questo motore confronta gli attributi forniti con una serie di politiche di accesso definite dall’organizzazione.

- Una **politica** in ABAC è una regola o un insieme di regole (policy) che stabiliscono condizioni logiche del tipo: “Permetti l’accesso a (managers) alle (risorse di tipo X) se (l’orario è compreso tra le 9:00 e le 18:00) e (l’utente è collegato dalla rete interna), a meno che (una specifica condizione non sia soddisfatta)”.

- Queste politiche sono molto più granulari e flessibili rispetto a modelli come RBAC (Role-Based Access Control), poiché permettono di combinare dinamicamente molteplici attributi invece di basarsi su ruoli prestabiliti.

- L’Authorization Engine valuta se, dati tutti gli attributi in gioco e le regole definite, la richiesta di accesso debba essere concessa (PERMIT) o negata (DENY).

### Vantaggi ABAC

- **Maggiore Flessibilità:** Non si è limitati a ruoli statici. È possibile aggiungere o modificare attributi e politiche senza dover ripensare l’intera struttura dei ruoli.

- **Contesto Dinamico:** Le decisioni di accesso possono cambiare in base al contesto (orario, luogo, stato di sicurezza del sistema) e non solo in base all’identità dell’utente.

- **Fine Granularità:** Permette di definire politiche molto dettagliate, ad esempio: “Permetti ad un manager di accedere ad un documento solo se è all’interno dell’ufficio e in orario lavorativo, e se il documento non è classificato come segreto”.