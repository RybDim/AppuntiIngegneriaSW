# Design patterns
I **design pattern** sono strutture software per un piccolo numero di classi che descrivono soluzioni testate e di successo a problemi ricorrenti nella progettazione. Essi specificano le diverse classi che devono essere implementate per la risoluzione del problema e le loro relazioni. Esistono un'enorme quantità di design pattern. 

Ricapitolando un design pattern descrive un problema di progettazione ricorrente che si incontra in specifici contesti e presenta una soluzione collaudata genereica ma specializzabile.

La descrizione di un design pattern include cinque parti fondamentali:
 - *Nome*: permette di identificare il design pattern e indica lo scopo del pattern stesso.
 - *Intento*: descrive la funzionalità e lo scopo del pattern.
 - *Problema*: descrive il problema a cui il pattern deve essere applicato e le condizioni necessarie affinché sia applicabile.
 - *Soluzione*: descrive le classi che costituiscono il pattern, le loro responsabilità e le loro relazioni.
 - *Conseguenze*: descrivono i risultati, i vantaggi e gli svantaggi ottenuti dall'applicazione del pattern.

I design pattern vengono suddivisi in categorie in base al loro scopo finale:
 - **Creazionali**: riguardano problemi di creazione di istanza. Tra questi rientrano il *Singleton*, *Factory Method*, *Abstract Factory*, *Builder* e *Prototype*.
 - **Strutturali**: riguardano problemi di scelta della struttura. Permetton di astrarre il processo di creazione di istanze di classi. In particolare permettono di separare la logica di creazione, composizione e rappresentazione degli oggetti dal resto del programma. Tramite l'astrazione nascondono come le istanze di classi sono create e composte. Tra questi rientrano l'*Adapter*, *Facade*, *Composite*, *Decorator*, *Bridge*, *Flyweight* e *Proxy*.
 - **Comportamentali**: descivono problemi di scelta di incapsulamento di algoritmi. Tra questi troviamo *Iterator, Template Method, Mediator, Observer, State, Strategy, Chain of Responsibility, Command, Interpreter, Memento, Visitor*.

--- 

- [Singleton](./Singleton.md)
- [Factory Method](./FactoryMethod.md)
- [Adapter](./Adapter.md)
- [Abstract Factory](./AbstractFactory.md)
- [Facade](./Facade.md)
- [State](./State.md)
- [Observer](./Observer.md)