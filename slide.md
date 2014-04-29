# <span style="background: #0099ff; color: white">Let's</span> Go
## Una Breve Introduzione A Go

---
= data-x="500" id="install"

## Installare Go

Su Debian/Ubuntu:

    sudo apt-get install golang
    
Su ARCH:
    
    sudo pacman -S go
    
Per ulteriori informazioni andare [qui](http://golang.org/doc/install).


---
= data-x="500" data-y="500" id="intro"

# <span style="background: #0099ff; color: white">Intro</span>duzione

---
= data-x="500" data-y="1000" id="facts"

## Go Facts

- Go è un [**linguaggio di programmazione**](index.html#/prog).
- Go è [**compilato ed eseguito nativamente**](index.html#/compilazione).
- Go è [**linkato staticamente**](index.html#/linking) di _default_.
- Go **non usa GCC** di _default_.
- Go è [**Garbage Collected**](index.html#/gc) e ha una **Runtime**.
- Go ha un _feeling_ simile a un [**linguaggio di scripting**](index.html#/scripting).
- Go propone delle primitive per il **parallelismo**
- _Chuck Norris può compilare qualsiasi linguaggio di programmazione, a mente._

---
= data-x="1000" data-y="1000" data-rotate-y="-35" id="prog"

## Linguaggio di programmazione

Caratteristiche:

- *Compilato*
- *Concorrente*
- *Tipizzazione Statica*
- *Fortemente Tipizzato*

--- 
= data-x="1000" data-y="1500" data-rotate-y="-35"

# [MEH](http://www.urbandictionary.com/define.php?term=meh)

--- 
= data-x="1000" data-y="2000" data-rotate-y="-35" id="compilazione"


## Compilato ed Esecuzione

Si propone come sostituto moderno a C/C++:

- Condivide stile 'minimale' di C
- Non dimentica *programmazione* *funzionale* e *a oggetti*
- [Il compilatore di Go è molto più veloce di gpp](https://stackoverflow.com/questions/2976630/why-does-go-compile-so-quickly)
- [Eseguibili Go possono essere più veloci di eseguibili C](http://roberto.costumero.es/en/2012/02/07/go-vs-c-benchmark-puede-ser-go-mas-rapido-que-c/)

--- 
= data-x="1000" data-y="2500" data-rotate-y="-35" id="linking"

## Linking Statico

### Cos'è il linking?

> Il linking (letteralmente "collegamento") è il procedimento di integrazione dei vari moduli a cui un programma 
> fa riferimento (i quali possono essere sottoprogrammi o librerie), per creare una singola unità eseguibile.

--- 
= data-x="1000" data-y="3000" data-rotate-y="-35"

## Linking Statico

### Cos'è il linking statico?

> Il link statico delle librerie avviene direttamente in fase di compilazione. 
> Linker più semplici inglobano nell'eseguibile finale l'intera libreria, 
> mentre quelli più avanzati solo la parte di codice realmente usata, 
> evitando quindi inutile spreco di spazio e riducendo i tempi di avvio 
> del programma e la quantità di memoria principale usata.

--- 
= data-x="1000" data-y="3500" data-rotate-y="-35"

## Linking Statico

Vantaggi:

- Velocità/Facilità di distribuzione
  1. Velocità deploy in ottica cloud/sistemi eterogenei.
  2. Evita dependency madness.
  3. Evita rotture per incompatibilità ABI.

--- 
= data-x="1000" data-y="4000" data-rotate-y="-35"

## Linking Statico

Svantaggi:

- Maggiore utilizzo RAM/disco in caso di funzioni condivise linkate staticamente più volte.
  1. Il linker di go 'importa' solo le funzioni usate.
  2. Di questi tempi il costo principale non è dato dalla memoria RAM/HD ma dal setup.
- Problemi di licenza con LGPL.

--- 
= data-x="1000" data-y="4500" data-rotate-y="-35" id="gc"

## Garbage Collection e Runtime

- Non c'è bisogno di liberare la memoria manualmente.
    
- Non esiste aritmetica dei puntatori.
    
- I thread sono managed:
  1. Di default sono mappati a **GOMAXPROCS** processi fisici.
  2. Istantaneamente non ci sono mai in esecuzione più di **GOMAXPROCS** managed thread.
  
- La Runtime viene inclusa integralmente nell'eseguibile statico.

--- 
= data-x="1000" data-y="5000" data-rotate-y="-35" id="scripting"

## Scripting Feeling

Condivide:

- Sintassi simile a pseudo-codice.
- Runtime avanzata.
- Garbage collection.

Per compilare e eseguire velocemente uno 'script' go si può invocare:

    go run main.go
    
---
= data-x="500" data-y="5000" id="syntax"

# <span style="background: #0099ff; color: white">Sinta</span>ssi

---
= data-x="1000" data-y="5000" data-rotate-y="-35" id="vars"

## Variabili

Dichiarazione:

    var ident [tipo]
    // example:
    var i int
    
Assegnamento:

    ident = [istanza]
    // example:
    i = 42
    
- Assegnamento simile a C
- Dichiarazione tipo variabile a destra per:
  1. Migliore leggibilità
  2. Maggiore efficienza del compilatore

    
---
= data-x="1000" data-y="5500" data-rotate-y="-35"

## Variabili

Dichiarazione + Assegnamento:

    ident := [istanza]
    // example:
    j := "The Answer to The Question"
    
- Tipo _inferito_ dal compilatore.
- Differente da linguaggi dinamici:
  1. Non è possibile assegnare a `j` un altro tipo.
  2. Feeling identico.
    
---
= data-x="1000" data-y="6000" data-rotate-y="-35"

## Funzioni

Definizione:

    func getTheAnswer(question string) int {
      if question == "The Answer to the Question" {
	    return 42
      } else {
	    return -1
      }
    }
    
- Il tipo è sempre a destra
- Le definizioni sono procedute dalla keyword `func`

---
= data-x="500" data-y="6000" id="tour"

# <span style="background: #0099ff; color: white">To</span>ur

Andate su [tour.golang.org](http://tour.golang.org).

