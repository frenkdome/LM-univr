XACML è uno standard OASIS basato su XML progettato specificamente per ==definire e applicare politiche di controllo degli accessi== in modo centralizzato. 

### Caratteristiche

| **Caratteristica**                                       | **Descrizione**                                                                                                                       |
| -------------------------------------------------------- | ------------------------------------------------------------------------------------------------------------------------------------- |
| **XML-based Policy Language**                            | Utilizza un linguaggio basato su **XML** per definire le politiche di accesso in maniera standardizzata.                              |
| **XML-based Request and Response Language**              | Definisce il formato per le **richieste** di accesso e le **risposte** ai controlli, usando XML.                                      |
| **Standard data-types, functions, combining algorithms** | Supporta **tipi di dati standard** (stringhe, numeri, date), **funzioni** logiche e algoritmi per combinare decisioni.                |
| **Architettura definita**                                | Fornisce un'**architettura chiara** con i componenti chiave come PEP, PDP, PIP, PAP.                                                  |
| **Privacy profile e RBAC profile**                       | Supporta profili avanzati come il **Privacy Profile** (per esigenze specifiche di privacy) e il **RBAC** (Role-Based Access Control). |

### Architettura

![[Pasted image 20241215110510.png]]

| **Componente**      | **Descrizione**                                                                                                 |
| ------------------- | --------------------------------------------------------------------------------------------------------------- |
| **PEP**             | *Policy Enforcement Point*: Intercetta le richieste e **applica** la decisione del PDP (permit/deny).           |
| **PDP**             | *Policy Decision Point*: Valuta la **richiesta** di accesso in base alle politiche definite.                    |
| **PAP**             | *Policy Administration Point*: Gestisce e crea le **politiche di accesso** da applicare al sistema.             |
| **Context Handler** | È un intermediario che converte le richieste native nel formato canonico per XACML.                             |
| **PIP**             | *Policy Information Point*: Fornisce informazioni e **attributi** necessari per la valutazione delle richieste. |

### Flusso di lavoro

1. **Creazione della politica**: Le politiche di accesso vengono definite tramite il PAP.
2. **Invio della richiesta**: Il PEP invia una richiesta di autorizzazione.
3. **Risoluzione degli attributi**: Il Context Handler recupera gli attributi richiesti tramite il PIP.
4. **Valutazione della politica**: Il PDP valuta la richiesta usando le politiche applicabili.
5. **Decisione**: Il PDP invia una risposta con Permit, Deny, Indeterminate o NotApplicable.
6. **Esecuzione della decisione**: Il PEP applica la decisione e implementa le eventuali **Obligations**.

![[Pasted image 20241215111231.png]]

### Componenti delle politiche XACML
XACML definisce le politiche usando una struttura **gerarchica** basata su **XML**.

1. **PolicySet**:
	Raggruppa più **Policy** o altri **PolicySet**. 
	Usa algoritmi di combinazione per determinare il risultato finale.

2. **Policy**:
	Contiene uno o più **Target** e **Rule**.
	Fornisce l’ambito delle politiche applicabili. Contiene:
	
	 1. **`<Policy>`**  
	   - È l'elemento principale che il PDP (Policy Decision Point) valuta per prendere decisioni di autorizzazione.  
	   - Contiene `<Target>` per determinare se la politica si applica alla richiesta.
	
	2. **`<Target>`**  
	   - Definisce condizioni semplici su soggetti, risorse, azioni e ambiente.  
	   - Serve per **filtrare rapidamente** le richieste che non sono applicabili.
	
	3. **`<Rule>`**  
	   - Esprime singole regole di accesso, ognuna con un effetto (`Permit` o `Deny`) e condizioni opzionali.  
	   - Multiple regole possono coesistere all'interno della stessa politica.
	
	4. **`<ObligationExpression>`**  
	   - Specifica **obblighi** o azioni che devono essere eseguiti dal PEP (Policy Enforcement Point) quando la decisione viene applicata.  
	   - Esempio: *Inviare un'email di notifica quando un record viene accesso*.
	
	```xml
<Policy PolicyId="example-policy-1" RuleCombiningAlgId="urn:oasis:names:tc:xacml:1.0:rule-combining-algorithm:permit-overrides">
    <Description>Policy che permette l'accesso a documenti dalle 8:00 alle 17:00</Description>

    <!-- Target: Definisce quando la policy è applicabile -->
    <Target>
        <AnyOf>
            <AllOf>
                <Match MatchId="urn:oasis:names:tc:xacml:1.0:function:string-equal">
                    <AttributeValue DataType="http://www.w3.org/2001/XMLSchema#string">document</AttributeValue>
                    <AttributeDesignator AttributeId="urn:oasis:names:tc:xacml:1.0:resource:resource-id" DataType="http://www.w3.org/2001/XMLSchema#string"/>
                </Match>
            </AllOf>
        </AnyOf>
    </Target>

    <!-- Rule: Una regola applicabile -->
    <Rule RuleId="rule-1" Effect="Permit">
        <Condition>
            <Apply FunctionId="urn:oasis:names:tc:xacml:1.0:function:time-in-range">
                <AttributeValue DataType="http://www.w3.org/2001/XMLSchema#time">08:00:00</AttributeValue>
                <AttributeValue DataType="http://www.w3.org/2001/XMLSchema#time">17:00:00</AttributeValue>
                <AttributeDesignator AttributeId="urn:oasis:names:tc:xacml:1.0:environment:current-time" DataType="http://www.w3.org/2001/XMLSchema#time"/>
            </Apply>
        </Condition>
    </Rule>

    <!-- Obligation: Azione da compiere se la regola è soddisfatta -->
    <ObligationExpression FulfillOn="Permit" ObligationId="urn:example:log-access">
        <AttributeAssignmentExpression AttributeId="urn:example:action:log">
            <AttributeValue DataType="http://www.w3.org/2001/XMLSchema#string">Accesso concesso durante l'orario lavorativo</AttributeValue>
        </AttributeAssignmentExpression>
    </ObligationExpression>
</Policy>
	```
	
	![[Pasted image 20241215111800.png]]

3. **Target**
	Componente utilizzato per associare una risorsa a una politica applicabile. Viene usato per trovare una policy che fa una richiesta.
	
	Contiene:
	- `<AnyOf>`:  
       Rappresenta una **disgiunzione logica** tra più gruppi di condizioni.  
     - `<AllOf>`:  
       Rappresenta una **congiunzione logica** di condizioni. Ogni condizione deve essere soddisfatta.  
     - `<Match>`:  
       Specifica una singola **condizione** contro **subject**, **resource** e **action**.  
       
	```xml
<Target>
    <AnyOf>
        <AllOf>
            <!-- Match sulla risorsa -->
            <Match MatchId="urn:oasis:names:tc:xacml:1.0:function:string-equal">
                <AttributeValue DataType="http://www.w3.org/2001/XMLSchema#string">document</AttributeValue>
                <AttributeDesignator AttributeId="urn:oasis:names:tc:xacml:1.0:resource:resource-id" DataType="http://www.w3.org/2001/XMLSchema#string"/>
            </Match>
            <!-- Match sull'azione -->
            <Match MatchId="urn:oasis:names:tc:xacml:1.0:function:string-equal">
                <AttributeValue DataType="http://www.w3.org/2001/XMLSchema#string">read</AttributeValue>
                <AttributeDesignator AttributeId="urn:oasis:names:tc:xacml:1.0:action:action-id" DataType="http://www.w3.org/2001/XMLSchema#string"/>
            </Match>
        </AllOf>
    </AnyOf>
</Target>
	```
	
	![[Pasted image 20241215114630.png]]

4. **RuleSet**
	Permette di raggruppare più **Rule**.

5. **Rule**:
	Elemento fondamentale che contiene :
	
	1. **`<Target>`**  
	   - Specifica le condizioni per cui la regola si applica. Determina se una richiesta è rilevante per questa regola.
	   - Esprime condizioni come soggetti, risorse, azioni e ambiente.  
	   - Serve a **filtrare** rapidamente richieste non rilevanti.
	
	2. **`<Effect>`**  
	   - Valore associato alla regola quando la condizione è vera.  
	   - Può essere:
	     - `Permit`: La richiesta viene accettata.  
	     - `Deny`: La richiesta viene rifiutata.
	
	3. **`<Condition>`**  
	   - Espressione **booleana** utilizzata per raffinare ulteriormente la regola.  
	   - Consente logica avanzata come orari specifici, attributi di ambiente, o restrizioni contestuali.
	
	4. **`<Obligation>`**  
	   - (Facoltativo) Azioni che devono essere intraprese come parte della decisione. 
	   - Esempio: Loggare un accesso riuscito, inviare una notifica, o eseguire operazioni di audit.
	
	```xml
<Rule RuleId="rule-allow-read" Effect="Permit">
    <Description>Regola che permette la lettura dei documenti a utenti specifici</Description>
    <Target>
        <AnyOf>
            <AllOf>
                <!-- Controllo sull'utente -->
                <Match MatchId="urn:oasis:names:tc:xacml:1.0:function:string-equal">
                    <AttributeValue DataType="http://www.w3.org/2001/XMLSchema#string">alice</AttributeValue>
                    <AttributeDesignator AttributeId="urn:oasis:names:tc:xacml:1.0:subject:subject-id" DataType="http://www.w3.org/2001/XMLSchema#string"/>
                </Match>
            </AllOf>
        </AnyOf>
    </Target>
    <Condition>
        <!-- Condizione aggiuntiva: orario specifico -->
        <Apply FunctionId="urn:oasis:names:tc:xacml:1.0:function:time-in-range">
            <AttributeValue DataType="http://www.w3.org/2001/XMLSchema#time">08:00:00</AttributeValue>
            <AttributeValue DataType="http://www.w3.org/2001/XMLSchema#time">18:00:00</AttributeValue>
            <AttributeDesignator AttributeId="urn:oasis:names:tc:xacml:1.0:environment:current-time" DataType="http://www.w3.org/2001/XMLSchema#time"/>
        </Apply>
    </Condition>
</Rule>
	```
	
	![[Pasted image 20241215113257.png]]![[Pasted image 20241215113317.png]]![[Pasted image 20241215120455.png]]

### Rule Combining Algorithms
Questi algoritmi determinano come combinare i risultati delle singole regole per produrre la decisione finale. Vengono specificate nelle **`<Rule>`**  

| **Algoritmo**              | **Descrizione**                                                                                      |
| -------------------------- | ---------------------------------------------------------------------------------------------------- |
| ==`Deny-Overrides`==           | Se **qualunque regola** restituisce `Deny`, il risultato finale è `Deny`, ignorando le altre regole. |
| ==`Permit-Overrides`==         | Se **qualunque regola** restituisce `Permit`, il risultato finale è `Permit`, ignorando le altre.    |
| ==`First-Applicable`==         | Viene applicata la **prima regola** valutata come `Permit` o `Deny`.                                 |
| ==`Only-One-Applicable`==      | Viene applicata **solo una policy** se è l'unica applicabile alla richiesta.                         |
| `Ordered-Deny-Overrides`   | Variante di `Deny-Overrides` che rispetta l'**ordine** delle regole definite.                        |
| `Ordered-Permit-Overrides` | Variante di `Permit-Overrides` che rispetta l'**ordine** delle regole definite.                      |
| `Deny-Unless-Permit`       | Se **nessuna regola** restituisce `Permit`, il risultato è `Deny`.                                   |
| `Permit-Unless-Deny`       | Se **nessuna regola** restituisce `Deny`, il risultato è `Permit`.                                   |

### Formato delle Request in XACML
La _Request_ è il messaggio inviato al **Policy Decision Point (PDP)** che contiene le informazioni necessarie per determinare se un’azione è consentita o negata in base alle politiche definite.

**Struttura:**

| Componente         | Descrizione                                                                |
| ------------------ | -------------------------------------------------------------------------- |
| `<Request>`        | Elemento principale che rappresenta una richiesta di accesso.              |
| `<Attributes>`     | Contiene gli attributi relativi a soggetto, risorsa, azione e ambiente.    |
| `Category`         | Specifica la categoria degli attributi (es. subject, action, environment). |
| `<Attribute>`      | Definisce un singolo attributo, con `AttributeId` e il valore associato.   |
| `<AttributeValue>` | Valore effettivo dell'attributo (es. "GET", "pamoda").                     |
| `<Content>`        | (Opzionale) Incapsula la risorsa stessa nella richiesta.                   |
|                    |                                                                            |

**Esempio:**

```xml
<Request xmlns="urn:oasis:names:tc:xacml:3.0:core:schema:wd-17" CombinedDecision="false">
    <Attributes Category="urn:oasis:names:tc:xacml:1.0:subject-category:access-subject">
        <Attribute AttributeId="urn:oasis:names:tc:xacml:1.0:subject:subject-id" IncludeInResult="false">
            <AttributeValue DataType="http://www.w3.org/2001/XMLSchema#string">pamoda</AttributeValue>
        </Attribute>
    </Attributes>
    <Attributes Category="urn:oasis:names:tc:xacml:3.0:attribute-category:action">
        <Attribute AttributeId="urn:oasis:names:tc:xacml:1.0:action:action-id" IncludeInResult="false">
            <AttributeValue DataType="http://www.w3.org/2001/XMLSchema#string">GET</AttributeValue>
        </Attribute>
    </Attributes>
</Request>
```


### Formato delle Response in XACML
La _Response_ è la risposta generata dal **Policy Decision Point (PDP)** dopo l’elaborazione della _Request_. Contiene l’autorizzazione finale e obblighi da adempiere.

**Struttura:**

| Componente            | Descrizione                                                              |
|-----------------------|--------------------------------------------------------------------------|
| `<Response>`          | Elemento principale che incapsula la risposta PDP.                      |
| `<Result>`            | Contiene il risultato dell'elaborazione della richiesta.                |
| `<Decision>`          | Indica la decisione: Permit, Deny, Indeterminate, Not Applicable.       |
| `<Status>`            | Fornisce informazioni sullo stato della decisione (es. errori).         |
| `<Obligations>`       | (Opzionale) Specifica obblighi che il PEP deve eseguire.                |
| `<Obligation>`        | Un obbligo specifico con `ObligationId` e i dettagli necessari.         |
| `<AttributeAssignment>` | Assegna valori specifici associati all'obbligo (es. email, logging).  |

**Esempio:**

```xml
<Response xmlns="urn:oasis:names:tc:xacml:3.0:core:schema:wd-17">
    <Result>
        <Decision>Permit</Decision>
        <Status>
            <StatusCode Value="urn:oasis:names:tc:xacml:1.0:status:ok"/>
        </Status>
        <Obligations>
            <Obligation ObligationId="email_obligation">
                <AttributeAssignment AttributeId="email" DataType="http://www.w3.org/2001/XMLSchema#string">admin@example.com</AttributeAssignment>
            </Obligation>
        </Obligations>
    </Result>
</Response>
```
