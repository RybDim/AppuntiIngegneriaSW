# Introduzione
L'ingegneria del software si occupa dello sviluppo di sistemi di grandi dimensioni che coinvolgno un elevato numero di sviluppatori per un lungo periodo di tempo. L'ingegneria del software definisce quindi tecniche e principi per lo sviluppo di grandi applicazioni software minimizzando bug e massimizzando la loro longevità.

Lo sviluppo di un software di grandi dimensioni segue un processo di sviluppo composto da diverse fasi:
- Analisi dei requisiti, cioè quella fase in cui si raccolgono i requisiti e le caratteristiche che il sistema completo deve avere una volta terminato.
- Progettazione, fase che prevede la organizzazione e la progettazione dei componenti che formeranno il software completo.
- Implementazione, fase che prevede l'implementazione dei componenti del software.
- Test
- Manutenzione

## Caratteristiche del Software
Una delle principali caratteristiche del sofwtare è la sua **modificabilità**. Il software è, infatti, intrinsecamente modificabile poiché non ha parti fisiche rendendo la modificabilità abbastanza facile. La modificabilità permette di aumentare la longevità del software e viceversa. Un software longevo ha bisogno di essere modificato per tenerlo aggiornato con le nuve teconolgie hardware, software, per risolvere problemi sorti nel tempo. 

## Qualità del Software
La valutazione della qualità del software tiene conto di diversi criteri tra cui la **correttezza**. Un software si dice essere corretto se soddisfa tutti i requisiti richiesti dal cliente nei tempi e nei costi stabiliti e passa correttamente la fase di testing.

Altri criteri da cui dipende la qualità del software sono:
- **Efficienza** --> fa riferimento alla capacità del software di svolgere la propria funzione usando in modo appropriato (senza sprechi) le risorse hardware su cui gira.
- **Manuntenibilità**--> possibilità, dopo la release del software, di apportare modifiche minimali al software facilmente e in un tempo ragionevolmente breve.
- **Dependability** (sicurezza e affidabilità) --> sicurezza nel senso di **security** indica che i dati memorizzati dal software sono protetti dal mondo esterno e dagli utenti che interagiscono con esso, sicurezza nel senso di **safety** coinvolge la protezione del sistema fisico (hardware) e delle vite umane (per software usati in ambiti in cui vite umane dipendono da esso come in aerei, navi, ospedali ecc.). L'affidabilità garantisce che il sistema software non abbia frequenti episodi di failure.
- **Usabilità** --> stabilisce quanto il software sia semplice ed intuitivo da usare per gli utenti finali.

## Miglioramenti sul codice
Per poter scrivere buon codice ed evitare il cosiddetto spghetti code, cioè codice che contiene metodi estremamente lunghi, senza parametri e che usano variabili globali, è importante seguire delle linee guida. Bisogna utilizzare correttamente la programmazzione ad oggetti, ogni metodo deve svolgere una piccola funzione in modo da rendderla riutilizzabile dove serve. 

È utile usare il paradigma **command e query**. I metodi query sono metodi che restituiscono un risultato e non modificano lo stato del sistema mentre i metodi command non restituiscono nulla ma modificano lo stato del sistema. Di conseguenza le chiamate ai metodi command devono essere attenzionate ed fatte con cognizione di causa per evitare modifiche non volute al sistema.

In un buon codice, quindi, le varie operazioni sono suddivise ciascuna in un metodo. In questo modo è più semplice verificarne la correttezza e il loro riuso; sono presenti astrazioni di diversi livelli con metodi che si chiamano tra di loro.