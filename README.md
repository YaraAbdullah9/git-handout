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

_Dieser Abschnitt wird noch ergänzt._

---

## 4. Git mit IntelliJ/PyCharm

_Dieser Abschnitt wird noch ergänzt._

---

## 5. Nützliche Git-Tools und Plattformen

_Dieser Abschnitt wird noch ergänzt._

---

## 6. Entstehung und Beiträge

_Dieser Abschnitt wird noch ergänzt._
