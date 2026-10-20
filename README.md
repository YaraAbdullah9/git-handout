# Git-Handout für Einsteiger:innen

Dieses Handout erklärt die wichtigsten Grundlagen von Git: was Git ist, welche Befehle man im Alltag braucht, wie man mit Branches und Merge-Konflikten umgeht, wie Git in IntelliJ/PyCharm funktioniert und welche Tools und Plattformen hilfreich sind.

## Inhalt

1. [Was ist Git und warum sollte man es verwenden?](#1-was-ist-git-und-warum-sollte-man-es-verwenden)
2. [Grundlegende Git-Befehle](#2-grundlegende-git-befehle)
3. [Branches und Merge-Konflikte](#3-branches-und-merge-konflikte)
4. [Git mit IntelliJ/PyCharm](#4-git-mit-intellijpycharm)
5. [Nützliche Git-Tools und Plattformen](#5-nützliche-git-tools-und-plattformen)
6. [Entstehung und Beiträge](#6-entstehung-und-beiträge)

---

## 1. Was ist Git und warum sollte man es verwenden?

Git ist ein **verteiltes Versionskontrollsystem**. Es speichert den Verlauf aller Änderungen an Dateien eines Projekts, sodass man jederzeit nachvollziehen kann, wer wann was geändert hat, und bei Bedarf zu früheren Ständen zurückkehren kann. Git wurde 2005 von Linus Torvalds für die Entwicklung des Linux-Kernels entwickelt und ist heute der Standard in der Softwareentwicklung.

„Verteilt“ bedeutet: Jede Person hat eine vollständige Kopie des Repositorys inklusive der gesamten Historie auf ihrem Rechner. Man kann also auch offline arbeiten und committen.

### Wichtige Begriffe

| Begriff | Bedeutung |
|---|---|
| **Repository (Repo)** | Projektordner, dessen Änderungen von Git verwaltet werden (enthält den versteckten Ordner `.git`) |
| **Commit** | Gespeicherter „Schnappschuss“ des Projekts mit Beschreibung, Autor:in und Zeitstempel |
| **Branch** | Unabhängige Entwicklungslinie, z. B. für ein neues Feature |
| **Remote** | Entferntes Repository, z. B. auf GitHub (Standardname: `origin`) |
| **Merge** | Zusammenführen von zwei Branches |
| **Pull Request (PR)** / **Merge Request (MR)** | Anfrage auf einer Plattform, Änderungen eines Branches in einen anderen zu übernehmen, inklusive Review |

### Die drei Bereiche von Git

```
 Working Directory  ──git add──▶  Staging Area  ──git commit──▶  Lokales Repository  ──git push──▶  Remote (GitHub)
   (Dateien, an                   (vorgemerkte                    (gespeicherte                     (gemeinsames
    denen man arbeitet)            Änderungen)                     Commits)                          Repository)
                       ◀──────────────────────────── git pull ─────────────────────────────────────
```

### Warum Git?

- **Nachvollziehbarkeit:** Jede Änderung ist dokumentiert und kann rückgängig gemacht werden.
- **Zusammenarbeit:** Mehrere Personen können gleichzeitig am selben Projekt arbeiten, ohne sich gegenseitig Dateien zu überschreiben.
- **Paralleles Arbeiten:** Mit Branches lassen sich Features, Bugfixes und Experimente getrennt entwickeln.
- **Sicherheit:** Durch Remote-Repositorys gibt es automatisch eine Sicherungskopie.
- **Industriestandard:** Git wird in nahezu allen Softwareprojekten eingesetzt.

> **Git ≠ GitHub:** Git ist das Programm zur Versionskontrolle auf dem eigenen Rechner. GitHub (oder GitLab, Bitbucket) ist eine Plattform, auf der Git-Repositorys gehostet und gemeinsam bearbeitet werden.

---

## 2. Grundlegende Git-Befehle

### Einmalige Einrichtung

```bash
git config --global user.name "Vorname Nachname"
git config --global user.email "name@example.com"
git config --global init.defaultBranch main
git config --list          # Einstellungen prüfen
```

### Die wichtigsten Befehle

| Befehl | Beschreibung |
|---|---|
| `git init` | Neues Repository im aktuellen Ordner anlegen |
| `git clone <URL>` | Bestehendes Remote-Repository herunterladen |
| `git status` | Zeigt geänderte, vorgemerkte und neue Dateien |
| `git add <datei>` | Datei für den nächsten Commit vormerken (`git add .` = alle Änderungen) |
| `git commit -m "Nachricht"` | Vorgemerkte Änderungen als Commit speichern |
| `git log --oneline` | Kompakte Übersicht der Commit-Historie |
| `git diff` | Zeigt noch nicht vorgemerkte Änderungen |
| `git push` | Lokale Commits ins Remote-Repository hochladen |
| `git pull` | Änderungen vom Remote holen und einarbeiten (= `fetch` + `merge`) |
| `git fetch` | Änderungen vom Remote holen, ohne sie einzuarbeiten |
| `git restore <datei>` | Ungespeicherte Änderungen an einer Datei verwerfen |
| `git restore --staged <datei>` | Datei aus der Staging Area entfernen (Änderung bleibt erhalten) |
| `git revert <commit>` | Neuen Commit erstellen, der einen alten Commit rückgängig macht |

### Typischer Ablauf

```bash
git clone https://github.com/team/git-handout.git
cd git-handout
# ... Dateien bearbeiten ...
git status
git add README.md
git commit -m "Abschnitt zu Git-Grundbefehlen ergänzt"
git push
```

### Tipps für gute Commit-Messages

- Kurz und aussagekräftig (ca. 50 Zeichen), im Imperativ oder als Beschreibung: `Tabelle mit Grundbefehlen ergänzt`
- Ein Commit = eine logische Änderung
- Nicht: `update`, `fix`, `asdf`

### Die Datei `.gitignore`

In der `.gitignore` steht, welche Dateien Git ignorieren soll, z. B. IDE-Einstellungen (`.idea/`), Build-Ordner (`target/`, `build/`), virtuelle Umgebungen (`.venv/`) oder Passwörter/Konfigurationsdateien (`.env`).

```gitignore
.idea/
__pycache__/
.venv/
.env
```

---

## 3. Branches und Merge-Konflikte

### Was sind Branches?

Ein Branch ist eine eigene Entwicklungslinie. Der Haupt-Branch heißt meist `main` (früher `master`). Neue Features oder Änderungen entwickelt man in einem separaten Branch und führt sie erst nach Fertigstellung und Review in `main` zusammen. So bleibt `main` stabil.

```
main:        A───B───────────E (Merge)
                  \         /
feature/x:         C───D───
```

### Wichtige Branch-Befehle

| Befehl | Beschreibung |
|---|---|
| `git branch` | Alle lokalen Branches anzeigen (`-a` inklusive Remote) |
| `git switch -c feature/x` | Neuen Branch anlegen und wechseln (älter: `git checkout -b`) |
| `git switch main` | Zu einem Branch wechseln |
| `git merge feature/x` | Branch `feature/x` in den aktuellen Branch übernehmen |
| `git push -u origin feature/x` | Branch erstmals hochladen und mit Remote verknüpfen |
| `git branch -d feature/x` | Branch nach dem Merge löschen |

### Namenskonventionen

- `feature/<beschreibung>` für neue Inhalte, z. B. `feature/grundbefehle`
- `fix/<beschreibung>` für Korrekturen
- `docs/<beschreibung>` für Dokumentation

### Merge-Konflikte

Ein Merge-Konflikt entsteht, wenn zwei Branches **dieselbe Stelle derselben Datei** unterschiedlich geändert haben. Git kann dann nicht automatisch entscheiden, welche Version richtig ist, und markiert die Stelle:

```text
<<<<<<< HEAD
Git ist ein verteiltes Versionskontrollsystem.
=======
Git ist ein Werkzeug zur Versionsverwaltung.
>>>>>>> feature/einleitung
```

- Zwischen `<<<<<<< HEAD` und `=======` steht die Version des aktuellen Branches.
- Zwischen `=======` und `>>>>>>>` steht die Version des Branches, der hineingemergt wird.

### Konflikt lösen

1. `git status` zeigt die betroffenen Dateien.
2. Datei öffnen, die gewünschte Version behalten (oder beide kombinieren) und **alle Markierungen entfernen**.
3. Gelöste Datei vormerken und Merge abschließen:

```bash
git add README.md
git commit -m "Merge-Konflikt in Einleitung gelöst"
```

Falls man den Merge abbrechen möchte: `git merge --abort`

### Konflikte vermeiden

- Vor dem Arbeiten immer `git pull` auf `main` ausführen.
- Kleine, häufige Commits statt großer Änderungen.
- Im Team absprechen, wer welche Datei bzw. welchen Abschnitt bearbeitet.
- Den eigenen Branch regelmäßig mit `main` aktualisieren: `git merge main`

---

## 4. Git mit IntelliJ/PyCharm

IntelliJ IDEA und PyCharm (beide von JetBrains) haben eine eingebaute Git-Integration. Die meisten Befehle lassen sich per Mausklick ausführen. *(Menünamen können je nach Version und „New UI“/„Classic UI“ leicht abweichen.)*

### Lokales Repository

**Neues Repository anlegen:**
`VCS` → `Create Git Repository…` (bzw. `Enable Version Control Integration`) → Projektordner auswählen. Das entspricht `git init`.

**Änderungen committen:**
- Commit-Fenster öffnen: `Ctrl + K` (macOS: `Cmd + K`)
- Dateien auswählen (entspricht `git add`), Commit-Message eingeben, auf **Commit** klicken.
- Geänderte Dateien werden farbig markiert: **blau** = geändert, **grün** = neu, **rot** = nicht versioniert.

**Historie ansehen:**
Git-Tool-Window öffnen: `Alt + 9` (macOS: `Cmd + 9`) → Reiter **Log**. Hier sieht man alle Commits und Branches grafisch.

**Branches:**
Über das Branch-Widget (New UI: oben links neben dem Projektnamen, Classic UI: unten rechts in der Statusleiste) → `New Branch…`, Branch wechseln (`Checkout`) oder mergen (`Merge into Current`).

### Remote Repository

**Bestehendes Repository klonen:**
`File` → `New` → `Project from Version Control…` (oder auf dem Startbildschirm **Get from VCS**) → URL einfügen → **Clone**.

**GitHub-Konto verbinden:**
`Settings` → `Version Control` → `GitHub` → **+** → mit GitHub anmelden.

**Remote hinzufügen:**
`Git` → `Manage Remotes…` → URL des Repositorys eintragen (entspricht `git remote add origin <URL>`).

**Pushen und Pullen:**
- Push: `Ctrl + Shift + K` (macOS: `Cmd + Shift + K`) bzw. im Commit-Fenster **Commit and Push**
- Pull/Update: `Ctrl + T` (macOS: `Cmd + T`) → **Update Project**

**Projekt direkt auf GitHub veröffentlichen:**
`Git` → `GitHub` → `Share Project on GitHub`

### Merge-Konflikte in der IDE

Bei einem Konflikt öffnet die IDE einen Dialog mit den betroffenen Dateien. Optionen:
- **Accept Yours:** eigene Version übernehmen
- **Accept Theirs:** fremde Version übernehmen
- **Merge…:** dreigeteilte Ansicht (links eigene Version, rechts fremde Version, Mitte Ergebnis), in der man Änderungen einzeln per Pfeil übernehmen kann

### Pull Requests in der IDE

Mit verbundenem GitHub-Konto gibt es das Tool-Window **Pull Requests**, in dem man PRs erstellen, ansehen, kommentieren und reviewen kann, ohne den Browser zu öffnen.

---

## 5. Nützliche Git-Tools und Plattformen

### Hosting-Plattformen

| Plattform | Besonderheiten |
|---|---|
| **GitHub** | Größte Plattform, Pull Requests, Issues, GitHub Actions (CI/CD), GitHub Pages, kostenloses Student Developer Pack |
| **GitLab** | Merge Requests, starke integrierte CI/CD-Pipelines, auch selbst hostbar |
| **Bitbucket** | Gute Integration mit Jira und anderen Atlassian-Tools |

---

## 6. Entstehung und Beiträge

_Dieser Abschnitt wird noch ergänzt._
