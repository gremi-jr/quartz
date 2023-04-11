---
title: "AppData"
tags:
- Windows
---

Der AppData Ordner ist innerhalb des [[notes/Technik/Windows/Windows 10|Windows Betriebssystems]] in deinem [[Windows User Profile]] angesiedelt. Dieser Ordner ist ein versteckter Ordner (Hidden Folder).
**Er wird vorallem von Programmen genutzt um weitere Dateien abzulegen die dann vom Programm genutzt werden.** Allerdings sind sie nicht Teil der Installationsdateien die in C:\\ProgramFiles abgelegt werden.
Jetzt kann man sich die berechtigte Frage stellen, warum die Dateien nicht auch innerhalb den ProgramFiles abgelegt werden, wenn sie doch zum Programm gehören. 
**Viele Programme speichern Benutzereinstellungen in einer Datei (oder mehreren) im AppData Ordner**, da jeder seinen eigenen besitzt. Dies vereinfacht die Handhabung von Benutzereinstellungen enorm. Außerdem haben Benutzer in der Regel keine Rechte um in den ProgramFiles Ordner zu schreiben, welches dann das speichern von Benutzereinstellungen unmöglich macht.

Viele Programme bieten auch eine Benutzerinstallation an. Bei der Installation wird dann abgefragt ob es "nur für diesen Benutzer" installiert werden soll oder für das gesamte System. Dann wird das Programm nur in dem AppData Ordner installiert anstatt im ProgramFiles.

Der AppData Ordner wird nochmals in drei weitere Unterordner (Local, Locallow, Roaming) unterschieden. Dabei entscheidet der Entwickler des Programmes was in welchem Ordner geschrieben wird, wobei es für die unterschiedlichen Ordner unterschiedlichen Anwendungsfälle gibt. 

![[notes/images/AppData.png]]

## Local
Innerhalb des Local Ordner befinden sich alle Dateien die auch nur auf diesem Ordner bleiben (sollen). In der Regel werden dort auch größere Dateien gespeichert, da es schwieriger ist sie zu synchronisieren. Dieser Unterordner ist durch die Umgebungsvariable %localappdata% erreicht werden.

## Locallow
Der Locallow Ordner hat den gleichen Zweck die der Local Ordner, allerdings ist dieser für Programme mit dem "[[notes/Technik/Windows/Windows Integrity Level#Low|Low Integrity Level]]" vorgesehen. 

## Roaming
Der Roaming Ordner wird als Standard AppData Ordner erachtet, deshalb führt die %appdata% Umgebungsvariable direkt zum Roaming Ordner. 
Neben den oben aufgelisteten Verwendungszwecken, wird dieser Ordner im Rahmen von bspw. Roaming User Profiles synchronisiert. 
Dabei wird der Roaming Ordner auf einem Server synchronisiert und sobald der Benutzer seinen Computer wechselt, wird der Roaming Ordner auf dem neuen Computer kopiert. Auch wenn dieser Anwendungsfall eher in Rahmen von Unternehmensumgebungen, gibt es dem Roaming Ordner unabhängig davon ob es ein Domain Computer ist oder nicht. So kann der Roaming Order sofort synchronisiert werden, wenn dieser in einer Umgebung mit Roaming User Profiles hinzugefügt wird.



---
# References
[What Are the Different Windows "AppData" Folders for, Anyway? - YouTube](https://www.youtube.com/watch?v=3XjSTG-oIMw)