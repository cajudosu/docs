BASTA! Keynote
==============

Sebastian Meyen
---------------
- .NET 6 ist da
- jährlicher Release-Zyklus
- Zielsetzung:
  - Was ist mit aktuellen Technologien mögich, was vorher nicht möglich war?
  - Was ist mit neuen Technologien nun besser möglich als vorher?

Christian Nagel
---------------
- 20 Jahre .NET und C#
- Was hat sich seit dem geändert?
  - Requirements
    - Beispiele:
      - Neuer Lieferservice
      - Impfpflicht Österreich
    - Möglich mit
      - Continuous Integration
    - Generell wird nach schnellen Lösungen gesucht
  - Darstellung am Code
    - Main-Methode
      - Dependency Injection
      - Controller
      - Konfiguration
      - API mit Swagger
    - Vereinfachungen durch
      - Top Level Statments
      - Global Usings
      - Implicit Usings
        - Bestimmte Namespace in Abhängigkeit des SDKs werden importiert
      - FAZIT: Vieles ist soviel einfacher
        - Current version benutzen, integriert schneller Features, die die Lösung gewisser Aufgaben beschleunigen
        - LTS für längere Release-Zyklen

Dr. Holger Schwichtenberg
-------------------------
- Entity Framework 6
- Verbesserungen im Bereich Reverse Engineering
  - Abastraktion von N:M-Zwischentabellen
- Compiled Models
  - Beschleunigt den Anwendungsstart
- Undo-Funktion über temporale Tabellen
  - POCO-Klasse (plain old class object ???)
- OR-Mapper
  - Wird dieser bei Billbee auch genutzt?
- Migration Bundles
  - .exe-Datei für Schemamigrationen
- .NET EF Core 6.0 läuft nur auf .NET6
- Es gibt noch andere OR-Mapper z.B. von DevExpress

Christian Weyer
---------------
- Blazor
- WebAssembly Deployment Layout (WASM)
  - DLLs werden in Browser geladen und ausgeführt
  - Binärdaten werden durch Firewall/Virenscanner blockiert
- Native Dependencies (WASM)
  - Ausführen von externen Bibliotheks-Funktionen z.B. erzeugt aus RUST-Code
- Ahead-of-Time (AoT)-Kompilierung
- DLLs werden im Browser ausgeführt ???
  - Braucht man dafür eine spezielles Plugin??
- Multi-threading für Blazer Web Assembly wird kommen
  - Für Browser, die es unterstützen

Rainer Stropek
--------------
- Cloud Readiness
- vor 20 Jahren war .NET = Windows
  - C++, Visual Basic, Java
- Die Situation ist heute von Grund auf anders
- Protokolle
  - HTTP
  - OPENAPI
  - SignalR
  - gRPC
  - GraphQL
    - Lib: Hot Chocolate
  - AMQT
  - MQTT
  - OpenID
  - OpenTelemetry
- .NET ist eine opinionate Plattform
  - Durch Unterstützung für bestimmte Protokolle wird sanft gelenkt
  - Diese Lenkung führt zu Anwendunge, die besonders gut auf Azure Cloud laufen
- Packaging und Runtimes
  - Docker
    - Microsoft wartet mittlerweile eigene Docker-Images
  - Kubernetes
  - Dapr
    - wird von MS vorangetrieben
  - WS (web assembly)
