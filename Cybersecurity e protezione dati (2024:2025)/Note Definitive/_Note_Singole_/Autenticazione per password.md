È una delle ==forme più diffuse di autenticazione==, utilizzata per verificare l’identità di un utente e controllare l’accesso a sistemi informatici.

- Richiede di fornire solamente **username** e **password**
- Il sistema per autenticare confronta una password immessa dall'utente con quella memorizzata nel **file delle password** (di solito archiviata sotto forma di [[Hash]] per motivi di sicurezza).

-  Una volta verificata, l’identità dell’utente è confermata e il sistema può:
	- **Autorizzare l’accesso**: Concedere all’utente i permessi per utilizzare risorse o servizi.
	- **Generare audit log**: Registrare l’accesso e le attività dell’utente per scopi di monitoraggio e analisi (accountability).

### Fasi autenticazione per password

1. **Inserimento dei dati**:
	L’utente inserisce il proprio nome utente e password in un’interfaccia.

2. **Invio delle credenziali**:
	I dati vengono inviati dal client al **Directory Server** attraverso la rete.

3. **Confronto della password**:
	Il server confronta l’hash della password fornita con l’hash memorizzato nel file delle password.

4. **Autorizzazione dell’accesso**:
	Se la verifica ha successo, l’utente è autenticato e il sistema concede l’accesso.

![[Pasted image 20241119072254.png]]

### Problematiche legate all'utilizzo di password

- **Password overload:** gli utenti per ogni servizio devono fornire una password, perciò per chi non è dotato di tecnologie all'avanguardia come gestori di password, preferiscono l'utilizzo della stessa password per servizi diversi.
  ![[Pasted image 20241119080659.png]]
  
- **Predictable password**: si commenta da se'
  ![[Pasted image 20241119080801.png]]
  ![[Pasted image 20241119080822.png]]
  
- **Password reuse:** consiste nel problema di alcuni utenti di utilizzare sempre la stessa password per l'accesso ai servizi online.
  ![[Pasted image 20241119084658.png]]

### Conseguenze per gli utenti di queste problematiche
![[Pasted image 20241119111642.png]]

### Tipologie di attacchi su sistemi basati su password
Ogni categoria rappresenta un approccio diverso per compromettere la sicurezza di un sistema attraverso la manipolazione o il furto di credenziali di autenticazione.

![[Pasted image 20241119112309.png]]

**1. Offline Attacks**
	L’attaccante deve ottenere l’accesso fisico o remoto a un sistema per accedere a file di hash o database delle password.

**2. Active Online Attacks**
	L’attaccante interagisce direttamente con il sistema, tentando di indovinare le credenziali di accesso in tempo reale.

**3. Passive Online Attacks**
	Gli attacchi passivi mirano a catturare credenziali senza interagire direttamente con il sistema. Viene utilizzato lo “sniffing” per intercettare dati in transito sulla rete, mirando alle sessioni di login dell'utente.

**4. Non-Technical Attacks**
	Questi attacchi non richiedono competenze tecniche avanzate; l’obiettivo è manipolare l’utente per ottenere le credenziali. Sono spesso classificati come **ingegneria sociale (soprattutto al phishing)**.

### Come vengono crackate le password?
- [[Brute force]]: 
  L’attaccante utilizza software per indovinare tutte le possibili combinazioni di password in modo sistematico fino a trovare quella corretta.
  ![[Pasted image 20241119113004.png]]
  
- **Manual guessing:** 
  L’attaccante prova manualmente a indovinare la password utilizzando informazioni personali della vittima (es. nome, data di nascita, nomi di familiari, ecc.).
  ![[Pasted image 20241119120930.png]]
  
- Interception
  Le password vengono intercettate mentre sono trasmesse su una rete non sicura.
  Attacchi come [[Man-in-the-Middle(MITM)]] e [[Packet Sniffing]] rientrano in questa categoria.
  ![[Pasted image 20241119121522.png]]
  ![[Pasted image 20241119120941.png]]
  
- [[Shoulder Surfing]]
  L’attaccante osserva fisicamente un utente mentre digita la propria password.
  Questo può avvenire in ambienti pubblici o tramite videocamere nascoste.
  ![[Pasted image 20241119120954.png]]
  
- Stealing Passwords
  Password memorizzate in modo non sicuro vengono rubate.
  Questo include file di password non protetti o appunti scritti lasciati vicino ai dispositivi.
  ![[Pasted image 20241119121009.png]]
  
- Searching
  Gli attaccanti cercano informazioni sui sistemi IT per recuperare password memorizzate (ad esempio, file di configurazione, database compromessi, o cache del browser).
  ![[Pasted image 20241119121020.png]]
  
- Using [[Keylogger]]
  Malware o hardware installati catturano i tasti digitati da un utente, inclusi username e password.
  ![[Pasted image 20241119121032.png]]
  
- [[Ingegneria Sociale]]
  Manipolazione psicologica per convincere gli utenti a rivelare le proprie password.
  Esempi includono **phishing**, **pretexting** o **vishing**.
  ![[Pasted image 20241119121045.png]]
  

### Come vengono salvate nei sistemi le password?
Le password vengono salvate in modo diverso ==in base al sistema operativo==.
#### Windows
Windows per salvare le password sfrutta dei **SAM Database**

##### Cosa intendiamo per SAM?
Il **Security Account Manager (SAM)** è il database principale in cui Windows memorizza gli hash delle password degli utenti locali.

È un file situato in:
  - C:\Windows\System32\config\SAM
  - HKLM\SAM (HKEY_LOCAL_MACHINE\SAM). -> REGISTRO DI SISTEMA

SAM è protetto utilizzando l’API Windows DPAPI (Data Protection API), che cifra i dati. Questo dovrebbe renderlo inaccessibile durante l’esecuzione del sistema operativo, ma strumenti di attacco possono aggirare questa protezione.

**Caratteristiche**:
- Le password non vengono memorizzate in chiaro, ma come hash (ad esempio NTLM o LM).

**Vulnerabilità**:
- Un attaccante può accedere al SAM montando il disco da un sistema operativo esterno.
- Strumenti come **Mimikatz** o **pwdump** possono estrarre gli hash delle password dal SAM per ulteriori attacchi (es. brute force o rainbow table).


##### Come vengono Hashate le password su Windows?
SAM non memorizza le password in chiaro, ma bensì come Hash.
![[Pasted image 20241120143850.png]]

Queste possono essere cifrate in due diversi modi:
- LM
- NTLM
![[Pasted image 20241120144004.png]]

**Attacco sfruttando il meccanismo NTLM** : ==Pass-the-hash==
![[Pasted image 20241120181948.png]]
**Pass-the-Hash (PTH)** è una tecnica utilizzata per compromettere i sistemi Windows sfruttando il protocollo **NTLM** (un protocollo di autenticazione ancora utilizzato, ma considerato insicuro). Questo attacco è basato sul meccanismo **challenge-response**, tipico dell’autenticazione NTLM

**Fasi dell’attacco**

1. **Accesso iniziale**:
	 L’attaccante ottiene accesso alla macchina vittima (ad esempio, tramite malware o credenziali compromesse).
	 Una volta entrati nel sistema, vengono estratti gli hash NTLM memorizzati nel SAM database o nella memoria.

2. **Autenticazione falsa**:
	L’attaccante invia una richiesta di autenticazione a un server o a una macchina remota (es. condivisore di rete). Viene utilizzato l’hash della password rubata per rispondere al challenge del server.

3. **Accesso al sistema remoto**:
	Il server accetta l’hash rubato come valido, concedendo all’attaccante l’accesso al sistema remoto come se fosse il legittimo proprietario delle credenziali.

#### Linux
Linux gestisce due file per salvare le password: **/etc/passwd** e **/etc/shadow**

##### /etc/passwd
Un file leggibile da tutti gli utenti del sistema, che contiene informazioni sugli account, ma **non le password**. Una volta conteneva anche gli hash, ma ora sono stati spostati su /etc/shadow.

![[Pasted image 20241120144856.png]]

##### /etc/shadow
Contiene gli hash delle password ed è accessibile solo dall’utente root.

Ogni riga rappresenta un account utente e il suo hash della password, insieme ad altre informazioni come la data di scadenza della password.

![[Pasted image 20241120144914.png]]
##### Come vengono Hashate le password su Linux?
Le password su Linux, nelle ultime versioni le password vengono hashate di default con l'algoritmo **SHA-512**, dimostrandosi molto più sicuri della codifica effettuata su Windows.

![[Pasted image 20241120145416.png]]


#### MacOS
##### File di Configurazione e Memorizzazione

**Directory Services Database**:
macOS utilizza un sistema centralizzato chiamato **Open Directory** per gestire gli account utente.
Gli hash delle password sono memorizzati in un database specifico, crittografato e accessibile solo da root o tramite API di sistema.

**File /etc/passwd**:
Simili a Linux, macOS ha un file **/etc/passwd**, ma:
- Contiene solo informazioni base sugli utenti, come nome e ID.
- Non memorizza hash delle password.

**Non è presente /etc/shadow**
Le password hashate sono conservate in un **database separato crittografato**, non visibile direttamente agli utenti, migliorando la sicurezza rispetto a /etc/shadow di Linux.

#### Keychain Access
macOS introduce il **Keychain**, un sistema dedicato per la gestione sicura delle password degli utenti.

**Caratteristiche del Keychain**:
- Memorizza credenziali, chiavi private, certificati e altre informazioni sensibili in un file crittografato.
- È protetto dalla password dell’utente o dall’accesso biometrico (Touch ID o Face ID nei dispositivi supportati).
- Accessibile tramite un’applicazione grafica (Keychain Access) o tramite API per gli sviluppatori.

**Keychain e Sicurezza**:
- I dati sono cifrati con **AES-256**, utilizzando chiavi legate all’account utente.
- Ogni utente ha uno o più keychain, con quello principale legato alla password di accesso al sistema.

**Vantaggi del Keychain**:
- Riduce la necessità di memorizzare manualmente le password.
- Permette il riempimento automatico delle credenziali nei browser e nelle applicazioni.


#### Tipologie di Hash Utilizzate

Gli hash delle password su macOS sono generati utilizzando **PBKDF2 (Password-Based Key Derivation Function 2)** con SHA-256 o SHA-512. Questo include l’uso di **salting** e iterazioni per rendere gli attacchi a forza bruta più difficili.


#### Protezioni Aggiuntive

**System Integrity Protection (SIP)**:
macOS include SIP, che impedisce modifiche ai file di sistema protetti, incluso il database delle password, anche con privilegi di root.

**Cifratura del Disco (FileVault)**:
FileVault cifra l’intero disco utilizzando **XTS-AES-128** con una chiave a 256 bit.
Questo garantisce che, in caso di accesso fisico al dispositivo, i dati rimangano protetti, inclusi gli hash delle password.

**Autenticazione Biometrica**:
Touch ID e Face ID, dove disponibili, sono integrati con il Keychain e permettono un accesso più sicuro senza la necessità di digitare frequentemente la password.

#### Confronto Gestione delle Password: Windows, Linux e macOS

| **Caratteristica**                   | **Windows**                                                                                                 | **Linux**                                                                  | **macOS**                                                                 |
| ------------------------------------ | ----------------------------------------------------------------------------------------------------------- | -------------------------------------------------------------------------- | ------------------------------------------------------------------------- |
| **Archivio Password**                | SAM Database (`C:\Windows\System32\config\SAM`).                                                            | `/etc/passwd` (info utente) e `/etc/shadow` (hash).                        | Open Directory (centralizzato) + Keychain.                                |
| **Formato di Memorizzazione**        | Hash NTLM o LM (obsoleto, meno sicuro).                                                                     | Hash SHA-512 (con salting).                                                | Hash PBKDF2 con SHA-256 o SHA-512 (salting).                              |
| **Protezione dell'Archivio**         | - Crittografia tramite DPAPI.<br>- Bloccato durante il runtime.                                             | - Accessibile solo da root.<br>- Non cifrato ma con permessi limitati.     | - Archivio centralizzato cifrato.<br>- SIP protegge i file di sistema.    |
| **Posizione Fisica**                 | - File SAM sul disco.<br>- Registro di sistema (`HKLM\SAM`).                                                | File `/etc/passwd` e `/etc/shadow` nella root directory.                   | Database cifrato + file Keychain nella directory utente.                  |
| **Interfaccia Utente**               | Nessuna gestione grafica nativa delle credenziali.                                                          | Nessuna interfaccia grafica nativa.                                        | Keychain Access per gestione grafica.                                     |
| **Protezione Contro Accessi Fisici** | Nessuna protezione disco di default (FileVault opzionale con BitLocker).                                    | Nessuna protezione disco di default (opzionale con LUKS).                  | FileVault (cifratura del disco con AES-256).                              |
| **Autenticazione Biometrica**        | Opzionale con strumenti terzi (es. Windows Hello).                                                          | Non integrata di default, dipende dal setup.                               | Integrata con Touch ID e Face ID.                                         |
| **Meccanismo di Crittografia**       | DPAPI per SAM (AES-256).                                                                                    | Algoritmi SHA-512 configurabili.                                           | AES-256 (Keychain) + PBKDF2 con SHA-256/512.                              |
| **Resistenza ad Attacchi**           | - Vulnerabile a **Dump del SAM** con strumenti (es. Mimikatz).<br>- Possibili attacchi offline al registro. | - Accessibile solo da root, ma vulnerabile a compromissioni del sistema.   | - SIP blocca modifiche al sistema.<br>- Keychain cifrato con AES-256.     |
| **Vulnerabilità Comuni**             | - Attacchi offline (dump SAM).<br>- Reti non cifrate (password in transito).                                | - Privilegi di root.<br>- Exploit su `/etc/shadow`.                        | - Phishing per accedere al Keychain.<br>- Dump di memoria.                |
| **Strumenti di Protezione**          | - BitLocker per la cifratura disco (opzionale).<br>- Windows Defender.                                      | - LUKS per cifrare il disco.<br>- Strumenti di terze parti (es. Fail2Ban). | - FileVault per cifratura disco.<br>- SIP per proteggere file di sistema. |

---

#### **Punti di Forza di Ogni Sistema**
##### **Windows**:
- Integrazione con il sistema DPAPI per protezione del SAM.
- Supporto a soluzioni di autenticazione multifattore (Windows Hello).

##### **Linux**:
- Alta configurabilità, uso di algoritmi moderni (SHA-512).
- Separazione degli hash delle password nel file `/etc/shadow`.

##### **macOS**:
- Keychain Access offre una gestione centralizzata e sicura delle credenziali.
- Protezioni aggiuntive come SIP (System Integrity Protection) e FileVault integrate.

### Quanto tempo ci vuole per crackare una password?
![[Pasted image 20241120182633.png]]


### Come posso misurare quanto sicura è una password?
La robustezza di una password misura la sua **efficacia contro attacchi brute force**. Si basa sulla difficoltà di un attaccante nel provare tutte le possibili combinazioni.

Esistono diversi modi di misurare la qualità di una password, solo che non tutti sono effettivamente rilevanti nel nostro utilizzo.

- **Entropia**:
	L’entropia è una misura di casualità espressa in bit. Più elevata è l’entropia, più la password è difficile da indovinare. La formula è:
	
	$$\text{Entropia} = \log_2(|A|^N)$$
	
	• **|A|**: numero di simboli possibili (es. lettere, numeri, simboli).
	• **N**: lunghezza della password.
	
	• **Esempio**:
	• Se una password ha solo lettere minuscole, **|A| = 26**.
	• Una password lunga 8 caratteri ha entropia:
	$$\log_2(26^8) = 37.60 \text{ bit.}$$
	Questo valore è considerato basso per una password forte.
	
	• **Requisiti per una password forte**:
	Un’entropia di **almeno 60 bit** è raccomandata per resistere a tentativi di brute force

Solitamente però utilizziamo password che sono sicure perché generate, ma difficili da ricordare. Dobbiamo però ricordarci che in verità una password può essere molto sicura anche senza caratteri speciali o simboli.
![[Pasted image 20241123114913.png]]

### Tools per misurare la qualità di una password
![[Pasted image 20241123114949.png]]
**xzcvbn** è una libreria open-source sviluppata da Dropbox progettata per misurare la robustezza delle password in modo **più realistico** rispetto ai tradizionali controlli basati su regole (ad esempio, il classico “almeno 8 caratteri, una maiuscola, un numero”). La libreria analizza le password simulando come un attaccante esperto potrebbe tentare di violarle.

**Elementi analizzati**:
![[Pasted image 20241123115445.png]]

- **Pattern comuni**:
	- Sequenze (12345, abcdef).
	- Ripetizioni (aaaaaa).

- **Dizionari**:
	- Parole comuni (es. password, dragon, welcome).
	- Frasi di uso comune (es. correct horse battery staple).

- **Sostituzioni prevedibili**:
	- Sostituzioni tipiche come @ per a, 3 per e, etc.

- **Date**:
	- Password basate su anni (1990, 2023).

- **Pattern sulla tastiera**: 
	- Movimenti sequenziali (es. qwerty, asdf).

- **Lunghezza e complessità**:
	- Tiene conto del numero di caratteri e del set di simboli utilizzati.

**Risultato**:
La libreria restituisce un punteggio da 0 a 4, dove:
• **0**: Password estremamente debole.
• **4**: Password molto robusta.

### Come posso rendere più sicura l'autenticazione con password?
- Introducendo il [[Password Salt]] nel nostro meccanismo di autenticazione
- Restringendo i permessi con [[Access Control]]
- Instaurando meccanismi di lockout per numero di tentativi
- Meccanismi di delay in base ai tentativi (throttling)
- Controllo all'inserimento della password se questa è presente in liste di parole comuni
- ==Formare l'utente sulla comprensione di cosa sia e a cosa serva una password, su come scriverla e su cosa non deve fare (lasciarle vicino a dove devo fare il login)==

### Predizione del 2004 secondo Bill Gates
![[Pasted image 20241117185813.png]]
Le password, pur essendo ancora ampiamente utilizzate, sono considerate un metodo di autenticazione sempre meno sicuro per proteggere informazioni critiche, a causa delle problematiche legate al suo utilizzo.