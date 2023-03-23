---
title: "AppData"
tags:
- Windows
---

- Ordner im [[Windows User Profile]] innerhalb von [[notes/Technik/Windows/Windows 10]] oder auch 11  
- Hidden Folder
- Wird benutzt von Programmen um weitere Dateien abzulegen die dann genutzt werden, allerdings nicht Part von der Installation Files sind
- Warum nicht innerhalb von ProgramFiles wenn es zu Programm gehört?
	- Einfachere Verwaltung von Usersettings innerhalb des Programms, da jeder User sein eigenen hat
	- Benutzer haben in der Regel keine Rechte um nach ProgramFiles zu schreiben
- Es ist möglich das gesamte Programm in AppData zu installieren anstatt in ProgramFiles. Das ist das wenn das Programm fragt "nur für mich installieren"
- Alle drei Unterordner machen im Prinzip das gleiche aber für unterschiedliche Anwendungsfälle
- Der Entwickler (vom Programm) entscheidet was in welchen Ordner geschrieben wird
	- Große Dateien werden in der Regel in Local gespeichert weils schwieriger ist diese zu synchronisieren
- Manche Programme packen diese Dateien in den Documents Folder weil der Benutzer diesen Ordner eher kennt.

## Local
- Für alle Dateien die Local bleiben
- Nur auf dem PC, nach dem löschen sind sie weg
- Erreichbar unter %localappdata%
## Locallow
- Gleich wie Local allerdings mit "[[notes/Technik/Windows/Windows Integrity Level#Low|Low Integrity Level]]"
## Roaming
- Werden bspw. bei Roaming Profiles mit auf andere Computer mitgenommen/synchronisiert
- Unabhänig des Gerätes worauf sich der Benutzer anmeldet
- Ordner gibt es unabhängig ob es ein Domain PC ist oder nicht
- %appdata% ist Roaming und wird als Standard erachtet


---
# References
[What Are the Different Windows "AppData" Folders for, Anyway? - YouTube](https://www.youtube.com/watch?v=3XjSTG-oIMw)