---
title: "Gickup - Backup für GitHub, Gitea und co."
tags:
- Backup
---

## Einleitung
[Gickup](https://github.com/cooperspencer/gickup) ist eine Möglichkeit ein Backup seiner Git Repositories zu erstellen. Dabei können Repositories von bspw. GitHub, GitLab, Gitea, oder auch Gogs gesichert werden. Dabei können die Repositories von Plattform zu Plattform synchronisiert werden. So habe ich meine Repositories von GitHub zu einer Self-Hosted Gitea Instanz gesichert. 
In diesem Artikel wird kurz beschrieben, wie so etwas erreicht werden kann. 

>[!INFO] Voraussetzung!
>
> Vorausgesetzt wird eine funktionierende Gitea Instanz!

## Konfiguration

### Gickup Installation
Gickup kann als Binary oder Docker-Compose ausgeführt werden. Dabei kann es sowohl unter Windows als auch Linux ausgeführt werden. Ich verwende die Linux Binary. 

Das folgende Skript kann genutzt werden, um die aktuellste Version herunterzuladen. Dabei wird die aktuelle amd64 Linux Binary unter `/root/gickup` heruntergeladen.
```bash {title="update-gickup.sh"}
#!/bin/bash
gickup_type=linux_amd64
URL=$(curl -s https://api.github.com/repos/cooperspencer/gickup/releases/latest | jq -r ".assets[] | select(.name | test(\"${gickup_type}\")) | .browser_download_url")

wget $URL
tar -xf *linux_amd64.tar.gz
rm "/root/gickup"/*linux_amd64.tar.gz
```

---

Um nun die Binary von überall auszuführen, muss der Pfad zur Binary zum `$PATH` hinzugefügt werden.
```bash
PATH=$PATH:/root/gickup
```
---

Testweise kann `gickup --version` ausgeführt werden. Ist alles korrekt konfiguriert, wird die aktuelle Version angezeigt.

![[notes/images/Gickup-Version.png]]

### Gickup YAML Konfiguration
Zur Konfiguration welche Source und Destination Plattform genutzt werden soll, anders gesagt von wo nach wo die Repos gesichert werden sollen, wird eine YML Konfigurationsdatei genutzt welche in die Binary gefüttert werden muss. Dabei kann die Konfigurationsdatei wie folgt aussehen:
 ```yaml {title="gickup-config.yml"}
 source:
  github:
    - token: ****************
      #user: gremi-jr
      #url: https://github.com
      ssh: true # can be true or false
      sshkey: /path/to/key # if empty, it uses your home directories' .ssh/id_rsa
destination:
  gitea:
    - token: ******************
      url: http://url-to-gitea-instance:3000
 ```

Wenn in der Konfigurationsdatei kein Benutzer angegeben wurde, werden alle Repositories des Benutzers gesichert. **Dies beinhaltet auch Forks oder Repos auf die der Benutzer berechtigt ist!**
Ein Token ist ebenfalls nur notwendig, wenn private Repositories gesichert werden sollen. Für öffentliche Repos ist dies nicht notwendig.

Die Konfiguration der einzelnen Parameter kann in der Gickup Doku unter [diesem Link](https://cooperspencer.github.io/gickup-documentation/docs/configuration/) nachgeschlagen werden.

## Periodische Ausführung
Wenn man nun möchte das bspw. jede Nacht  die neuesten Repositories gesichert werden, so kann man einfach im crontab folgende Zeile hinzufügen.
Öffne den Contab via `contrab -e`.
```bash
0 2 * * * /root/gickup/gickup /root/gickup/gickup-config.yml >> /root/gickup/gickup-backup.log 2>&1
```
Dabei wird jede Nacht um 2 Uhr das Backup ausgeführt und **ein Log nach gickup-backup.log** geschrieben.

