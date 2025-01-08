È una proprietà che possiede un dataset se ogni record è indistinguibile da almeno altri k-1 record in termini di “quasi-identificatori”.

Ogni classe di equivalenza (gruppo di record con gli stessi valori per i quasi-identificatori) deve contenere almeno k record per garantire che nessun record sia distinguibile dagli altri nel gruppo.

È stato introdotto da Latanya Sweeney e Pierangela Samarati in un articolo pubblicato nel 1998.

![[Pasted image 20241230124007.png]]

## Come posso ottenere le classi di equivalenza

1. **Generalizzazione:**
	I quasi-identificatori vengono resi meno specifici (es. il CAP 47601 diventa 476**, l’età 29 diventa 2*). Questo raggruppa i record in classi con valori generalizzati.

2. **Soppressione:**
	In alcuni casi, i record che non possono essere raggruppati per formare una classe di almeno k elementi vengono rimossi (operazione comune per gli outliers).

## Esempio di K-anonymity

![[Pasted image 20241230124204.png]]![[Pasted image 20241230124226.png]]![[Pasted image 20241230124255.png]]![[Pasted image 20241230124308.png]]

![[Pasted image 20241230124450.png]]![[Pasted image 20241230124523.png]]

## Esempio esercizio calcolo k

![[Pasted image 20241230125233.png]]
Il valore di \(k\) rappresenta il numero minimo di record in ogni **classe di equivalenza** in un dataset anonimizzato. Ecco come calcolarlo usando il dataset della slide come esempio:

---
**Passo 1: Identificare i Quasi-identificatori**
I **quasi-identificatori** sono attributi che, se combinati, possono identificare un individuo.  
Nel dataset fornito, i quasi-identificatori sono:  
- **Birth (anno di nascita)**  
- **Gender (sesso)**  
- **ZIP (codice postale generalizzato a 0213\*)**  
Questi attributi formano le basi per raggruppare i record in classi di equivalenza.

---
**Passo 2: Determinare le Classi di Equivalenza**
Una **classe di equivalenza** è un gruppo di record che condividono gli stessi valori per i quasi-identificatori.  
Raggruppiamo i record in base a **Birth**, **Gender**, e **ZIP**. Esempio dal dataset:

| Birth | Gender | ZIP   | Numero di record |
|-------|--------|-------|------------------|
| 1965  | m      | 0213* | 2                |
| 1965  | f      | 0213* | 2                |
| 1964  | f      | 0213* | 2                |
| 1964  | m      | 0213* | 3                |
| 1967  | m      | 0213* | 2                |

---
**Passo 3: Calcolare il valore di \(k\)**
Il valore di \(k\) corrisponde al numero minimo di record presenti in una classe di equivalenza.  
Dal calcolo sopra, il gruppo più piccolo (ad esempio, **1965, f, 0213\*** e **1967, m, 0213\***) contiene **2 record**.  
**Pertanto, \(k = 2\)**.

---
**Passo 4: Verifica del Dataset**
Assicurati che tutte le classi di equivalenza abbiano almeno \(k\) record:
- **1965, m, 0213\*** → 2 record ✅
- **1965, f, 0213\*** → 2 record ✅
- **1964, f, 0213\*** → 2 record ✅
- **1964, m, 0213\*** → 3 record ✅
- **1967, m, 0213\*** → 2 record ✅  
Tutte le classi rispettano la regola che il numero di record è almeno \(k = 2\).

---
**Nota Importante**
Se una classe di equivalenza avesse meno di \(k\) record:
1. **Generalizzazione aggiuntiva:** I quasi-identificatori devono essere resi ancora meno specifici (es. includendo range più ampi).  
2. **Soppressione:** I record problematici potrebbero essere rimossi dal dataset.

## Come mai K-Anonymity non è una soluzione perfetta
![[Pasted image 20241230130043.png]]

**k-Anonymity non è una soluzione perfetta:**
- Protegge contro identificazioni dirette ma non contro deduzioni indirette. 
- Gli attacchi mostrano la necessità di diversificare i valori sensibili e considerare le conoscenze esterne.
  
  ==Homogeneity Attack (Attacco di Omogeneità)==
  Questo attacco si verifica quando tutti i record in una classe di equivalenza condividono lo stesso valore per l’attributo sensibile.
  ==Background Knowledge Attack (Attacco con Conoscenza di Base)==
  Questo attacco si verifica quando un attaccante utilizza conoscenze esterne o di dominio per restringere le possibilità e dedurre informazioni sensibili..