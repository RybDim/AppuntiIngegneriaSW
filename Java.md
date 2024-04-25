# Java
Con l'avanzare del tempo, i nuovi paradigmi e linguaggi di programmazione tendono a semplificare il lavoro del programmatore, nascondendo dietro librerie e costrutti del linguaggio parte della programmazione che prima doveva essere implementata direttamente dal programmatore.

Da Java 5 ad esempio si può iterare una lista o array senza dover specificare il valore di inizio e di fine dell'indice.
```java
List<String> nomi;
...
for(String nome : nomi){}
```
Da Java 7, invece è possibile omettere il tipo di elementi della collection al momento della sua istanziazione, lasciando al compilatore il compito di inferenza.
```java
List<String> nomi = new ArrayList<>();
```
Pur essendo un linguaggio imperativo, Java 8 ha introdotto caratteristiche tipiche della programmazione funzionale che spesso è più concisa ed espressiva.

## Espressioni lambda
```java
s -> System.out.println("Ciao " + s);
```
Un'espressione lambda è una **funzione anonima** (un metodo senza nome) che prende in ingresso parametri con nome dato a sinistra della freccia e un blocco di codice posizionato a destra della freccia. La caratteristica principale delle funzioni lambda è che possono essere passate come argomento di una funzione.

Nei linguaggi funzionali un'espressione lambda è detta **funzione pura** cioè una funzione il cui risultato dipende esclusivamente dai parametri in ingresso e che quindi non mantiene un proprio stato. In Java un'espressione lambda può essere non pura perché è possibile accedere a variabili esterne da dentro l'espressione.

Un'esempio di espressione lambda è
```java
(x, y) -> x + y
```
che prende in ingresso due parametri, `x` e `y`, e ne restituisce la somma. Non è necessario specificare il tipo dei parametri in input perché sarà il compilatore a dedurre il tipo a run-time.

Se il corpo dell'espressione è composto da più di un'istruzione è necessario usare le parentesi graffe
```java
(x, y) -> {
	System.out.println("x = " + x);
	return x + y;
}
```

## Stile funzionale
Lo stile di programmazione funzionale è dichiarativo è permette, all'interno di Java 8, di definire funzioni di ordine più alto cioè funzioni che prendono in input o ritornato altre funzioni.

## Java Collection
Le libreria standard di Java forniscono diverse inetrfacce e classi [collection](https://www.baeldung.com/java-collections-complexity). `Collection` è un'interfaccia che definisce metodi classici come `add()`, `remove()`, `size()`, `contains()`, `containsAll()` etc. che possono essere applicati in generale su collezioni di oggetti. 

|              | `get()`    | `add()`     | `contains()` | `remove()`  |
| ------------ | ---------- | ----------- | ------------ | ----------- |
| `ArrayList`  | *costante* | *costante*  | $O(n)$       | $O(n)$      |
| `LinkedList` | $O(n)$     | *costante*  | $O(n)$       | *costante*  |
| `TreeSet`    |            | $O(\log n)$ | $O(\log n)$  | $O(\log n)$ |

### Metodi di default
In Java 8 un metodo di default è un metodo che può essere implementato all'interno di un'interfaccia ma che non possono intervenire sullo stato delle classi che implementano l'interfaccia. Quaesta nuova funzionalità ha permesso l'inclusione di nuovi metodi su interfacce già esistenti senza compromettere la compatibilità delle applicazioni conformi a precedenti versioni di Java. Uno dei metodi di default dell'interfaccia *Collection* è il motodo `stream()`. Il metodo `stream()` permette di applicare la programmazione funzionale alle strutture dati.

Esso restituisce un tipo `Stream<T>` cioè una sequenza di elementi di tipo `T` cioè lo stesso tipo di elementi contenuti nella collection su cui si invoca `stream()`. Questo metodo permette di effettuare operazioni sugli elementi presenti nell'istanza di *Collection* su cui viene invocato. Il tipo *Stream*, inoltre, definisce diversi metodi di ordine più alto cioè che prendono in ingresso altre funzioni.

### Metodo filter
Il metodo `filter()`, definito dal tipo *Stream*, permette di applicare un criterio di filtraggio per gli elementi presenti nello stream. Facciamo un esempio.
```java
List<String> nomi = List.of("Nobita", "Nobi", "Suneo");
long c = nomi.stream()
			 .filter(s -> s.equals("Nobi")) 
			 .count();
```
Il metodo `filter(Predicate<T> p)` è un metodo del tipo *Stream* che prende come argomento una funzione che ritorna un booleano quindi un predicato e che ritorna in output uno stream composto da soli gli elementi che soddisfano il predicato.

Nell'esempio viene creato uno stream a partire dall'istanza `nomi` di *List* attraverso il metodo `stream()`, poi viene applicato il metodo `filter()` con funzione lambda `s -> s.equals("Nobi")`. `filter()` applicherà la funzione lambda a tutti gli elementi dello stream e scarterà tutti gli elementi per cui il predicato risulta falso, in questo caso scarterà tutte le stringhe che non sono uguali a *"Nobi"*. Infine viene applicato allo stream ritornato da `filter()` il metodo `count()` restituisce il numero di elementi presenti nello stream.

`filter()` si dice essere un metodo **lazy** o un'**operazione intermedia** cioè un metodo che non viene eseguito finché non è necessario. Quando diventa necessario eseguire un metodo lazy? Quando si richiama un metodo **eager** o **operazione terminale** cioè quei metodi che generano un valore di ritorno su cui ovviamente non posso eseguire altri metodi lazy. Nel nostro esempio il metodo `count()` è un metodo eager che restituisce il numero di elementi dello stream e che di fatto forza l'esecuzione di tutti i metodi lazy che lo precedono. 

Tutti i metodi che restituiscono un tipo *Stream* sono operazioni intermedie mentre tutti i metodi che restituiscono un valore sono operazioni terminali.
#### Tipo Predicate
*Predicate* è un'**interfaccia funzionale** cioè un'interfaccia che definisce un solo metodo. Nello specifico con *Predicate* è possibile implementare l'unico metodo tramite un'espressione lambda che restituisce true o false.
```java
Predicate<Integer> positive = x -> x >= 0;
```
Si può definire una classe che funge da interfaccia funzionale tramite l'annotazione `@FunctionalInterface` che indica al compilatore che l'interfaccia ha e deve avere un solo metodo astratto. Se aggiungiamo un altro metodo astratto all'interfaccia, il compilatore genererà un errore.

*Predicate* definisce il metodo `test()` che prende in ingresso un parametro di tipo *Object*.
### Metodo Reduce
`reduce(T identity, BinaryOperator<T> accumulator)` è un motodo dell'interfaccia `Stream` che prende in input due parametri: un valore dello stesso tipo degli elementi nello stream e un'operazione binaria. `reduce()` è un'**operazione terminale**.

`reduce()` serve quando si vuole passare da un insieme di valori ad un unico valore. Ad esempio il metodo `count()` è una sorta di reduce perché riduce l'insieme di valori in un unico valore. Ad esempio, per ottenere la somma dei valori di uno stream scriveremo
```java
reduce(0, (accum, v) -> accum + v);
```
`reduce()` applica la funzione di accumulazione `(accum, v)` ,che prende in input un valore iniziale di accumulazione `accum` e un valore dello stream `v`, a tutti gli elementi dello stream e ritorna un risultato dello stesso tipo dei valori nello stream. Lo `0` rappresenta il valore iniziale dell'accumulatore `accum`. 
```java
public class Pagamenti {
	private List<Float> import = new ArrayList<>();
	public float calcolaSomma(){
		return importi.stream()
					  .reduce(0f, Float::sum);
	}
}
```
Tramite un overload del metodo possiamo anche non specificare il valore iniziale dell'accumulatore che prenderà il valore del primo elemento dello stream. Dato che lo stream potrebbe essere vuoto e non sarebbe possibile assegnare un valore all'accumulatore bisogna memorizzare il risultato in un'istanza di tipo `Optional`.
```java
Optional<Integer> sum = list.stream().reduce(Integer::sum);
if(sum.isPresent())
	System.out.println("sum = " + sum.get());
```
### Metodo Map
`map(Function<T, R> mapper)` è un metodo che prende in ingresso una funzione che mappa ogni valore di ciascun elemento dello stream in un altro valore applicando la funzione ad ogni elemento dello stream. `map()`, quindi, restituisce uno stream i cui valori sono il risultato dell'applicazione della funzione su ciascuno degli elementi dello stream iniziale. Dato che restituisce uno stream, `map()` è un'**operazione intermedia**. Ad esempio `map(x -> x * 2)` restituisce uno stream in cui ciascun elemento è il doppio dell'elemento nello stream originale.
```java
List<Persona> amici = Arrays.asList(
	new Persona("Saro", 24), new Persona("Taro", 21),
	new Persona("Ian", 19), new Persona("Al", 16));

// map restituisce uno stream contenente le eta di ciascuna istanza di Persona, lo stream viene dato in input a reduce che calcola la somma di tutti gli elementi
int somma = amici.stream()
				 .map(Persona::getEta)
				 .reduce(0, Integer::sum);
```
## Stateless-Stateful
Le operazioni come `map()` e `filter()` si dicono operazioni **stateless** perché non mantengono uno stato interno, semplicemente prendono un elemento dello stream e restituiscono zero oppure un risultato per ciascuno degli elementi.

Le operazioni come `sorted()` e `distinct()`, invece, devono conoscere necessariamente tutti gli elementi dello stream per poter essere eseguiti, di conseguenza si dicono essere operazioni **stateful**.

## Iterate
`iterate()` è un metodo che permette di generare uno *Stream* a partire da una funzione. `iterate()` restituisce uno stream infinito e ordinato dato dall’esecuzione iterativa di una funzione `f` applicata inizialmente ad un elemento seme,
quindi produce uno stream di `seme, f(seme), f(f(seme))` ecc.

Per troncare la lunghezza dello stream ad un valore fissato si usa il metodo
`limit()` che prende in input un valore.
```java
Stream.iterate(2, n -> n * 2)
	  .limit(10)
	  .forEach(System.out::println);
```
Nell’esempio il metodo `iterate(2, n -> n * 2)` genera uno stream infinito di potenze di 2 (2, 4, 8, 16...). Il metodo `limit(10)` tronca lo stream ai primi 10 elementi e il metodo `.forEach(System.out::println)` applica ad ogni elemento la funzione passata in input, in questo caso stampa gli elementi.
## Generate
Il metodo generate() permette di produrre uno stream infinito di valori tramite
una funzione di tipo Supplier ovvero che fornisce un valore. Il metodo non
applica una funzione per ogni elemento dello stream.
```java
Stream.generate(() -> Math.round(Math.random() * 10))
	  .limit(5)
	  .forEach(System.out::println());

Stream.generate(Math::random)
	  .limit(5)
	  .forEach(System.out::println));
```
L’esempio genera uno stream contenenti numeri casuali tra 0 e 10 e lo tronca
a 5 elementi.

La differenza sostanziale tar il metodo `iterate()` e `generate()` è che il primo prende in input il risultato dell'iterazione precedente mentre il secondo genera ogni volta un elemento in maniera indipendente dall'iterazione precedente.