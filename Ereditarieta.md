# Ereditarietà
L'ereditarietà nella programmazione ad oggetti rende possibile definire una nuova classe che eredita attributi e metodi di una classe esistente definendo allo stesso tempo attributi e metodi propri. Consideriamo una classe *Persona* che ha attributi *nome* e *cognome*. Se definissimo una classe *Studente* potremmo dichiarare nuovamente gli attributi *nome* e *cognome* e aggiungere altri attributi come *matricola*, *voti*, ecc. oppure, seguendo una buona programmazione ad oggetti facciamo usiamo l'ereditarietà. Diremo che la classe *Studente* eredita la classe *Persona* seguendo la sintassi
```java
public class Studente extends Persona {}
```
Potremo accedere a tutti gli attributi e metodi di *Perona* attraverso la classe *Studente* e diremo che *Studente* è sottoclasse di *Persona* e *Persona* è superclasse di *Studente*.

La sottoclasse eredita tutti i metodi e gli attributi della superclasse e può usarli come fossero definiti localmente e allo stesso tempo può definire ulteriori metodi e attributi. La sottoclasse non può eliminare alcun attributo o metodo della superclasse.

### Visibilità
- Ciò che è `private` non è visibile alla sottoclasse.
- Ciò che `public` è visibile a tutti, comprese le sottoclassi.
- Ciò che è `protected` è visibile alle sottoclassi ma non a tutte le altri classi.

## Interfacce
Un'**interfaccia** è una classe che lascia il compito dell'implementazioni dei metodi alle sue sottoclassi. Non fornisce, quindi, alcuna implementazione dei metodi dichiarati, non permette di dichiarare attributi non inizializzati e non possiede un costruttore rendendola quindi non istanziabile. In poche parole, quello che fa un'interfaccia è di definire un tipo generico che deve essere specializzato ed implementato dalle sottoclassi. Un'interfaccia si definisce con la seguente sintassi
```java
public interface Interfaccia {/*elenco di signature di metodi*/}
```
Per specificare che una classe implementa un'interfaccia scriveremo
```java
public class Classe implements Interfaccia {/*implementazione dei metodi elencati nell'interfaccia*/}
```

## Classi astratte
Le classi astratte sono classi parzialmente implementate, contengono cioè alcuni metodi implementati e altri che non hanno implementazione (definiti tramite la keyword `abstract`). Un metodo `abstract` può essere invocato da altri metodi della classe e forza le sottoclassi ad implementare il metodo. Le classi astratte, così come le interfacce, non può essere istanziata.
Un esempio di classe astratta:
```java
public abstract class Libro {
	private String autore;
	public abstract void insert(); //metodo non implementato
	public String getAutore() { //metodo implementato
		return autore;
	}
}
```

## Compatibilità fra tipi
L'ereditarietà permette di definire una classificazione dei tipi. Una sottoclasse, infatti, è un **sottotipo** compatibile con la sua superclasse. Un modo semplice per vederlo è considerare che una sottoclasse è anche ciò che è la superclasse. Ad esempio una sottoclasse *Studente* è anche la sua superclasse *Persona*.

Questa compatibilità, ovviamente è unidirezionale. Una sottoclasse è compatibile con la sua superclasse ma non il viceversa. *Studente* è necessariamente *Persona* ma *Persona* non è necessariamente anche *Studente*. Grazie a tale compatibilità si può sostituire ogni istanza della superclasse con una istanza della sottoclasse. Ad esempio ogni istanza della classe *Persona* può essere sostiuita da istanze della classe *Studente* perché tutti i metodi e attributi di *Persona* possono essere richiamati da *Studente*.

### Late binding e polimorfismo
```java
public void m() {
	Persona p = new Persona();
	Studente s = new Studente();
	Persona px;
	if (i > 10)
		px = p;
	else
		px = s;
	px.printAll();
}
```
Il metodo `printAll()` invocato sull'istanza `px` di *Persona* può assumere il comportamente definito nella classe *Persona* o nella classe *Studente* (supponendo che *Studente* faccia overriding del metodo).

Nel ramo condizionale si decide se l'istanza `px` dovrà puntare all'istanza `p` di *Persona* o all'istanza `s` di *Studente*. In base alla decisione il metodo `printAll()` verrà richiamato sulla classe a cui `px` punta. A runtime, quindi, si decide quale implementazione di `printAll()` eseguire ovvero si ha una situazione di **late binding** (il tipo di un istanza viene stabilito a runtime) e il comportamento del metodo `printAll()` è polimorfo perché cambia durante l'esecuzione del codice.

Vediamo un'altro esempio
```java
public class Account {
	protected float balance;
	public void setBalance(float amount) {
		System.out.println("in account set-balance“);
		if (check(amount))
			balance += amount;
	}

	public boolean check(float amount) {
		System.out.println("in account check");
		return (balance + amount) >= 0;
	}
}
						   
public class SavingAccount extends Account {
	public boolean check(float amount) {
		System.out.println("in saving-account check");
		return (balance + amount) >= 1000;
	}
}

public class AccTest {
	public static void main(String[] args) {
		Account acc = new SavingAccount();
		acc.setBalance(1234);
	}
}
```

 Vediamo come nel main della classe `AccTest` viene dichiarata un'istanza della classe *SavingAccount* e memorizzata nella variabile `acc` di tipo *Account*. In segiuto sulla variabile `acc` viene richiamato il metodo `setBalance()` della superclasse *Account*.

Dentro `setBalance()` però viene richiamato il metodo `check()` che è definito sia nella superclasse che nella sottoclasse. Quindi quale di questi due viene richiamato? Quando un metodo (nel nostro caso `setBalance()`) viene chiamato su un oggetto, se ne controlla il tipo a runtime (*SavingAccount*). Si cerca quindi il metodo chiamato (`setBalance()`) nel tipo dell'oggetto a runtime (*SavingAccount*). Se questo non viene trovato allora viene eseguito quello della superclasse (*Account*).

Dato che `Account.setBalance()` esegue una chiamata a `check()` si ripete il processo. La classe *SavingAccount* ha il metodo `check()` quindi si esegue `SavingAccount.check().

In parole povere, dato che c'è late binding, quando si esegue un metodo su un oggetto, si andrà a cercare prima il metodo nel tipo a runtime dell'oggetto, se il metodo non viene trovato allora si comincia a risalire la gerarchia delle classi. Questa situazione viene detta **dispatch**.