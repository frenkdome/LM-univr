TrickBot è nato nel 2016 ed è un [[Trojan]] avanzato inizialmente utilizzato per Bank Intrusion, principalmente inoltrato tramite campagne di phishing che scaricava un script malevolo Javascript che quando aperto apriva un canale di comunicazione C2 che scaricava il vero e proprio malware.

Parliamo di questo perché Trickbot si è evoluto, permettendo di:

- Caricare altri malware
- Aggiornando la sua struttura rendendola modulare
- Diffondersi nella rete attaccata tramite il protocollo Server Message Block (SMB) → stessa vulnerabilità utilizzata per il malware Wannacry

### Analisi dell’attacco (Mitre Att&ck)
    
[https://mitre-attack.github.io/attack-navigator//#layerURL=https%3A%2F%2Fattack.mitre.org%2Fsoftware%2FS0266%2FS0266-enterprise-layer.json](https://mitre-attack.github.io/attack-navigator//#layerURL=https%3A%2F%2Fattack.mitre.org%2Fsoftware%2FS0266%2FS0266-enterprise-layer.json)
![[Pasted image 20241013114414.png]]

1. Initial Access : email con impersonificazione di persone di fiducia che allegava / portava a scaricare un allegato malevolo
   ![[Pasted image 20241013114659.png]]
   
2. Execution : 
   
3. Persistence :
   
4. Privilege Escalation :
   
5. Defense Evasion :
   
6. Credential Access :
   
7. Discovery :
   
8. Lateral Movement :
   
9. Collection :
   
10. Command and Control :

11. Exfiltration :

12. Impact