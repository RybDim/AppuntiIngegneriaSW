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