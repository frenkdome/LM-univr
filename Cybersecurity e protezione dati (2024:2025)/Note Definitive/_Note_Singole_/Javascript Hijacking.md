È una tecnica di attacco che sfrutta le ==vulnerabilità nelle applicazioni web che utilizzano JavaScript== per trasmettere dati, specialmente quando utilizzano il formato JSON (JavaScript Object Notation). L'obiettivo dell'attaccante è ottenere accesso non autorizzato a dati sensibili sfruttando il modo in cui le applicazioni web gestiscono le richieste e le risposte in JavaScript.

### **Esempio Semplificato**

1. **Scenario**
    - Un utente è autenticato su un'applicazione web (ad esempio, un servizio bancario online).
    - L'attaccante crea una pagina web malevola e convince l'utente a visitarla.
2. **Attacco**
    - La pagina malevola contiene uno script che effettua una richiesta al server dell'applicazione bancaria.
    - A causa dei cookie di sessione, il server riconosce l'utente come autenticato e restituisce i dati richiesti.
3. **Compromissione dei Dati**
    - Lo script malevolo può ora accedere ai dati sensibili restituiti dal server e inviarli all'attaccante.