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

_Dieser Abschnitt wird noch ergänzt._

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
