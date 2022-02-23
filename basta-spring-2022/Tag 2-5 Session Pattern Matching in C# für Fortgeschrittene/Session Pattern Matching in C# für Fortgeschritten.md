Session Pattern Matching in C# für Fortgeschrittene
===================================================

- C#7
  - `value is Type t` also in `switch`
- C#8
  - `switch` expressions
  - property
  - tuple
  - positional patterns
  - deconstructor
- C#9
  - local operators in patterns
    - and, or, not
  - relational operators

- Example pattern in `switch` statement:

```csharp
class DeadPerson : Person {
	public bool isAlive = false;
}
class Zombie : Person {
	public bool isAlive = true;
}

Person p = new Zombie();
switch (p) {
	case Zombie z:
	  ...
	  break;
	case Deadperson dp:
	  ...
	  break;
}
```

- Pattern matching for deconstructable types
