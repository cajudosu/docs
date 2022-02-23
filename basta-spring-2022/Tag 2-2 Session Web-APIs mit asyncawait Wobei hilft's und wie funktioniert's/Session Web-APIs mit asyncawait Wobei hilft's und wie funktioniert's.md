# Session Web-APIs mit async/await: Wobei hilft's und wie funktioniert's?


- Macht async/await meine API schneller?
  - NEIN
  - Aber es macht die Arbeit effizienter
- Prozesse und Threads
  - frühe Virtualisierungskonzepte
- Threads
  - terminiert
  - gibt Ressource ab
  - muss warten
  - Management erzeugt Overhead
    - Kontextwechsel benötigt Zeit
    - Registerinhalte müssen ausgetauscht werden
    - Benötigte werde sind möglicherweise nicht im Cache
  - CPU mit Hyperthreading hat mehrere Sätze von Registern
    - Austasuch von Registerwerten blockiert nicht die CPU
    - Kaum CPU-Zyklen werden verschenkt
    - Wenn Thread plötzlich warten muss, kann Thread in anderen Registern weiterlaufen
  - Thread-Zahl erhöhen
    - Trugschluss: Dadurch laufen mehr meiner Threads auf den Cores
  - ist Abstraktion einer CPU
  - Ein lauffähiger Thread pro CPU ideal
- Synchroner vs Asynchroner I/O
  - Beispiel: Datei-Lesen Synchron
    - Datenstruktur IRP (I/O request packet) allokieren
    - Thread wechselt in Kernel-Mode
    - Thread blockiert während Hardware arbeitet
    - Warten ...
    - Interrupt von der Hardware
    - Thread wird unblocked
  - Beispiel: Datei-Lesen Asynchron
    - Unser Thread started asynchrone I/O-Operation UND läuft dann weiter
  - Code-Beispiele
    - Thread-Objecte
    - Frühe asynchrone Programmierung
	  - Thread.SpinWait(10000);
	    - Lässt Thread in enger (??) Schleife warten
	- Task-based asynchronous Patter
	  - Methode wird an Task.Run() übergeben
	  - Wo läuft ein Task? Auf anderem Thread??
- Task
  - abstrahiert Threads
  - Erhält Methode
  - "Kleines Stück Code", das "irgendwo" laufen kann
  - .NET Thread Pool
    - Wann immer ein Task erzeugt wird, wird er "in den Pool geschmissen"
    - Task-Liste
    - Endlosschlaufe schaut in der Task-Liste nach
    - Falls ein Task vorhanden ist, wird Task in einem der Threads ausgeführt
    - Thread Pool Management
      - kümmert sich darum, eine optimale Anzahl bestehender Threads im Pool zu haben
      - Nicht die Einstellungen des Managements verändern!
Thread Pool
  - Wenn in Thread, der nicht der Main-Thread ist, eine UnhandledException auftritt, wird der ganze Prozess inkl. aller Threads abgeräumt
async & await
  - async Task<> MyAsyncMethod()
  - Statemachine wird generiert, die wiederholt aufgerufen wird
Tipps & Tricks

