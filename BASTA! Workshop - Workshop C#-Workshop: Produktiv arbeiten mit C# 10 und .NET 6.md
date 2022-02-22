
BASTA! Workshop - Workshop C#-Workshop: Produktiv arbeiten mit C# 10 und .NET 6
===============================================================================

Redner: Rainer Stropek

### Links
- https://rainerstropek.me/
- https://slides.com/rainerstropek/csharp-10/fullscreen
- https://github.com/rstropek/Samples/tree/master/CSharp10/FunWithTrees
- sharplab.io
- source.dot.net (Kommentierter .NET source code)
- https://devblogs.microsoft.com/dotnet/string-interpolation-in-c-10-and-net-6/
- https://create.kahoot.it/share/net-6-strings/39b3d6b4-9ecf-41ce-9ff0-46a76833489e (String interpolation Kahoot quiz)
- https://slides.com/rainerstropek/csharp-11/fullscreen
- https://softwarearchitects1com-my.sharepoint.com/personal/rainer_software-architects_at/_layouts/15/onedrive.aspx?id=%2Fpersonal%2Frainer%5Fsoftware%2Darchitects%5Fat%2FDocuments%2Fcsharp%2D11%2Epdf&parent=%2Fpersonal%2Frainer%5Fsoftware%2Darchitects%5Fat%2FDocuments
- https://softwarearchitects1com-my.sharepoint.com/personal/rainer_software-architects_at/_layouts/15/onedrive.aspx?id=%2Fpersonal%2Frainer%5Fsoftware%2Darchitects%5Fat%2FDocuments%2Fcsharp%2D10%2Epdf&parent=%2Fpersonal%2Frainer%5Fsoftware%2Darchitects%5Fat%2FDocuments
- https://softwarearchitects1com-my.sharepoint.com/personal/rainer_software-architects_at/_layouts/15/onedrive.aspx?id=%2Fpersonal%2Frainer%5Fsoftware%2Darchitects%5Fat%2FDocuments%2Fdotnet%2D6%2Epdf&parent=%2Fpersonal%2Frainer%5Fsoftware%2Darchitects%5Fat%2FDocuments
- https://slides.com/rainerstropek/ (Alle Foliensätze)

## Session 1 (Code-Beispiel mit Neuerungen)

### Current vs LTS
- Current und Long Termin Support abwechselnd
- Long Term Support - konservativ
- Current - Neue Features, öfter updaten

### Projekt
- Hashbasiert Fraktalbaum zeichnen

### csproj-Datei
TFM - target framework moniker

### Implicit usings
- usings die MS als besonders wichtig erachtet werden automatisch importiert
- hängt ab vom Projekt-Typ
- Komplexität reduzieren
- gut für Studenten, die zunächst Spaß ander Sprache bekommen sollen
- Global usings um implicit usings zu erweitern

### Nullable
- zukünftig am besten immer mit Nullable:enable arbeiten
```csharp
Person p = new(); // Neue Schreibweise
```
- Variablen, die null enthalten können sollen, müssen explizit mit dem '?' markiert werden
```csharp
Person? p; p = null;
Console.WriteLine(p?.FirstName ?? string.Empty);
```
- GROßES ZIEL: NullReferenceExceptions vermeiden
- Datei-spezifisch: `# nullable enable`

### AllowUnsafeBlocks
```xml
<AllowUnsafeBlocks>true</AllowUnsafeBlocks>
```

### SkiaSharp
- Wrapper für Skia
- 2D rendering engine
- wird unter anderem von Chrome genutzt

### Usings.cs
- global usings SkiaSharp;
- Diese usings werden im gesamten Projekt genutzt
- Etwas mehr für IntelliSense zu durchsuchen
- Code hingegen wird prägnanter

### String-Konstanten C#6
```csharp
const string foo = $"{IAmAlsoAStringConst}"
```
- Erzeugung von String-Konstanten aus String-Interpolation durch andere String-Konstanten zur Kompilierzeit

### UTF8
- C#7 wird besser mit UTF8 umgehen können

### Fixed Seed
- Durch fixend Seed (Saat, Ausgangspunkt) immer die gleichen randomisierten Winkel für Äste

### Linq
- Linq-Enhancements: Neue Linq-Funktionen in C#6
- Chunk()
- Hash-Array wird in 4-Byte-Chunks unterteilt

### #region
- zusammenklappbare benannte Region im Editor
- Wird genutzt um verschiedene Programm-Regionen nach und nach aus GitHub in eigene Applikation zu kopieren

### record structs
- records (record classes)
  - immutable
  - Default constructor
  - Klasse die ausschließlich Daten beinhaltet
  - IEquatable (zum Vergleichen)
  - ToString
  - Gut für Schnittstellen und DataTransferObjects
  - records waren immer Klassen
  - record-Deklaration müsste korrekterweise record class geschrieben werden, record ist Abkürzung
- record structs
  - wie records nur als Value-Type
  - Werte werden zu einem value type zusammengefasst 
  - können auch als readonly deklariert werden
  - Beispiel: Vector
  - Alternative Konstruktoren möglich

### stackalloc
  - anstelle von new
  - Array von value types auf Stack statt auf Heap allokieren
  - Warum Stack? 
    - Kein GC nötig
    - Bei Verlassen des Scopes wird Speicher automatisch deallokiert
    - record structs können mit stackalloc auf den Stack gelegt werden
    - Beispiel:
      - Limit() Methode
        - wirft Exception wenn Limit von 256KB des Stacks überschritten wird
      - CallerArgumentExpression
        - Ermöglicht die Rückgabe des Ausdrucks, der als Parameter übergeben wurde, als String
        - Für bessere Ausgaben bei Expressions

### implicit typing
- new ohne Typ benutzen
- Beispiel: Person p = new();
- macht Git-Commits kleiner
- Evtl. ist Code nicht so selbsterklärend

### Natural Type für Lambda-Funktionen
- Kein expliziter Typ für Lambda-Funktionen mehr benötigt
- var ausreichend

### using var
```csharp
using var x;
```
- Alternative zu
```csharp
using (var x = ...) {
    
}
```
- sorgt dafür, dass Objekt automatisch disposed wird bei Verlassen des Blocks
- alte Variante erlaubt exakte Kontrolle darüber, wann Objekt disposed wird

### record structs (Fortsetzung)
- haben automatisch Methode zur Generierung eines HashKeys
- können dadurch als Key eines Dictionarys genutzt werden
- `TryGetValue()` eines Dictionarys
  - Schaut nach ob schon Wert für einen Key existiert
    - falls ja, wird out value gesetzt
    - sonst, gibt false zurück

### feature flags
- wenn man bestimmte Funktion haben will muss explizit Feature aktiviert werden
- Für Features, die noch nicht ganz fertig sind, aber viellicht trotzdem schon genutzt werden sollen

### ISupportAdding
- Datentyp der Addition unterstützt
- in C#10 können Interfaces static abstract Methoden hinzugefügt werden
- static Methoden konnten zuvor nicht zu Intefaces hinzugefügt werden
- Operatoren wie + sind als statische Methoden umgesetzt

### Lambda-Expressions
```csharp
x => x * x
```

## Session 2 (C#10)

### Record Classes vs Record Structs
- record classes
  - Sind im Prinzip GENERIERTE KLASSEN
  - Gut zu sehen in sharplab.io
  - per default immutable
  - Sealed overrides
    - Damit bei Generierung bestimmte Methoden nicht generiert und dadurch überschrieben werden
- record struct
  - ist per se veränderbar
  - readonly macht record struct unveränderbar
  - PrintMembers() method wird automatisch generiert
    - Diese kann überlagert werden mit privater Methode mit gleicher Signatur
    - Kommt so bisher an keinen anderen Stellen in C# vor

### Global Usings
  - bereits zuvor erklärt

### File-scoped Namespaces
  ```csharp
  namespace MyApp;
  ```
  - statt
  ```csharp
  namespace MyApp {
...
}
```
### Definite Assignment Improvements
- Assignment of variable inside a pattern
```csharp
if (getAnimal(out Animal animal) && animal is Cat c) {
    WriteLine(c.Purr()); // c ist definitely assigned here!
}
WriteLine(c.Purr()); // Does not work because not definitely assigned outside if block, only declard in outer block
```

### Static Abstract Members in Interfaces
- Demnächst Änderungen am System namespace -> kommt äußerst selten vor
- Generische Mathematik
- Interfaces für arithmetische Operationen
- Anwendungsfälle: Generische Implementierung Algorithmen, die mit Datentypen arbeiten, die arithmetische Operationen unterstützen
- Zum Ausprobieren System.Runtime.Experimental einziehen

### Lambda Improvements
- In the past
```csharp
Func<int> f1 = () => 42;
```
- With C#10
```csharp
var f2 = () => 42;
```
- Add attributes directly to lambda expression that is passed as a parameter
```csharp
AddAction([HttpGet("/")] () => "Home");
```
  - Useful für ASP.NET

### String Interpolation
- String Interpolation zur Kompilierzeit zur Erzeugung von String-Konstanten
- C# holt gegenüber anderen Sprachen z.B. Rust auf
  - Rust hat intelligenten Compiler der viel bereits zur Kompilierzeit berechnet

### Caller Argument Expression
- Expressions, die als Parameter übergeben werden, könne in Exception als String ausgeben

### Declarations and Deconstruction
- Für Go-Programmierer
  - In Go hat eine Funktion immer zwei Rückgabewerte
    1. Ergebniswert im Erfolgsfall
    2. Error-Objekt
```csharp
(int?, string?) GetAnswer() => (42, "foo");
(var foo, bar) = getResult();
```
- Argumentation gegen Exceptions
  - Fehler dort behandeln wo er auftritt

### Pattern Matching Enhancements
- ALT:
```csharp
if (hero is Hero { Flying : { CanFly : true })
```
- NEU:
```csharp
if (hero is Hero { Flying.CanFly : true })
```

### Quiz
- String templates/Interpolated Strings können und sollen genutzt werden.
- C# compiler erkennt einfache concats.
- String mit `$@" ... "` funktioniert (interpolated verbatim string
```csharp
var string = $@"I'm line 1
and I'm line 2 and the val of {nameof(x)} is {x}."
```

- ArrayPool
  - Cache/Pool von großen ByteArrays
  - Ziel: Weniger Speicher allokieren
- string.Create()
  - Kann Byte Array übergeben werden, insbesondere eines, das auf dem Stack erzeugt wurde
- Span direkt mit Interpolation beschreiben

## Session 3 (C#11)

### .NET vNext
- LDM - language design meeting
  - Entwickler der Sprache diskutieren über Erweiterungen

### Newlines In interpolation
```csharp
Console.WriteLine($"{
    random.Next();
}");
```

### Pattern Matching Enhancements
- list pattern (C#11)
```csharp
if (numbers is [1,2,3,5,8]) {
    WriteLine("Fibonacci!");
}
```
- list pattern can be combined with all other patterns
  - var and list pattern combination
```csharp
if (numbers is [var first, 2,3,5, var last] && first is 1 && last is 8)
```
  - list patterns and switch expressions
  - relational patterns with list patterns
  - relational patterns
    - können überall stehen wo expresseions stehen können
    - and ist spezifisch für relational patterns

### Simplified Null Checking
- Diskussionen auf Twitter: Community ist gespalten
- Bang-Operator: ! (pass null as a parameter although forbidden by type)
- Neuer Operator: !! (generates check for null that throws exception)

### Inlining
- Analog zu Inlining bei C/C++
- Wird angewendet wenn Methoden "kurz genug" sind

### Raw string literals
- Verbatim String Interpolations
- Gut, um Code einzubetten:

```csharp
var s = """
SELECT *
FROM products
WHERE id = 345
""";
```

- Bei `"""` im String den String mit `""""` einschließen

### Generic Attributes
```csharp
[MyVersion<int>(2)]
class MyClass {}
```
### Deconstructing Defaults
- Methods that return tuples
```csharp
public static (int, float, string) getData();

int foo;
float bar;
string baz;

(foo, bar, baz) = getData();
```
- Deconstructors
```csharp
Person person = new() {First = "John", Last = "Doe"};
(string first, string last) = person; // Deconstruction here
Console.WriteLine($"{first} {last}");

class Person {
    public string First { get; init; }
    public string Last { get; init; }
    
    public void Deconstruct(out string first, out string last) {
        first = First;
        last = Last;
    }
}
```

- Deconstructing defaults
```csharp
 (int foo, float bar) = default;
 ```


### Semi-Auto Properties
- automated property
```csharp
public string foo { get; set; }
```

- semi-automated property
```csharp
public string foo {
    get => field;
    set {
      value.Trim();
      field = value;
      PropertyChanged?.Invoke(this, ...);
    }
}
```

- per `value` kann auf den übergebenen Wert, per `field` auf das Objekt-Feld zugegriffen werden

### Required Members
- new keyword: `required`
```csharp
class Person {
    public required string FirstName { get; init; }
}
```

### UTF8 String Literals
```csharp
byte[] arr = "hello"; // Gets converted to UTF-8 automatically
var s = "hello"u8;    // UTF-8 string literal
```


## Session 4. (.NET)
- Existierten gleichzeitig
  - .NET Framework
  - Mono
  - .NET Core
  - .NET Standard
- **.NET: Ziel wieder zu vereinheitlichen**
  - .NET 5 (current version, kurze Haltbarkeit)
  - .NET 6 (LTS)
- Wozu .NET Standard
  - Libs schreiben, die in allen Frameworks funktionieren
- .NET 6
  - NEU: macOS Arm64
  - Patches for 3 years (LTS)
  - "Have a plan to switch to the new world"
- Redner hat selbst Firma
  - Projekt, die noch auf .NET Framework basieren
  - ... auch mit Angular.js
  - stellen nach und nach um (ähnlich Billbee)
  - Hat Billbee einen Umstell-Plan?
- **Crossgen2 / ReadyToRun**
  - IL wird generiert
  - JIT übersetzt in Maschinensprache (ML)
  - ML Code wird gecached
  - Folgeaufrufe auf bestimmte Methoden landen sofort in ML
  - Ahead of time compilation, um initiale langsame Ausführung zu verhindern
  - Vorstellung am Beispiel
    - ReadyToRun benötigt mehr Speicher ~2MB vs ~6MB
    - Messung der Startup-Zeit einer Sample Application mit einem Low Level Debugger (PerfView)
    - Messung auch möglich mit: Benchmark.NET
- **Sync-over-async**
  - for-Schleife die n Tasks startet
  - Anschließendes WaitAll()
  - .NET6 erkannt sync-over-async-Muster und ist aggressiver beim Hinzufügen von Threads zum Thread-Pool
- **JsonSerializeCodeGen**
  - Zur Kompilierzeit wird bereits ein Deserialisierer für bestimmte Klassen generiert
  - Startup Performance wird verbessert -> Gut für Server Instanzen die in der Cloud oft gestartet/gestoppt werden
  - **Generelles Muster:** So viel wie möglich zur Kompilierzeit generieren
    - In nächsten .NET-Versionen auch für reguläre Ausdrücke
  - ISourceGenerator
    - Interface, falls man selbst einen Code-Generator schreiben möchte
    - Generator wird beim Kompilier-Prozess mit eingebunden
    - Pro Token wird eine Callback-Methode aufgerufen
    - Callback-Methode prüft anhand von Reflection und Attributen, ob für bestimmte Tokens Code generiert werden soll
    - Strings mit dreifachen Anführungszeichen (""", siehe oben) sind geignet, um zu generierenden Source Code zu hinterlegen
- **LinkerLibraryClient / Assembly Trimming**
  - Entfernt Code, der nie aufgerufen wird
  - Vorsichtig sein: Es gibt Randfälle, wo zuviel getrimmt wird
    - Dynamisches Laden von DDLs, die in einem bestimmten Verzeichnis liegen
  - Über .csproj-Datei kann man bestimmte Assemblies vom Trimming ausschließen
  - Properties werden nicht getrimmt, Methoden sehr wohl
- **Gesamt-Strategie**
  - Berechnungen zu Kompilierzeit
  - Source-Code-Generation
  - Ahead-of-time-compilation

### Async Enumerables
- Verzahnung des Abrufs von Daten mit der eigentlichen Verarbeitung
- yield-Keyword

### JsonNode
- dynamischer Datentyp
- Szenario: JSON empfangen, dessen Struktur erst zur Laufzeit klar wird

### Linq Enhancements
- Take()-Methode
  - Akzeptiert jetzt Ranges z.B. ^2, 2..^2
- TryGetNonEnumeratedCount(out var count)
  - Falls eine vorberechneter Wert für die Länge existiert, liefere mir diesen (z.B. bei Array)
- Key Selectors
  - DistinctBy
    - Für jeden eindeutigen Wert eines bestimmten Attributs, liefere mir ein zufällig gewähltes Beispiel
  - MaxBy
    - Ein Beispiel für den maximalen Werte eines bestimmten Attributs
- Chunk
  - siehe oben
- Zip
  - Führt zwei Enumerables zusammen, 1 zu 1, 2 zu 2, usw.
  - Hört auf, sobald eine Enumerable zuende ist

### Weitere Neuerungen
- DateOnly
  - Nur das Datum
- TimeOnly
  - Nur die Zeit
- Weder DateOnly noch TimeOnly können derzeit mit dem JsonGenerator verwendet werden


