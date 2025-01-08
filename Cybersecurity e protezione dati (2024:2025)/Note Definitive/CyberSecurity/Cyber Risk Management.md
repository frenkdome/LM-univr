Una cosa c'è da dirla: le aziende non sono interessate alle problematiche di sicurezza, per loro l'unica cosa che giustamente conta è fare tornare i conti, essere costanti nel ==fatturato==.

Il nostro compito da esperti è quello di aiutare gli imprenditori e le aziende a gestire le aziende con strumenti all'avanguardia, portando consapevolezza sui problemi e su come questi possono essere prevenuti.

È importante quindi:

- Stimare e decidere quanto **tempo** e **denaro** è necessario investire per la protezione delle tecnologie e dei servizi.
  
- Creare un report sulla situazione attuale della struttura:
	- Analisi dell'infrastruttura di rete
	- Analisi dei dispositivi connessi nella struttura
	- Analisi del personale e della percezione / rilevazione di pericolo
	- Analisi delle politiche attuali di gestione del pericolo

- Mitigare secondo dei criteri di importanza le criticità trovate.
  
- Fare formazione per diffondere la consapevolezza.
  
- Modificare l'infrastruttura per soddisfare standard e regolamentazioni come:
	- ISO 27001 (ISMS)
	- GDPR
	- PCI DSS
	- DORA
	- NIS2
	- ....

### Cosa intendiamo per Gestione del rischio?
La **Gestione del rischio** è questo processo continuo e pro-attivo che ha lo scopo di mantenere in produzione un'azienda, evitando quindi problemi legati alla sicurezza informatica.

![[Pasted image 20241217155528.png]]

### Fasi del Risk Management

1. **Frame Risk (Inquadrare il rischio)**
	Scopo: stabilire il contesto operativo e identificare i rischi accettabili.
	
	- **Mission e obiettivi** dell’organizzazione.
	- Requisiti legali, normativi e contrattuali.
	- Determinare le responsabilità per il processo di gestione dei rischi.

2. **Assess Risk (Valutare il rischio)**
	Questa fase mira a identificare, valutare e dare una priorità ai rischi interni ed esterni all'azienda.

	**Metodologie e Modelli**: 
	- [[NIST 800-30]]: guida dettagliata per condurre una valutazione dei rischi.
	- [[OWASP Risk Rating Methodology]]: calcola il rischio in base a fattori di minaccia e impatto.
	- Altri standard:
		- **EBIOS** (Francia)
		- **MAGERIT** (Spagna)
		- **IT-Grundschutz** (Germania)
		- **OCTAVE**
		- **CORAS**
	
	**Componenti delle Metodologie**
	![[Pasted image 20241217163706.png]]
	
	**Componenti principali del modello:**
	1. [[Asset]] : risorse da proteggere
	2. **Vulnerabilità**: debolezze interne/esterne sfruttabili dalle minacce.
	3. [[Attaccante (Threat Actor)]] : chi vuole colpire l'azienda.
	4. **Minacce** [[Cyber Threat]]: eventi o soggetti che possono arrecare danno.
	5. **Probabilità**: stima della possibilità che una minaccia causi un danno.
	6. **Impatto**: conseguenze negative se una minaccia si realizza.
	
	![[Pasted image 20241217164031.png]]
	
	

3. **Respond to Risk (Rispondere al rischio)**
	Questa fase mira all'analisi e alla priorità dei rischi e mettere 
	
	Identificare le strategie per mitigare i rischi:
	1. **Accettare il rischio**: se il rischio è basso o tollerabile.
	2. **Evitare il rischio**: modificando attività/processi.
	3. **Trasferire il rischio**: utilizzando assicurazioni o terze parti.
	4. **Trattare il rischio**: implementare controlli di sicurezza adeguati.
	
	Tipologie di sicurezza da proteggere:

| Tipo di sicurezza       | Descrizione                                                                                                                                                               | Esempi                                                                                                                                        |
| ----------------------- | ------------------------------------------------------------------------------------------------------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------------------- |
| Sicurezza procedurale   | Controlli di sicurezza che mirano a mitigare o trattare rischi identificati attraverso policy, procedure, processi o linee guida.                                         | Policy di sicurezza informatica, procedure operative standard, linee guida per la gestione delle password                                     |
| Sicurezza fisica        | Controlli che mirano a mitigare o trattare rischi identificati tramite la protezione fisica di beni quali edifici, impianti, attrezzature IT, personale, ecc.             | Serrature di sicurezza, sistemi di videosorveglianza, barriere fisiche, controllo degli accessi alle strutture                                |
| Sicurezza del personale | Misure messe in atto per mitigare o trattare rischi derivanti dagli utenti autorizzati dei sistemi informatici, ad es. controlli, formazione e campagne di awareness      | Controlli sul background del personale, corsi di formazione, campagne di sensibilizzazione sulle minacce, piani di risposta                   |
| Sicurezza tecnica       | Misure integrate nei sistemi informatici per mitigare o trattare rischi identificati. Ad es. firewall, configurazioni sicure, controlli di accesso, software anti-malware | Firewall, strumenti di rilevamento delle intrusioni, configurazioni sicure, sistemi di controllo degli accessi, patch di sicurezza, antivirus |
|                         |                                                                                                                                                                           |                                                                                                                                               |

4. **Monitor Risk (Monitorare il rischio)**
	Monitoraggio continuo delle misure adottate per garantire che:
	- I controlli siano **efficaci**.
	- Vengano gestiti nuovi **vulnerabilità** e **cambiamenti** tecnologici.
	  
	Per verificare questo abbiamo bisogno di metriche e di validare anche gli utenti che utilizzano il sistema (ad esempio con campagne di phishing interne)


ESEMPIO ANALISI NIST
![[Pasted image 20241217171314.png]]![[Pasted image 20241225103526.png]]![[Pasted image 20241225103538.png]]![[Pasted image 20241225103553.png]]![[Pasted image 20241225103612.png]]![[Pasted image 20241225103635.png]]