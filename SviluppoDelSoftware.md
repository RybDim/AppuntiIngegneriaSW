# Processi di sviluppo del software
Un processo software descrive le attività necessarie allo sviluppo di un prodotto software e come queste attività devono essere relazionate tra di loro. Ciascun processo software si distingue dagli altri sia per l’ordine in cui le attività vengono svolte sia per come queste vengono svolte.

Le fasi dello sviluppo di un software sono:
- **Analisi dei requisiti**
- **Progettazione**
- **Codifica o implementazione**
- **Convalida o testing**
- **Manutenzione**
## Analisi dei requisiti
Con la fase di analisi dei requisiti, chiamati anche specifiche, si ha l’obbiettivo di raccogliere i requisiti cioè un elenco di funzionalità che dovranno essere implementate nel prodotto software. Pur essendo sinonimi, spesso ci si riferisce alle specifiche come una descrizione più dettagliata e completa dei requisiti. Una volta raccolti i requisiti, si cerca di ottenere una lista di specifiche più dettagliate
che il software deve rispettare. Le attività più specifiche che l’analisi dei requisiti comprende troviamo: 
- **Studio di fattibilità**: consente all’azienda che vuole produrre il software di capire se riuscirà a fornire un software che rispetti i requisiti del cliente nei tempi previsti, nei costi previsti e con le tecnologie che il cliente chiede.
- **Analisi dei requisiti**: studio, organizzazione e arricchimento dei requisiti minimali raccolti durante lo studio di fattibilità.
- **Specifiche dei requisiti**: stesura del documento finale che descrive in minuziosi dettagli le specifiche raccolte analizzando i requisiti.
- **Convalida dei requisiti**: interazione con il cliente che permette di capire se il documento delle specifiche rispetta i requisiti del cliente.

I requisiti si possono dividere in due categorie: **funzionali** e **non funzionali**. I primi descrivono cosa il software deve fare, in poche parole le funzionalità che deve avere. I secondi descrivono come devono essere implementate le funzionalità (tecnologie da usare, prestazioni che deve avere il software, affidabilità, manutenibilità ecc.). Un raggruppamento di requisiti poco specifici compone una feature.
## Progettazione ed Implementazione
### Progettazione
La fase di progettazione permette di determina quali sono le componenti che comporranno il sistema software e quali sono le relazioni che devono intercorrere tra le varie componenti. Con componenti si può intendere o una classe nel caso di progettazione di software ad oggetti, oppure un qualcosa di più ampio, meno dettagliato come un modulo. La progettazione segue delle attività stabilite:
- Suddivisione dei requisiti.
- Identificazione dei sottosistemi: a partire dei requisiti si cerca di suddividere il sistema in sottosistemi più piccoli che si occupano di determinate funzionalità che il software deve avere.
- Specifica delle responsabilità dei sottosistemi.
- Progettazione di interfacce, componenti, strutture dati e algoritmi.
Ciascuna delle attività produce un documento che descrive un modello del
sistema generale.
### Implementazione
La fase di implementazione consiste nella traduzione dei modelli del progetto in un programma. In poche parole, a partire dai documenti prodotti nella fase di progettazione, si implementa in codice le specifiche del software. Inoltre si effettua una dettagliata fase di testing sul codice per scoprire e rimuovere eventuali errori o bug del software. La rimozione dell’errore prevede innanzitutto la localizzazione dell’errore all’interno del sistema. In seguito si rimuove l’errore nel modello del software e poi nel codice. Infine si effettuano nuovamente i test per essere sicuri che la risoluzione dell’errore non abbia introdotto altri errori.
### Convalida
La convalida viene effettuata dopo che la parte di codice testata singolarmente viene inserita nel contesto più ampio del software. A questo punto il software viene validato. Si intende, cioè, mostrare che il sistema software è conforma alle specifiche raccolte nel documento delle specifiche e che soddisfa le aspettative del cliente. La convalida di un sistema software si può fare in due modi. Il modo più ricorrente è convalidare tramite test che mirano a testare il sistema software nella sua interezza. Come input si prendono dati reali che il sistema dovrà elaborare.

Un secondo modo è la revisione che consiste nella lettura del codice da parte
di esperti che analizzano e comprendono il codice scritto da qualcun altro e
valutano la presenza di difetti. La revisione, inoltre, permette di mettere in luce
un uso sbagliato o inefficiente di costrutti interni al linguaggio.
#### Test
- **Test di componenti**: detti unit test, vengono effettuati sulle singole componenti del software in modo indipendenti. Alle componenti di un software appartengono funzioni, classi, oggetti ecc. Spesso gli unit test vengono effettuati direttamente dallo sviluppatore che ha implementato quelle componenti.
- **Test di sistema**: test che coprono l’intero sistema composto dalle componenti su cui si erano fatti gli unit test.
- **Test di accettazione**: detti alpha test, quando si è in una fase molto avanzata dello sviluppo, il sistema viene testato con dati veri forniti dal cliente per verificare che le sue esigenze e i suoi requisiti sono soddisfatti. Un software su cui vengono eseguiti test alpha è detto essere nella versione alpha, cioè una versione integrata che ha ancora difetti e certe parti mancanti.
- **Beta test**: test eseguito dal cliente sul prodotto quasi completo. Il software che subisce beta test è detto essere in versione beta, cioè una versione che include tutte le feature richieste ma che potrebbe ancora avere difetti.
## Processo a cascata
Il processo a cascata è uno dei primi ad essere stati utilizzati. Viene detto a cascata perché le varie fasi dello sviluppo vengono eseguite una dopo l’altra senza mai tornare indietro. Prima si eseguirà la fase della raccolta dei requisiti per produrre il documento delle specifiche dei requisiti che sarà in forma finale perché non potrà più essere cambiato. Una volta prodotto il documento delle specifiche, si passa alla progettazione completa e dettagliata del sistema. Solo una volta finita la progettazione si può avviare la fase di implementazione del codice sulla base del documento che descrive il design del sistema. Una volta finita l’implementazione e il test si passa all’integrazione delle varie componenti in un unico software e, di conseguenza, al testing di sistema. Infine, completata l’implementazione e il testing di sistema, si può consegnare il prodotto al cliente e cominciare l’eventuale manutenzione.

Quello che raccomanda il processo a cascata è di eseguire le varie fasi in modo individuale in modo da passare alla fase successiva solo quando hai completato quella corrente. Inoltre vieta di ritornare a fasi precedenti. Come conseguenza di questo processo di sviluppo, se la progettazione eseguita non è corretta in qualche punto, non posso cambiarla ma continuo con le parti che sono sicuro che siano corrette. Una volta finito tutto il processo di sviluppo per le parti del sistema corrette si può ricominciare dalla fase in cui si scopre ci sono errori. 

Il processo di sviluppo a cascata produce una elevata quantità di documentazione che permette di evitare errori e gestire più efficientemente il team di sviluppo. Poiché i documenti prodotti durante le varie fasi non vengono modificati, questi hanno una elevata consistenza che rende più semplice l’implementazione. I problemi maggiori del processo a cascata sono i tempi eccessivamente lunghi per ottenere il prodotto, poche interazioni con i clienti concentrate nelle fasi iniziali dello sviluppo e difficoltà nell’introdurre eventuali cambiamenti richiesti dal cliente. Non è quindi adatto per progettazioni in cui i requisiti cambiano nel tempo. Si adatta invece bene per sistemi molto grandi, complessi, critici, con requisiti stabili e definiti nel dettaglio e per gestire team numerosi. Con questo processo la fase che richiede più tempo è l’integrazione e testing del sistema. 

## Processi Evolutivi
I processi di sviluppo evolutivi sono l’opposto del processo a cascata. Esistono
due varianti: **sviluppo per esplorazione** e **sviluppo build and fix**.
### Sviluppo per esplorazione
Nello sviluppo per esplorazione il team di sviluppo comprende il sistema da realizzare durante la realizzazione. Man mano che una componente è chiara viene documentata attraverso requisiti minimali, viene implementata e testata e la si fa vedere al cliente per ricevere dei feedback. In seguito si passa ad un’altra componente del software fino a implementare l’intero sistema. Questo consente di avere feedback immediato da parte del cliente e permette di andare avanti nello sviluppo per priorità (sviluppo prima ciò che il cliente ritiene più importante). Tra gli svantaggi si ha una progettazione che viene riadattata spesso in base ai requisiti del cliente.
### Sviluppo build and fix
Lo sviluppo build and fix permette di implementare codice anche se non si hanno chiari i requisiti del cliente. Si costruisce una prima versione approssimativa del software e lo si modifica fino a che il cliente non è soddisfatto del prodotto. Come conseguenza alla quasi totale assenza dei requisiti, non viene prodotta quasi nessuna documentazione e la fase di design del sistema non viene approfondita. Il codice del prodotto, quindi, risulta di bassa qualità. 

Entrambi i processi descritti costringono quindi di passare costantemente dalla fase di analisi dei requisiti alla fase di progettazione e implementazione e alla fase di validazione del codice.

I problemi maggiori dei processi di sviluppo evolutivi sono tempi lunghi di sviluppo del progetto, mancanza di visione d’insieme del progetto dovuta alla mancanza di specifiche dettagliate del progetto. Inoltre la progettazione potrebbe proseguire in modo abbastanza confusa senza un’architettura ben definita.

Vengono quindi applicati per sistemi di piccole dimensioni, singole parti di sistemi più grandi oppure per sistemi che avranno vita breve ad esempio dei prototipi di un software più grande.
## Processi incrementali
Con un processo di sviluppo incrementale si costruisce il sistema software realizzando a poco a poco prototipi via via più completi e funzionanti. Ogni versione viene sviluppata seguendo nel dettaglio i requisiti specificati. Una volta sviluppata e testata una versione, si passa ad implementare un’altra parte del software che porterà ad una versione del software più completa della precedente.
## Processo CBSE o basato su COTS
Il processo CBSE (Components Based Software Engineering) o basato su COTS (Components Off the Shelf) basa la progettazione del software su componenti preesistenti già realizzati da qualcuno al di fuori del team di sviluppo. Si cerca di selezionare tra componenti software già esistenti quelli più simili alle funzionalità che il sistema deve avere e li si compone facendoli interagire tra di loro. C’è quindi un’enfasi maggiore sul riuso di codice già esistente. In alternativa si cerca di adattare i requisiti del cliente alle funzionalità che i componenti già esistenti forniscono.
## Sviluppo Agile
Lo sviluppo agile dà più importanza alle persone piuttosto che alla documentazione. Questo significa che tra un documento dei requisiti dettagliato ed organizzato e l’interazione tra gli individui si sceglie quest’ultima facendo qualche compromesso sulla scrittura dei documenti. Questo permette una collaborazione più stretta tra gli sviluppatori del software e meno documentazione.

Con questo tipo di processo, le richieste di cambiamenti sono benvenute anche in fasi avanzate dello sviluppo perché non si ha una documentazione specifica che impone una certa schedule da seguire.

Per attuare in modo giusto questo tipo di processo di sviluppo occorrono persone addette allo sviluppo ben motivate e che hanno una certa esperienza nello sviluppo di software.
### Extreme Programming
Il processo di sviluppo extreme programming, detto XP, è un approccio che si basa sullo sviluppo e sulla consegna di piccoli incrementi di funzionalità. Solitamente si cerca di sviluppare incrementi al sistema esistente in un paio di settimane. È un processo particolarmente adatto a piccoli gruppi di sviluppatori, da 2 a 12 persone. Si ha un costante miglioramento del codice scritto. Si fa un uso scarso di documentazione, le uniche documentazioni utiizzate sono le story card e le CRC. Si enfatizza molto sulla comunicazione costante con il cliente e tra gli sviluppatori.

È quindi adatto per progetti in cui i requisiti non sono stabili e si hanno grandi rischi ad esempio tempi di consegna molto brevi o software innovativo per gli sviluppatori che non hanno familiarità con le tecnologie da utilizzare per costrutire il sistema.
Il processo XP si basa su 12 pratiche assolutamente necessarie.

#### Gioco di pianificazione 
Mira ad individuare i requisiti e a stabilire gli obbiettivi dello sviluppo per le prossime due settimane. Consiste nella scrittura delle story card cioè delle card di circa 12x7 cm su ciascuna delle quali viene scritto dal cliente un requisito in modo sintetico e preciso. Il cliente viene invitato ad interagire con il team di sviluppo che gli fa delle domande e gli fa compilare le story card.

Le story card vengono quindi analizzate dagli sviluppatori che valutano la comprensibilità e la fattibilità del requisito. In caso negativo si chiede al cliente di scrivere nuovamente la story card in modo che sia più precisa, dettagliata e più comprensibile.

Gli sviluppatori, inoltre, devono fornire una stima sul tempo che richiede sviluppare quel particolare requisito. Un problema della stima del tempo è che sviluppatori diversi potrebbero avere una stima del tempo diversa per lo sviluppo di quel requisito. In questo caso si deve trovare un accordo. Un altro problema legato alla stime del tempo è quello della lunghezza massima accettabile. Stime di tempo troppo grandi non vanno bene perché le story card dovrebbero descrivere requisiti realizzabili in un paio di ore fino ad un massimo di un paio di giorni.

Un’altra cosa da valutare nella scrittura delle story card è che i requisiti dovranno poi essere testati. Se uno sviluppatore, leggendo un requisito, si rende conto che non è possibile scrivere un test per quel requisito allora questo dovrà essere rescritto.

Comunicando con il cliente, inoltre, si associa alle story card delle priorità. In questo modo il team di sviluppo saprà su quali requisiti focalizzarsi per prima. 

Riassumendo, quindi, una story card deve contenere, data di scrittura della story card, numero della story card, priorità, tempo stimato, riferimenti, descrizione del requisito, lista di attività che permette di implementare il requisito ed eventuali note.

Una volta scritte le story card si deve scegliere quali dei requisiti scritti si dovranno implementare nelle prossime due settimane. Le story card vengono attaccate in una story board in file verticali dove ognuna rappresenta i requisiti da implementare nelle due settimane.
#### Piccole release
Ogni due settimane si effettua una release interna del codice implementato. Si cerca di rendere ogni release il più piccola possibile. Questa viene fatta esaminare dal cliente in sede il che permette di avere rapidamente un feedback sul codice implementato. Di conseguenza si ha un rischio ridotto e si guadagna la fiducia del cliente che rimane sempre aggiornato sul prodotto richiesto. Le piccole release permettono inoltre di fare aggiustamenti sul codice per dei requisiti nuovi che il cliente introduce.
#### Metafora
Il progetto viene guidato tramite una singola metafora che rappresenta l’architettura del sistema. Questo permette di rendere le discussioni soprattuto con il cliente più semplici.
#### Testing
Non appena è stato prodotto nuovo codice, si eseguono i test anche più volte al giorno. Si eseguono sia test funzionali che unit test. I test funzionali spesso vengono scritti dall’utente in modo informale. Il cliente testa le funzionalità del software e dà un feedback sui possibili problemi e possibili migliorie che si possono apportare al sistema. Si utilizzano spesso tool di automatizzazione per test funzionali. Vengono eseguiti almeno su base giornaliera perché avere tanti test permette di soddisfare i requisiti che cambiano spesso durante lo sviluppo.
#### Refactoring
Come già sappiamo il refactoring permette di migliorare la struttura del codice senza comprometterne il comportamento. Il refactoring viene fatto sempre in coppia e in piccoli passi. Il refactoring è facilitato dagli unit test, dal pair programming e dal design semplice. Si cerca sempre di evitare ripetizioni inutili nel codice.
#### Pair programming
Una volta fatta la pianificazione delle attività da svolgere nelle due settimane successive si passa all’implementazione. Si usa la tecnica del pair programming. Si formano delle coppie tra gli sviluppatori, ciascuna coppia sceglie una story card su cui lavorare. Una volta finita l’implementazione del requisito descritto nella story card scelta, la coppia riattacca la story card nella parte bassa della story board dove vengono attaccate tutte le story card implementate. La coppia si suddivide in due ruoli: driver e navigator.

Il driver usa il mouse e tastiera per scrivere il codice mentre il navigator revisiona il codice scritto dal driver, comincia a progettare i test e cerca delle soluzioni migliori al codice scritto dal driver. Il confronto delle conoscenze dei due sviluppatori, quindi, permette di scrivere codice corretto e di qualità.

Condizione fondamentale per applicare questa tecnica è che i due sviluppatori abbiano stessa esperienza di medio-alto livello. Una disparità di esperienza e conoscenze potrebbe portare a ruoli sbilanciati in cui lo sviluppatore con più esperienza lavora più di quello con meno esperienza.

Ogni volta che si deve implementare un nuovo requisito descritto in una story card, le coppie vengono cambiate cosı̀ come vengono scambiati i ruoli. in questo modo tra tutto il team di sviluppo si sparge la conoscenza su tutto il software.
#### Cliente in sede
Il cliente scrive i test funzionali e stabilisce le priorità dei requisiti. Risponde inoltre alle domande del team di sviluppo fornendo costante feedback sul codice.
#### Design semplice
Quando la coppia di programmatori prende la story card deve effettuare le scelte più semplici possibili nella progettazione del requisito descritto nella story card. Un sistema sarà semplice se si effettuano le scelte giuste nella progettazione del codice. Fare un design semplice permette di avere tempistiche abbastanza brevi per la realizzazione del codice.

Il design del codice implementato viene documentato tramite le Class Responsibility Collaboration card. Il navigator che fa delle scelte di progettazione compila le CRC. In alto viene scritto il nome della classe, a sinistra le responsabilità della classe e a destra le collaborazioni cioè la relazione che questa classe ha con altre classi utili. Le varie CRC vengono raccolte in ordine alfabetico e forniscono una visione complessiva del sistema implementato.
#### Possesso del codice collettivo
Possesso del codice collettivo significa che se durante la letture del codice scritto, uno sviluppatore si accorge che ha qualche problema, è autorizzato a modificarlo con l’obbiettivo di risolvere il problema trovato. Questo vale per tutti gli sviluppatori del team. Ognuno può modificare codice senza chiedere permessi. Come conseguenza ciascuno degli sviluppatori è egualmente responsabile dell’intero sistema.
#### Integrazione continua
Integrazione continua significa che ogni volta che una coppia di programmatori finisce l’implementazione di una componente, questa viene testata e integrata immediatamente nel sistema. Con il processo XP si integra una nuova componente nel sistema ogni poche ore o al massimo un giorno. Se il test di un componente fallisce, la coppia che l’ha implementato deve cercare una soluzione. Nel caso in cui non riesca a trovare l’errore si consiglia di buttare via il codice difettoso e ricominciare. Buttare via il codice è abbastanza violenta come soluzione ma spesso trovare errori in un codice richiede più tempo che implementarlo da capo. Il codice da buttare, inoltre, non è molto in quanto si tratta di codice sviluppato nel giro di poche ore.
#### Settimana di 40 ore
La programmazione delle attività da svolgere nelle settimane tiene conto che una giornata lavorativa di uno sviluppatore è di 8 ore per 5 giorni a settimana per un totale di 40 ore la settimana. Si deve rispettare sempre gli orari di lavoro dei dipendenti perché ore eccessive di lavoro porta alla stanchezza dei dipendenti. La stanchezza dei dipendenti riduce la produttività e aumenta la probabilità di errori nel codice. Se una stima dei tempi porta il team di sviluppo a lavorare più di 40 ore a settimana allora la stima è stata eseguita in modo errato e si deve rieseguire la stima.
#### Uso di standard per il codice
Poiché il codice è condiviso da tutto il team di sviluppo e ognuno ha il permesso di modificarlo in qualunque momento, è necessario stabilire degli standard di codifica già documentato che tutti gli sviluppatori devono utilizzare per rendere il codice più leggibile, evitare di dover riformattare il codice e far apparire il codice più uniforme.
