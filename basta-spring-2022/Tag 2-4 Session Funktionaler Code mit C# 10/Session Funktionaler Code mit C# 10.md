Functional Code in C#10 and beyond
==================================

Links
-----
- https://oliversturm.github.io/functional-cs10/slides.pdf (Slides)
- https://github.com/oliversturm/functional-cs10-samples (Code)
- https://github.com/oliversturm/FCSlib (FCSlib)

What's FP in C#?
----------------
- functions are the building blocks of the language
- Currying
  - Funktion zurück geben, bei der der Parameter der Eingabe-Funktion an einen Wert gebunden ist
- Komposition
  - neben Currying zweite wichtige Technik

Monads
------
- Handhabung von Seiteneffekten
- Pure Funktion
  - Nimmt Parameter entgegen
  - Gibt Ergebnis zurück
- Parallelisierbarkeit mit puren Funktionen gut erreichbar
- Haskell schreibt pure Funktionen vor
  - Es sei denn, man schreibt einen bestimmten Kontext für die Ausführung vor
- Ein Monad erfüllt folgende Bedingungen:
  - Kapselt Wert und versieht diesen mit zusätzlichen Informationen
  - Definiert Operationen auf dem Wert. Anwendung der Operation liefert neuen Monad.
