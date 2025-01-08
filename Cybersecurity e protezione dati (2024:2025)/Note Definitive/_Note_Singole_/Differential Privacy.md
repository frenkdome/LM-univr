La **privacy differenziale** è un paradigma che garantisce la protezione della privacy in un dataset. L’obiettivo è fornire informazioni statistiche aggregate senza rivelare nulla di significativo su individui specifici presenti nel dataset.

![[Pasted image 20241230160738.png]]
Un meccanismo di privacy differenziale ==garantisce che la probabilità di osservare un determinato output non cambi significativamente se un singolo record viene aggiunto o rimosso== dal dataset.

![[Pasted image 20241230160838.png]]

## Definizione formale

![[Pasted image 20241230160916.png]]
**Epsilon (ε)**:
	È il parametro di privacy che misura il livello di protezione. Valori più piccoli di ε indicano una maggiore privacy : è difficile distinguere i dati di un singolo individuo dal dataset.

![[Pasted image 20241230161730.png]]![[Pasted image 20241230161743.png]]
## Meccanismi principali

**Sensibilità**: È il massimo cambiamento possibile nell’output della funzione se un singolo record viene aggiunto o rimosso.

1. **Meccanismo Laplaciano**:
	Aggiunge “rumore” basato su una distribuzione Laplaciana ai risultati di una funzione, proporzionale alla “sensibilità” della funzione.![[Pasted image 20241230162225.png]]![[Pasted image 20241230162236.png]]

2. **Meccanismo di Rumore Gaussiano**:
	Aggiunge rumore distribuito normalmente (gaussiano). Utilizzato in contesti con **δ** > 0, dove un’accuratezza leggermente inferiore è accettabile.

### Global Sensitivity Method nella Privacy Differenziale
Il **Global Sensitivity Method** è una componente fondamentale per calibrare il rumore aggiunto in modo proporzionale alla sensibilità della funzione di query sul dataset. 
Serve a garantire che le informazioni sensibili di un singolo individuo non possano essere dedotte dall’output.![[Pasted image 20241230162633.png]]![[Pasted image 20241230162645.png]]![[Pasted image 20241230162659.png]]


## Cosa può essere calcolato con la Privacy Differenziale
- **Statistiche descrittive:** conteggi, media, mediana, istogrammi, boxplot, ecc.
- **Compiti di ML supervisionati e non supervisionati:** classificazione, regressione, clustering, apprendimento della distribuzione, apprendimento federato, ecc.
- Generazione di dati sintetici

## Utilizzi pratici

1. **US Census Bureau 2020**:
	Analisi dei flussi di entrata/uscita (Inflow/Outflow Analysis) utilizzando dati geolocalizzati.
	Visualizzazione di statistiche sui movimenti di lavoro, residenza e spostamenti dei cittadini.![[Pasted image 20241230163738.png]]

2. **Google - RAPPOR**:
	Tecnologia per raccogliere statistiche aggregate preservando la privacy degli utenti.
	Utilizzo di risposte randomizzate per garantire la privacy differenziale a livello locale, permettendo comunque analisi sui dati aggregati.![[Pasted image 20241230163828.png]]

3. **Apple - Privacy Differenziale**:
	Applicazione della privacy differenziale per raccogliere dati aggregati, minimizzando le informazioni su singoli individui.
	Focus sulla raccolta di dati utilizzabili senza compromettere la privacy personale.![[Pasted image 20241230170508.png]]
	
	Sono stati però evidenziati i limiti nella privacy differenziale implementata da Apple (perdite di privacy causate da parametri non ottimali e frequenze elevate di accesso ai dati).![[Pasted image 20241230170541.png]]

5. **Local Differential Privacy (LDP)**:
	Privacy differenziale a livello locale con l’aggiunta di rumore ai dati individuali prima dell’invio.
	Implementazioni da parte di Google e Apple per analizzare statistiche senza compromettere la privacy dei singoli utenti.![[Pasted image 20241230170611.png]]

6. **Learning Heavy Hitters**:
	Analisi di parole/emoticon più frequentemente utilizzate dagli utenti.
	Tecniche per identificare tendenze popolari senza accedere ai dati grezzi degli utenti.![[Pasted image 20241230170638.png]]

7. **Smart Grid**:
	Utilizzo della privacy differenziale nelle reti intelligenti per analizzare consumi energetici a livello aggregato.
	Protezione dei dati individuali dei consumatori, concentrandosi sulle analisi generali.![[Pasted image 20241230170729.png]]

8. **Financial Institutions**:
	Applicazioni di privacy differenziale nella ricerca di frodi e nel training di modelli di machine learning.
	Creazione di dataset sintetici con distribuzioni simili ai dati reali per migliorare gli algoritmi.![[Pasted image 20241230170828.png]]

9. Training Machine Learning
10. Nuovi dataset con stesse distribuzioni -> Dataset sintetici