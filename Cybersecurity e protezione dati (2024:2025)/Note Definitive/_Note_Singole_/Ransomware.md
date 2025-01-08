Malware che ==cripta i file della vittima== o blocca l'accesso al sistema, ==richiedendo un pagamento (riscatto)== per ripristinare l'accesso o decriptare i dati. Può causare gravi perdite finanziarie e interruzioni operative.

### Tipologie di ransomware
![[Pasted image 20241020173124.png]]
- Ransomware classico: cripta i file della vittima
- Lockers: cripta solamente una porzione di dati contenuti nelle partizioni della vittima
- Master Boot Record (MBR): ransomware che colpiscono la MBR -> Settore di avvio principale (primi 512 byte) che contiene le istruzioni necessarie per il boot del sistema.
- Wipers: lo scopo di questi attacchi è quello di eliminare i dati del sistema attaccato

### Fasi di un ransomware
![[Pasted image 20241020173833.png]]

1. Infezione del trojan
	![[Pasted image 20241020174022.png]]

2. Crittografia dei dati
   La crittografia dei dati può avvenire utilizzando:
   - algoritmi a chiave simmetrica
   - algoritmi a chiave asimmetrica
   con la chiave (singola o privata) sempre in mano all'attaccante
   
3. Estrazione della chiave![[Pasted image 20241020174608.png]]
   
4. Modulo di richiesta di riscatto ![[Pasted image 20241020173926.png]]

### Esempi di ransomware
[[Hidden Tear]]

### Ciclo di attacco di un ransomware (Cyber Kill Chain)
![[Pasted image 20241020174945.png]]

### Metodologie di riscatto per un ransomware
I criminali, vista la tendenza degli infettati di non pagare mai il riscatto dei dati, escogitarono delle nuove strategie per massimizzare i profitti.

- ==Doppia estorsione== 
  ![[Pasted image 20241020181359.png]]
	**Criptazione + Esfiltrazione dei Dati**: Oltre a criptare i dati, gli attaccanti rubano (esfiltrano) una copia dei dati prima di criptarli.
	**Minaccia Aggiuntiva**: Se la vittima non paga il riscatto, gli attaccanti minacciano di pubblicare o vendere i dati rubati.
  
- ==Tripla estorsione==
  ![[Pasted image 20241020181831.png]]
  **Criptazione + Esfiltrazione dei Dati + Attacchi ai Clienti o Partner**: Gli attaccanti estendono la minaccia ai clienti, partner o pazienti della vittima, contattandoli direttamente e richiedendo pagamenti o minacciando di divulgare i loro dati.
  
- ==Quadrupla estorsione==
  ![[Pasted image 20241020182005.png]]
  **Criptazione + Esfiltrazione dei Dati + Attacchi ai Clienti + Attacchi DDoS**: Oltre alle tattiche precedenti, gli attaccanti lanciano attacchi di Denial of Service distribuiti (**DDoS**) contro l'infrastruttura della vittima, rendendo i servizi online inaccessibili.

### Nuove tendenze nell'infezione da malware
- Cifratura intermittente dei file:
  essendo che la cifratura è un processo lungo, per criptare più informazioni possibili durante un'infezione i file possono venir criptati parzialmente, così da avere maggiore possibilità di infezione prima di essere scoperti dagli antivirus.
  ![[Pasted image 20241020182319.png]]
  
- Negoziazione via chat con gli attaccanti
  ![[Pasted image 20241020182415.png]]
  
- Riscrittura malware utilizzando nuovi linguaggi (rust, go)
  permette di cifrare i file in modo più efficace e la gestione della memoria viene semplificata
  ![[Pasted image 20241020182719.png]]
  
- Business logic nuove degli attaccanti (ransomware-as-a-service)
  ![[Pasted image 20241020182804.png]]
  
- Bug bounty per ransomware organizzati da cyber groups 
  Vengono invitati i migliori esperti del settore per sfidarli a trovare vulnerabilità nei prodotti, offrendo bei premi per chi riesce a trovare i nomi dei capi delle attività criminali.![[Pasted image 20241020183012.png]]

### Come prevenire un attacco Ransomware
- non aprire su link non verificati
- non aprire allegati sospetti
- non scaricare software non verificato
- aggiornare i sistemi e fare backup regolari

### Cosa fare in caso di un attacco Ransomware
1. Disconnettersi dalla rete
2. Scannerizzare la rete con strumenti di controllo sicurezza
3. Utilizzare ransomware decryption tools (https://www.nomoreransom.org/it/index.html)
4. In caso di mancata decriptazione, ripristinare il sistema da un backup

--- 
Risorse:
https://www.ncsc.gov.uk/guidance/mitigating-malware-and-ransomware-attacks
https://www.ncsc.gov.uk/collection/small-business-guide/protecting-your-organisation-malware
https://www.kaspersky.com/resource-center/threats/how-to-prevent-ransomware