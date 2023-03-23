---
title: "Windows 10"
tags:
- Windows
---

Windows 10 ist ein Microsoft Betriebssystem, welches zu den *[[Mehrbenutzerbetrieb#Halbe Mehrbenutzerbetriebssystem|halben Multi-User-Betriebssystemen]]* zählt. 

## User
- Wenn ein neuer Benutzer über "New-LocalUser -NoPassword" angelegt wird, dann muss er immer beim **nächsten Login Standardmäßig sein Passwort ändern/setzen**
- Gast Account ist deprecated - sollte nicht mehr genutzt werden
	- Egal welche Rollen der Gast Account noch hat - **nach dem Ausloggen wird er gelöscht**

### Built in Group
- **Power Users**: Keine keine besonderen oder **mehr** Recht als ein **normaler Benutzer** - eher Richtung legacy, Stand heute nicht mehr relevant bzw. als normaler Benutzer zu betrachten
- **Network Configuration Operators**: Können Änderungen im Netzwerkeinstellungen bzw. TCP/UDP machen und Releases von IP Addressen erneuern
- **Performance Log Users**: Verwalten von Performance Counters, Logs und Alters (**remote** und lokal)
- **Performance Monitor Users**:  Monitor Performance Counters (**remote** und lokal)
- **Backup Operators**: Können Backup von Dateien machen und diese **wiederherstellen** - **unabhängig von den Rechten** auf den Dateien. Kann keine Security Settings ändern
	- **Keine Restore Points** - Nur File History?

## Administrator
- Standardmäßig ist die User Account Control auf "Consent" (Ja/Nein) ausgelegt
- Geräte-Manager kann ohne Consent geöffnet werden

## Support
- Alle Versionen haben einen Supportzeitraum von **18 Monaten** 
	-  **Enterprise und Education** haben 12 mehr = **30 Monate** insgesamt

## [[notes/Technik/Windows/Windows Updates]]
### Feature Updates
- Feature Updates können **maximal 10 Tage** nach der Installation deinstalliert werden

## Backup
- System Image inkludiert **alle Festplatten** und ist ein exaktes Abbild des Systems
	- System Image kann in Windows 10 über **Backup and Restore (Windows 7)** gemacht werden


## Sperrbildschirm
- Wenn man ein Android Handy hat, können über die Dynamic Lock Settings und dem verbundenen Handy den Bidlschrim sperren


## Aktivierung
- slmgr = System License Manager Command


## Features
- Windows **Features wie Hyper-V** können über **dism** oder eine **Unattend.xml** aktiviert/installiert werden

## Logging
### Boot Logging
- **Boot Logging** kann über MSConfig.exe aktiviert werden (Standardmäßig aus) und wird unter **C:\\Windows gespeichert** 

## Dienste
- Wenn ein Dienst mit Startup Type "**Automatic**" abhängig von einem **manuellen** Startup Dienst ist, wird dieser **automatisch mit gestartet**


## Boot
- Jede Festplatte mit dem OS darauf hat bestimmte Partitionen und Konfigurationen
- **MBR / GPT** ist verantwortlich für die Partition und wie etwas partitioniert wird 
	- MBR ist älter und kann nur bis 2 TB 
	- GPT ist neuer in kann Partitionen bis in die Exabytes Bereiche erstellen
- **Bootsector** sagt aus das die Partition gestartet (boot) werden kann
- **Boot Configuration Data** = Konfiguration des eigentlichen Boot hergang, verwaltet auch bspw Dualboot mit einem Menü
- **Boot Manager** ist ein kleines Programm welches nur dafür da ist Windows bzw den Boot Loader zu starten
- **Boot Loader** ist das eigentliche Betriebssystem 
![[notes/images/Windows10-Boot.png]]