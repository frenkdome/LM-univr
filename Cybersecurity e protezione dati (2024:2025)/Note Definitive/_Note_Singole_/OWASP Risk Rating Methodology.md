OWASP propone una metodologia per calcolare il rischio in base alla:

### PROBABILITÀ: 

1. **Fattori di minaccia** (Threat Agents): 
   livello di competenza, motivazione, risorse disponibili.

| Fattore     | Descrizione                                                               | Esempi di Valori (indicativi)                                                                                                     |
| ----------- | ------------------------------------------------------------------------- | --------------------------------------------------------------------------------------------------------------------------------- |
| Skill Level | Livello di competenza tecnica del gruppo di attaccanti.                   | No skill (1), <br>Utente avanzato (5), <br>Esperto di rete/programmazione (6), Pentester (9)                                      |
| Motive      | Motivazione del gruppo di attaccanti a sfruttare la vulnerabilità.        | Nessuna ricompensa (1), <br>Possibile ricompensa (4), <br>Alta ricompensa (9)                                                     |
| Opportunity | Risorse/opportunità necessarie per scoprire e sfruttare la vulnerabilità. | Richiesto accesso/risorse costose (0), Accesso speciale richiesto (4), <br>Alcune risorse richieste (7), <br>Nessun requisito (9) |
| Size        | Dimensione del gruppo di attaccanti potenziali.                           | Sviluppatori (2), <br>Amministratori (2), <br>Partner (5), <br>Utenti autenticati (6), <br>Anonimi Internet (9)                   |

   
2. **Fattori di vulnerabilità**: 
   facilità di scoperta, sfruttamento, rilevamento delle vulnerabilità.

| Fattore             | Descrizione                                               | Esempi di Valori (indicativi)                                                                              |
| ------------------- | --------------------------------------------------------- | ---------------------------------------------------------------------------------------------------------- |
| Ease of Discovery   | Facilità con cui la vulnerabilità può essere individuata. | Praticamente impossibile (1), <br>Difficile (3), <br>Facile (7), <br>Tool automatizzati (9)                |
| Ease of Exploit     | Facilità con cui la vulnerabilità può essere sfruttata.   | Teorico (1), <br>Difficile (3), <br>Facile (5), <br>Tool automatizzati (9)                                 |
| Awareness           | Conoscenza della vulnerabilità da parte degli attaccanti. | Sconosciuta (1), <br>Nascosta (4), <br>Ovvia (6), <br>Conoscenza pubblica (9)                              |
| Intrusion Detection | Probabilità che l’exploit venga rilevato.                 | Rilevato attivamente nell’app (1), Loggato e rivisto (3), <br>Loggato non rivisto (8), <br>Non loggato (9) |


### IMPATTO:

3. **Impatto tecnico**: perdita di **riservatezza**, **integrità** e **disponibilità**.

| Fattore                 | Descrizione                                               | Esempi di Valori (indicativi)                                                                                                                |
| ----------------------- | --------------------------------------------------------- | -------------------------------------------------------------------------------------------------------------------------------------------- |
| Loss of Confidentiality | Quantità e sensibilità dei dati esposti.                  | Minimo dato non sensibile (2), <br>Dato critico minimo (6), <br>Dato critico esteso (7), <br>Tutti i dati (9)                                |
| Loss of Integrity       | Quantità di dati corrotti e gravità del danno.            | Corruzione minima (1), <br>Corruzione seria minima (3), <br>Dati seriamente corrotti (7), <br>Tutti i dati corrotti (9)                      |
| Loss of Availability    | Quanta parte del servizio viene persa e quanto è critico. | Interruzione servizi secondari (1), Interruzione minima servizi primari (5), Estesi servizi primari persi (7), <br>Tutti i servizi persi (9) |
| Loss of Accountability  | Tracciabilità delle azioni degli attaccanti.              | Completamente tracciabili (1), Possibilmente tracciabili (7), Completamente anonimi (9)                                                      |


4. **Impatto aziendale**: danni finanziari, reputazionali, violazioni di compliance.

| Fattore           | Descrizione                                        | Esempi di Valori (indicativi)                                                                           |
| ----------------- | -------------------------------------------------- | ------------------------------------------------------------------------------------------------------- |
| Financial damage  | Danno finanziario risultante dall’exploit.         | Costo di fix < manutenzione (1), <br>Lieve su profitto annuo (3), Significativo (7), <br>Bancarotta (9) |
| Reputation damage | Danno reputazionale per l’organizzazione.          | Danno minimo (1), <br>Perdita clienti importanti (4), Perdita di goodwill (5), <br>Danno al brand (9)   |
| Non-compliance    | Entità della violazione normativa e regolamentare. | Violazione minore (2), <br>Violazione chiara (5), <br>Violazione di alto profilo (7)                    |
| Privacy violation | Quantità di dati personali esposti.                | Una persona (3), <br>Centinaia (5), <br>Migliaia (7), <br>Milioni (9)                                   |


Per queste valutazioni viene dato un ==punteggio==, che va da 0 a 9.

![[Pasted image 20241217171000.png]]
![[Pasted image 20241217171151.png]]


Esempio di calcolo per Probabilità e Impatto :
![[Pasted image 20241217171207.png]]
![[Pasted image 20241217171218.png]]