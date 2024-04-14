# Refactoring
Il refactoring è una tecnica di miglioramento del codice. Con il refactoring si segue un processo che cambia in piccole parti (con grosse modifche è più facile rompere il codice) il software senza modificarne il comportamento esterno ma che migliora la sua struttura interna cioè il codice sorgente. Il refactoring si esegue sia durante l'implementazione del codice che durante la fase di manutenzione. Un esempio banale di refactoring è eliminare frammenti di codice duplicati esternizzandoli in una funzione. 

Il refactoring rende più semplice la leggibilità del codice, ne diminuisce la dimensione e di conseguenza ne aumenta la manuntenibilità. Permette inoltre di scoprire bug presenti nel codice perché promuove una comprensione profonda dello stesso, permette di velocizzare la progettazione (un codice scritto bene è più semplice da cambiare in corso d'opera).

Il refactoring si effettua seguendo delle tecniche stabilite. Il refactoring deve sempre essere accompagnato dal testing del codice: si effettua il test, si fa refactoring e si effettuano nuovamente i test. Se anche un solo test non viene superato allora il refactoring ha introdotto problemi nel codice che devono essere immediatamente risolti.

## Estrai metodo
Una tecnica di refactoring è quella di raggruppare un frammento di codice in un metodo che ne descrive lo scopo. Ad esempio applicando questa tecnica di refactoring al seguente codice
```java
public void printDovuto(double amount) {
	printBanner();
	System.out.println(“nome: ” + nome);
	System.out.println(“tot: ” + somma);
}
```
otteniamo
```java
public void printConto(double somma) {
	printBanner();
	printDettagli(somma);
}
public void printDettagli(double amount) {
	System.out.println(“nome: ” + nome);
	System.out.println(“tot: ” + somma);
}
```
### Motivazioni
Quindi applichiamo questa tecnica quando si ha un metodo inutilmente lungo che probabilmente svolge più funzioni contemporaneamente. Separando le funzioni in metodi diversi non solo aggiungiamo un livello di astrazione che, come nel nostro caso separa le chiamate alle funzioni di libreria del linguaggio, ma rendiamo quei metodi riutilizzabili in altre parti del codice. Il metodo `printConto()` è diventato una descrizione di alto livello delle operazioni che sto effettuando al suo interno. Solo leggendo il codice senza commenti so che per stampare il conto devo effettuare due operazioni diverse `printBanner()` e `printDettagli()`. 
### Meccanismi
Si crea un nuovo metodo il cui nome esprime l'intenzione precisa del metodo stesso. SI copia il frammento di codice estratto dal metodo sorgente nel nuovo metodo dichiarato. Se il codice estratto utilizza variabili locali al metodo sorgente queste vengono rese paramentri del nuovo metodo nel caso in cui le legga semplicemente, altrimenti si dichiarano tali variabili nel nuovo metodo. Se una variabile dichiarata dal metodo sorgente viene modificata dal codice estratto allora si rende il nuovo metodo un metodo query che ritorna al codice sorgente la variabile modificata. Infine si sostituisce nel metodo sorgente il codice estratto con la chiamata al nuvo metodo.
### Esempio
```java
public class Ordine {
	private double importo;
	public double getImporto() {
		return importo;
	}
}
public class Stampe {
	private ArrayList<Ordine> ordini;
	private String nome = "Mike";

	public void printDovuto() {
		Iterator<Ordine> i = ordini.iterator();
		double tot = 0;
	
		// scrivi banner
		System.out.println("----------------");
		System.out.println("- Cliente Dare -");
		System.out.println("----------------");
	
		// calcola totale
		while (i.hasNext()) {
			Ordine o = i.next();
			tot += o.getImporto();
		}
	
		// scrivi dettagli
		System.out.println("nome: " + nome);
		System.out.println("tot: " + tot);
	}
}
```
Diventa
```java
public class Stampe2 {
	private ArrayList<Ordine> ordini;
	private String nome = "Mike";

	public void printDovuto() {
		printBanner();
		double tot = getTotale();
		printDettagli(tot);
	}

	public double getTotale() {
		Iterator<Ordine> i = ordini.iterator();
		double tot = 0;
		while (i.hasNext()) {
			Ordine o = i.next();
			tot += o.getImporto();
		}
		return tot;
	}

	public void printBanner() {
		System.out.println("----------------");
		System.out.println("- Cliente Dare -");
		System.out.println("----------------");
	}

	public void printDettagli(double somma) {
		System.out.println("nome: " + nome);
		System.out.println("tot: " + somma);
	}
}
```


## Sostituizione var temporanea con query
Viene applicata quando un metodo utilizza una variabile locale temporanea che memorizza il risultato di un'espressione. La presenza di variabili temporanee induce ad un aumento della lunghezza del codice e di un eventuale maggiore complessità di questo nel caso fosse necessario rendere la variabile visibile ad altri metodi. Per risolvere il problema si estrae l'espressione che da il valore alla variabile in un metodo separato e si sostituiscono tutte le referenziazioni alla variabile temporanea con la chiamata al nuovo metodo query che sarà visibile a tutti i metodi della classe. Ad esempio il codice
```java
double prezzoBase = quantita * prezzo;
```
diventa
```java
private double prezzoBase(){
	return quantita * prezzo;
}
```
Questa tecnica è banale se la variabile temporanea viene assegnata una sola volta.
### Esempio
```java
private double quantita, prezzo;

public double getPrezzo1() {
	double prezzoBase = quantita * prezzo;
	double sconto;
	if (prezzoBase > 1000) sconto = 0.95;
	else sconto = 0.98;
	return prezzoBase * sconto;
}
```
Diventa
```java
private double quantita, prezzo;

public double getPrezzo2() {
	return prezzoBase() * sconto();
}

private double prezzoBase() {
	return quantita * prezzo;
}
private double sconto() {
	if (prezzoBase() > 1000) return 0.95;
	return 0.98;
}
```

## Divisione variabile temporanea
Si usa quando una stessa variabile temporanea viene assegnata più volte fuori da loop e che non viene utilizzata per accumulare valori. La tecnica consiste nell'usare variabili diverse per ciascun assegnamento. Ad esempio il seguente codice
```java
double temp = 2 * (height + width);
System.out.println(temp);
temp = height * width;
System.out.println(temp);
```
diventa
```java
final double perim = 2 * (height + width);
System.out.println(prim);
final double area = height * width;
System.out.println(area);
```
### Motivazioni
Se una viariabile temporanea viene assegnata più volte allora molto probabilmente ha più di una responsabilità all'interno del metodo quando ogni variabile dovrebbe avere una singola responsabilità.
### Esempio
```java
private double primaryForce, secondaryForce, mass, delay;
public double getDistanceTravelled1(int time) {
	double result;
	double acc = primaryForce / mass; // prima assegnazione
	int primaryTime = (int) Math.min(time, delay);
	result = 0.5 * acc * primaryTime * primaryTime;
	int secondT = (int) (time - delay);
	if (secondT > 0) {
		double primaryVel = acc * delay;
		acc = (primaryForce + secondaryForce) / mass; // seconda assegnazione
		result += primaryVel * secondT + 0.5 * acc * secondT * secondT;
}
return result;
}
```
Diventa
```java
public double getDistanceTravelled2(int time) {
	double result;
	final double primAcc = primaryForce / mass;
	int primaryTime = (int) Math.min(time, delay);
	result = 0.5 * primAcc * primaryTime * primaryTime;
	int secondT = (int) (time - delay);
	if (secondT > 0) {
		double primaryVel = primAcc * delay;
		final double secondAcc = (primaryForce + secondaryForce) / mass;
		result += primaryVel * secondT + 0.5 * secondAcc * secondT * secondT;
	}
	return result;
}
```