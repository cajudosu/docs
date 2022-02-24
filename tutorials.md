Tutorials
=========
## Entwicklungs-Aufgabe bearbeiten
-------------------------------
- Aufgabe wird im TFS zugewiesen
- Weiter Informationen sind im evtl. im HelpScout zu finden
  - Link zum HelpScout Ticket unter _Links_ im TFS
- Sobald Aufgabe bearbeitet wird den Status der Aufgabe auf _In Umsetzung_ stellen
- Für jede Unteraufgaben, die begonnen wird den Status auf _In Bearbeitung_ stellen
 
### Feature Branch erstellen
- Feature-Branch erstellen vom Master
- Änderungen in Feature-Branch committen
- Feature-Branch pushen
- In TFS wechseln -> Neue Feature-Branch wird bereits im TFS angezeigt und die Erstellung eines Pull Requests wird angeboten
- Pull Request erstellen
- Als Titel des Pull Requests den Namen des Feature Branches wählen z.B. `#1995_payment_type_mapping_shopify_mollie`
- Beschreibung des Feature Branches kann auf Beschreibung des Commits belassen werden
- WICHTIG: TFS-Ticket als verknüpfte Arbeitselemente hinzufügen
- Pull Request speichern (auf OK / Speichern klicken)
- Zurück zum Arbeitselement wechseln und Changelog-Eintrag ausfüllen
- Changelog-Eintrag nach folgendem Format schreiben: <Type-Prefix>-<kurze pregnante Beschreibung>
  - Folgende Type-Prefixes gibt es
    - `Fix` ist die Behebung eines Fehlers/Bugs
    - `Feature` ist eine neue Funktion/ein neues Feature
- Status der Haupt-Aufgabe auf `Umgesetzt` stellen (natürlich nur wenn die gesamte Haupt-Aufgabe gelöst ist)
- Status der Unter-Aufgaben auf `Erledigt` setzen
