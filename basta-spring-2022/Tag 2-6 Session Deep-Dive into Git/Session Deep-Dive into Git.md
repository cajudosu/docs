# Session Deep-Dive into Git

## Links
- https://github.com/wulfland/DeepDive (Code)

## Materialien
- Git für Dummies
- GitPro Buch (umsonst, E-Book)

## 3 things to know
- Git uses Hashes
- Everything is a graph
- Git saves snapshots and not changes

```sh
git hash-object file.txt
```

- `watch` and `tree` um Ordnerinhalt anzuzeigen
- .git/HEAD beinhaltet Branch in dem ich gerade bin
- kann auch Hash für Commit beinhalten

```sh
git add file.txt
```

- Fügt eine Datei im Ordner `objects` hinzu
- `git diff` vergleicht echte Datei mit Datei im Object-Store
- `git commit` sorgt für viele neue Dateien in objects

```sh
git cat-file -p e08d
```

- Zeigt Inhalt der Datei mit diesem Hash (`-p` für pretty)

##  Patches

**Pro Commit Patch-Dateien erzeugen**

```sh
git format-patch HEAD~2..HEAD
```

```sh
git reset HEAD~2 --hard
```

```sh
git apply foo-bar.patch
```

## Working with your history

**Änderungen dem letzten Commit hinzufügen ohne neuen Commit zu erzeugen**

```sh
git commit --amend
```

- Git wirft nichts weg

**Zeige alle Commits an, die jemals ausgeführt wurde**

```sh
git reflog
```

- Das Reflog ist ausschließlich lokal
- Löschen des .git-Verzeichnisses löscht dieses

**Einen Commit rauspicken und an anderer Stelle anwenden**

```sh
git cherry-pick 2ds9
```

**Rebase vom Wurzel-Commit (??)**

```sh
git rebase -i --root
```

- Beim Rebase hat man die Möglichkeit bestimmte Commits abzuändern. Die Historie wird dann komplett neue generiert. Sind es Commits inmitten der Historie werden sich die Hash-Werte ab dem geänderten Commit ändern.
  
## Hunks

**Selektieren, welche Änderungen INNERHALB der Datei in dem Commit sein sollen**

```sh
git add index.html -p
```

- Hunks werden leider von den meisten Editoren nicht unterstützt.



