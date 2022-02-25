Tutorials
=========

Aufgaben-Bearbeitung vorbereiten
--------------------------------
### Billbee.TestingTool installieren
- Billbee.TestingTool.zip in das Wurzel-Verzeichnis des Billbee-Repos kopieren und entpacken
- In Billbee.TestingTool die Solution Billbee.TestingTool.sln öffnen
- In Branch `#177775440_Create_testing_library` wechseln

Aufgabe bearbeiten
------------------

### 1\. Aufgabe vestehen
- Aufgabe im TFS durchlesen
- Verlinkte Aufgabe mit HelpScout durchlesen
- Fehlerfall nachstellen mit dem Billbee.TestingTool

### 2\. Teil-Aufgaben anlegen
- Aufgabe analysieren und in Teil-Aufgaben Teil-Aufgaben zerlegen
- Teil-Aufgaben im TFS anlegen
- Jede Teil-Aufgabe mit einer aussagekräftigen Beschreibung versehen

### 3\. Vorbereitung zum Bearbeiten der Teil-Aufgaben
- `master`-Branch auschecken und pullen

```sh
git checkout master;
git pull;
```

- Test-Lib-Branch auschecken und pullen

```sh
git checkout '#177775440_Create_testing_library';
git pull;
```

### 4\. Teil-Aufgaben bearbeiten
- Teil-Aufgaben nacheinander abarbeiten
- Wenn eine neue Teil-Aufgabe begonnen wird, deren Status auf _In Bearbeitung setzen_
- Bei Beginn der ersten Teil-Aufgabe außerdem das Haupt-Ticket auf _In Umsetzung_ stellen
- Wenn Teil-Aufgabe erledigt ist, diese auf _Erledigt_ setzen

### 5\. Code-Änderungen committen + pushen
- `master`-Branch auschecken und ggf. nochmal pullen

```sh
git checkout master;
git pull;
```
- Vom `master` einen neuen Feature-Branch erstellen

```sh
git branch '#855_this_is_my_super_cool_bugfix'
```

- Dabei ist `#855` die Ticket-Nummer aus dem TFS und der rest eine kurze Beschreibung auf **English**.

- Neuen Branch auschecken

```sh
git checkout '#855_this_is_my_super_cool_bugfix'
```

- Neuen Branch pushen

```sh
git push --set-upstream origin '#855_this_is_my_super_cool_bugfix'
```
### 6\. Pull Request anlegen
- In TFS wechseln
- Der neue Feature-Branch wird bereits unter Branches im TFS angezeigt und die Erstellung eines Pull Requests wird angeboten
- Pull Request erstellen
- Als Titel des Pull Requests den Namen des Feature Branches wählen z.B.

```
#1995_payment_type_mapping_shopify_mollie
```

- (Dieser kann aus der URL im Browser kopiert werden)
- Beschreibung des Feature Branches kann auf Beschreibung des Commits belassen werden
- WICHTIG: TFS-Ticket als verknüpfte Arbeitselemente hinzufügen
- Pull Request speichern (auf OK / Speichern klicken)

### 7\. Changelog-Eintrag setzen
- Zurück zum Arbeitselement wechseln und Changelog-Eintrag ausfüllen
- Changelog-Eintrag nach folgendem Format schreiben: <Type-Prefix>-<Titel>-<kurze pregnante Beschreibung>
  - Folgende Type-Prefixes gibt es
    - `Fix` ist die Behebung eines Fehlers/Bugs
    - `Feature` ist eine neue Funktion/ein neues Feature

### 8\. Aufgabe abschließen
- Status der Haupt-Aufgabe auf `Umgesetzt` stellen
- Noch einmal kontrollieren das alle Unter-Aufgaben auf `Erledigt` gesetzt sind

