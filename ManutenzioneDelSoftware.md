# Manutenzione del Software
La consegna del software al cliente come prodotto completo segna un punto importante per la storia di sviluppo del software. Da quel momento, infatti, hanno inizio le attività di manutenzione ed evoluzione del software. Per manutenzione intendiamo il processo di introduzione di modifiche ad un prodotto software dopo la sua consegna al cliente. Queste modifiche mirano a continuare il supporto al cliente assicurando che il codice non abbia bug o difetti dopo la consegna e a introdurre modifiche che non rendano il software obsoleto rispetto alla concorrenza.

Spesso si usano i termini manutenzione ed evoluzione come sinonimi. In realtà per evoluzione si intende un singolo passo della manutenzione del software in particolare modifica del codice che porta il software da uno stato ad un altro. La manutenzione, invece, è composta da diverse attività che riguarda non solo il codice ma anche ad esempio supporto tecnico delle macchine su cui il software è installato.

I costi di manutenzione di software di grandi dimensioni rappresentano circa il 67-80% del costo totale di sviluppo del software. I cambiamenti che si possono effettuare al codice durante la fase di manutenzione si possono suddividere in 4 categorie:
- Correttivi: sono tutte quelle modifiche che mirano alla rimozione di errori lasciati nel codice prima della consegna del software.
- Adattivi: sono le modifiche al software che vengono richieste dal cliente per poterlo adattare a nuovi ambienti ad esempio nuovi sistemi operativi, nuove macchine ecc.
- Perfettivi: sono le modifiche che mirano al miglioramento del codice e all’aggiunta di nuove funzionalità.
- Preventivi: modifiche che migliorano la qualità del codice il che permette di gestirne la complessità e previene problemi futuri. In questa categoria ricade il refactoring.
## Dinamiche di evoluzione
Le dinamiche di evoluzione sono i processi di cambiamento di un sistema. Le dinamiche sono state studiate dagli albori dell’ingegneria del software. In questo ambito ricadono le leggi di Lehman e Belady, usate e confermate tutt’oggi che descrivono le dinamiche di evoluzione del software. Queste leggi sono state formulate sulla base di studi su software di grandi dimensioni sviluppati da grandi aziende, quindi alcune delle caratteristiche di queste leggi non si applicano a software più piccolo.
- **Cambiamento Continuo \[1974\]**:  il sistema, per rimanere utile al cliente, deve essere continuamente modificato adattandosi all’ecosistema circostante altrimenti l’applicazione diventa via via meno utile al cliente.
- **Aumento della Complessità \[1974\]**: quando un sistema evolve nel tempo la complessità della sua struttura interna aumenta diminuendone la qualità a meno che non si effettuino delle attività di refactoring per preservare e semplificare la struttura del sistema.
- **Auto-Regolazione \[1974\]** attributi come la dimensione del codice, l’intervallo di rilascio delle release e il numero di errori introdotti nel codice in ciascuna release rimangono approssimativamente invarianti. Questa situazione è dovuta al fatto che tutti questi attributi dipendono da molte delle scelte che vengono prese durante la fase di progettazione.
- **Stabilità Organizzativa \[1978\]**: i tempi di sviluppo di ogni singola versione è circa costante indipendentemente dalle risorse impiegate per lo sviluppo. Questo avviene perché se si assumono nuovi sviluppatori, prima di poter mettere mano al codice, questi devono studiare la documentazione e se il sistema è grande il tempo di studio sarà notevole.
- **Conservazione di Familiarità \[1978\]**: in media la dimensione del sistema rimane costante o diminuisce perché spesso l’introduzione di nuovo codice scritto bene porta alla cancellazione di codice corrispondente a funzionalità che non servono più.
- **Continua Crescita \[1978\]**: il contenuto di funzioni di un sistema deve continuare ad essere incrementato per mantenere la soddisfazione dell’utente.
- **Diminuzione della Qualità \[1994\]**: la qualità di un sistema (design, struttura, codice) diminuisce se non viene correttamente gestita apportando adeguate attività che mantengano la qualità alta.
## Costo di manutenzione
Fattori che contribuiscono al costo di manutenzione del software:
- Il costo è ridotto se il team di sviluppo è coinvolto nella manutenzione. Il team di sviluppo sa perfettamente la struttura generale del sistema il che facilita la manutenzione futura.  
- Gli sviluppatori potrebbero non avere responsabilità contrattuali per la manutenzione, quindi potrebbero non avere incentivi a fare una progettazione che può essere cambiata in futuro.
- Ogni introduzione di cambiamenti nel codice introduce potenzialmente anche errori che degradano il software.
## Modelli di manutenzione
I modelli di manutenzione sono degli approcci che danno delle indicazioni su come la manutenzione deve essere portata vanti nel tempo.
- **Quick-fix**: si apportano dei cambiamenti a livello del codice. Quando il cliente richiede una modifica, si va a cercare il punto giusto nel codice e si effettuano subito le modifiche. Questo modello è quello che causa maggiormente ladegradazione del codice perché non si passa da una fase di progettazione. 
- **Miglioramento interattivo**: prima di passare a modificare il codice si effettua un’analisi della documentazione e del codice. Si controlla la complessità e il design del sistema e si modifica il codice di conseguenza. Oltre alle modifiche al codice si modifica anche la documentazione e il design del sistema dopo le modifiche.
- **Riuso**: si stabiliscono i nuovi requisiti del sistema e si implementano cercando di riusare più codice possibile.
## Tipi di modifiche
- **Refactoring o restructuring**: processo di cambiamento del software che non altera il comportamento ma migliora la struttura interna.
- **Reverse engineering**: consiste nell’analizzare un sistema per estrarre informazioni sul suo comportamento o sulla sua struttura.
- **Re-engineering**: alterare un sistema per ricostruirlo in un’altra forma.
